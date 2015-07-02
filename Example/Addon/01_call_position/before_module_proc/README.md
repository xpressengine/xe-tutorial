# 애드온 예제

- [애드온 호출 시점](../)
 - [`before_module_init`](../before_module_init)
 - `before_module_proc`
 - [`after_module_proc`](../after_module_proc)
 - [`before_display_content`](../before_display_content)
- [애드온 호출 시 전달되는 변수](../../02_pass_variables_when_call)
- [애드온 파일 작성](../../03_write_addon)
- [XE XML 쿼리 사용법](../../04_use_xml_query)
- [애드온 생성 시 고려 사항](../../05_consideration)

## before_module_proc

**메타 태그**

이 애드온은 메타 설명과 키워드, 제작자 등의 메타 태그를 모든 페이지에 삽입하는 역할을 합니다. 콘텐츠가 모듈 처리 작업에서 생성되기 전에 메타 태그를 삽입해야 하기 때문에 `before_module_proc` 지점을 후크로 사용합니다.
