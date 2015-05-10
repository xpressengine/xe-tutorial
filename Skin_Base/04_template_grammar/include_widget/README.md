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
 - 위젯 삽입하기
 - [XE 블럭 템플릿 문법](../block_template_grammar)

## 위젯 삽입하기

위젯은 XE core 또는 모듈에 포함된 정보를 사용자에게 의미 있는 형태로 가공해서 보여주는 인터페이스 역할을 합니다. 웹 사이트 초기 화면에 최근 게시물을 나타내는 위젯과 로그인 양식을 보여주는 위젯이 XE core에 포함되어 있습니다. 위젯이 존재하는 이유는 스킨 제작자가 복잡한 프로그램 로직을 모르는 경우에도 쉽게 원하는 기능을 구현할 수 있도록 지원하기 위해서입니다.

스킨 제작자는 템플릿 코드 한 줄만으로도 원하는 기능을 구현할 수 있습니다. 위젯을 삽입하기 위한 템플릿 코드는 `<img />` 요소에 widget이라는 속성을 포함하고 있습니다. `<img />` 요소는 HTML 표준이기도 하지만 widget이라는 속성을 포함하게 되면 XE 템플릿 문법으로 해석되어 서버에서 표준 HTML로 변환됩니다.

다음은 로그인 양식을 출력하는 위젯 삽입 코드입니다.

```html
<img widget="login_info" skin="xe_official" />
```

위젯을 삽입하기 위한 코드는 XE 관리자 페이지에서 `사이트 설정 > 위젯`을 선택하고 코드생성 기능을 사용하면 자동으로 생성됩니다.
