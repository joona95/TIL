# Sequelize 로 JSON 데이터 다루기

## 0. 문제

- 한 테이블 내의 JSON 데이터를 가진 컬럼 데이터에서 조건문 적용이 필요

```
people = [
    {
        name: "a",
        age: 20,
        sex: "F",
        height: 180,
    },
    {
        name: "b",
        age: 25,
        sex: "M",
        height: 160,
    },
    {
        name: "c",
        age: 20,
        sex: "F"
        height: 180,
    },
]
```

- 예를 들어 people 컬럼의 JSON 데이터들 중에서 여성인 데이터들만 가지고 오고 싶었음

```
[Op.and]: sequelize.literal(`people->"$.sex"='F'`),
```

- 처음 참고하던 이 문법은 Postgresql에서만 지원하는 JSONB를 위한 문법이었는데 현재 mariadb를 사용중이어서 sql syntax error 발생

```
where: {
    people: {
        '"sex"': params
    }
}
```
```
where: {
    people: {
        '"sex"': {
            $eq: params
        }
    }
}
```

- 두 번째로 참고하였으나 Invalid value Error 가 발생함

## 1. 해결

```
where: {
    [Op.and]: [sequelize.where(sequelize.fn('JSON_EXTRACT', sequelize.col('people'), sequelize.literal(`'$.sex'`)), params)]
}
```

- JSON_EXTRACT라는 function을 사용하여 해결

- sequelize.literal() 은 SQL injection을 막아주지 못하므로 쓸 때 유의할 필요가 있음. 지금은 입력값을 literal함수가 다루지 않기 때문에 상관없음.