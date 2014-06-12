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

## XML 쿼리 기본

### XML 쿼리의 작성

XML 쿼리는 XML 쿼리 정의 언어(XML Query Language)로 작성되며, 하나의 쿼리는 하나의 XML파일에 저장됩니다.

XML 쿼리 파일은 세가지 경로 중 한 곳에 저장될 수 있습니다.

* 애드온 디렉토리의 하위 queries 디렉토리

	예) ./addons/adminlogging/queries/

* 모듈 디렉토리의 하위 queries 디렉토리

	예) ./modules/member/queries/

* 위젯 디렉토리의 하위 queries 디렉토리

	예) ./widgets/content/queries/

### XML 쿼리 ID

XML 쿼리는 각각 쿼리 ID를 가집니다. XML 쿼리 파일의 파일명은 쿼리의 ID와 동일해야 합니다.

쿼리의 최상위 요소(element)는 `<query>`입니다. `<query>` 요소의  `id`속성에 쿼리의 ID가 명시되어야 합니다.

```
<!-- ./modules/member/queries/getMemberInfo.xml -->

<query id="getMemberInfo" action="select">
    <tables>
        <table name="member" />
    </tables>
    <columns>
        <column name="*" />
    </columns>
    <conditions>
        <condition operation="equal" column="user_id" var="user_id" notnull="notnull" />
    </conditions>
</query>

```

위 XML 쿼리는 ID가 `getMemberInfo`이며 `getMemberInfo.xml`에 저장됩니다.
