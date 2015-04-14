# 모듈 예제

- [config/info.xml 작성](../01_write_config_info)
- 액션 작성
- [Action forward 작성](../03_write_action_forward)
- [트리거 사용](../04_use_trigger)
- [룰셋 사용](../05_use_ruleset)
- [폼 필터 사용](../06_use_form_filter)
- [DB 쿼리 정의](../07_define_db_query)

## 액션 작성

XE에서 모든 입출력은 `index.php`를 통해 처리됩니다. 액션 요청 인수는 `Module Handler`에서 결정하며, 보통 `$act` 변수를 사용합니다. 모듈의 액션은 `conf/module.xml` 파일에 선언됩니다. 

```xml
<?xml version="1.0" encoding="utf-8"?>
<module>
   <grants>
       <grant name="post" default="guest">
           <title xml:lang="en">Post</title>
   </grants>
   <permissions>
       <permission action="dispForumAdminInsertForum" target="manager" />
       <permission action="dispForumAdminForumInfo" target="manager" />

       <permission action="procForumAdminInsertForum" target="manager" />
       <permission action="procForumAdminInsertListConfig" target="manager" />
   </permissions>
   <actions>
       <action name="dispForumIndex" type="view"   />
       <action name="dispForumContent" type="view" index="true"/>
       <action name="dispForumNoticeList" type="view" />
       <action name="dispForumContentList" type="view" />
       <action name="dispForumContentView" type="view" />
       <action name="dispForumCatogoryList" type="view" />
       <action name="dispForumContentCommentList" type="view" />
       <action name="dispForumContentFileList" type="view" />

       <action name="procForumInsertDocument" type="controller" />
       <action name="procForumDeleteDocument" type="controller" />
       
       <action name="dispForumAdminContent" type="view" standalone="true" admin_index="true" menu_name="forum" menu_index="true" />
       <action name="dispForumAdminForumInfo" type="view" standalone="true" menu_name="forum" />
       <action name="dispForumAdminExtraVars" type="view" standalone="true" menu_name="forum" />
       <action name="dispForumAdminForumAdditionSetup" type="view" standalone="true" menu_name="forum" />
       <action name="procForumAdminDeleteForum" type="controller" standalone="true" menu_name="forum" ruleset="deleteForum" />
       <action name="procForumAdminInsertListConfig" type="controller" standalone="true" menu_name="forum" ruleset="insertListConfig" />

       <action name="dispForumCategory" type="mobile" />
       <action name="getForumCommentPage" type="mobile" />
   </actions>
   <menus>
       <menu name="forum">
           <title xml:lang="en">Forum</title>
           <title xml:lang="ko">포럼</title>
       </menu>
   </menus>
</module>
```

`conf/module.xml`에서 사용되는 속성은 다음과 같습니다.

|속성|설명|
|-|-|
|name|모듈 이름도 포함하는 액션 이름. 관리자 권한이 필요한 액션의 이름에는 꼭 `Admin` 문자열을 포함해야 합니다.|
|type|액션이 어떤 타입이며 어떤 파일(뷰, 모델, 컨트롤러)에 저장돼야 하는지 정의. 이름에 `Admin`이 포함되어 있으면 관리자 뷰, 모델 또는 컨트롤러 PHP 파일에 있어야 합니다.|
|index|모듈의 기본 액션 설정. 한 액션에만 적용되어야 합니다.|
|admin_index|모듈 백 엔드의 기본 액션. 한 액션에만 적용됩니다.|
|setup_index|모듈 설정 페이지로 사용되며, 관리자 액션에만 설정할 수 있습니다.|
|menu_name|해당 액션이 속한 메뉴의 이름|
|menu_index|이 속성이 `true`로 설정되면 이 액션이 현재 메뉴의 초기 액션이라는 의미입니다.|
|ruleset|해당 액션에 적용할 룰셋 이름|
|action|권한(permission)이 선언된 액션의 이름|
|target|지원되는 권한은 다음과 같습니다.<ul><li>`member` 회원</li><li>`manager` 관리자</li></ul>|
