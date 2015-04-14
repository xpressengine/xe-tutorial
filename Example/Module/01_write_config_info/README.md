# 모듈 예제

- config/info.xml 작성
- [액션 작성](../02_write_action)
- [Action forward 작성](../03_write_action_forward)
- [트리거 사용](../04_use_trigger)
- [룰셋 사용](../05_use_ruleset)
- [폼 필터 사용](../06_use_form_filter)
- [DB 쿼리 정의](../07_define_db_query)

## config/info.xml 작성

`info.xml`은 다음과 같은 형태로 되어 있습니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<module version="0.2">
   <title xml:lang="ko">모듈 이름</title>
   <description xml:lang="ko">모듈 설명</description>
   <version>1.0.0</version>
   <date>2015-01-01</date>
   <category>service</category>
   <author email_address="foo@bar.com" link="http://www.foobar.com/">
      <name xml:lang="ko">제작자명</name>
   </author>
</module>
```

`<category>` 요소는 관리자 메뉴에서 모듈 분류를 나타냅니다. 입력할 수 있는 옵션은 다음과 같습니다. 
- `service` 서비스 관리
- `member` 회원 관리
- `content` 정보 관리
- `construction` 사이트 설정
- `utility` 기능 설정
- `accessory` 부가 기능 설정 
- `system` 시스템 관리/설정
- `package` cafeXE, textyle 등의 패키지 모듈
