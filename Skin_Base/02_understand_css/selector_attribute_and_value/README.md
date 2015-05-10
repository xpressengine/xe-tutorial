# XE 스킨 제작의 기초

- [HTML의 이해](../../01_understand_html)
 - [요소와 속성, 값](../../01_understand_html/element_attribute_and_value)
 - [HTML의 시작과 끝](../../01_understand_html/start_and_end_of_html)
 - [부모 요소와 자식 요소](../../01_understand_html/parent_and_child_element)
 - [인라인 요소와 블록 요소](../../01_understand_html/inline_and_block_element)
- [CSS의 이해](../)
 - 선택자와 속성, 값
 - [CSS 선택자의 종류](../type_of_selector)
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

## 선택자와 속성, 값

CSS는 **선택자**와 **속성**과 **값**으로 구성되어 있습니다. **선택자**는 HTML의 특정 **요소**를 선택하고 **속성**과 **값**은 선택된 HTML 요소가 화면에 어떻게 출력될 것인지를 정의합니다.

**선택자(selector)**

```css
h1 {font-size:24px}
```

**h1**은 **선택자**입니다. `<h1>` 요소를 가리킵니다.

**속성(property)**

```css
h1 {font-size:24px}
```

**font-size**는 **속성**입니다. `<h1>` 요소의 글꼴 크기를 제어하는 선언입니다.

**값(value)**

```css
h1 {font-size:24px}
```

**24px**은 **값**입니다. `<h1>` 요소의 `font-size` 속성(글꼴 크기) 값을 구체적으로 명시합니다.
