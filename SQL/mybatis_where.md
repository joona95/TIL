# Mybatis \<where> 문법

## 문제상황

```
<select id="getTest" resultType="testDto">

SELECT * FROM 테이블명
WHERE id = #{id} AND name = #{name}

</select>
```

- id가 null 이거나 name이 null 인 경우 "\<if test="조건">" 사용해서 WHERE 조건 제외하고 싶었음

- id와 name이 null인지 여부에 따라서 WHERE 과 AND 처리가 애매해짐

<br>

## 해결방안

```
<select id="getTest" resultType="testDto">

SELECT * FROM 테이블명

<where>
<if test="id!=null"> AND id = #{id} </if> 
<if test="name!=null"> AND name = #{name} </if>
</where>

</select>
```

- \<where> 문 사용하면 AND 나 OR 이 알아서 문법에 맞게 치환해줌

    - id!=null && name==null

        ```
        SELECT * FROM 테이블명 WHERE id = #{id}
        ```

    - id==null && name!=null

        ```
        SELECT * FROM 테이블명 WHERE name = #{name}
        ```

    - id!=null && name!=null

        ```
        SELECT * FROM 테이블명 WHERE id = #{id} AND name = #{name}
        ```
