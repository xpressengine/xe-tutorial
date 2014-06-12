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

## SELECT 쿼리 - JOIN

XML 쿼리를 이용하여 LEFT JOIN(또는 LEFT OUTER JOIN), RIGHT JOIN(또는 RIGHT OUTER JOIN)을 사용할 수 있습니다.

```
SELECT files.* 
FROM xe_files AS files 
 LEFT join xe_member AS member on files.member_srl = member.member_srl
WHERE files.isvalid = 'Y';
```

```
<query id="getFileList" action="select">
    <tables>
        <table name="files" alias="files" />
        <table name="member" alias="member" type="left join">
            <conditions>
                <condition operation="equal" column="files.member_srl" default="member.member_srl" />
            </conditions>
        </table>
    </tables>
    <columns>
        <column name="files.*" />
    </columns>
    <conditions>
        <condition operation="equal" column="files.isvalid" var="isvalid" pipe="and" />
    </conditions>
</query>
```

`<table>`요소의 `type` 속성에 사용할 JOIN(LEFT JOIN|LEFT OUTER JOIN|RIGHT JOIN|RIGHT OUTER JOIN)을 명시한 후, `<table>`요소의 자식요소로 `<contidion>`요소를 추가하여 on절에서 사용될 조건문을 작성합니다.

> FULL OUTER JOIN과 INNER JOIN은 제공하지 않습니다. INNER JOIN 대신, 암묵적인 INNER JOIN(implicit INNER JOIN)을 사용할 수 있습니다.



