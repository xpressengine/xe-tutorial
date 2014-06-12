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

## SELECT 쿼리 - ORDER BY절

XML 쿼리에서는 ORDER BY, OFFSET, LIMIT절 그리고 paging 처리를 위한 pagination을 구현하기 위해 `<navigation>` 요소를 사용합니다.

`<navigation>` 요소는 자식요소로 `<index>`, `<list_count>`, `<page_count>`, `<page>` 요소를 갖습니다.


ORDER BY절은 `<index>` 요소로 작성할 수 있습니다.

`<index>` 요소의 `var` 속성은 정렬 기준 컬럼명이 바인딩되는 변수명이며, `order` 속성은 정렬 차순(내림차순, 오름차순)이 바인딩되는 변수명입니다.

```
<query id="getMemberList" action="select">
    <tables>
        <table name="member" />
    </tables>
    <columns>
        <column name="*" />
    </columns>
    <conditions>
        <condition operation="equal" column="is_admin" var="is_admin" />
    </conditions>
    <navigation>
        <index var="sort_index" default="list_order" order="sort_order" />
        <list_count var="list_count" default="20" />
        <page_count var="page_count" default="10" />
        <page var="page" default="1" />
    </navigation>
</query>
```

```
SELECT * FROM member WHERE is_admin = ':is_admin' ORDER BY :sort_index :sort_order OFFSET 
-- ex) SELECT * FROM member WHERE is_admin = 'Y' ORDER BY user_id desc
```


> Note: XML 쿼리에서는 ORDER BY나 OFFSET, LIMIT절을 별도로 사용할 수 없습니다. `<navigation>` 요소를 통해 항상 동시에 사용됩니다.

## SELECT 쿼리 - OFFSET, LIMIT절 및 pagination

`<navigation>` 요소의 자식요소인 `list_count`, `page_count`, `page` 요소를 사용하여 작성됩니다.

각 요소의  `var` 속성은 변수바인딩, `default` 속성은 기본값을 지정합니다.

### list_count 요소

LIMIT절에 해당됩니다. result set의 row를 지정합니다.

### page_count 요소

pagination에서 출력될 페이지 수를 지정합니다.

### page 요소

pagination에서 현재 페이지를 지정합니다.

```
<query id="getMemberList" action="select">
    <tables>
        <table name="member" />
    </tables>
    <columns>
        <column name="*" />
    </columns>
    <conditions>
        <condition operation="equal" column="is_admin" var="is_admin" />
    </conditions>
    <navigation>
        <index var="sort_index" default="list_order" order="sort_order" />
        <list_count var="list_count" default="20" />
        <page_count var="page_count" default="10" />
        <page var="page" default="1" />
    </navigation>
</query>
```
```
SELECT * FROM member WHERE is_admin = ':is_admin' ORDER BY :sort_index :sort_order
-- 예) 한 페이지에 20(default)개씩 출력할 때, 1(default)페이지에 해당하는 목록을 조회 => LIMIT 0, 20

```

> pagination은 게시판의 목록 페이지와 같이 쿼리 결과를 뷰페이지에 출력할 때, 목록 하단에 나오는 page navigation을 처리하기 위한 기능입니다.



