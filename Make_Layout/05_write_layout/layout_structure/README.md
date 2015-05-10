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
 - 레이아웃 스킨의 문서 구조
 - [{$content} 변수로 본문 출력](../print_content)
 - [글로벌 메뉴 출력](../print_global_menu)
 - [로컬 메뉴 출력](../print_local_menu)
 - [통합검색 양식 출력](../print_search_form)
 - [로그인 양식 출력](../print_login_form)
- [사이트맵 작성](../../06_write_sitemap)
- [레이아웃에 사이트맵 연결](../../07_link_sitemap)
- [페이지 모듈에 레이아웃 연결](../../08_link_layout)
 - [페이지 생성](../../08_link_layout/make_page)
 - [페이지 확인](../../08_link_layout/confirm_page)
 - [페이지 수정](../../08_link_layout/edit_page)

## 레이아웃 스킨의 문서 구조

예제 레이아웃 스킨은 *header*, *gnb(global navigation bar)*, *body*, *lnb(local navigation bar)*, *content*, *footer*로 구성되어 있습니다. 따라서 *layout.html*의 문서 구조는 다음과 같습니다.

```html
<div class="user_layout">
    <div class="header">
        <h1>Site Logo</h1>
        <hr />
        <div class="gnb">.gnb</div>
    </div>
    <hr />
    <div class="body">
        <div class="lnb">.lnb</div>
        <hr />
        <div class="content">.content</div>
    </div>
    <hr />
    <div class="footer">.footer</div>
</div>
```

HTML로 작성된 `<div>` 요소에 클래스 이름을 지정한 이유는 CSS 파일에서 HTML 요소를 선택해서 원하는 배치를 구현할 수 있도록 하기 위해서입니다.
