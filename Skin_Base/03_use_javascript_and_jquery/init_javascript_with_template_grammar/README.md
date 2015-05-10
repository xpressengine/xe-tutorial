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
 - XE 템플릿 문법으로 자바스크립트 선언
 - [표준 문법으로 자바스크립트 선언](../init_javascript_with_standard_grammar)
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

## XE 템플릿 문법으로 자바스크립트 선언

jQuery 코드는 자바스크립트이기 때문에 자바스크립트 문법에 따라 작성해야 합니다. 자바스크립트의 선언 위치는 HTML 문서의 `<head>` 요소 또는 `<body>` 요소 안쪽이어야 하며 이 밖의 위치에 선언하면 HTML 문법 오류가 발생합니다. HTML 문법이 허용하지 않는 위치에 자바스크립트 코드를 작성하면 표준에 따라 엄격하게 구현된 브라우저에서는 자바스크립트를 해석하지 못할 수도 있습니다. 자바스크립트 코드를 HTML 문서에 직접 포함하는 방법도 있지만 별도의 `*.js` 파일로 분리하여 HTML 문서에서 불러오는 방법도 있습니다.

자바스크립트는 용도에 따라 다음과 같이 선언 위치를 구분해서 사용합니다.

**`<head>` 요소에서 JS 파일 참조**

웹 브라우저가 화면 표시를 끝내기 전에 자바스크립트로 사용자 화면의 일부 콘텐츠를 보여주거나 감추는 동작을 실행한다면 자바스크립트 코드를 HTML 문서의 `<head>` 요소 위치에 포함하는 것이 좋습니다. 이런 경우 자바스크립트 코드를 `<body>` 요소에 포함하면 자바스크립트가 HTML보다 늦게 해석되어 일시적으로 화면이 제대로 보이지 않을 수 있습니다.

`<head>` 요소에 포함된 자바스크립트는 HTML 문서보다 먼저 해석되지만 HTML 문서의 로딩이 완료된 이후에 실행하도록 코드를 작성해야 합니다.

**`<body>` 요소에서 JS 파일 참조**

자바스크립트가 HTML 문서를 로딩하는 시점에 화면 표시를 위한 어떤 동작을 실행하지 않는다면 HTML 문서의 `<body>` 요소에 포함하되 가장 아래쪽에 선언하는 것이 좋습니다. 웹 브라우저는 HTML 코드와 자바스크립트 코드를 동시에 해석하지 않고 작성된 순서대로 해석하기 때문에 자바스크립트 코드를 나중에 해석하도록 하면 HTML 문서를 화면에 표시하는 속도가 빨라집니다.
