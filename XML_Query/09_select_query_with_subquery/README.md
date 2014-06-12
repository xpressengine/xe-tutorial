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

## SELECT 쿼리 - 서브쿼리

XML 쿼리는 서브쿼리를 제공합니다.

### SELECT절에서 서브쿼리

SELECT절에서 서브쿼리를 사용할 수 있습니다.

```
SELECT 	*, (SELECT count(*) AS "count" 
			FROM "xe_documents" AS "documents" 
			WHERE "documents"."user_id" = "member"."user_id" 
 		) AS "totaldocumentcount" 
 FROM "xe_member" AS "member" 
 WHERE "user_id" = 7
 ```
 
```
<query id="getStatistics" action="select">
    <tables>
        <table name="member" alias="member" />
    </tables>
    <columns>
        <column name="*" />
        <query id="getMemberDocumentCount" alias="totalDocumentCount">
            <tables>
                <table name="documents" alias="documents" />
            </tables>
            <columns>
                <column name="count(*)" alias="count" />
            </columns>
            <conditions>
                <condition operation="equal" column="documents.user_id"
                           default="member.user_id" />
            </conditions>
        </query>
    </columns>
    <conditions>
        <condition operation="equal" column="user_id" var="user_id" />
    </conditions>
</query>

```

#### WHERE절에서의 서브쿼리

WHERE절에서 서브쿼리를 사용할 수 있습니다.

```
SELECT * 
FROM xe_member AS member 
WHERE regdate = (SELECT MAX(regdate) AS regdate 
				FROM xe_documents AS documents 
				 WHERE documents.user_id = member.user_id) 
```

```
<query id="getMemberInfo" action="select">
    <tables>
        <table name="member" alias="member" />
    </tables>
    <columns>
        <column name="*" />
    </columns>
    <conditions>
        <query operation="equal" column="regdate" alias="documentMaxRegdate">
            <tables>
                <table name="documents" alias="documents" />
            </tables>
            <columns>
                <column name="max(regdate)" alias="maxregdate" />
            </columns>
            <conditions>
                <condition operation="equal" column="documents.user_id"
                           var="member.user_id" notnull="notnull" />
            </conditions>
        </query>
    </conditions>
</query> 
```

#### FROM절에서의 서브쿼리

FROM절에서 서브쿼리를 사용할 수 있습니다.

서브쿼리를 `table` 요소로 사용하세요. `table` 요소에 `query` 속성을 'true'으로 지정하고, 서브쿼리를 넣으면 됩니다.

```
SELECT m.member_srl, m.nickname, m.regdate, a.count 
FROM 
	(SELECT documents.member_srl AS member_srl, count(*) AS count 
	 FROM xe_documents AS documents 
	 GROUP BY documents.member_srl) AS a 
LEFT JOIN xe_members m on m.member_srl = a.member_srl
```

```
<query id="getMemberInfo" action="select">
    <tables>
        <table query="true" alias="a">
            <table>
                <table name="documents" alias="documents" />
            </table>
            <columns>
                <column name="member_srl" alias="member_srl" />
                <column name="count(*)" alias="count" />
            </columns>
            <groups>
                <group column="member_srl" />
            </groups>
        </table>
        <table name="member" alias="m" type="left join">
            <conditions>
                <condition operation="equal" column="m.member" default="a.member_srl" />
            </conditions>
        </table>
    </tables>
    <columns>
        <column name="m.member_srl" />
        <column name="m.nickname" />
        <column name="m.regdate" />
        <column name="a.count" />
    </columns>
</query>
```

