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
 - [HTML 해석 이후 jQuery 실행](../run_jquery_after_html_loading)
 - jQuery의 동작 방식 실습
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

## jQuery의 동작 방식 실습

jQuery 동작 방식을 한 마디로 설명하면 **선택과 실행**이라고 할 수 있습니다. 이 말을 조금 더 친절하게 풀이하면 **HTML 요소를 선택하고 필요한 시점에는 동작을 실행한다**라는 의미입니다.

간단한 예제를 통해서 살펴보겠습니다.

```html
<head>
    <style type="text/css">
    #help {display:none}
    </style>
    <script type="text/javascript" src="jquery.js"></script>
</head>
<body>
    <a href="#help" class="helpBtn">도움말</a>
    <p id="help">이 내용은 CSS 선언에 의해 화면에 표시되지 않습니다.<p>
    <script type="text/javascript">
    //<![CDATA[
    jQuery(function($){
        $('a.helpBtn').click(function(){ // HTML 요소를 선택하고
            $('p#help').css('display','block'); // 동작을 실행합니다
        });
    });
    //]]>
    </script>
</body>
```

이 코드는 `p#help`가 최초에 `display:none` 상태로 되어 있지만 사용자가 `a.helpBtn`이라는 요소를 클릭하면 `display:block`으로 상태가 바뀌는 동작을 구현한 것입니다. jQuery 함수 안에서 HTML 요소를 **선택**하고 사용자의 이벤트를 기다렸다가 선택한 요소의 CSS 변경을 **실행**했습니다.

특정 HTML 요소를 화면에서 감추거나 보여주는 동작은 매우 빈번하게 발생하기 때문에 jQuery는 이런 동작을 좀 더 쉽게 처리할 수 있도록 `show()` `hide()`라는 내장 함수를 제공합니다. 위 코드는 다음과 같이 더 간결하게 작성할 수 있습니다.

```html
<head>
    <style type="text/css">
    #help {display:none}
    </style>
    <script type="text/javascript" src="jquery.js"></script>
</head>
<body>
    <a href="#help" class="helpBtn">도움말</a>
    <p id="help">이 내용은 CSS 선언에 의해 화면에 표시되지 않습니다.<p>
    <script type="text/javascript">
    //<![CDATA[
        jQuery(function($){
            $('a.helpBtn').click(function(){ // HTML 요소를 선택하고
                $('p#help').show(); // show() 함수를 실행합니다
            });
        });
    //]]>
    </script>
</body>
```

다음 예제는 `a.helpBtn` 링크를 한 번 클릭하면 보여주고 다시 한 번 클릭하면 감추는 토글 함수를 실행하도록 동작을 개선한 것입니다.

```html
<head>
    <style type="text/css">
    #help {display:none}
    </style>
    <script type="text/javascript" src="jquery.js"></script>
</head>
<body>
    <a href="#help" class="helpBtn">도움말</a>
    <p id="help">이 내용은 CSS 선언에 의해 화면에 표시되지 않습니다.<p>
    <script type="text/javascript">
    //<![CDATA[
        jQuery(function($){
            $('a.helpBtn').click(function(){ // HTML 요소를 선택하고
                $('p#help').toggle(); // toggle() 함수를 실행합니다
            });
        });
    //]]>
    </script>
</body>
```

지금까지 jQuery 사용과 간단한 동작 방식을 알아보았습니다. jQuery 매뉴얼이나 jQuery 관련 서적을 참고하면 보다 다양한 방법으로 HTML 요소를 선택하고 더 많은 동작을 구현할 수 있습니다.

> jQuery를 사용하여 HTML을 선택하고 어떤 동작을 실행하는 자세한 방법은 [jQuery 공식 웹 사이트](http://jquery.com/)를 참조하십시오.
