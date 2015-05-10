# XE 스킨 제작의 기초

- [HTML의 이해](../01_understand_html)
 - [요소와 속성, 값](../01_understand_html/element_attribute_and_value)
 - [HTML의 시작과 끝](../01_understand_html/start_and_end_of_html)
 - [부모 요소와 자식 요소](../01_understand_html/parent_and_child_element)
 - [인라인 요소와 블록 요소](../01_understand_html/inline_and_block_element)
- [CSS의 이해](../02_understand_css)
 - [선택자와 속성, 값](../02_understand_css/selector_attribute_and_value)
 - [CSS 선택자의 종류](../02_understand_css/type_of_selector)
- [자바스크립트와 jQuery 라이브러리 사용](../03_use_javascript_and_jquery)
 - [jQuery 라이브러리 포함](../03_use_javascript_and_jquery/include_jquery)
 - [XE 템플릿 문법으로 자바스크립트 선언](../03_use_javascript_and_jquery/init_javascript_with_template_grammar)
 - [표준 문법으로 자바스크립트 선언](../03_use_javascript_and_jquery/init_javascript_with_standard_grammar)
 - [HTML 해석 이후 jQuery 실행](../03_use_javascript_and_jquery/run_jquery_after_html_loading)
 - [jQuery의 동작 방식 실습](../03_use_javascript_and_jquery/practice_jquery)
- XE 템플릿 문법
 - [변수](./variables)
 - [XE core 변수](./variables_of_xe_core)
 - [조건문](./condition_grammar)
 - [반복문](./loop_grammar)
 - [간단한 PHP문 사용](./use_php_grammar)
 - [include문](./include_grammar)
 - [CSS 파일 참조](./css_reference)
 - [JS 파일 참조](./js_reference)
 - [XML JS 필터 적용](./use_xml_js_filter)
 - [위젯 삽입하기](./include_widget)
 - [XE 블럭 템플릿 문법](./block_template_grammar)

## XE 템플릿 문법

XE 템플릿 문법은 서버 측에서 PHP 문법으로 해석되며 DB로부터 원하는 정보를 뽑아내어 사용자 화면에 출력합니다. XE 템플릿 문법을 사용하면 모듈 또는 위젯의 기능이나 내용을 허용된 범위 안에서 확장하거나 축소할 수 있습니다.

XE 템플릿 문법을 적용하여 XE 스킨을 작성하는 방법에는 다음과 같은 네 가지가 있습니다.

- HTML 주석 `<!--...-->` 안에 작성하는 방법. 예) `<!--@if(...)-->...<!--@end-->`
- 가상의 `<block>` 요소 안에 작성하는 방법. 예) `<block>...</block>`
- HTML 요소에 직접 작성하는 방법. 예) `<p cond="조건절">...</p>`
- 주석이나 요소에 의존하지 않고 작성하는 방법. 예) {$content} 내용 변수로 데이터를 출력함.

> `<block>` 요소는 HTML 표준 요소가 아니라 XE core만의 가상의 요소입니다. HTML 요소의 형식을 빌려 쓰고는 있지만 제어문을 실행할 뿐 실제로 화면에 요소가 출력되지는 않습니다. cond 속성 또한 XE core만의 가상의 속성으로서 조건문 역할을 합니다.
