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
 - [XML JS 필터 적용](../use_xml_js_filter)
 - [위젯 삽입하기](../include_widget)
 - XE 블럭 템플릿 문법

## XE 블럭 템플릿 문법

**조건식이 참이면 포함된 내용을 출력**

```html
<block cond="조건식">
    <p>Welcome XE!</p>
</block>
```

**조건식이 참이면 `<p>` 요소와 함께 포함된 내용을 출력**

```html
<p cond="조건식">
    Welcome XE!
</p>
```

**`<p>` 요소는 무조건 출력하는데 조건식이 참이면 `attr="value"` 속성과 값을 함께 출력**

```html
<p attr="value"|cond="조건식">
    Welcome XE!
</p>
```

**$key값 없이 `<tr>...</tr>` 반복**

```html
<block loop="변수명=>$val">
    <tr>...</tr>
</block>
```

**$key값 없이 `<tr>...</tr>` 반복**

```html
<tr loop="변수명=>$val">...</tr>
```

**$key값 포함 `<tr>...</tr>` 반복**

```html
<block loop="변수명=>$key, $val">
    <tr>...</tr>
</block>
```

**$key값 포함 `<tr>...</tr>` 반복**

```html
<tr loop="변수명=>$key,$val">...</tr>
```

**초기값 0부터 시작하여 `<tr>...</tr>` 100회 반복**

```html
<block loop="$i=0;$i<100;$i++">
    <tr>...</tr>
</block>
```

**초기값 0부터 시작하여 `<tr>...</tr>` 100회 반복**

```html
<tr loop="$i=0;$i<100;$i++">...</tr>
```

**header.html을 포함(include)**

```html
<include target="header.html" />
```

**CSS/JS/SML JS 필터 파일을 `<head>`에 포함**

```html
<load target="xxx.xxx" />
```

**JS/XML JS 필터 파일을 문서 `<body>`에 포함**

```html
<load target="xxx.xxx" type="body" />
```

**경로가 일치하는 CSS/JS/XML JS 필터 파일을 제외**

```html
<unload target="xxx.xxx" />
```
