# XE 스킨 제작의 기초

- [HTML의 이해](../)
 - [요소와 속성, 값](../element_attribute_and_value)
 - [HTML의 시작과 끝](../start_and_end_of_html)
 - 부모 요소와 자식 요소
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

## 부모 요소와 자식 요소

HTML에서 요소는 다른 요소를 포함할 수 있습니다.

예를 들어, 제목 `XE`를 클릭하면 초기 화면으로 이동하는 콘텐츠를 작성해 보겠습니다.

```html
<h1 title="Xpress Engine">
   <a href="index.html">XE</a>
</h1>
```

`<h1>` 요소 안에 `<a>` 요소가 포함되어 있습니다. 이와 같이 하나의 데이터는 여러 개의 요소로 중첩할 수 있습니다. 이때 `<h1>` 요소와 같이 바깥쪽에 있는 요소를 **부모 요소**라 부르고, `<a>` 요소와 같이 안쪽에 있는 요소를 **자식 요소**라 부릅니다.

`<a>` 요소는 데이터가 다른 자원을 참조하도록 연결합니다. href 속성은 `<a>` 요소 안에서 참조 대상을 지정합니다. 즉, 위의 예제 코드는 **XE라는 데이터는 최상위 수준 제목이며 index.html을 참조하고 있다**라는 것을 정의합니다.

단, 요소를 중첩해서 사용할 때는 시작 태그와 종료 태그의 사용 순서를 지켜야 합니다. 다음과 같이 선언하는 것은 중첩 규칙을 어긴 잘못된 예입니다.

```html
<h1 title="Xpress Engine">
   <a href="index.html">XE</h1>
</a>
```
