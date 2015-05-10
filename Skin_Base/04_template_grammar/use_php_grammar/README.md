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
 - 간단한 PHP문 사용
 - [include문](../include_grammar)
 - [CSS 파일 참조](../css_reference)
 - [JS 파일 참조](../js_reference)
 - [XML JS 필터 적용](../use_xml_js_filter)
 - [위젯 삽입하기](../include_widget)
 - [XE 블럭 템플릿 문법](../block_template_grammar)

## 간단한 PHP문 사용

XE 스킨 파일에서는 PHP 문법을 사용할 수 없지만, 다음과 같이 중괄호 안에 앳 기호(@)를 포함하면 간단한 PHP 문장을 사용할 수 있습니다.

```
{@$is_logged = Context::get('is_logged')}
```

PHP문을 사용할 때 하나의 문장은 하나의 줄에 작성해야 합니다. 예를 들어 다음과 같은 문장은 PHP에서는 문제가 없지만 XE에서는 치명적인 오류를 내기도 합니다. 여러 개의 문장이 한 줄에 작성되었기 때문입니다.

```
{@$test = 365; $test = $test * $test}
```

위 문장은 다음과 같이 한 줄에 한 문장씩 작성해야 합니다.

```
{@
    $test = 365;
    $test = $test * $test;
}
```
