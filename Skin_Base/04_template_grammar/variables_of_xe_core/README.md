# XE 스킨 제작의 기초

- [HTML의 이해](../../01_understand_html)
 - [요소와 속성, 값](../../01_understand_html/element_attribute_and_value)
 - [HTML의 시작과 끝](../../01_understand_html/start_and_end_of_html)
 - [부모 요소와 자식 요소](../../01_understand_html/parent_and_child_element)
 - [인라인 요소와 블록 요소](../../01_understand_html/inline_and_block_element)
- [CSS의 이해](../../02_understand_css)
 - [선택자와 속성, 값](../../02_understand_css/selector_attribute_and_value)
 - [CSS 선택자의 종류](../../02_understand_css/type_of_selector)
- [자바스크립트와 jQuery 라이브러리 사용](../../03_use_javascript_and_jquery)
 - [jQuery 라이브러리 포함](../../03_use_javascript_and_jquery/include_jquery)
 - [XE 템플릿 문법으로 자바스크립트 선언](../../03_use_javascript_and_jquery/init_javascript_with_template_grammar)
 - [표준 문법으로 자바스크립트 선언](../../03_use_javascript_and_jquery/init_javascript_with_standard_grammar)
 - [HTML 해석 이후 jQuery 실행](../../03_use_javascript_and_jquery/run_jquery_after_html_loading)
 - [jQuery의 동작 방식 실습](../../03_use_javascript_and_jquery/practice_jquery)
- [XE 템플릿 문법](../)
 - [변수](../variables)
 - XE core 변수
 - [조건문](../condition_grammar)
 - [반복문](../loop_grammar)
 - [간단한 PHP문 사용](../use_php_grammar)
 - [include문](../include_grammar)
 - [CSS 파일 참조](../css_reference)
 - [JS 파일 참조](../js_reference)
 - [XML JS 필터 적용](../use_xml_js_filter)
 - [위젯 삽입하기](../include_widget)
 - [XE 블럭 템플릿 문법](../block_template_grammar)

## XE core 변수

**XE core 변수**란 XE core에서 사용하는 변수를 말합니다. XE core 변수는 여러 모듈에서 두루 사용할 수 있습니다. 특정 모듈에서만 사용할 수 있는 변수들도 있는데 이런 변수들은 그냥 **변수**라고 부릅니다. XE core 변수는 다음과 같습니다.

|변수|설명|
|---|---|
|$is_logged|사용자의 로그인 여부를 확인|
|$current_url|현재 페이지 URL|
|$request_uri|XE core 설치 URL|
|$logged_info|로그인 사용자에게 자신의 회원정보를 보여 줌|
|$logged_info->member_srl|로그인 사용자 고유번호|
|$logged_info->user_id|로그인 사용자 아이디|
|$logged_info->email_address|로그인 사용자 이메일 주소|
|$logged_info->email_id|로그인 사용자 이메일 아이디|
|$logged_info->email_host|로그인 사용자 이메일 호스트|
|$logged_info->user_name|로그인 사용자 이름|
|$logged_info->nick_name|로그인 사용자 닉네임|
|$logged_info->homepage|로그인 사용자 홈페이지|
|$logged_info->blog|로그인 사용자 블로그|
|$logged_info->birthday|로그인 사용자 생년월일 (YYYYMMDD)|
|$logged_info->profile_image|로그인 사용자 프로필 이미지|
|$logged_info->image_name|로그인 사용자 이름 이미지 경로|
|$logged_info->image_mark|로그인 사용자 그룹 이미지 경로|
|$logged_info->signature|로그인 사용자 서명|
|$logged_info->group_list|로그인 사용자 가입 그룹 목록|
|$logged_info->is_admin|로그인 사용자가 관리자인지 확인|
|$logged_info->is_site_admin|로그인 사용자가 가상 사이트 관리자인지 확인|
|$module_info|모듈 정보로서 현재 모듈의 정보를 보여 줌|
|$module_info->module|모듈 이름|
|$module_info->use_mobile|모듈 모바일 스킨 사용 여부|
|$module_info->mid|모듈 아이디|
|$module_info->skin|모듈 스킨 이름|
|$module_info->mskin|모듈 모바일 스킨 이름|
|$module_info->browser_title|모듈 문서 제목|
|$module_info->string|모듈에서 만들어진 확장 변수|
