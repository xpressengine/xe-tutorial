# XE 스킨 제작의 기초

- [HTML의 이해](../../01_understand_html)
 - [요소와 속성, 값](../../01_understand_html/element_attribute_and_value)
 - [HTML의 시작과 끝](../../01_understand_html/start_and_end_of_html)
 - [부모 요소와 자식 요소](../../01_understand_html/parent_and_child_element)
 - [인라인 요소와 블록 요소](../../01_understand_html/inline_and_block_element)
- [CSS의 이해](../)
 - [선택자와 속성, 값](../selector_attribute_and_value)
 - CSS 선택자의 종류
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

## CSS 선택자의 종류

CSS 선택자는 특정 HTML 요소를 선택하는 역할을 합니다. 선택자를 사용하면 선택된 요소에 고유한 CSS 양식을 표현할 수 있습니다. CSS는 다양한 유형의 선택자를 지원합니다.

**타입 선택자(type selector)**

```css
h1 { … }
```

HTML 요소 이름을 그대로 선택자 이름으로 사용하는 것을 타입 선택자라고 합니다. HTML 문서에서 요소 이름이 일치하면 모두 선택합니다. 표준 HTML 요소 이름을 선택자 이름으로 사용할 수 있습니다.

**아이디 선택자(id selector)**

```css
#selector { … }
```

