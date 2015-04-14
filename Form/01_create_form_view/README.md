# 폼 사용 예제

- [폼 사용](../)
 - 폼 뷰 생성
 - [XML 룰셋 파일과 컨트롤러 액션 추가](./02_ruleset_and_controller_action)
 - [인사 메시지 출력](./03_print_hello_world)

## 폼 뷰 생성

사용자에게 이름을 물어 입력하게 한 다음 환영 인사를 보여 주는 페이지를 나타내는 아주 간단한 폼을 만들어 보겠습니다. 모듈에는 하나의 뷰만 있습니다. 이 뷰는 사용자가 이름을 입력한 후 hello 메시지를 표시하거나 이름을 입력하는 폼을 다시 출력합니다.

먼저 입력 상자와 등록 버튼만 있는 폼 형태를 만들어 보겠습니다. `파일 이름(name.html)`을 정한 후 `modules/hello/tpl`에 저장합니다.

```html
<h1>Enter your name:</h1>
<form id="name_form" action="./" method="post" ruleset="say_hello">
   <input type="hidden" name="module" value="hello" />
   <input type="hidden" name="act" value="procHelloGreet" />
   <input type="text" name="name" id="name" value="" />
   <br />
   <input type="submit" value="OK" />
</form>
```

XE에서 폼을 전송하려면 기본적으로 어떤 모듈의 어떤 액션으로 데이터를 전송할 지 추가하고, 데이터 유효성 검사를 위해 룰셋을 지정하여야 합니다. 위의 예제에서는 hello 모듈의 `procHelloGreet` 액션에 데이터를 전송하도록 하고, say_hello라는 룰셋 파일로 유효성 검사를 하도록 설정했습니다.

**참고**
> form 태그의 ruleset 속성은 적용할 룰셋 파일의 파일 이름입니다. 해당 속성값 앞에 @를 붙이면 XE에서 동적으로 생성되는 룰셋을 참고하라는 뜻이 됩니다. 예를 들어, XE 1.8에서는 로그인 계정으로 `user_id` 또는 `email_address`를 선택하도록 되어 있습니다. 이때 설정값에 따라 로그인 데이터 유효성 검사 방식이 달라져야 하므로 동적 룰셋을 적용합니다. 동적 룰셋 파일은 `files/ruleset`에 저장됩니다.

템플릿 파일을 출력하는 뷰 메서드를 생성합니다. `modules/hello/hello.view.php`에 다음의 메서드를 추가합니다.

```php
/**
 * @brief Display form for entering a name
 **/
function dispHelloName()
{
    $this->setTemplateFile('name');
}
```

`modules/hello/conf/module.xml`에 다음과 같이 추가해서 최종 사용자가 사용할 수 있게 합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<module>
   <grants />
   <permissions />
   <actions>
       <action name="dispHelloName" type="view" standalone="true" index="true" />
   </actions>
</module>
```

이제 `/?module=hello`로 접근하면 만들어진 폼을 확인할 수 있습니다.
