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
>>>>>>> 링크 정리

<!-- index end -->

## 테이블 생성하기

XE의 구성요소 중에서 DB 테이블을 생성할 수 있는 구성요소는 오직 모듈입니다. 위젯, 애드온과 같은 다른 요소는 질의(query)만 할 수 있습니다.

테이블을 생성하려면 우선 생성할 테이블의 스키마를 정의해야 합니다. XE는 테이블의 스키마를 정의하기 위해 XML 스키마 정의 언어(XML Schema Language)를 사용합니다. 

XML 스키마 정의 언어로 작성된 테이블 스키마는 테이블당 하나의 XML파일을 가지며, XML파일의 이름은 테이블명과 동일해야 합니다. XML 스키마 파일은 모듈의 schemas 폴더에 저장됩니다.

XE는 모듈을 설치할 때, 모듈의 schemas 폴더에 등록된 스키마들을 조회하여 테이블을 생성합니다.

## XML 스키마 정의


### 테이블 선언

```
<table name="member">
...
</table>
```

XML스키마의 최상위 요소(element)는 `<table>`입니다. `name`속성은 테이블명입니다.

### 컬럼 선언

```
<table name="member">
	<column name="member_srl" type="number" size="11" />
	...
</table>
```

`<table>`요소의 자식인 `<column>`요소는 테이블의 컬럼을 정의합니다. 사용가능한 속성은 아래와 같습니다.

속성(예시)  | 설명
------------- | -------------
name="title" | 컬럼명을 지정
type="varchar" | 데이터 타입을 지정, 다음중 하나의 값을 가집니다. <br>(number,bignumber,varchar,char,text,bigtext,date,float)
size="11" | 데이터 사이즈를 지정
notnull="notnull" | notnull 여부를 지정
primary_key="primary_key" | 기본키 여부를 지정
index="index_title" | 컬럼에 인덱스를 지정
unique="unique_title" | 컬럼에 unique index를 지정
default="제목없음" | 기본값을 지정
auto_increment="auto_increment" | 자동 증가 컬럼 여부를 지정

> Note: XML스키마 정의 언어로 복합(다중컬럼) 인덱스는 추가할 수 없습니다. 복합 인덱스를 사용하는 방법은 [TODO:스키마 변경 장 링크]()를 보세요

