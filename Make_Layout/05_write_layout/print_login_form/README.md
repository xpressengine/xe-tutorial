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
 - [통합검색 양식 출력](../print_search_form)
 - 로그인 양식 출력
- [사이트맵 작성](../../06_write_sitemap)
- [레이아웃에 사이트맵 연결](../../07_link_sitemap)
- [페이지 모듈에 레이아웃 연결](../../08_link_layout)
 - [페이지 생성](../../08_link_layout/make_page)
 - [페이지 확인](../../08_link_layout/confirm_page)
 - [페이지 수정](../../08_link_layout/edit_page)

## 로그인 양식 출력

운영하려는 웹 사이트가 회원제 웹 사이트면 회원 가입을 받고 회원이 로그인할 수 있어야 합니다. XE core에는 이미 회원 가입 페이지와 로그인 양식이 준비되어 있습니다. 로그인 양식을 레이아웃 스킨에 포함하려면 원하는 위치에 로그인 양식 출력 코드를 추가합니다.

예제 레이아웃 스킨에서는 다음과 같이 `<div class="lnb">...</div>` 내부의 영역 윗부분에 로그인 위젯을 출력하도록 작성했습니다.

```html
...
<div class="lnb">
    .lnb
    <div class="account">
        <img widget="login_info" skin="xe_official" />
    </div>
    <h2>...</h2>
    <ul>...</ul>
</div>
...
```
