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
 - JS 파일 참조
 - [XML JS 필터 적용](../use_xml_js_filter)
 - [위젯 삽입하기](../include_widget)
 - [XE 블럭 템플릿 문법](../block_template_grammar)

## JS 파일 참조

JS 파일을 HTML 문서에서 참조하는 방법을 설명합니다.

JS 파일은 HTML 문서의 `<head>` 요소 또는 `<body>` 요소에서만 불러올 수 있습니다. `<head>` 요소 또는 `<body>` 요소 이외의 요소에서 JS 파일을 참조하면 HTML 문법 오류가 발생하여 JS 파일을 해석하지 못하는 브라우저가 있을 수 있습니다.

**`<head>` 요소에서 JS 파일 참조**

다음은 xe.js 파일을 HTML 문서의 `<head>` 요소에서 불러오는 방법입니다.

```html
<!--%import(“xe.js")-->
또는
<load target="xe.js" />
```

결과 코드는 다음과 같습니다.

```html
<head>
    <script type="text/javascript" src="xe.js"></script>
</head>
```

**`<body>` 요소에서 JS 파일 참조**

다음은 xe.js 파일을 HTML 문서의 `<body>` 요소에서 불러오는 방법입니다.

```html
<load target="xe.js" type="body" />
```

`<load />` 요소는 대상 파일을 HTML 문서에서 불러옵니다. 속성과 값은 다음과 같습니다.

|속성|값|설명|
|---|---|---|
|media|aural, braille, embossed, handheld, print, projection, screen, tty, tv|CSS 파일의 대상이 되는 미디어를 선택하여 지정할 수 있습니다. 쉼표(,)를 이용하여 여러 개의 값을 지정할 수 있습니다. 기본값은 **all**입니다.|
|target|IE 6, IE 7, IE 8, ...|IE 조건부 주석을 사용하여 IE 브라우저 범위 안에서 CSS/JS 적용 브라우저를 선택할 수 있습니다. 기본값은 빈 값으로서 *적용 안 함*입니다.|
|index|정수|CSS/JS 참조 선언의 위치를 변경할 수 있습니다. 값은 양의 정수와 음의 정수를 사용할 수 있습니다. 양의 정수는 현재 위치보다 나중에 선언되고 음의 정수는 현재 위치보다 먼저 선언됩니다. 기본값은 빈 값으로서 선언 순서를 변경하지 않으며 기본값으로 두는 경우 다른 CSS 파일보다 늦게 선언됩니다.|
|type|head, body|JS 참조 선언 위치를 문서의 <head> 요소로 할 것인지 `<body>` 요소로 할 것인지 결정할 수 있습니다. 기본값은 **head**로서 생략하는 경우 JS 파일은 문서 `<head>` 요소에 포함됩니다.|

`<body>` 요소에서 JS 파일을 불러오면 `<body>` 요소가 끝나기 직전에 JS 파일 참조가 선언됩니다. 결과 코드는 다음과 같습니다.

```html
<body>
    ...
    <script type="text/javascript" src="xe.js"></script>
</body>
```

**IE 조건부 주석 사용**

```html
<load target=“xe.js" targetie="IE 6" />
```

targetie 속성을 사용하면 JS 파일을 IE의 특정 브라우저 버전에서만 해석할 수 있도록 조건부 주석으로 출력합니다. 결과 코드는 다음과 같습니다.

```html
<!--[if IE 6]>
    <script type="text/javascript" src="xe.js"></script>
<![endif]-->
```

이 코드는 모든 브라우저에서 주석으로 처리하지만 IE 6 브라우저는 주석으로 처리하지 않고 해석합니다.

**JS 파일 참조 선언 순서 변경**

```html
<load target=“xe.js" index="-1" />
```

index 속성을 사용하면 JS 파일의 선언 순서를 변경할 수 있습니다. index 속성의 값은 양의 정수 또는 음의 정수를 사용할 수 있습니다. 음의 정수를 사용하면 더 빨리 선언할 수 있고, 양의 정수를 사용하면 더 늦게 선언할 수 있습니다. `index="-1"` 값을 지정하면 다른 CSS 파일보다 한 줄 빠른 위치에서 선언됩니다.
