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
 - 글로벌 메뉴 출력
 - [로컬 메뉴 출력](../print_local_menu)
 - [통합검색 양식 출력](../print_search_form)
 - [로그인 양식 출력](../print_login_form)
- [사이트맵 작성](../../06_write_sitemap)
- [레이아웃에 사이트맵 연결](../../07_link_sitemap)
- [페이지 모듈에 레이아웃 연결](../../08_link_layout)
 - [페이지 생성](../../08_link_layout/make_page)
 - [페이지 확인](../../08_link_layout/confirm_page)
 - [페이지 수정](../../08_link_layout/edit_page)

## 글로벌 메뉴 출력

`<div class="gnb">.gnb</div>` 요소 내부에 레이아웃과 연결된 글로벌 메뉴를 출력할 수 있습니다.

XE 관리자 페이지에서 레이아웃과 메뉴를 연결하면 레이아웃은 항상 연결된 메뉴를 화면에 표시하는데, 이때 연결된 메뉴를 표시할 수 있도록 레이아웃 스킨에서 미리 코드를 작성해야 합니다.

예제 레이아웃 스킨에서는 다음과 같이 연결된 메뉴를 화면에 출력하는 코드를 작성했습니다. 메뉴를 최대 2단계까지 출력합니다.

```html
<div class="gnb">
    .gnb
    <ul>
        <li loop="$global_menu->list=>$key1,$val1" class="active"|cond="$val1['selected']"><a href="{$val1['href']}" target="_blank"|cond="$val1['open_window']=='Y'">{$val1['link']}</a>
            <ul cond="$val1['list']">
                <li loop="$val1['list']=>$key2,$val2" class="active"|cond="$val2['selected']"><a href="{$val2['href']}" target="_blank"|cond="$val2['open_window']=='Y'">{$val2['link']}</a></li>
            </ul>
        </li>
    </ul>
</div>
```

위 코드에서 사용된 템플릿 문법과 변수는 다음과 같습니다.

|템플릿 문법/변수|설명|구분|
|---|---|---|
|`loop="$global_menu->list=>$key1,$val1"`|연결 메뉴 목록이 있으면 출력|반복문|
|`cond="$val1['list']"`|연결 메뉴가 하위 목록을 포함하면 출력|조건문|
|`loop="$val1['list']=>$key2,$val2"`|연결 메뉴가 하위 목록을 포함하면 출력|반복문|
|`class="active"|cond="$val1['selected']"` `class="active"|cond="$val2['selected']"`|연결 메뉴 또는 연결 메뉴 하위 목록과 현재 페이지가 일치하면 `<li>` 요소에 `class="active"` 속성을 추가|조건문|
|`target="_blank"|cond="$val1['open_window']=='Y'"` `target="_blank"|cond="$val2['open_window']=='Y'"`|연결 메뉴 링크 옵션이 새 창이면 target="_blank" 출력|조건문|
|`{$val1['href']}` `{$val2['href']}`|연결 메뉴 링크 URL|변수|
|`{$val1['link']}` `{$val2['link']}`|연결 메뉴 링크 텍스트|변수|
