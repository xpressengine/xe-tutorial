# 모듈 예제

- [config/info.xml 작성](../01_write_config_info)
- [액션 작성](../02_write_action)
- Action forward 작성
- [트리거 사용](../04_use_trigger)
- [룰셋 사용](../05_use_ruleset)
- [폼 필터 사용](../06_use_form_filter)
- [DB 쿼리 정의](../07_define_db_query)

## Action forward 작성

일반적으로 액션은 XE 모듈에 속합니다. 하지만 하나의 액션이 여러 모듈에서 사용되는 경우도 있습니다. 이를 Action forward라고 부릅니다.

가장 전형적인 예는 RSS 모듈입니다. RSS 액션은 게시판 모듈에서 정의한 액션이 아니지만 Action forward 기능에서 호출하고 실행합니다.

```
?mid=board&act=rss
```

Action forward를 사용해서 독립된 기능과 함께 모듈을 처리할 수 있습니다.

위의 요청에서 XE는 `board`라는 mid를 찾습니다. 이 mid가 rss 액션을 포함하지 않으면 XE는 DB에서 Action forward 테이블을 통해 등록된 rss를 찾습니다. rss 액션은 rss 모듈의 뷰 타입으로 DB에 등록되어 있으므로 XE는 게시판을 위한 모든 mid 정보를 설정하고 rss 모듈의 뷰 객체를 생성해서 rss 메서드를 실행합니다.

이 Action forward는 XE가 레이아웃이나 현재 요청된 모듈의 정보를 유지하면서 다른 메서드를 필요로 할 때 필요합니다. 다른 예제로는 친구 목록을 보기 위한 communication 모듈의 `dispCommunicationFriend` 액션이 있습니다. 이 액션은 현재 모듈의 레이아웃을 유지하면서 해당 콘텐츠를 친구 목록으로 교체합니다.

즉, 콘텐츠 영역 출력은 지정된 액션에 의해 변경될 수 있으며, 요청된 모듈의 정보에 따라 다른 결과가 나올 수 있습니다.

### Action forward 등록

일반적으로 Action Forward는 `module.class.php`에서 `moduleInstall()`를 처리할 때 저장됩니다. 등록 방법은 다음과 같습니다. 

```php
$oModuleController = &getController('module');
$oModuleController->insertActionForward('module', 'type(Ex:controller)', 'action_name');
```

### Action forward 검증

다음과 같이 Action Forward의 등록을 확인할 수 있습니다. 보통 `module.class.php`의 `checkUpdate()` 메서드에서 사용됩니다.

```php
$oModuleModel = &getModel('module');
if(!$oModuleModel->getActionForward('action_name')) ...
```

### Action forward 삭제

Action forward가 필요 없어지면 다음과 같이 삭제합니다.

```php
$oModuleModel = &getModel('module');
$oModuleModel = &getController('module');
if($oModuleModel->getActionForward('Action Name'))
{
   $oModuleController->deleteActionForward('Module Name','Type','Action Name');
}
```

액션 이름이 `(disp|proc|get)+ModuleName+ActionName`으로 되어 있다면 Action forward를 등록하지 않아도 됩니다.
