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

## SELECT 쿼리 - WHERE절

WHERE절은 `<condition>` 요소를 사용하여 작성할 수 있습니다. WHERE절은 SELECT, UPDATE, DELETE 쿼리에서 모두 동일하게 사용됩니다.

```
<query id="getMemberInfo" action="select">
    <tables>
        <table name="member" />
    </tables>
    <columns>
        <column name="*" />
    </columns>
    <conditions>
        <condition operation="equal" column="user_id" default="admin" var="user_id" />
    </conditions>
</query>
```

```
SELECT * FROM member WHERE user_id = ':user_id'; 
-- :user_id => user_id 변수의 값이 바인딩 됨
```

### operation 속성

`<condition>` 요소의 `operation` 속성은 조건 연산자 지정합니다. 아래의 연산자를 가질 수 있습니다.

연산자 | 의미
-----|----
equal | column = (var or default)
more | column >= (var or default)
excess | column > (var or default)
less | column <= (var or default)
below | column < (var or default)
notequal | column != (var or default)
notnull | column is not null
null | column is null
like_prefix | column like 'var or default%'
like_tail | column like '%var or default'
like | column like '%var or default%'
in | column in (var or default)
notin | column not in (var or default) 


### var 속성

`<condition>` 요소의 `var` 속성을 사용하여 쿼리에 변수를 바인딩 할 수 있습니다.

executeQeury()함수를 실행할 때, 두번째 파라메터에 할당한 변수의 값이 바인딩됩니다.

```
$arg = new stdClass();
$arg->user_id = 'khongchi'; // user_id인 var 속성에 'khongchi'가 바인딩 됨
$output = executeQuery('member.getMemberInfo', $arg);
```

```
SELECT * FROM member WHERE user_id = 'khongchi';
```


### default 속성

`<condition>` 요소에 `var` 속성이 없거나 `var`속성에 변수가 바인딩되지 않았을 경우 `default` 속성을 사용하여 기본값을 지정할 수 있습니다.


### notnull 속성

`<condition>` 요소의 `notnull`속성을 이용하여 사용자가 `var` 속성에 변수 바인딩을 빼트리지 않도록 차단할 수 있습니다.

`notnull=notnull`로 지정하면 됩니다. 단, `notnull=notnull`이 지정되어 있고 `var` 속성에 변수가 바인딩 되지 않아도 `default` 속성이 지정되어 있을 경우에는 쿼리가 정상적으로 실행됩니다. 이럴 경우 default 값을 사용하게 됩니다.


### filter 속성

`<condition>` 요소의 `filter`속성을 이용하면 `var`속성에 바인딩된 변수의 값을 실제 DB에 질의하기 전에 필터링 할 수 있습니다.

```
<query id="getMemberInfo" action="select">
    <tables>
        <table name="member" />
    </tables>
    <columns>
        <column name="*" />
    </columns>
    <conditions>
        <condition operation="equal" column="user_id" default="admin" var="user_id" filter="user_id" />
    </conditions>
</query>
```

`filter`의 종류는 아래와 같습니다.

* email, email_address: 메일 형식
* homepage: http|https:// 같은 웹사이트 주소 형식
* userid, user_id: XE 의 사용자 id 형식(첫 두 글자는 알파벳이어야 합니다. 세 번째 문자부터 number+alphabet+ _ 형식으로 합니다.)
* number: 숫자 허용
* alpha: 알파벳 허용
* alpha_number: 숫자와 문자 모두 허용

`var` 속성에 바인딩된 변수의 값이 지정된 `filter`에 충족하지 못하면 쿼리는 실행되지 않습니다.

### maxlength, minlength 속성

`<condition>` 요소의 `maxlength`, `minlength` 속성을 사용하여 바인딩된 변수의 최소/최대 길이를 필터링할 수 있습니다.





## pipe 속성 - 다중 WHERE절

조건이 두개 이상일 경우 `pipe` 속성 사용합니다. `pipe`속성은 'and'나 'or'를 지정할 수 있습니다.

```
<query id="getMemberInfo" action="select">
    <tables>
        <table name="member" />
    </tables>
    <columns>
        <column name="*" />
    </columns>
    <conditions>
        <condition operation="equal" column="user_id" var="user_id"/>
        <condition operation="equal" column="is_admin" default="Y" pipe="and" />
    </conditions>
</query>
```

```
SELECT * FROM member WHERE user_id = ':user_id' and is_admin = 'Y';
```

## 중첩 WHERE절

중첩된 조건을 가진 WHERE절의 경우 `<group>` 요소를 사용할 수 있습니다.

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
        <group pipe="and">
            <condition operation="equal" column="user_id" var="s_user_id" />
            <condition operation="equal" column="user_name" var="s_user_name" pipe="or" />
        </group>
    </conditions>
</query>
```

```
SELECT * FROM member WHERE is_admin = ':is_admin' and (user_id = ':s_user_id' or user_name = ':s_user_name' )
-- ex) SELECT * FROM member WHERE is_admin = 'Y' and (user_id = 'khongchi' or user_name = '콩치' )
```


> Note: GROUP BY에서 사용했던 `<group>` 요소와 동일한 명칭을 사용합니다. 주의하세요.

