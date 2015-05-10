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
 - 로컬 메뉴 출력
 - [통합검색 양식 출력](../print_search_form)
 - [로그인 양식 출력](../print_login_form)
- [사이트맵 작성](../../06_write_sitemap)
- [레이아웃에 사이트맵 연결](../../07_link_sitemap)
- [페이지 모듈에 레이아웃 연결](../../08_link_layout)
 - [페이지 생성](../../08_link_layout/make_page)
 - [페이지 확인](../../08_link_layout/confirm_page)
 - [페이지 수정](../../08_link_layout/edit_page)

## 로컬 메뉴 출력

`<div class="lnb">.lnb</div>` 요소 내부에 레이아웃과 연결된 로컬 메뉴를 출력할 수 있습니다. 로컬 메뉴를 출력하는 문법은 기본적으로 글로벌 메뉴를 출력하는 방법과 유사합니다.

글로벌 메뉴와 로컬 메뉴 출력의 다른 점은 로컬 메뉴가 1단계 메뉴를 표시하지 않는다는 점입니다. 글로벌 메뉴가 `<div class="gnb">.gnb</div>` 영역에 이미 1~2단계를 표시하고 있기 때문에 로컬 메뉴는 현재 페이지를 기준으로 관련된 2~3단계 메뉴를 표시합니다.

로컬 메뉴는 메뉴에 연결된 페이지가 있을 때에만 출력되기 때문에 메뉴를 생성하는 과정에서 실제 연결할 수 있는 페이지의 URL을 입력해야 합니다.

예제 레이아웃 스킨에서는 다음과 같이 로컬 메뉴 출력 코드를 작성했습니다.

```html
<div class="lnb">
    .lnb
    <h2 loop="$global_menu->list=>$key1,$val1" cond="$val1['selected']"><a href="{$val1['href']}" target="_blank"|cond="$val1['open_window']=='Y'">{$val1['link']}</a></h2>
    <ul loop="$global_menu->list=>$key1,$val1" cond="$val1['selected'] && $val1['list']">
        <li loop="$val1['list']=>$key2,$val2" class="active"|cond="$val2['selected']"><a href="{$val2['href']}" target="_blank"|cond="$val2['open_window']=='Y'">{$val2['link']}</a>
            <ul cond="$val2['list']">
                <li loop="$val2['list']=>$key3,$val3" class="active"|cond="$val3['selected']"><a href="{$val3['href']}" target="_blank"|cond="$val3['open_window']=='Y'">{$val3['link']}</a>
                </li>
            </ul>
        </li>
    </ul>
</div>
```

위 코드에서 사용된 템플릿 문법과 변수는 다음과 같습니다.

|템플릿 문법/변수|설명|구분|
|---|---|---|
|`loop="$global_menu->list=>$key1,$val1"`|연결 메뉴 목록이 있으면 출력|반복문|
|`cond="$val1['selected']"`|연결 메뉴와 현재 페이지가 일치하면 내용을 출력|조건문|
|`cond="$val1['selected'] && $val1['list']"`|연결 메뉴와 현재 페이지가 일치하고 동시에 하위 목록을 포함하면 출력|조건문|
|`loop="$val1['list']=>$key2,$val2"` `loop="$val2['list']=>$key3,$val3"`|연결 메뉴가 하위 목록을 포함하면 출력|반복문|
|`cond="$val2['list']"`|연결 메뉴가 하위 목록을 포함하면 출력|조건문|
|`class="active"|cond="$val2['selected']"` `class="active"|cond="$val3['selected']"`|연결 메뉴 또는 연결 메뉴 하위 목록과 현재 페이지가 일치하면 `<li>` 요소에 `class="active"` 속성을 추가|조건문|
|`target="_blank"|cond="$val1['open_window']=='Y'"` `target="_blank"|cond="$val2['open_window']=='Y'"` `target="_blank"|cond="$val3['open_window']=='Y'"`|연결 메뉴 링크 옵션이 새 창이면 target="_blank" 출력|조건문|
|`{$val1['href']}` `{$val2['href']}` `{$val3['href']}`|연결 메뉴 링크 URL|변수|
|`{$val1['link']}` `{$val2['link']}` `{$val3['link']}`|연결 메뉴 링크 텍스트|변수|