아이디 선택자는 선택자 이름 앞에 숫자 기호(#)를 표시합니다. HTML 문서에서 아이디의 값이 일치하는 요소를 선택합니다. 아이디 선택자의 이름은 사용자가 정의할 수 있습니다. 아이디 선택자의 이름을 정의하는 규칙은 다음과 같습니다.

- 모든 자연어를 선택자 이름으로 사용할 수 있지만 영문 대소문자와 숫자의 조합을 권장합니다.
- 선택자 이름으로 특수문자를 사용할 수 없지만 언더스코어(_)와 하이픈(-)은 사용할 수 있습니다.
- 숫자로 시작할 수 없습니다.

HTML 문서는 한 페이지에 2개 이상의 아이디 값을 사용하도록 허용하지 않습니다. 아이디 값은 하나의 HTML 문서 안에서 고유해야 합니다.

**클래스 선택자(class selector)**

```css
.selector { … }
```

클래스 선택자는 선택자 이름 앞에 점(.)을 표시합니다. HTML 문서에서 클래스의 값이 일치하는 요소를 선택합니다. 클래스 선택자의 이름은 사용자가 정의할 수 있습니다. 클래스 선택자의 이름을 정의하는 규칙은 다음과 같습니다.

- 모든 언어를 선택자 이름으로 사용하는 것이 가능하지만 영문 대소문자와 숫자의 조합을 권장합니다.
- 선택자 이름으로 특수문자를 사용할 수 없지만 언더스코어(_)와 하이픈(-)은 사용할 수 있습니다.
- 클래스 선택자 이름은 숫자로 시작할 수 없습니다.

HTML 문서는 한 페이지에 2개 이상의 동일한 클래스 값을 사용할 수 있습니다.

**자식 선택자(child selector)**

```css
h1>a { … }
```

자식 선택자는 선택자 사이에 꺾은 괄호(>)를 적용해서 표시합니다. 선택자의 나열이 HTML 요소의 중첩 순서와 일치하면 선택합니다. 중첩이 2단계 이상 깊어지는 자손(자식의 자식)은 선택하지 않습니다. 오직 한 단계 바로 아래 포함된 자식만 선택합니다. *IE 6 브라우저는 자식 선택자를 지원하지 않습니다.*

**자손 선택자(descendant selector)**

```css
h1 a { … }
```

자손 선택자는 선택자 사이에 띄어쓰기를 적용해서 표시합니다. 선택자의 나열이 HTML 요소의 중첩 순서와 일치하면 선택합니다. 즉, 다음과 같이 `<h1>` 요소 안에 포함된 `<a>` 요소만을 선택한다는 의미입니다.

```html
<h1><a>XE</a></h1>
```

`<h1>` 요소 밖에 존재하는 `<a>` 요소는 이 선언의 영향을 받지 않습니다.

**공용 선택자(universal selector)**

```css
* { … }
```

공용 선택자는 별표(*)로 표시합니다. 이 선택자는 모든 HTML 요소를 선택합니다. 웹 브라우저는 보통 HTML 요소마다 기본 CSS 양식을 지정해 두는데 이것을 동일한 값으로 초기화할 수 있습니다.

공용 선택자를 사용하면 페이지 표시 속도가 느려지므로 꼭 필요한 경우가 아니면 사용을 권장하지 않습니다.

**가상 선택자(pseudo selector)**

```css
a:focus { … }
```

가상 선택자는 다른 선택자 뒤에 콜론(:)을 붙여 표시합니다. 요소의 상태를 선택하는 **가상 클래스 선택자**와 HTML 코드 속에 없는 가상의 요소를 선택하는 **가상 요소 선택자**가 있습니다. 다른 선택자들이 정적인 상태의 HTML 요소를 선택하는 것에 반해서 가상 선택자는 HTML 요소의 동적인 변화 상태를 선택하거나 HTML 코드에 없는 가상의 요소를 선택합니다.

가상 클래스 선택자의 종류는 다음과 같습니다.

|가상 클래스 선택자|설명|예제|
|---|---|---|
|:link|아직 방문한 적이 없는 링크를 선택합니다. `a`라는 타입 선택자와 결합해서 사용합니다.|a:link|
|:visited|이미 방문한 링크를 선택합니다. `a`라는 타입 선택자와 결합해서 사용합니다.|a:visited|
|:hover|마우스 포인터가 가리키는 동안의 상태를 선택합니다.|a:hover|
|:active|마우스가 클릭되는 순간 또는 엔터 키를 누른 순간의 상태를 선택합니다.|a:active|
|:focus|포커스를 받은 요소의 상태를 선택합니다.|a:focus|
|:first-child|첫 번째 자식 요소를 선택합니다.|li:first-child|
|:lang(language)|언어 속성이 일치하면 선택합니다.|p:lang(en)|

*IE 6 브라우저는 `:first-child` `:lang()` 가상 클래스 선택자를 지원하지 않습니다. IE6 브라우저는 `:hover` `:active` `:focus` 가상 클래스 선택자를 `a` 이외의 요소에 지원하지 않습니다.*

`a` 요소에 다양한 상태의 가상 클래스 선택자를 지정할 때는 `:link(링크)` `:visited(방문 시)` `:hover(지나치게)` `:active(활동하면)` `:focus(주목받습니다)` 순서를 유지하는 것이 좋습니다. 나중에 선언된 클래스의 우선순위가 높기 때문에 먼저 선언된 것들을 모두 덮어쓰게 됩니다. 예를 들어, `:hover` 뒤에 `a:visited`를 쓰면 이미 방문한 링크 위에 마우스를 올려도 `:hover`가 적용되지 않습니다. 이미 방문한 링크 위에 마우스를 올렸을 때 반응하게 하려면 `:visited` 다음에 `:hover` 클래스가 오도록 작성해야 합니다.

가상 요소 선택자의 종류는 다음과 같습니다.

|가상 요소 선택자|설명|예제|
|---|---|---|
|:first-line|첫 번째 행을 선택합니다. 블록 요소에만 적용할 수 있습니다.|p:first-line|
|:first-letter|첫 번째 문자를 선택합니다. 블록 요소에만 적용할 수 있습니다.|p:first-letter|
|:before|요소 시작 지점 안쪽의 가상 요소를 선택합니다.|div:before{content:"…"}|
|:after|요소 종료 지점 안쪽의 가상 요소를 선택합니다.|div:after{content:"…"}|

*IE 6 브라우저는 **가상 요소 선택자**를 지원하지 않습니다.*

**선택자 묶음(Selector Grouping)**

```css
.apple, .tomato {color:red}
```
선택자 묶음은 쉼표(,)를 사용해서 여러 개의 선택자를 하나로 묶고 속성과 값을 한 번만 선언합니다. 여러 선택자가 같은 속성과 값을 공유할 때 하나의 선택자로 묶을 수 있습니다.

위의 선택자 묶음 선언은 아래의 선언과 같은 의미입니다.

```css
.apple {color:red}
.tomato {color:red}
```

**인접 형제 선택자(Adjacent Sibling Selector)**

```css
h1 + h2 {color:red}
```

형제 선택자는 선택자 사이에 덧셈 기호(+)를 넣어 표시합니다. 요소가 형제 관계에 있고 나열 순서가 같으면 뒤에 등장하는 요소를 선택합니다.

위의 인접 형제 선택자 선언 예제에 따르면, 다음과 같은 HTML 코드에서 `<h1>` 요소 다음에 `<h2>` 요소가 순서대로 등장하므로 `<h2>` 요소는 붉은색 글꼴로 처리됩니다.

```html
<h1>XE</h1>
<h2>Textyle</h2>
```

*IE 6 브라우저는 **형제 선택자**를 지원하지 않습니다.*

**속성 선택자(Attribute Selector)**

```css
input[checked] { ... }   /* input 요소에 checked 속성이 사용되면 무조건 선택 */
input[type=text] { ... } /* input 요소의 type 속성이 text인 경우에만 선택 */
img[alt~=dog] { ... }    /* img 요소의 alt 속성 값에 'dog'이라는 단어가 포함되면 선택 */
p[lang|=en] { ... }      /* p 요소의 lang 속성이 en-us와 같이 en-으로 시작되면 선택 */
```

HTML 요소에 선언된 속성을 사용하여 해당 요소를 선택합니다. 속성 선택자의 종류는 다음과 같습니다.

|속성 선택자|설명|예제|
|---|---|---|
|[attribute]|HTML 요소에 attribute라는 속성이 사용되면 값의 존재 여부와 무관하게 요소를 선택합니다.|input[checked]|
|[attribute=value]|HTML 요소에 attribute라는 속성이 사용되고 오직 하나의 값이 존재하는데 그 값이 정확하게 value일 때 요소를 선택합니다.|input[type=text]|
|[attribute~=value]|HTML 요소에 attribute라는 속성이 사용되고 하나 이상의 값이 공백으로 분리되어 존재하는데 그 중 하나의 값이 value일 때 요소를 선택합니다.|img[alt~=dog]|
|[attribute&#124;=value]|HTML 요소에 attribute라는 속성이 사용되고 값이 value로 시작되면 요소를 선택합니다.|p[lang&#124;=en]|

*IE 6 브라우저는 **속성 선택자**를 지원하지 않습니다.*
