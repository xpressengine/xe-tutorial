# XE 스킨 제작의 기초

- [HTML의 이해](../)
 - [요소와 속성, 값](../element_attribute_and_value)
 - HTML의 시작과 끝
 - [부모 요소와 자식 요소](../parent_and_child_element)
 - [인라인 요소와 블록 요소](../inline_and_block_element)
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

## HTML의 시작과 끝

모든 HTML 요소에는 데이터의 범위를 명시하기 위하여 시작과 끝이 있습니다.

```html
<h1 title="Xpress Engine">XE</h1>
```

- 이 요소의 시작은 `<h1>`입니다. 여기서부터 첫 번째 제목이 시작됩니다.
- 이 요소의 끝은 `</h1>`입니다. 첫 번째 제목은 여기서 끝납니다.

텍스트 콘텐츠가 아닌 경우 HTML 요소 자체가 데이터가 되는 경우도 있는데 이런 경우는 시작과 동시에 끝납니다. 다음과 같은 경우 이미지가 다른 콘텐츠를 포함하지 않으므로 시작과 동시에 닫습니다.

```html
<img />
```
