# 애드온 예제

- [애드온 호출 시점](../)
 - `before_module_init`
 - [`before_module_proc`](../before_module_proc)
 - [`after_module_proc`](../after_module_proc)
 - [`before_display_content`](../before_display_content)
- [애드온 호출 시 전달되는 변수](../../02_pass_variables_when_call)
- [애드온 파일 작성](../../03_write_addon)
- [XE XML 쿼리 사용법](../../04_use_xml_query)
- [애드온 생성 시 고려 사항](../../05_consideration)

## before_module_init

**카운터 애드온**

이 애드온은 XE를 사용해서 구축한 웹사이트의 방문 통계를 보기 위해 개발됐습니다. 이 애드온은 카운터 모듈을 사용합니다. 카운터 애드온은 `$is_logged` 변수의 정보를 사용해서 웹사이트 방문 횟수를 계산합니다. 모듈 처리 작업으로부터 더 이상 정보를 얻을 필요가 없으므로, 이 모듈은 시간상으로 첫 번째 후크인 `before_module_init`을 사용합니다.
