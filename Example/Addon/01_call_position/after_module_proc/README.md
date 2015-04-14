# 애드온 예제

- [애드온 호출 시점](../)
 - [`before_module_init`](../before_module_init)
 - [`before_module_proc`](../before_module_proc)
 - `after_module_proc`
 - [`before_display_content`](../before_display_content)
- [애드온 호출 시 전달되는 변수](../../02_pass_variables_when_call)
- [애드온 파일 작성](../../03_write_addon)
- [XE XML 쿼리 사용법](../../04_use_xml_query)
- [애드온 생성 시 고려 사항](../../05_consideration)

## after_module_proc

**태그 목록**

모든 문서의 태그 목록을 한 페이지에 출력하는 애드온이 있다고 가정해 봅시다. 이런 태그 목록을 생성하려면 먼저 현재 페이지의 `module_srl`이 포함된 문서를 가져와야 하고, 그 전에 `module_srl`을 알아야 합니다. 이를 위해 `after_module_proc`라는 지점을 선택해야 합니다. 모듈 정보가 처리된 후에 이전에 정의된 모든 작업을 실행할 수 있습니다.
