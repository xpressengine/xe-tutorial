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
 - [jQuery 라이브러리 포함](../include_jquery)
 - [XE 템플릿 문법으로 자바스크립트 선언](../init_javascript_with_template_grammar)
 - [표준 문법으로 자바스크립트 선언](../init_javascript_with_standard_grammar)
 - HTML 해석 이후 jQuery 실행
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

## HTML 해석 이후 jQuery 실행

XE로 생성된 모든 문서는 jQuery 라이브러리를 참조하기 때문에 `<script>` 요소 안에서 jQuery 문법을 사용할 수 있습니다. 그런데 HTML 문서를 완전히 해석하기 전에 자바스크립트가 실행되면 HTML 구조에 의존하고 있는 자바스크립트 구문에서 오류가 발생할 수 있습니다. 이런 오류를 예방하기 위하여 jQuery 문서의 해석 시점과 실행 시점을 다르게 처리할 수 있습니다.

다음과 같은 방법으로 jQuery 함수를 선언하면 HTML 문서의 로딩이 끝난 이후에 jQuery를 실행할 수 있습니다.

```html
<script type="text/javascript">
//<![CDATA[
    jQuery(function($){
        jQuery 문법을 이곳에 작성합니다.
    });
//]]>
</script>
```

> jQuery 문법에서 `jQuery`는 `달러 기호($)`로 치환하여 표기할 수 있습니다. 그러나 XE는 `$` 기호를 사용하는 다른 자바스크립트 라이브러리와의 충돌을 피하기 위하여 jQuery 함수를 시작하는 부분에서만큼은 `$` 기호로 치환하는 것을 허락하지 않습니다. 따라서 XE에서는 jQuery 함수를 처음 작성할 때 `jQuery(function($){ ... })`라고 작성해야 합니다.
