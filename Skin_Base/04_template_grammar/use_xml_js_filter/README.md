# XE 스킨 제작의 기초

- [HTML의 이해](../../01_understand_html)
 - [요소와 속성, 값](../../01_understand_html/element_attribute_and_value)
 - [HTML의 시작과 끝](../../01_understand_html/start_and_end_of_html)
 - [부모 요소와 자식 요소](../../01_understand_html/parent_and_child_element)
 - [인라인 요소와 블록 요소](../../01_understand_html/inline_and_block_element)
- [CSS의 이해](../../02_understand_css)
 - [선택자와 속성, 값](../../02_understand_css/selector_attribute_and_value)
 - [CSS 선택자의 종류](../../02_understand_css/type_of_selector)
- [자바스크립트와 jQuery 라이브러리 사용](../../03_use_javascript_and_jquery)
 - [jQuery 라이브러리 포함](../../03_use_javascript_and_jquery/include_jquery)
 - [XE 템플릿 문법으로 자바스크립트 선언](../../03_use_javascript_and_jquery/init_javascript_with_template_grammar)
 - [표준 문법으로 자바스크립트 선언](../../03_use_javascript_and_jquery/init_javascript_with_standard_grammar)
 - [HTML 해석 이후 jQuery 실행](../../03_use_javascript_and_jquery/run_jquery_after_html_loading)
 - [jQuery의 동작 방식 실습](../../03_use_javascript_and_jquery/practice_jquery)
- [XE 템플릿 문법](../)
 - [변수](../variables)
 - [XE core 변수](../variables_of_xe_core)
 - [조건문](../condition_grammar)
 - [반복문](../loop_grammar)
 - [간단한 PHP문 사용](../use_php_grammar)
 - [include문](../include_grammar)
 - [CSS 파일 참조](../css_reference)
 - [JS 파일 참조](../js_reference)
 - XML JS 필터 적용
 - [위젯 삽입하기](../include_widget)
 - [XE 블럭 템플릿 문법](../block_template_grammar)

## XML JS 필터 적용

XML JS 필터는 XML 형식으로 입력 항목을 정의해 두면 폼을 전송할 때 유효성 검사를 자동으로 수행하는 기능입니다. 유효성 검사는 XML 기반으로 자동으로 변환된 자바스크립트가 수행하므로 사용자는 복잡한 자바스크립트를 작성할 필요가 없습니다. XML JS 필터는 유효성 검사를 통과한 폼 데이터를 어떤 모듈의 어떤 명령어로 보낼 것인지 정하는 기능도 합니다.

XML JS 필터를 적용하는 방법은 CSS, JS 파일을 참조하는 문법과 동일합니다.

```html
<!--%import(“xe.xml")-->
```

이렇게 XML JS 필터를 불러오면 XML 문서는 JS 문서로 컴파일되어 소스 코드로 출력됩니다. 출력 결과는 다음과 같습니다.

```html
<body>
    ...
    <script type="text/javascript" src="xe.js"></script>
</body>
```
