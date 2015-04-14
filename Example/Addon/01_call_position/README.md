# 애드온 예제

- 애드온 호출 시점
 - [`before_module_init`](./before_module_init)
 - [`before_module_proc`](./before_module_proc)
 - [`after_module_proc`](./after_module_proc)
 - [`before_display_content`](./before_display_content)
- [애드온 호출 시 전달되는 변수](../02_pass_variables_when_call)
- [애드온 파일 작성](../03_write_addon)
- [XE XML 쿼리 사용법](../04_use_xml_query)
- [애드온 생성 시 고려 사항](../05_consideration)

## 애드온 호출 시점

애드온을 호출하는 시점은 다음과 같습니다. 

- `before_module_init` 모듈 객체 생성 전. 사용자가 요청한 모듈을 찾은 후, 해당 모듈의 객체를 생성하기 전
- `before_module_proc` 모듈 실행 전. 모듈의 객체를 초기화한 후, 해당 모듈을 실행하기 전
- `after_module_proc` 모듈 실행 후. 생성된 모듈 객체를 실행하고 결과를 얻은 직후
- `before_display_content` 결과 출력 전. 레이아웃이 적용된 모듈의 결과를 출력하기 직전
각 후크가 어떤 역할을 하고, 왜 XE 제어 경로(control path)에서 일부 애드온이 특정 시점만 사용하는지 이해하기 위해 몇 가지 예를 들어보겠습니다.

- [`before_module_init`](./before_module_init)
- [`before_module_proc`](./before_module_proc)
- [`after_module_proc`](./after_module_proc)
- [`before_display_content`](./before_display_content)
