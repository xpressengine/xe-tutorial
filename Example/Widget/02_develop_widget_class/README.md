# 위젯 예제

- [위젯](../)
 - [config/info.xml 작성](../01_write_config_info)
 - 위젯 클래스 개발
 - [확장 변수 사용](../03_use_extra_vars)

## 위젯 클래스 개발

위젯이 무슨 기능을 하는지는 `widgetName.class.php`라는 클래스 파일에 구현합니다. 위젯을 구현하는 모든 클래스는 `WidgetHandler`를 상속해서 `proc()` 메서드를 구현해야 합니다.

```php
<?php
class myWidget extends WidgetHandler {
   function proc($args) {
            // .. Widget implementation ..

            // Template, specify the path of the skin (skin, colorset according to the value)
            $tpl_path = sprintf('%sskins/%s', $this->widget_path, $args-> skin);
            Context::set ('colorset', $args->colorset);

            // Template file name
            $tpl_file = 'HTML template file except the extension ';

            // Template compilation
            $oTemplate = &TemplateHandler::getInstance();
            return $oTemplate->compile($tpl_path, $tpl_file);
   }
}
?>
```
