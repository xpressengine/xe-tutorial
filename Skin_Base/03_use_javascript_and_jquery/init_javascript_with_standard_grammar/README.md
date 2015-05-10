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
 - 표준 문법으로 자바스크립트 선언
 - [HTML 해석 이후 jQuery 실행](../run_jquery_after_html_loading)
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

## 표준 문법으로 자바스크립트 선언

별도로 작성된 자바스크립트 파일을 HTML 문서에서 불러오는 경우 XE 템플릿 문법을 사용하면 HTML 문서의 `<head>` 요소 또는 `<body>` 요소의 종료 지점 가운데 선언 위치를 선택할 수 있습니다. 그러나 `<body>` 요소의 종료 지점이 아니라 `<body>` 요소 내부의 원하는 위치에 정확하게 삽입하려면 삽입을 원하는 위치에 다음과 같이 HTML 표준 문법으로 선언합니다.

```html
<body>
    ...
    <script type="text/javascript" src="xxx.js"></script>
    ...
</body>
```

별도의 자바스크립트 파일을 작성하지 않고 HTML 문서에서 직접 자바스크립트 코드를 작성하려면 다음과 같이 선언합니다.

```html
<body>
    ...
    <script type="text/javascript">
    // <![CDATA[
        자바스크립트 코드를 이곳에 작성합니다.
    // ]]>
    </script>
    ...
</body>
```

> 자바스크립트 코드의 시작과 종료 지점에 `<![CDATA[...]]>`를 선언하는 것은 자바스크립트 코드에 포함된 문자들이 HTML 코드로 해석되는 것을 방지하기 위한 것입니다. `<![CDATA[...]]>`를 선언하지 않으면 꺾은 괄호(<, >)와 각종 자바스크립트 연산자가 문자 그대로 해석되지 않고 HTML 태그가 시작되거나 HTML 엔티티가 시작되는 것으로 잘못 해석될 수 있습니다. `<![CDATA[...]]>` 선언은 자바스크립트 문법이 아니기 때문에 선언된 라인을 한 줄 주석으로 처리합니다.
