# 모듈 예제

- [config/info.xml 작성](../01_write_config_info)
- [액션 작성](../02_write_action)
- [Action forward 작성](../03_write_action_forward)
- 트리거 사용
- [룰셋 사용](../05_use_ruleset)
- [폼 필터 사용](../06_use_form_filter)
- [DB 쿼리 정의](../07_define_db_query)

## 트리거 사용

어떤 모듈이 다른 모듈의 특정 액션에 어떤 동작을 하고 싶을 때 트리거를 사용합니다. 단, 해당 모듈에서 트리거를 제공해야 합니다.

예를 들면, document 모듈의 `triggerDisplayDocumentAdditionSetup`에 이미 있는 관리자용 뷰를 포럼 모듈에서 사용하고 싶은 경우가 있는데 이때 트리거를 사용합니다.

트리거를 사용하는 방법은 다음과 같습니다.

### DB에 트리거 삽입

```php
$oModuleController = getController('module');
$oModuleController->insertTrigger('forum.dispForumCommentSetup', 'comment', 'view', 'triggerDispCommentAdditionSetup', 'before');
```

### 트리거 가져오기

```php
$oModuleModel = getModel('module');
if(!$oModuleModel->getTrigger('forum.dispForumAdditionSetup', 'document', 'view', 'triggerDispDocumentAdditionSetup', 'before'))
{
   return TRUE;
}
```

### 트리거 호출

```php
ModuleHandler::triggerCall('Trigger Name', 'call time (Called Position)', /* the trigger will be used as a parameter of the object */);
```

### 트리거 삭제

```php
$oModuleController = getController('module');
$oModuleController->deleteTrigger('Trigger Name', 'module name', 'call the method belongs to the type of instance', 'call the method (Called Method)', 'call time (Called Position)');
```
