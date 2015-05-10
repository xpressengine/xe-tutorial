# 레이아웃 스킨 만들기

- [레이아웃 스킨이란](../../01_about_layout)
- [레이아웃 스킨의 위치와 디렉터리 구조](../../02_layout_structure)
 - [레이아웃 스킨의 위치 확인](../../02_layout_structure/confirm_directory)
 - [레이아웃 스킨 디렉터리 구조](../../02_layout_structure/directory_structure)
- [레이아웃 스킨 정보 작성](../../03_write_layout_info)
- [레이아웃 생성](../../04_make_layout_instance)
 - [사용자 정의 레이아웃 확인](../../04_make_layout_instance/confirm_user_defined_layout)
 - [레이아웃 사본 생성](../../04_make_layout_instance/copy_layout)
- [레이아웃 스킨 작성](../)
 - [레이아웃 스킨의 문서 구조](../layout_structure)
 - [{$content} 변수로 본문 출력](../print_content)
 - [글로벌 메뉴 출력](../print_global_menu)
 - [로컬 메뉴 출력](../print_local_menu)
 - 통합검색 양식 출력
 - [로그인 양식 출력](../print_login_form)
- [사이트맵 작성](../../06_write_sitemap)
- [레이아웃에 사이트맵 연결](../../07_link_sitemap)
- [페이지 모듈에 레이아웃 연결](../../08_link_layout)
 - [페이지 생성](../../08_link_layout/make_page)
 - [페이지 확인](../../08_link_layout/confirm_page)
 - [페이지 수정](../../08_link_layout/edit_page)

## 통합검색 양식 출력

웹 사이트 통합검색은 특정 모듈만을 검색 대상으로 하지 않고 생성된 모든 모듈을 검색 결과에 포함시키는 기능입니다. 그러나 통합검색 양식을 제공하지 않으면 통합검색 기능도 사용할 수 없습니다. 통합검색 양식은 보통 레이아웃 스킨에서 제공합니다.

통합검색 양식 코드는 XE 관리자 페이지의 *고급 > 설치된 모듈 > 통합검색*에서 제공합니다.

예제 레이아웃 스킨에서는 다음과 같이 `<div class="header">...</div>` 요소에 통합검색 양식 코드 `<form class="search">...</form>`을 추가했습니다.

```html
<div class="user_layout">
    <div class="header">
        <h1>Site Logo</h1>
        <form action="{getUrl()}" method="get" class="search">
            <input type="hidden" name="vid" value="{$vid}" />
            <input type="hidden" name="mid" value="{$mid}" />
            <input type="hidden" name="act" value="IS" />
            <input type="text" name="is_keyword" value="{$is_keyword}" title="{$lang->cmd_search}" class="iText" />
            <input type="submit" value="{$lang->cmd_search}" class="btn" />
        </form>
        <hr />
        <div class="gnb">
            .gnb
            ...
        </div>
    </div>
    <hr />
    <div class="body">
        <div class="lnb">
            .lnb
            ...
        </div>
        <hr />
        <div class="content">{$content}</div>
    </div>
    <hr />
    <div class="footer">.footer</div>
</div>
```

위 코드에서 사용된 변수는 다음과 같습니다.

|변수|설명|
|---|---|
|`{getUrl()}`|사용자의 검색어를 전송할 페이지의 URL|
|`{$vid}`|가상 사이트 아이디|
|`{$mid}`|모듈 아이디|
|`{$is_keyword}`|사용자가 입력한 통합검색 키워드. 검색 결과 페이지에서 사용자가 입력한 키워드를 다시 보여 줍니다.|
|`{$lang->cmd_search}`|언어 변수. *검색*이라는 단어가 변수에 할당되어 있습니다.|
