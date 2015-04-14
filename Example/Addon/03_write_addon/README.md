# 애드온 예제

- [애드온](../)
 - [애드온 호출 시점](../01_call_position)
   - [`before_module_init`](../01_call_position/before_module_init)
   - [`before_module_proc`](../01_call_position/before_module_proc)
   - [`after_module_proc`](../01_call_position/after_module_proc)
   - [`before_display_content`](../01_call_position/before_display_content)
- [애드온 호출 시 전달되는 변수](../02_pass_variables_when_call)
- 애드온 파일 작성
- [XE XML 쿼리 사용법](../04_use_xml_query)
- [애드온 생성 시 고려 사항](../05_consideration)

## 애드온 파일 작성

addons 폴더에 다양한 이름으로 된 파일을 저장할 수 있고, 폴더 내에서 클래스를 사용할 수도 있습니다. 하지만 함수 선언은 네이티브 코드로 동작하는 include 구조를 사용하기 때문에 허용되지 않습니다.

### config/info.xml

`info.xml` 파일은 다음과 같이 작성합니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<addon version="0.2">
 <title xml:lang="en">Addon title</title>
 <description xml:lang="en">Addon description</description>
 <version>Addon version</version>
 <date>Year-Month-Date</date>
 <author email_address="The email address of an author" link="The homepage address of an author">
	<name xml:lang="en">Author name</name>
 </author>
 <extra_vars>
	<var name="Variable name" type="textarea">
 	<title xml:lang="en">Variable name (for output)</title>
 	<description xml:lang="en">Variable description</description>
	</var>
 </extra_vars>
</addon>
```

필요하면 extra_vars를 생성합니다. 세부 내용이 없으면 `<extra_vars />` 명령어를 사용해서 생략합니다. 위와 같이 작성한 파일을 `info.xml`이라는 이름으로 conf 폴더 아래에 저장합니다.

### addon_name.addon.php

애드온이 어떤 액션을 수행하기로 되어 있다면 PHP 형식으로 애드온 파일을 작성합니다. 단, 애드온은 대개 클래스 객체의 메서드 내에서 호출되므로 함수는 선언할 수 없습니다. 애드온 내에서 클래스를 정의하고 사용할 수 있습니다.

애드온 파일의 시작 부분은 다음과 같아야 합니다.

```php
<?php

	/**
  	* @file addon name.addon.php
  	* @author author name (email address)
  	* @brief description
  	**/
 	if(!defined('__ZBXE__')) exit();
```

XE의 모든 기능은 `index.php`를 통해 실행되며, `index.php`는 `__ZBXE__` 상수가 `true`로 설정되면 시작됩니다. 따라서, `index.php`에 선언되어 있는 `__ZBXE__` 상수가 `true`로 설정되어 있는지 기능을 실행하기 전에 확인합니다. 애드온 실행 시점은 `$called_position`으로 확인할 수 있으며, 이 작업은 반드시 해당 애드온에서 수동으로 해야 합니다.

예를 들어 페이지 아래에 모든 문서의 태그 목록을 출력하는 애드온이 있다고 가정해 보겠습니다. 우선 애드온을 호출하려면 어떤 후크가 적당한지 확인해야 합니다. 문서의 목록을 얻으려면 다음 코드와 같이 페이지 모듈을 처리해서 `after_module_proc`를 사용해야 합니다.

```php
<?php
if(!defined("__ZBXE__")) exit();
/**
* @file tag_list.addon.php
* @author Author (author@authorland.com)
* @brief Description of the addon
**/

if($called_position != 'after_module_proc' || Context::getResponseMethod()!=='HTML') return;

$obj->module_srl=Context::get('module_srl');
$document_list=executeQueryArray('addons.tag_list.getModuleDocumentTags',$obj);
$tags='';
foreach ($document_list->data as $val) {
	$tags=$tags.','.$val->tags;
}
$tags=explode(',', $tags);
for($i=1;$i<count($tags);$i++) {
	$tags[$i]='<a href="'.getUrl('act','TS','is_keyword',$tags[$i]).'">'.$tags[$i].'</a>';
}
$tags=implode(' ', $tags);
$tags='<div class="tags" align="center">'.$tags.'</div>';
$content=Context::get('page_content');
$content=$content.$tags;
Context::set('page_content',$content);
?>
```

위의 코드는 현재 보이는 HTML 페이지에 태그 목록 HTML 코드를 삽입합니다.
