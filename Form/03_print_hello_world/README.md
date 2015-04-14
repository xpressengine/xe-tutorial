# 폼 사용 예제

- [폼 사용](../)
 - [폼 뷰 생성](../01_create_form_view)
 - [XML 룰셋 파일과 컨트롤러 액션 추가](../02_ruleset_and_controller_action)
 - 인사 메시지 출력

## 인사 메시지 출력

`modules/hello/hello.view.php`에 있는 `dispHelloName` 메서드를 다음과 같이 수정합니다.

```php
/**
 * @brief Display form for entering a name
 **/
function dispHelloName()
{
   $name = Context::get('name');
   if(isset($name))
   {
      $hello_message = "Hello " . $name;
      Context::set('hello_message', $hello_message);
   }
   $this->setTemplateFile('name');
}
```

`템플릿 파일(modules/hello/tpl/name.html)`도 다음과 같이 수정합니다.

```html
<h1 cond="isset($hello_message)">{$hello_message}</h1>
<block cond="!isset($hello_message)">
    <h1>Enter your name:</h1>
    <form id="name_form" action="./" method="post" ruleset="say_hello">
        <input type="hidden" name="module" value="hello" />
        <input type="hidden" name="act" value="procHelloGreet" />
        <input type="text" name="name" id="name" value="" />
        <br />
        <input type="submit" value="OK" />
    </form>
</block>
```

브라우저에서 해당 페이지를 다시 로드하면 완성된 폼을 가진 인사 메시지를 볼 수 있습니다.
