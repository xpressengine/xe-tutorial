# XE 스킨 제작의 기초

- [HTML의 이해](../)
 - [요소와 속성, 값](../element_attribute_and_value)
 - [HTML의 시작과 끝](../start_and_end_of_html)
 - [부모 요소와 자식 요소](../parent_and_child_element)
 - 인라인 요소와 블록 요소
- [CSS의 이해](../../02_understand_css)
 - [선택자와 속성, 값](../../02_understand_css/selector_attribute_and_value)
 - [CSS 선택자의 종류](../../02_understand_css/type_of_selector)
- [자바스크립트와 jQuery 라이브러리 사용](../../03_use_javascript_and_jquery)
 - [jQuery 라이브러리 포함](../../03_use_javascript_and_jquery/include_jquery)
 - [XE 템플릿 문법으로 자바스크립트 선언](../../03_use_javascript_and_jquery/init_javascript_with_template_grammar)
 - [표준 문법으로 자바스크립트 선언](../../03_use_javascript_and_jquery/init_javascript_with_standard_grammar)
 - [HTML 해석 이후 jQuery 실행](../../03_use_javascript_and_jquery/run_jquery_after_html_loading)
 - [jQuery의 동작 방식 실습](../../03_use_javascript_and_jquery/practice_jquery)
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

## 인라인 요소와 블록 요소

블록 요소는 **하나의 독립된 덩어리**로 취급하며 줄을 바꿔서 표현합니다. `<div>` `<h>` `<p>` 요소 등이 블록 요소에 해당합니다. 인라인 요소는 **행 안의 일부**로서 줄 바꿈 없이 연속으로 표현합니다. `<span>` `<img>` `<a>` 요소 등이 대표적인 인라인 요소입니다.

블록 요소는 인라인 요소를 포함할 수 있지만 인라인 요소는 블록 요소를 포함할 수 없습니다. 어떤 요소가 블록이고 어떤 요소가 인라인인지는 HTML 규격을 보면 알 수 있습니다.

다음은 블록 요소가 인라인 요소를 감싸고 있는 올바른 마크업입니다. `<h1>` 요소는 블록 요소이고 `<a>` 요소는 인라인 요소입니다.

```html
<h1><a>XE</a></h1>     <!--올바른 마크업-->
```

다음은 인라인 요소가 블록 요소를 감싸고 있는 잘못된 마크업입니다.

```html
<a><h1>XE</h1></a>    <!--잘못된 마크업-->
```
