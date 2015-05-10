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
 - {$content} 변수로 본문 출력
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

## {$content} 변수로 본문 출력

*layout.html*은 아직 사용자 화면에서 확인할 수 없습니다. 어떤 모듈에서도 아직 이 레이아웃을 선택하지 않았기 때문입니다. 레이아웃 스킨 페이지는 스스로는 존재할 수 없고 특정 모듈에서 사용될 때 해당 모듈 페이지에 접근하면서 확인할 수 있습니다. 레이아웃 스킨은 **모듈**에 의존적입니다.

예제 레이아웃 스킨을 사용자 화면에서 확인하려면 특정 모듈(페이지, 게시판, 위키 등)을 하나 생성하여 이 레이아웃 스킨과 연결해야 합니다. 그 전에 스킨 제작자는 레이아웃 스킨과 연결된 모듈(페이지, 게시판, 위키 등)에서 레이아웃 스킨을 화면에 제대로 표시할 수 있도록 **내용 변수**를 작성해야 합니다.

예제 레이아웃 스킨에서는 다음과 같이 레이아웃의 본문 영역에 {$content} 변수를 사용해서 **내용 변수**를 작성했습니다.

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
        <div class="content">
            .content{$content}
        </div>
    </div>
    <hr />
    <div class="footer">.footer</div>
</div>
```

*{$content}*는 레이아웃 스킨에서 사용할 수 있는 가장 중요한 변수로서, 현재의 레이아웃 스킨이 어떤 종류의 모듈과 연결되더라도 연결된 모듈의 내용을 본문 영역에 출력합니다. 어떤 모듈과 연결되는지에 따라서 정적인 페이지가 될 수도 있고 동적인 게시판, 위키 페이지가 될 수도 있습니다.

XE에서 모듈과 레이아웃의 관계는 **레이아웃 스킨**에 여러 종류의 **모듈**을 탑재하는 것이 아니라 여러 종류의 **모듈**에 **레이아웃 스킨**을 연결하는 개념입니다. XE로 생성한 모듈 페이지에는 고유한 URL이 있지만, 레이아웃 스킨에는 URL이 없고 **모듈**에 연결된 상황에서만 표시된다는 것을 기억해 주시기 바랍니다.
