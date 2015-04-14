# 애드온 예제

- [애드온](../)
 - [애드온 호출 시점](../01_call_position)
   - [`before_module_init`](../01_call_position/before_module_init)
   - [`before_module_proc`](../01_call_position/before_module_proc)
   - [`after_module_proc`](../01_call_position/after_module_proc)
   - [`before_display_content`](../01_call_position/before_display_content)
- [애드온 호출 시 전달되는 변수](../02_pass_variables_when_call)
- [애드온 파일 작성](../03_write_addon)
- XE XML 쿼리 사용법
- [애드온 생성 시 고려 사항](../05_consideration)

## XE XML 쿼리 사용법

XE 애드온에서 다른 모듈이 생성한 DB에 있는 데이터는 XML 쿼리를 통해 사용할 수 있습니다. 이 경우 addon 폴더 아래에 queries라는 폴더를 하나 생성하고 XML 쿼리문을 정의한 XML 파일을 저장합니다. 쿼리를 실행하는 방법은 다음과 같습니다.

```php
$document_list = executeQueryArray('addons.tag_list.getModuleDocumentTags', $obj);
```

더 자세한 내용은 [3. DB 연동/XML 쿼리 실행하기](../../../XML_Query/13_execute_query)를 참조하십시오.
