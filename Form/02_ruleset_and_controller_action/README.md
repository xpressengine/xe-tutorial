# 폼 사용 예제

- [폼 사용](../)
 - [폼 뷰 생성](../01_create_form_view)
 - XML 룰셋 파일과 컨트롤러 액션 추가
 - [인사 메시지 출력](../03_print_hello_world)

## XML 룰셋 파일과 컨트롤러 액션 추가

아직 우리가 만든 폼은 아무 기능도 하지 않습니다. 이 폼에 사용자 이름을 조회하고 hello 메시지를 출력하는 메서드를 추가해 보겠습니다.

`modules/hello/hello.controller.php`에 다음과 같은 메서드를 추가합니다. 룰셋 파일을 사용할 때는 액션 실행 후 이동할 액션을 명시해야 합니다. `procHelloGreet` 함수의 실행이 완료되면 `dispHelloName` 화면으로 이동하도록 아래와 같이 `setRedirectUrl`을 설정합니다.

```php
/**
 * Action for handling the name input form submission
 * Retrieves the name given by the user and passes it on for displaying the greeting screen
 */
function procHelloGreet()
{
	$name = Context::get('name');
	$this->setRedirectUrl(getNotEncodedUrl('', 'module', 'hello', 'act', 'dispHelloName', 'name', $name));
}
```

`modules/hello/conf/module.xml`의 `<actions>` 요소에 다음과 같이 추가합니다.

```xml
<action name="procHelloGreet" type="controller" standalone="true" />
```

폼 내용의 유효성을 검사하려면 XML 룰셋 파일을 추가해야 합니다. 파일 이름을 `say_hello.xml`로 짓고 `modules/hello/ruleset` 아래에 저장합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<ruleset version="1.5.0">
    <fields>
        <field name="name" required="true" />
    </fields>
</ruleset>
```

룰셋 파일에 사용되는 요소와 속성에 대한 자세한 설명은 [2. XE 개발 예제/모듈/룰셋 사용](../../Example/Module/05_use_ruleset)을 참조하십시오.
