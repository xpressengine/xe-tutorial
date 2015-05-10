# 게시판 스킨 만들기

- [게시판 스킨이란](../01_about_board_skin)
- [게시판 모듈 설치](../02_install_board_module)
 - [쉬운 설치](../02_install_board_module/autoinstall)
 - [소스 파일 업로드](../02_install_board_module/upload_sources)
- [게시판 스킨의 위치와 필수 파일](../03_board_skin_structure)
 - [게시판 스킨의 위치 확인](../03_board_skin_structure/confirm_directory)
 - [게시판 스킨 필수 파일](../03_board_skin_structure/required_files)
- 게시판 스킨 정보 작성
- [게시판 생성 및 스킨 적용](../05_make_board_n_apply_skin)
- [게시판 헤더/푸터 작성](../06_write_header_n_footer)
 - [헤더 작성](../06_write_header_n_footer/write_header)
 - [푸터 작성](../06_write_header_n_footer/write_footer)
- [목록 페이지 작성](../07_write_list_page)
 - [_header.html, _footer.html 포함(include)](../07_write_list_page/include_header_n_footer)
 - [게시물이 없을 때 메시지 출력](../07_write_list_page/show_message_when_no_document)
 - [게시물 목록을 표로 작성](../07_write_list_page/listing_documents)
 - [게시물 목록 헤더 출력](../07_write_list_page/print_list_header)
 - [게시물 목록 출력](../07_write_list_page/print_list)
 - [페이지 번호 링크 출력](../07_write_list_page/print_page_no)
 - [쓰기 버튼 출력](../07_write_list_page/print_write_btn)
 - [게시판 검색 입력 양식 출력](../07_write_list_page/print_search_form)
 - [게시판 목록 화면 출력 결과 확인](../07_write_list_page/confirm_print_list)
- [쓰기 페이지 작성](../08_write_writing_page)
 - [_header.html, _footer.html 포함(include)](../08_write_writing_page/include_header_n_footer)
 - [쓰기 화면의 HTML 구조](../08_write_writing_page/html_structure_write_form)
 - [쓰기 양식 작성](../08_write_writing_page/write_writing_form)
 - [제목 입력 창 작성](../08_write_writing_page/write_title_form)
 - [내용 입력 창(편집 창) 작성](../08_write_writing_page/write_input_form)
 - [글쓴이 정보 입력 창 작성](../08_write_writing_page/write_author_form)
 - [등록 버튼 출력](../08_write_writing_page/print_write_btn)
 - [쓰기 페이지 출력 결과 확인](../08_write_writing_page/confirm_write_form)
- [읽기 페이지 작성](../09_write_reading_page)
 - [list.html에 _read.html 포함(include)](../09_write_reading_page/include_header_n_footer)
 - [읽기 페이지 구조](../09_write_reading_page/structure_read_form)
 - [제목, 글쓴이 출력](../09_write_reading_page/print_title_n_author)
 - [조회수, 추천 수, 날짜 출력](../09_write_reading_page/print_num_list)
 - [게시물 본문 출력](../09_write_reading_page/print_content)
 - [첨부 파일 출력](../09_write_reading_page/print_attach_files)
 - [목록, 수정, 삭제 버튼 출력](../09_write_reading_page/print_btns)
 - [엮인글 목록, 댓글 목록 포함(include)](../09_write_reading_page/include_trackback_n_comment_list)
 - [게시물에 대한 댓글 입력 양식 출력](../09_write_reading_page/print_input_comment_form)
- [엮인글/댓글 관련 페이지 작성](../10_write_trackback_n_comment_page)
 - [엮인글 목록 작성](../10_write_trackback_n_comment_page/write_trackback_form)
 - [댓글 목록 작성](../10_write_trackback_n_comment_page/write_comment_form)
 - [댓글의 댓글 쓰기 및 댓글 수정 페이지 작성](../10_write_trackback_n_comment_page/write_recomment_n_edit_form)
- [삭제 페이지 작성](../11_write_deleting_page)
 - [게시물 삭제 페이지 작성](../11_write_deleting_page/write_delete_document_form)
 - [댓글 삭제 페이지 작성](../11_write_deleting_page/write_delete_comment_form)
 - [엮인글 삭제 페이지 작성](../11_write_deleting_page/write_delete_trackback_form)
- [권한 안내 페이지 작성](../12_write_grant_page)
- [비밀번호 입력 페이지 작성](../13_write_password_page)

## 게시판 스킨 정보 작성

*skin.xml*은 게시판 스킨의 기본 정보를 포함하며 관리자 화면에 보여줄 설명과 옵션을 제공합니다. *skin.xml*의 이름은 바꿀 수 없습니다.

