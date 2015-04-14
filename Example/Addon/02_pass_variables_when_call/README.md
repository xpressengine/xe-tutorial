# 애드온 예제
- [애드온](../)
 - [애드온 호출 시점](../01_call_position)
   - [`before_module_init`](../01_call_position/before_module_init)
   - [`before_module_proc`](../01_call_position/before_module_proc)
   - [`after_module_proc`](../01_call_position/after_module_proc)
   - [`before_display_content`](../01_call_position/before_display_content)
- 애드온 호출 시 전달되는 변수
- [애드온 파일 작성](../03_write_addon)
- [XE XML 쿼리 사용법](../04_use_xml_query)
- [애드온 생성 시 고려 사항](../05_consideration)

## 애드온 호출 시 전달되는 변수

앞에서 설명한 네 번의 호출 시점에 XE core는 다음과 같은 공통 변수를 애드온에 전달합니다. 
- `$called_position` 호출 시간 정보를 포함합니다. 값은 `before_module_init` `before_module_proc` `after_module_proc` `before_display_content` 네 가지 중 하나입니다.
- `$addon_path` 호출된 애드온의 경로를 포함합니다.
- `$addon_info` XE의 애드온은 독립적으로 설정할 수 있고, 해당 애드온이 동작할 대상 모듈을 지정할 수 있습니다. `$addon_info` 변수는 애드온에서 선언된 extra_vars(info.xml 내)의 정보를 포함하며, 이는 애드온마다 다릅니다.
