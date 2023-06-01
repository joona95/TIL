# 계층적 매핑 resultMap

- JPA 사용 시 Entity 처럼 mybatis에서 도메인 객체에 매핑할 수 있는 방법이 없을까 고민

- \<resultMap> 은 SQL 외부에 정의된 태그로 SQL 조회 결과 데이터를 어떻게 매핑할지에 대한 제어 가능

- 종속적 데이터와 참조적 데이터에 대한 계층적 매핑 가능

```
<resultMap id="User" type="User">
    <id property="id" column="id" />
    <result property="passwd" column="passwd" />
    <result property="statusCd" column="statusCd" />
    <result property="name" column="name" />
    <result property="birth" column="birth" />
    <result property="gender" column="gender" />
    <result property="basePhone" column="basePhone" />
    <result property="regDTime" column="regDTime" />
    <result property="recentLoginDTime" column="recentLoginDTime" />
    <result property="updDTime" column="updDTime" />
    <association property="nickname" javaType="Nickname">
        <result property="nickname" column="nickname" />
    </association>
    <association property="email" javaType="UserEmail">
        <result property="email" column="email" />
    </association>
    <collection notNullColumn="imgId" property="images" javaType="ArrayList" ofType="Img" column="userId" >
            <id property="imgId" column="imgId" />
            <result property="userId" column="userId" />
            <result property="imgUrl" column="imgUrl" />
        </collection>
</resultMap>

<select id="findUserByUserId" resultMap="User">
...
</select>
```