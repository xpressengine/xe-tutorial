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
 - 조건문
 - [반복문](../loop_grammar)
 - [간단한 PHP문 사용](../use_php_grammar)
 - [include문](../include_grammar)
 - [CSS 파일 참조](../css_reference)
 - [JS 파일 참조](../js_reference)
 - [XML JS 필터 적용](../use_xml_js_filter)
 - [위젯 삽입하기](../include_widget)
 - [XE 블럭 템플릿 문법](../block_template_grammar)

## 조건문

주어진 조건에 따라 필요한 내용을 문맥에 알맞게 출력하거나 출력하지 않아야 할 때 조건문이 필요합니다. 조건문은 `if` `elseif` `else` `end`와 **조건식**으로 이루어져 있습니다. if문이 시작되면 반드시 end문으로 닫아서 조건문이 끝났음을 선언해야 합니다. 조건식 내용은 PHP로 해석되기 때문에 PHP에서 사용 가능한 여러 가지 연산자(&&, ||, ==, ! 등)를 사용할 수도 있습니다.

다음은 “Welcome XE!"라는 문장을 표현하는 다양한 조건문 사용법입니다.

**조건식이 참이면 포함된 내용을 출력**

```html
<!--@if(조건식)-->
    <p>Welcome XE!</p>
<!--@end-->
```

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

**`<p>` 요소는 무조건 출력하는데 조건식이 참이면 `attr="value"` 속성과 값을 출력**

```html
<p attr="value"|cond="조건식">
    Welcome XE!
</p>
```

> `<block>` 요소는 HTML 표준 요소가 아니라 XE core만의 가상의 요소입니다. HTML 요소의 형식을 빌려 쓰고는 있지만 제어문을 실행할 뿐 실제로 화면에 요소가 출력되지는 않습니다. cond 속성 또한 XE core만의 가상의 속성으로서 조건문 역할을 합니다. `if` `elseif` `else`문을 동시에 사용하면 참 또는 거짓뿐만 아니라 여러 가지 조건을 부여하고 조건에 따라 다른 결과를 출력할 수 있습니다.

> ```html
<!--@if(조건A)-->
    <p>조건A를 만족하면 이 문장을 출력합니다.</p>
<!--@elseif(조건B)-->
    <p>조건A를 만족하지 못하고 조건B를 만족하면 이 문장을 출력합니다.</p>
<!--@else-->
    <p>조건A, 조건B를 동시에 만족하지 못하면 이 문장을 출력합니다.</p>
<!--@end-->
```
> 위와 같은 조건식을 XE core 1.4.4 버전부터 새로 추가된 `cond` 조건식으로 바꾸면 다음과 같이 더 단순하게 표현할 수 있습니다.
> ```html
<p cond="조건A">조건A를 만족하면 이 문장을 출력합니다.</p>
<p cond="조건B">조건B를 만족하면 이 문장을 출력합니다.</p>
<p cond="!조건A && !조건B">조건A, 조건B를 동시에 만족하지 못하면 이 문장을 출력합니다.</p>
```
