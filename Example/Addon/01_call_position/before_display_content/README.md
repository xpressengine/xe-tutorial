# 애드온 예제

- [애드온 호출 시점](../)
 - [`before_module_init`](../before_module_init)
 - [`before_module_proc`](../before_module_proc)
 - [`after_module_proc`](../after_module_proc)
 - `before_display_content`
- [애드온 호출 시 전달되는 변수](../../02_pass_variables_when_call)
- [애드온 파일 작성](../../03_write_addon)
- [XE XML 쿼리 사용법](../../04_use_xml_query)
- [애드온 생성 시 고려 사항](../../05_consideration)

## before_display_content

**포인트 레벨 아이콘**

특정 회원이 쌓은 포인트 레벨에 따라 각 사용자에게 아이콘을 표시하는 애드온이 필요합니다. 이 애드온은 이미 처리된 일부 파라미터에 따라 콘텐츠 내의 HTML 코드를 수정해야 하기 때문에 `before_display_content` 지점을 후크로 사용합니다.
