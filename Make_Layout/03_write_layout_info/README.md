# 레이아웃 스킨 만들기

- [레이아웃 스킨이란](../01_about_layout)
- [레이아웃 스킨의 위치와 디렉터리 구조](../02_layout_structure)
 - [레이아웃 스킨의 위치 확인](../02_layout_structure/confirm_directory)
 - [레이아웃 스킨 디렉터리 구조](../02_layout_structure/directory_structure)
- 레이아웃 스킨 정보 작성
- [레이아웃 생성](../04_make_layout_instance)
 - [사용자 정의 레이아웃 확인](../04_make_layout_instance/confirm_user_defined_layout)
 - [레이아웃 사본 생성](../04_make_layout_instance/copy_layout)
- [레이아웃 스킨 작성](../05_write_layout)
 - [레이아웃 스킨의 문서 구조](../05_write_layout/layout_structure)
 - [{$content} 변수로 본문 출력](../05_write_layout/print_content)
 - [글로벌 메뉴 출력](../05_write_layout/print_global_menu)
 - [로컬 메뉴 출력](../05_write_layout/print_local_menu)
 - [통합검색 양식 출력](../05_write_layout/print_search_form)
 - [로그인 양식 출력](../05_write_layout/print_login_form)
- [사이트맵 작성](../06_write_sitemap)
- [레이아웃에 사이트맵 연결](../07_link_sitemap)
- [페이지 모듈에 레이아웃 연결](../08_link_layout)
 - [페이지 생성](../08_link_layout/make_page)
 - [페이지 확인](../08_link_layout/confirm_page)
 - [페이지 수정](../08_link_layout/edit_page)

## 레이아웃 스킨 정보 작성

레이아웃 스킨 정보는 *info.xml*에서 작성합니다. *info.xml*의 기본 구조는 다음과 같습니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<layout version="0.2">
    <title xml:lang="ko">테스트 레이아웃</title>
    <description xml:lang="ko">디자인이 없는 테스트 레이아웃입니다. 새 스킨을 만들 때 이 레이아웃 사본을 사용하면 좋습니다.</description>
    <version>1.0</version>
    <date>2010-12-24</date>
    <author email_address="user@user.com" link="http://user-define.com/">
        <name xml:lang="ko">제작자 이름</name>
    </author>
    <menus>
        <menu name="main_menu" maxdepth="3" default="true">
            <title xml:lang="ko">전역 메뉴</title>
        </menu>
    </menus>
</layout>
```

위 코드의 내용은 다음과 같습니다.

|코드|설명|
|---|---|
|`<?xml version="1.0" encoding="UTF-8"?>`|XML 문서 형식 선언|
|`<layout version="0.2">`|레이아웃 정보 문서임을 선언. version에는 XE core에서 지원하는 버전을 표시해야 합니다. XE core 1.4.4.2를 기준으로 지원하는 레이아웃 버전은 0.2입니다.|
|`<title xml:lang="ko">...</title>`|레이아웃 이름|
|`<description xml:lang="ko">...</description>`|레이아웃 설명|
|`<version>...</version>`|레이아웃 스킨의 버전|
|`<date>YYYY-MM-DD</date>`|레이아웃 스킨 제작 날짜. 년-월-일(YYYY-MM-DD) 형식으로 작성합니다.|
|`<author email_address="..." link="...">...</author>`|레이아웃 스킨 제작자 정보. 이메일 주소, 웹 사이트 주소, 제작자 이름을 작성합니다.|
|`<menus>...</menus>`|XE 관리자 페이지의 제어판에서 생성한 메뉴와 연결할 수 있습니다. `<menus>...</menus>` 요소 안에 2개 이상의 `<menu>...</menu>`를 작성할 수 있습니다.|

이 밖에도 *info.xml*에는 사용자 정의 가능한 여러 타입의 변수를 `<extra_vars>` 요소 안에 추가로 포함할 수 있습니다. 다음은 스킨 제작자가 *select*, *image*, *text*, *textarea* 타입의 데이터를 입력받아서 변수로 사용할 수 있도록 확장한 예제입니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<layout version="0.2">

    ...

    <extra_vars>
        <var name="colorset" type="select">
            <title xml:lang="ko">컬러셋</title>
            <description xml:lang="ko">원하는 컬러셋을 선택해주세요.</description>
            <options value="black">
                <title xml:lang="ko">Black (기본)</title>
            </options>
            <options value="white">
                <title xml:lang="ko">White</title>
            </options>
        </var>
        <var name="logo_image" type="image">
            <title xml:lang="ko">로고 이미지</title>
            <description xml:lang="ko">페이지 상단에 출력할 로고이미지를 입력하세요.</description>
        </var>
        <var name="logo_url" type="text">
            <title xml:lang="ko">로고 이미지 링크</title>
            <description xml:lang="ko">로고 이미지를 클릭할 때 이동할 URL을 입력해 주세요.</description>
        </var>
        <var name="title_description" type="textarea">
            <title xml:lang="ko">본문 상단 내용</title>
            <description xml:lang="ko">본문 상단에 표시되는 영역의 내용을 입력해주세요.(HTML 사용 가능)</description>
        </var>
    </extra_vars>

    ...

</layout>
```

위 코드의 내용은 다음과 같습니다.

|코드|설명|
|---|---|
|`<extra_vars>...</extra_vars>`|확장 변수 컨테이너|
|`<var name="colorset" type="select">...</var>`|*select* 타입의 확장 변수. 스킨 제작자는 `{$layout_info->colorset}` 형식으로 출력 가능|
|`<var name="logo_image" type="image">...</var>`|*image* 타입의 확장 변수. 스킨 제작자는 `{$layout_info->image}` 형식으로 출력 가능|
|`<var name="logo_url" type="text">...</var>`|*text* 타입의 확장 변수. 스킨 제작자는 `{$layout_info->logo_url}` 형식으로 출력 가능|
|`<var name="title_description" type="textarea">...</var>`|*textarea* 타입의 확장 변수. 스킨 제작자는 `{$layout_info->title_description}` 형식으로 출력 가능|

*info.xml*에서 추가된 확장 변수는 레이아웃이 생성된 이후 레이아웃 설정 페이지에 나타납니다. 웹 사이트 관리자가 확장 변수에 어떤 값을 입력하면 그 결과를 스킨에서 출력할 수 있습니다.
