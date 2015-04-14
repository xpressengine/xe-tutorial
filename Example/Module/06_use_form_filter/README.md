# 모듈 예제

- [config/info.xml 작성](../01_write_config_info)
- [액션 작성](../02_write_action)
- [Action forward 작성](../03_write_action_forward)
- [트리거 사용](../04_use_trigger)
- [룰셋 사용](../05_use_ruleset)
- 폼 필터 사용
- [DB 쿼리 정의](../07_define_db_query)

## 폼 필터 사용

필터는 HTML 폼에서 PHP에 있는 처리 메서드로 정보를 전달하고 자바스크립트 콜백 함수를 지정하기 위해 사용합니다. 필터는 `tpl/filter` 폴더 내에 있는 XML 파일에 저장됩니다. 다음은 폼 필터의 예제입니다. XE 1.5 이상 버전부터는 폼 필터보다 룰셋을 사용하기를 권장합니다.

```xml
<filter name="insert_contest" module="contest" act="procContestAdminInsertContest" confirm_msg_code="confirm_submit">
   <form>
       <node target="mid" required="true" maxlength="40" filter="alpha_number" />
       <node target="browser_title" required="true" maxlength="250" />
   </form>
   <parameter>
       <param name="contest_name" target="mid" />
       <param name="module_srl" target="module_srl" />
       <param name="module_category_srl" target="module_category_srl" />
       <param name="layout_srl" target="layout_srl" />
       <param name="skin" target="skin" />
       <param name="browser_title" target="browser_title" />
       <param name="header_text" target="header_text" />
       <param name="footer_text" target="footer_text" />
   </parameter>
   <response callback_func="completeInsertContest">
       <tag name="error" />
       <tag name="message" />
       <tag name="module" />
       <tag name="act" />
       <tag name="page" />
       <tag name="module_srl" />
   </response>
</filter>
```

폼 필터에서 사용되는 요소와 속성은 다음과 같습니다.

|요소|속성|설명|
|---|---|---|
|form||입력값이 유효한지 확인하는 최상위 요소|
|node||HTML 폼 확인|
||required|입력 요소가 반드시 필요한 값인지 설정. `required` 속성값이 `true`로 설정된 경우, 해당 요소에 값이 입력되지 않으면 경고가 발생합니다.|
||filter = "filter type"|필터에 사용할 수 있는 타입은 `email(email_address)` `userid(user_id)` `url(homepage)` `korean` `korean_number` `alpha` `number` `alpha_number`입니다.|
||equalto = "target person"|`equalto`에 넣은 요소의 값이 현재 요소의 값과 같아야 함을 나타냅니다(비밀번호, 비밀번호 확인 등).|
||maxlength|최대 길이|
||minlength|최소 길이|
|parameter||서버로 전송할 때 폼 요소의 이름을 변경하거나, 폼 요소 중 개발자가 parameter에 작성한 값만을 서버에 전송하고자 할 때 사용. 기본적으로 parameter를 사용하지 않으면 모든 폼 요소를 서버에 전송합니다.|
|param||재정의하거나 서버에 전송할 폼 요소 정보 작성|
||name|폼 요소 이름|
||target|재정의할 요소 이름|
|response|||
||callback_func|자바스크립트 콜백 함수. 실제 구현되어야 합니다.|
|tag||콜백 함수로 전달될 변수 정의|
||name|콜백 함수에 전달할 변수 이름. 이 변수들은 controller에서 액션을 실행한 후 콜백 함수에 전달할 값들을 `$this->add('변수명', '값');`으로 구현합니다.|
