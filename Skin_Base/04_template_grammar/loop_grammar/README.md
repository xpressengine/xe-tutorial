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
 - 반복문
 - [간단한 PHP문 사용](../use_php_grammar)
 - [include문](../include_grammar)
 - [CSS 파일 참조](../css_reference)
 - [JS 파일 참조](../js_reference)
 - [XML JS 필터 적용](../use_xml_js_filter)
 - [위젯 삽입하기](../include_widget)
 - [XE 블럭 템플릿 문법](../block_template_grammar)

## 반복문

주어진 조건에 따라 필요한 내용을 반복해서 출력해야 할 때 반복문이 필요합니다. 반복문은 `foreach` `end`와 **조건식**으로 이루어져 있습니다. foreach문이 시작되면 반드시 end문으로 닫아서 반복문이 끝났음을 선언해야 합니다.

**$key값 없이 `<tr>...</tr>` 반복**

```html
<!--@foreach(변수명 as $val)-->
    <tr>...</tr>
<!--@end-->
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
<!--@foreach(변수명 as $key => $val)-->
    <tr>...</tr>
<!--@end-->
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
<!--@foreach($i=0;$i<100;$i++)-->
    <tr>...</tr>
<!--@end-->
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

**조건문이 참이면 `<li>…</li>`를 반복**
*조건문이 "거짓"이 될 수 없다면 무한 반복 오류가 발생할 수 있음*

```html
<!--@while(조건문)-->
    <li>…</li>
<!--@end-->
```

> `loop` 속성은 HTML 표준 속성이 아니라 XE core만의 템플릿 문법 중 하나입니다. `loop`는 foreach문의 조건식을 표현할 때 사용하는 가상의 속성입니다.
