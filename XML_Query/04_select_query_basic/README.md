# XML Query

<!-- index start -->

- [Quick Start](/XML_Query)
- [테이블 생성하기](/XML_Query/01_create_schema/)
- [테이블 변경하기](/XML_Query/02_alter_schema/)
- [XML 쿼리 기본](/XML_Query/03_xml_query/)
- [SELECT 쿼리 - 기본](/XML_Query/04_select_query_basic/)
- [SELECT 쿼리 - GROUP BY절](/XML_Query/05_select_query_with_groupby/)
- [SELECT 쿼리 - WHERE절](/XML_Query/06_select_query_with_where/)
- [SELECT 쿼리 - ORDER BY절](/XML_Query/07_select_query_with_navigation/)
- [SELECT 쿼리 - JOIN절](/XML_Query/08_select_query_with_join/)
- [SELECT 쿼리 - 서브쿼리](/XML_Query/09_select_query_with_subquery/)
- [INSERT 쿼리](/XML_Query/10_insert_query/)
- [UPDATE 쿼리](/XML_Query/11_update_query/)
- [DELETE 쿼리](/XML_Query/12_delete_query/)
- [XML 쿼리 실행하기](/XML_Query/13_execute_query/)

<!-- index end -->

## SELECT 쿼리 - 기본

XML 쿼리의 최상위 요소(element)는 `<query>`입니다.

`<query>` 요소는 속성(attribute)으로 `id`와 `action`을 가집니다. 각 속성은 쿼리의 id와 쿼리의 타입(select, insert, update, delete)을 나타냅니다.


### SELECT절

`<table>`요소는 FROM절을 구성합니다. 테이블을 지정합니다.

```
<query id="getMember" action="select">
    <tables>
        <table name="member" />
    </tables>
    <columns>
        <column name="*" />
    </columns>
</query>
```

```
SELECT * FROM member;
```

`<column>`요소를 사용하여 SELECT절을 구성합니다. 특정 컬럼만 조회할 수 있습니다.

```
<query id="getMember" action="select">
    <tables>
        <table name="member" />
    </tables>
    <columns>
        <column name="user_id" />
        <column name="nick_name" />
    </columns>
</query>
```

```
SELECT user_id, nick_name FROM member;
```

### alias 속성 사용하기

`alias` 속성을 이용하여 별칭을 지정할 수 있습니다. `table`, `column`, `query` 요소에서 사용할 수 있습니다.


```
<query id="getMember" action="select">
    <tables>
        <table name="member"  alias="m" />
    </tables>
    <columns>
        <column name="m.user_id" alias="uid" />
        <column name="m.nick_name" alias="nick" />
    </columns>
</query>
```

```
SELECT m.user_id AS uid, nick_name AS nick FROM member AS m;
```
