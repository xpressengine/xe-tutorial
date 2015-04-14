# 모듈 예제

- [config/info.xml 작성](../01_write_config_info)
- [액션 작성](../02_write_action)
- [Action forward 작성](../03_write_action_forward)
- [트리거 사용](../04_use_trigger)
- 룰셋 사용
- [폼 필터 사용](../06_use_form_filter)
- [DB 쿼리 정의](../07_define_db_query)

## 룰셋 사용

룰셋은 HTML 폼의 정보를 PHP에 있는 처리 메서드로 전달할 때 클라이언트 측에서는 물론 서버 측에서도 정보의 유효성을 검증하기 위하여 사용합니다. 룰셋은 각 모듈 폴더의 `ruleset` 폴더에 있는 XML 파일에 저장됩니다. 다음은 룰셋의 예제입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<ruleset version="1.5.0">
    <customrules>
    </customrules>
    <fields>
        <field name="user_id" required="true" length="3:20" />
        <field name="user_name" required="true" length="2:40" />
        <field name="nick_name" required="true" length="2:40" />
        <field name="email_address" required="true" length="1:200" rule="email" />
    </fields>
</ruleset>
```

룰셋에서 사용되는 요소와 속성은 다음과 같습니다.

|요소|속성|설명|
|-|-|-|
|customrules||사용자 정의 규칙을 정의할 수 있습니다.|
|rule||사용자 정의 규칙|
||name|사용자 정의 규칙의 이름|
||type|사용자 정의 규칙의 유형. `regex` `enum` `expression` 중 하나를 사용할 수 있습니다.<ul><li>`regex` 정규표현식을 작성할 때</li><li>`enum` 주어진 값 중 하나만 선택할 수 있을 때</li><li>`expression` 수식이 필요할 때</li></ul>|
||test|사용자 정의 규칙의 테스트 코드|
|fields||유효성을 검사할 필드의 모임|
|field||유효성을 검사할 필드|
||name|폼 요소 이름|
||rule|적용할 규칙|
||required="true"|반드시 입력해야 합니다.|
||length|길이 제한. `최소:최대`와 같이 작성할 수 있습니다.|
||default|기본값.|
||equalto|`equalto`에 넣은 요소의 값이 현재 요소의 값과 같아야 함을 나타냅니다(비밀번호, 비밀번호 확인 등).|
||modifier|규칙을 사용하기 전에 입력값을 변경하거나 검사를 마친 후 결과를 변경할 수 있는 기능.|

더 자세한 내용은 [4. 폼 사용](../../../Form)을 참조하십시오.
