# 애드온 예제

- [애드온 호출 시점](./01_call_position)
 - [`before_module_init`](./01_call_position/before_module_init)
 - [`before_module_proc`](./01_call_position/before_module_proc)
 - [`after_module_proc`](./01_call_position/after_module_proc)
 - [`before_display_content`](./01_call_position/before_display_content)
- [애드온 호출 시 전달되는 변수](./02_pass_variables_when_call)
- [애드온 파일 작성](./03_write_addon)
- [XE XML 쿼리 사용법](./04_use_xml_query)
- [애드온 생성 시 고려 사항](./05_consideration)

XE에서 애드온은 후킹(hooking)을 수행합니다. 후킹이란 다른 정상적인 액션을 가져오는 행위를 말합니다. 후킹은 PHP 같은 인터프리터 기반 언어에서 사용하는 'include'를 사용합니다. XE에서는 애드온을 XE의 컨텍스트에 네이티브 코드로 삽입할 수 있도록 함수나 클래스 형태로 작성하지 않습니다. 이 때문에 XE의 애드온은 호출된 순간부터 강력한 효과를 발휘할 수 있습니다. 하지만 애드온은 XE의 전체 운영에 부하를 줄 수 있으므로 조심해서 생성해야 합니다.

애드온을 생성하려면 다음의 규칙을 따라야 합니다.

- 애드온은 `addons` 폴더 아래의 `addon_name` 폴더에 저장해야 합니다.
- 애드온 실행 파일의 이름은 `addon_name.addon.php`여야 합니다.
- `info.xml` 파일에 제작자 정보, 애드온 설명, 관리자(필요한 경우)로부터 받은 애드온 변수를 저장해야 합니다.
