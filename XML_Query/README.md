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

## Quick Start

XE에서는 DB SQL 쿼리를 사용하기 위하여 'XML 쿼리 정의 언어'(XML Query Language)를 제공합니다.  각 DBMS의 네이티브 SQL 대신 XML 쿼리 정의 언어를 이용함으로써 다양한 DBMS에 범용적으로 사용할 수 있는 쿼리를 만들수 있습니다. 또한 작성된 쿼리의 재사용이 가능해집니다.

XE에서 DB에 사용하려면 기본적으로 다음의 작업이 필요합니다.

* XML 테이블 스키마 정의
* XML 쿼리 작성
* XML 쿼리 실행

위 세가지 작업을 간략히 살펴보겠습니다.


### XML 테이블 스키마 정의

XE에서 연동된 DB에 질의(쿼리)를 하려면 DB 테이블의 스키마를 먼저 정의해야 합니다. 'XML 스키마 정의 언어'(XML Schema Language)를 사용합니다.

아래는 XML 스키마 언어를 이용하여 XE 회원테이블(member table)의 스키마를 정의한 예입니다.

```
<!-- modules/member/schemas/member.xml -->

<table name="member">
    <column name="member_srl" type="number" size="11" notnull="notnull" primary_key="primary_key" />
    <column name="user_id" type="varchar" size="80" notnull="notnull" unique="unique_user_id" />
    <column name="email_address" type="varchar" size="250" notnull="notnull" unique="unique_email_address" />
    <column name="password" type="varchar" size="60" notnull="notnull" />
    <column name="email_id" type="varchar" size="80" notnull="notnull" />
    <column name="email_host" type="varchar" size="160" index="idx_email_host" />
    <column name="user_name" type="varchar" size="40" notnull="notnull" />
    <column name="nick_name" type="varchar" size="40" notnull="notnull" unique="unique_nick_name" />
    <column name="find_account_question" type="number" size="11" />
    <column name="find_account_answer" type="varchar" size="250" />
    <column name="homepage" type="varchar" size="250" />
    <column name="blog" type="varchar" size="250" />
    <column name="birthday" type="char" size="8" />
    <column name="allow_mailing" type="char" size="1" default="Y" notnull="notnull" index="idx_allow_mailing" />
    <column name="allow_message" type="char" size="1" default="Y" notnull="notnull" />
    <column name="denied" type="char" size="1" default="N" index="idx_is_denied" />
    <column name="limit_date" type="date" />
    <column name="regdate" type="date" index="idx_regdate" />
    <column name="last_login" type="date" index="idx_last_login" />
    <column name="change_password_date" type="date" />
    <column name="is_admin" type="char" size="1" default="N" index="idx_is_admin" />
    <column name="description" type="text" />
    <column name="extra_vars" type="text" />
    <column name="list_order" type="number" size="11" notnull="notnull" index="idx_list_order" />
</table>
```
XE는 모듈이 설치될 때 각 모듈의 schemas 폴더에 등록되어 있는 XML 스키마를 참조하여 테이블을 생성합니다.

또한, XE에서는 DB질의시 대상이 되는 테이블의 스키마 정보를 항상 참조합니다. 따라서 XE에서는 스키마 정보가 등록되지 않은 테이블은 사용될 수 없습니다.


### XML 쿼리 작성

회원(member) 테이블에서 회원을 조회하는 XML 쿼리입니다.

```
<!-- modules/member/queries/getMemberInfo.xml -->

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


### XML 쿼리 실행

XML 쿼리를 실행하려면 `executeQuery()`, `executeQueryArray()`함수를 사용합니다.

아래는 `user_id`가 'admin'인 회원을 검색하는 코드입니다.

```
$arg = new stdClass();
$arg->user_id = 'admin';
$output = executeQuery('member.getMemberInfo', $arg);

if($output->toBool())
{
	$member = $output->data;
	echo $member->nickname;	
}
```




