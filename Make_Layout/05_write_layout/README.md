# 레이아웃 스킨 만들기

- [레이아웃 스킨이란](../01_about_layout)
- [레이아웃 스킨의 위치와 디렉터리 구조](../02_layout_structure)
 - [레이아웃 스킨의 위치 확인](../02_layout_structure/confirm_directory)
 - [레이아웃 스킨 디렉터리 구조](../02_layout_structure/directory_structure)
- [레이아웃 스킨 정보 작성](../03_write_layout_info)
- [레이아웃 생성](../04_make_layout_instance)
 - [사용자 정의 레이아웃 확인](../04_make_layout_instance/confirm_user_defined_layout)
 - [레이아웃 사본 생성](../04_make_layout_instance/copy_layout)
- 레이아웃 스킨 작성
 - [레이아웃 스킨의 문서 구조](./layout_structure)
 - [{$content} 변수로 본문 출력](./print_content)
 - [글로벌 메뉴 출력](./print_global_menu)
 - [로컬 메뉴 출력](./print_local_menu)
 - [통합검색 양식 출력](./print_search_form)
 - [로그인 양식 출력](./print_login_form)
- [사이트맵 작성](../06_write_sitemap)
- [레이아웃에 사이트맵 연결](../07_link_sitemap)
- [페이지 모듈에 레이아웃 연결](../08_link_layout)
 - [페이지 생성](../08_link_layout/make_page)
 - [페이지 확인](../08_link_layout/confirm_page)
 - [페이지 수정](../08_link_layout/edit_page)

## 레이아웃 스킨 작성

레이아웃 스킨의 내용은 *layout.html*에서 작성합니다.

XE는 *DOCTYPE*, *html*, *head*, *body* 요소를 XE core에서 자동으로 출력한다는 특징이 있습니다. 따라서 스킨 제작자는 이 요소들을 스킨 파일에서 작성할 필요가 없습니다. 스킨 파일에 이 요소들을 포함하면 중첩 문법으로 처리되어 HTML 오류가 발생하거나 화면 깨짐 현상이 발생합니다.

레이아웃 스킨을 적용한 웹 페이지의 기본 구조는 다음과 같습니다.

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html lang=".." xml:lang=".." xmlns="http://www.w3.org/1999/xhtml">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <!-- 이곳에 포함할 내용은 layout.html 문서 또는 관리자 모드에서 작성됨 -->
</head>
<body>
    <!-- layout.html 문서의 코드와 내용은 이곳에 출력된다 -->
</body>
</html>
```

*layout.html* 페이지에서 작성하는 HTML 코드와 내용은 모두 `<body>` 요소 안쪽에 HTML 코드로 출력됩니다. 따라서 스킨 제작자는 `<body>` 요소 안쪽에서 사용할 수 있는 유효한 HTML 문법으로 *layout.html*를 작성해야 합니다. `<head>` 요소에 포함해야 할 내용은 XE 템플릿 문법을 사용하여 `<body>` 요소 내부에서 작성할 수 있습니다.
