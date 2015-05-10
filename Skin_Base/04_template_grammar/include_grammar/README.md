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
 - include문
 - [CSS 파일 참조](../css_reference)
 - [JS 파일 참조](../js_reference)
 - [XML JS 필터 적용](../use_xml_js_filter)
 - [위젯 삽입하기](../include_widget)
 - [XE 블럭 템플릿 문법](../block_template_grammar)

## include문

스킨을 제작할 때 여러 페이지에 걸쳐 반복되는 콘텐츠 블록이 있으면 별도의 파일로 분할하여 관리하는 것이 편리합니다. 하나의 파일만 수정하면 여러 페이지에 한 번에 적용할 수 있기 때문입니다. include는 별도의 파일을 현재 페이지로 불러오는 명령어입니다.

|include문|설명|
|---|---|
|`<!--#include(“header.html")-->`|header.html을 포함(include)|
|`<include target="header.html" />`|header.html을 포함(include)|

> `<include />` 요소는 HTML 표준 요소가 아니라 XE core만의 가상의 요소입니다. HTML 요소의 형식을 빌려 쓰고는 있지만 include문을 실행할 뿐 실제로 화면에 `<include />` 요소가 출력되지는 않습니다. `target` 속성 또한 XE core만의 템플릿 문법 중 하나입니다. `target` 속성에는 포함(include)하려는 파일의 경로를 작성합니다.
