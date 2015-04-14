# 애드온 예제

- [애드온](../)
 - [애드온 호출 시점](../01_call_position)
   - [`before_module_init`](../01_call_position/before_module_init)
   - [`before_module_proc`](../01_call_position/before_module_proc)
   - [`after_module_proc`](../01_call_position/after_module_proc)
   - [`before_display_content`](../01_call_position/before_display_content)
- [애드온 호출 시 전달되는 변수](../02_pass_variables_when_call)
- [애드온 파일 작성](../03_write_addon)
- [XE XML 쿼리 사용법](../04_use_xml_query)
- 애드온 생성 시 고려 사항

## 애드온 생성 시 고려 사항

애드온을 생성할 때 고려 사항은 다음과 같습니다.

- XE의 애드온은 모든 모듈의 여러 부분에 삽입되므로 `<?php ... ?>` 앞뒤로 공백이 없어야 합니다. 공백이 포함되면 `before_display_content`가 호출되어도 제대로 동작하지 않습니다. 
- XE core는 애드온을 프로그래밍할 때 발생할 수 있는 예외를 별도로 처리하지 않습니다. 따라서 현재 호출 상황을 확인하는 루틴을 잘 구현해서 예외가 발생하지 않도록 해야 합니다.
- 애드온 코드 에러로 인해 웹 사이트에 심각한 에러가 발생한다면 `files/cache` 폴더를 지워봅니다.

XE 애드온은 강력한 액션을 수행할 수 있습니다. 하지만 코드를 적절하게 작성하지 않으면 예기치 않은 결과가 나오거나 XE가 중단될 수도 있습니다. 따라서 애드온을 생성할 때는 기본 애드온을 참조하는 것을 권장합니다.
