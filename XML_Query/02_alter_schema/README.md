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

## 테이블 변경하기 (Alter table)

테이블을 생성할 때에는 XML  스키마 정의 언어를 사용할 수 있지만, 이미 생성된 테이블을 변경 또는 삭제할 때에는  XML 스키마 정의 언어를 사용할 수는 없습니다.

XE에서는 테이블을 변경/삭제하기 위하여 DB 클래스를 사용합니다. DB 클래스의 위치는 `./classes/db/DB.class.php`입니다. 다양한 DBMS를 제공 하기위해 `DB`클래스를 확장한 커스텀 `DB`클래스(ex:`./classes/db/DBMysql.class.php`)도 같은 디렉토리에 존재합니다.

(특히 배포를 목적으로 하는 모듈일 경우) 테이블 변경은 모듈을 업데이트할 때 실행되도록 해야 합니다. 
테이블을 변경하는 코드를 테이블을 소유한 모듈의 `moduleUpdate()` 메소드 안에 넣으십시오. 

이 메소드는 각 모듈의 기본 클래스에 존재 합니다. 게시판 모듈의 경우, `./modules/board/board.class.php`입니다.


> Note: 테이블의 컬럼을 추가, 삭제할 때에는 해당 테이블의 XML 스키마도 동시에 변경해 주어야 합니다. XE는 DB질의(쿼리)를 실행시 XML스키마를 항상 참조합니다.

---

> Note: 테이블 변경은 모듈의 설치 및 업데이트/삭제 사이클과 깊이 연관되어 있습니다. [TODO:모듈 튜토리얼 링크]을 참고하세요.


### DB클래스 가져오기

```
$DB = DB::getInstance();
```
DB클래스의 싱글톤 객체를 가져올 수 있습니다.


### 컬럼 존재여부 확인

```
// $table_name 테이블에 $column_name 컬럼이 존재여부 검사
DB::isColumnExists($table_name, $column_name)
```
컬럼을 추가 삭제하기 전에 컬럼의 존재여부를 확인하세요.

```
// example

if($DB->isColumnExists('documents', 'is_secret'))
{
	...
}
```

### 컬럼 추가하기

```
// $table_name 테이블에 $column_name인 컬럼을 추가
DB::addColumn($table_name, $column_name, $type = 'number', $size = '', $default = '', $notnull = false)
```

컬럼을 추가할 때에는 위의 메소드를 사용하세요.


```
// example

$DB->addColumn('documents',"notify_message","char",1);
```

### 컬럼 삭제하기

```
DB::dropColumn($table_name, $column_name)
```


```
// example

if($DB->isColumnExists('documents', 'is_secret'))
{
	$DB->dropColumn('documents', 'is_secret');
}
```			

### 인덱스 존재 여부 확인

```
DB::isIndexExists($table_name, $index_name);
```


```
// example

if(!$DB->isIndexExists("comments", "idx_status"))
{
	...
}
```


### 인덱스 추가하기

```
DB::addIndex($table_name, $index_name, $target_columns, $is_unique = false)
```

단일 인덱스 추가

```
// example

$DB->addIndex("comments", "idx_voted_count", array("voted_count"));
```

복합(다중 컬럼) 인덱스 추가

```
// example

$DB->addIndex("documents", "idx_module_status", array("module_srl","status"));
```

### 인덱스 삭제하기

```
DB::dropIndex($table_name, $index_name, $is_unique = false)
```

```
// example

$DB->dropIndex("document_extra_vars", "unique_module_vars", true);
```











