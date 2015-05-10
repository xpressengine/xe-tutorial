# XE 스킨 제작의 기초

- [HTML의 이해](../../01_understand_html)
 - [요소와 속성, 값](../../01_understand_html/element_attribute_and_value)
 - [HTML의 시작과 끝](../../01_understand_html/start_and_end_of_html)
 - [부모 요소와 자식 요소](../../01_understand_html/parent_and_child_element)
 - [인라인 요소와 블록 요소](../../01_understand_html/inline_and_block_element)
- [CSS의 이해](../../02_understand_css)
 - [선택자와 속성, 값](../../02_understand_css/selector_attribute_and_value)
 - [CSS 선택자의 종류](../../02_understand_css/type_of_selector)
- [자바스크립트와 jQuery 라이브러리 사용](../)
 - jQuery 라이브러리 포함
 - [XE 템플릿 문법으로 자바스크립트 선언](../init_javascript_with_template_grammar)
 - [표준 문법으로 자바스크립트 선언](../init_javascript_with_standard_grammar)
 - [HTML 해석 이후 jQuery 실행](../run_jquery_after_html_loading)
 - [jQuery의 동작 방식 실습](../practice_jquery)
- [XE 템플릿 문법](../../04_template_grammar)
 - [변수](../../04_template_grammar/variables)
 - [XE core 변수](../../04_template_grammar/variables_of_xe_core)
 - [조건문](../../04_template_grammar/condition_grammar)
 - [반복문](../../04_template_grammar/loop_grammar)
 - [간단한 PHP문 사용](../../04_template_grammar/use_php_grammar)
 - [include문](../../04_template_grammar/include_grammar)
 - [CSS 파일 참조](../../04_template_grammar/css_reference)
 - [JS 파일 참조](../../04_template_grammar/js_reference)
 - [XML JS 필터 적용](../../04_template_grammar/use_xml_js_filter)
 - [위젯 삽입하기](../../04_template_grammar/include_widget)
 - [XE 블럭 템플릿 문법](../../04_template_grammar/block_template_grammar)

## jQuery 라이브러리 포함

XE core에는 이미 jQuery 라이브러리가 포함되어 있고 모든 페이지에서 참조하도록 선언되기 때문에 별도로 jQuery 라이브러리를 불러오는 선언을 할 필요가 없습니다. XE로 생성된 모든 웹 문서에는 HTML 코드의 <head> 요소 안쪽에 다음과 같이 jQuery 라이브러리 참조 코드가 포함됩니다.

```html
<script type="text/javascript" src="./common/js/jquery.js"></script>
```

자바스크립트 참조 코드는 문법적으로 HTML 코드의 `<head>` 요소 또는 `<body>` 요소 안쪽의 어느 곳에도 포함시킬 수 있지만 XE에서는 jQuery 라이브러리 참조 코드를 HTML 문서의 `<head>` 요소 안쪽에 포함시키고 있습니다. 웹 브라우저는 자바스크립트 코드를 선언된 순서대로 해석하는데 자바스크립트 코드의 해석 순서가 화면 표시에 영향을 미치는 경우가 있습니다. HTML 해석과 동시에 즉시 결과를 실행해야 하는 jQuery 의존 코드가 있는 경우 jQuery 라이브러리보다 먼저 해석되면 안 되기 때문에 XE는 jQuery 라이브러리 참조 선언을 HTML 문서의 `<head>` 요소 안쪽에 포함한 것입니다.

> *XE 설치 경로에 따라 jquery.js 파일의 참조 경로는 보기와 다를 수 있습니다.*