*skin.xml*의 기본 구조는 다음과 같습니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<skin version="0.2">
    <title xml:lang="ko">user_board</title>
    <title xml:lang="en">user_board</title>
    <title xml:lang="jp">user_board</title>
    <description xml:lang="ko">게시판 스킨 제작 실습을 위한 user_board입니다.</description>
    <description xml:lang="en">This is user_board for creating a board skin.</description>
    <description xml:lang="jp">掲示板スキン製作実習のためのuser_boardです。</description>
    <version>1.0</version>
    <date>2010-12-24</date>
    <author email_address="user@user.com" link="http://user-define.com/">
        <name xml:lang="ko">제작자 이름</name>
        <name xml:lang="en">Author Name</name>
        <name xml:lang="jp">製作者名</name>
    </author>
    <license>LGPL v2</license>
    <extra_vars>
        <var name="title" type="text">
            <title xml:lang="ko">게시판 제목</title>
            <title xml:lang="en">Board Title</title>
            <title xml:lang="jp">掲示板タイトル</title>
			<description xml:lang="ko">작성하면 화면에 표시됨</description>
			<description xml:lang="en">This will be displayed on the screen as you write.</description>
			<description xml:lang="jp">作成すると画面に表示される</description>
        </var>
        <var name="comment" type="textarea">
            <title xml:lang="ko">게시판 설명</title>
            <title xml:lang="en">Board Details</title>
            <title xml:lang="jp">掲示板詳細説明</title>
			<description xml:lang="ko">작성하면 화면에 표시됨</description>
			<description xml:lang="en">This will be displayed on the screen as you write.</description>
			<description xml:lang="jp">作成すると画面に表示される</description>
        </var>
    </extra_vars>
</skin>
```

이 코드의 내용은 다음과 같습니다.

|코드|설명|
|---|---|
|`<?xml version="1.0" encoding="UTF-8"?>`|XML 문서 형식 선언|
|`<skin version="0.2">`|스킨 정보 문서임을 선언. version에는 XE core에서 지원하는 버전을 표시해야 합니다. XE core 1.4.4.2를 기준으로 지원하는 버전은 0.2입니다.|
|`<title xml:lang="ko">...</title>`|게시판 스킨의 이름|
|`<description xml:lang="ko">...</description>`|게시판 스킨의 설명|
|`<version>...</version>`|게시판 스킨의 버전|
|`<date>YYYY-MM-DD</date>`|게시판 스킨 제작 날짜. 년-월-일(YYYY-MM-DD) 형식으로 작성해야 합니다.|
|`<author email_address="..." link="...">...</author>`|게시판 스킨 제작자 정보. 이메일 주소, 웹 사이트 주소, 제작자 이름을 작성합니다.|
|`<license>LGPL v2</license>`|게시판 스킨 라이선스 정보. XE core와 동일한 LGPL v2 라이선스를 권장합니다.|
|`<extra_vars>...</extra_vars>`|게시판 모듈에서 지원하는 확장 변수를 사용하려면 태그 안쪽에 내용을 추가할 수 있습니다.|
|`<var name="title" type="text">...</var>`|게시판의 제목을 입력받아서 화면에 표시합니다.|
|`<var name="title" type="textarea"></var>`|게시판의 설명을 입력받아서 화면에 표시합니다.|

게시판 스킨의 *skin.xml* 문서가 제대로 작성되었는지 확인하려면 게시판을 하나 생성한 다음, 스킨을 사용하도록 설정합니다.

이 밖에도 *skin.xml*에는 사용자 정의 가능한 여러 타입의 변수를 `<extra_vars>` 요소 안에 추가로 포함할 수 있습니다. 다음은 스킨 제작자가 *select*, *image* 타입의 데이터를 입력받아서 변수로 사용할 수 있도록 확장한 예제입니다.

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
        <var name="board_image" type="image">
            <title xml:lang="ko">게시판 헤더 이미지</title>
            <description xml:lang="ko">게시판 상단에 출력할 이미지를 입력하세요.</description>
        </var>
    </extra_vars>
    ...
</layout>
```

위 코드에서 사용된 확장 변수는 다음과 같습니다.

|변수|설명|
|---|---|
|`<var name="colorset" type="select">...</var>`|*select* 타입의 확장 변수. `{$module_info->colorset}` 형식으로 출력 가능|
|`<var name="board_image" type="image">...</var>`|*image* 타입의 확장 변수. `{$module_info->image}` 형식으로 출력 가능|

*skin.xml*에서 추가된 확장 변수는 XE 관리자 페이지의 *고급 > 설치된 모듈 > 게시판 > 설정 > 스킨 관리* 페이지에 표시됩니다. 게시판 관리자가 해당 변수에 값을 입력하면 스킨에서 출력할 수 있습니다.
