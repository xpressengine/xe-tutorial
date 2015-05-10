# XE 스킨 제작의 기초

- [HTML의 이해](../)
 - 요소와 속성, 값
 - [HTML의 시작과 끝](../start_and_end_of_html)
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

## 요소와 속성, 값

HTML은 요소와 속성, 값으로 구성되어 있습니다.

**요소(Element)**

```html
<h1 title="Xpress Engine">XE</h1>
```

`<h1>`로 시작해서 `</h1>`로 끝나는 전체가 **요소**입니다. 이 요소는 **`<h1>` 요소**라고 지칭하며, `<h1>`과 `</h1>`은 각각 **시작 태그**와 **종료 태그**라고 부릅니다. 그 사이에 있는 **XE**는 이 요소의 **내용(contents)**이라고 합니다.

**h**는 제목을 의미하는 **heading**의 약어로서 많은 태그가 이렇게 약어를 사용합니다. 숫자는 제목의 단계를 표시하고 **1**이면 최상위 수준의 제목입니다. 대부분의 웹 브라우저는 제목을 크고 굵게 표현하는데, 웹 제작자는 단순히 글꼴을 크고 굵게 표현하기 위하여 이 요소를 사용해서는 안 됩니다. 데이터에 아무런 의미를 부여하지 않고 크고 굵게 만드는 것은 **표현**에 해당하기 때문에 CSS로 처리해야 합니다.

**속성(Attribute)**

```html
<h1 title="Xpress Engine">XE</h1>
```

이 코드에서 **title**은 속성입니다. **속성**은 현재의 요소가 다른 요소와 어떤 차이가 있는지 나타냅니다. **title** 속성은 현재 요소의 의미를 부연 설명하는 **참고 제목** 역할을 합니다. HTML 요소마다 사용할 수 있는 속성이 다르게 규정되어 있습니다.

**값(Value)**

```html
<h1 title="Xpress Engine">XE</h1>
```

속성에는 반드시 **값**이 있습니다. **Xpress Engine**은 **title** 속성의 값입니다. 값은 현재의 **요소**가 어떤 **속성**을 지녔는지 구체적으로 정의하며, 화면 표시에 직접 영향을 주기도 합니다. 속성에 따라 잘못된 값을 입력하면 화면이 제대로 표시되지 않을 수도 있습니다. 값은 속성에 따라서 이미 정해져 있기도 하지만, 어떤 속성의 값은 사용자가 정의해야 합니다. **Xpress Engine**은 사용자 정의 값에 해당합니다.
