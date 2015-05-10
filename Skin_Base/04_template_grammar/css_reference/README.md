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
 - CSS 파일 참조
 - [JS 파일 참조](../js_reference)
 - [XML JS 필터 적용](../use_xml_js_filter)
 - [위젯 삽입하기](../include_widget)
 - [XE 블럭 템플릿 문법](../block_template_grammar)

## CSS 파일 참조

CSS 파일을 HTML 문서에서 참조하는 방법을 설명합니다.

**CSS 참조**

```html
<!--%import(“xe.css")-->
또는
<load target="xe.css" />
```

HTML 문서의 `<head>` 요소에서 `xe.css` 파일을 참조합니다. 결과 코드는 다음과 같습니다.

```html
<head>
    <link rel="stylesheet" type="text/css" href="xe.css" />
</head>
```

CSS 파일은 HTML 문서의 `<head>` 요소에서만 참조할 수 있습니다. `<body>` 요소에서 별도의 CSS 파일을 참조하면 HTML 문법 오류가 발생합니다.

**media 지정**

```html
<load target=“xe.css" media="print" />
```

CSS 파일의 대상이 되는 미디어를 선택하여 지정할 수 있습니다. 결과 코드는 다음과 같습니다.

```html
<head>
    <link rel="stylesheet" type="text/css" href="xe.css" media="print" />
</head>
```

media 속성의 값에 쉼표를 사용하면 여러 개의 값을 지정할 수 있습니다. 기본값은 all입니다. 사용 가능한 값은 다음과 같습니다.

|속성 값|설명|
|---|---|
|all|media를 지정하지 않았을 때의 기본값. 모든 출력 장치에 대응|
|aural|음성 출력 장치(스크린 리더)|
|braille|점자 출력기|
|embossed|점자 인쇄기|
|handheld|모바일 장치|
|print|인쇄기|
|projection|투사 장치|
|screen|스크린(모니터)|
|tty|전신 타자기(Tele Type Writer)|
|tv|텔레비전|

CSS media 속성을 지정할 때에는 의도하는 장치가 CSS 표준을 준수하는지 반드시 확인해야 합니다. 장치가 지원하지 않으면 지정한 media 속성은 적용되지 않습니다.

**IE 조건부 주석 사용**

```html
<load target=“xe.css" targetie="IE 6" />
```

targetie 속성을 사용하면 CSS 파일을 IE의 특정 브라우저 버전에서만 해석할 수 있도록 조건부 주석으로 출력합니다. 결과 코드는 다음과 같습니다.

```html
<!--[if IE 6]>
    <link rel="stylesheet" type="text/css" href="xe.css" />
<![endif]-->
```

이 코드는 모든 브라우저에서 주석으로 처리하지만 IE 6 브라우저는 주석으로 처리하지 않고 해석합니다.

**CSS 파일 참조 선언 순서 변경**

```html
<load target=“xe.css" index="-1" />
```

index 속성을 사용하면 CSS 파일의 선언 순서를 변경할 수 있습니다.

index 속성의 값은 양의 정수 또는 음의 정수를 사용할 수 있습니다. 음의 정수를 사용하면 더 빨리 선언할 수 있고, 양의 정수를 사용하면 더 늦게 선언할 수 있습니다. index="-1" 값을 지정하면 다른 CSS 파일보다 한 줄 빠른 위치에서 선언됩니다.

CSS 파일은 동일한 명령이 충돌하는 경우 나중에 선언된 값이 우선순위를 갖게 되기 때문에 우선순위를 높게 두어야 하는 경우 나중에 선언하는 것이 좋습니다.
