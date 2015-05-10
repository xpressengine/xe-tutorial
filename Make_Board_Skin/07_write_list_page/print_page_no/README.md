# 게시판 스킨 만들기

- [게시판 스킨이란](../../01_about_board_skin)
- [게시판 모듈 설치](../../02_install_board_module)
 - [쉬운 설치](../../02_install_board_module/autoinstall)
 - [소스 파일 업로드](../../02_install_board_module/upload_sources)
- [게시판 스킨의 위치와 필수 파일](../../03_board_skin_structure)
 - [게시판 스킨의 위치 확인](../../03_board_skin_structure/confirm_directory)
 - [게시판 스킨 필수 파일](../../03_board_skin_structure/required_files)
- [게시판 스킨 정보 작성](../../04_write_board_skin_info)
- [게시판 생성 및 스킨 적용](../../05_make_board_n_apply_skin)
- [게시판 헤더/푸터 작성](../../06_write_header_n_footer)
 - [헤더 작성](../../06_write_header_n_footer/write_header)
 - [푸터 작성](../../06_write_header_n_footer/write_footer)
- [목록 페이지 작성](../)
 - [_header.html, _footer.html 포함(include)](../include_header_n_footer)
 - [게시물이 없을 때 메시지 출력](../show_message_when_no_document)
 - [게시물 목록을 표로 작성](../listing_documents)
 - [게시물 목록 헤더 출력](../print_list_header)
 - [게시물 목록 출력](../print_list)
 - 페이지 번호 링크 출력
 - [쓰기 버튼 출력](../print_write_btn)
 - [게시판 검색 입력 양식 출력](../print_search_form)
 - [게시판 목록 화면 출력 결과 확인](../confirm_print_list)
- [쓰기 페이지 작성](../../08_write_writing_page)
 - [_header.html, _footer.html 포함(include)](../../08_write_writing_page/include_header_n_footer)
 - [쓰기 화면의 HTML 구조](../../08_write_writing_page/html_structure_write_form)
 - [쓰기 양식 작성](../../08_write_writing_page/write_writing_form)
 - [제목 입력 창 작성](../../08_write_writing_page/write_title_form)
 - [내용 입력 창(편집 창) 작성](../../08_write_writing_page/write_input_form)
 - [글쓴이 정보 입력 창 작성](../../08_write_writing_page/write_author_form)
 - [등록 버튼 출력](../../08_write_writing_page/print_write_btn)
 - [쓰기 페이지 출력 결과 확인](../../08_write_writing_page/confirm_write_form)
- [읽기 페이지 작성](../../09_write_reading_page)
 - [list.html에 _read.html 포함(include)](../../09_write_reading_page/include_header_n_footer)
 - [읽기 페이지 구조](../../09_write_reading_page/structure_read_form)
 - [제목, 글쓴이 출력](../../09_write_reading_page/print_title_n_author)
 - [조회수, 추천 수, 날짜 출력](../../09_write_reading_page/print_num_list)
 - [게시물 본문 출력](../../09_write_reading_page/print_content)
 - [첨부 파일 출력](../../09_write_reading_page/print_attach_files)
 - [목록, 수정, 삭제 버튼 출력](../../09_write_reading_page/print_btns)
 - [엮인글 목록, 댓글 목록 포함(include)](../../09_write_reading_page/include_trackback_n_comment_list)
 - [게시물에 대한 댓글 입력 양식 출력](../../09_write_reading_page/print_input_comment_form)
- [엮인글/댓글 관련 페이지 작성](../../10_write_trackback_n_comment_page)
 - [엮인글 목록 작성](../../10_write_trackback_n_comment_page/write_trackback_form)
 - [댓글 목록 작성](../../10_write_trackback_n_comment_page/write_comment_form)
 - [댓글의 댓글 쓰기 및 댓글 수정 페이지 작성](../../10_write_trackback_n_comment_page/write_recomment_n_edit_form)
- [삭제 페이지 작성](../../11_write_deleting_page)
 - [게시물 삭제 페이지 작성](../../11_write_deleting_page/write_delete_document_form)
 - [댓글 삭제 페이지 작성](../../11_write_deleting_page/write_delete_comment_form)
 - [엮인글 삭제 페이지 작성](../../11_write_deleting_page/write_delete_trackback_form)
- [권한 안내 페이지 작성](../../12_write_grant_page)
- [비밀번호 입력 페이지 작성](../../13_write_password_page)

## 페이지 번호 링크 출력

게시물의 수가 한 페이지를 넘어가면 과거에 작성된 게시물을 탐색할 수 있도록 페이지 이동 링크를 제공해야 합니다.

예제 게시판 스킨의 *list.html*에서는 게시물 목록 아래쪽에 다음과 같이 페이지 번호 링크를 출력하도록 작성했습니다. 페이지 번호를 `<div class="list_footer">...</div>` 요소로 한 번 더 감싼 이유는 이 요소 안쪽에 쓰기 버튼과 검색 입력 양식을 추가로 포함할 예정이기 때문입니다.

```html
<table summary="List of Articles" id="board_list" class="board_list">
    <!-- LIST HEADER -->
    <!-- /LIST HEADER -->
    <!-- NOTICE -->
    <!-- /NOTICE -->
    <!-- LIST -->
    <!-- /LIST -->
</table>
<div class="list_footer">
    <!-- PAGINATION -->
    <div class="pagination" cond="$document_list || $notice_list">
        <a href="{getUrl('page','','document_srl','','division',$division,'last_division',$last_division)}" class="prevEnd">{$lang->first_page}</a> 
        <block loop="$page_no=$page_navigation->getNextPage()">
                <strong cond="$page==$page_no">{$page_no}</strong> 
                <a cond="$page!=$page_no" href="{getUrl('page',$page_no,'document_srl','','division',$division,'last_division',$last_division)}">{$page_no}</a>
        </block>
        <a href="{getUrl('page',$page_navigation->last_page,'document_srl','','division',$division,'last_division',$last_division)}" class="nextEnd">{$lang->last_page}</a>
    </div>
    <!-- /PAGINATION -->
</div>
<include target="_footer.html" />
```

위 코드에서 사용된 템플릿 문법과 변수는 다음과 같습니다.

|XE 템플릿 문법/변수|설명|
|---|---|
|`<div class="pagination" cond="$document_list || $notice_list">...</div>`|게시물이 있거나 공지가 하나라도 있을 때 페이지 번호를 출력|
|`<a href="{getUrl('page','','document_srl','','division',$division,'last_division',$last_division)}" class="prevEnd">{$lang->first_page}</a>`|첫 페이지 링크|
|`<a href="{getUrl('page',$page_navigation->last_page,'document_srl','','division',$division,'last_division',$last_division)}" class="nextEnd">{$lang->last_page}</a>`|끝 페이지 링크|
|`<block loop="$page_no=$page_navigation->getNextPage()">...</block>`|페이지 번호를 반복|
|`<strong cond="$page==$page_no">{$page_no}</strong>`|페이지 번호가 현재 페이지와 일치하면 출력|
|`<a cond="$page!=$page_no" href="{getUrl('page',$page_no,'document_srl','','division',$division,'last_division',$last_division)}">{$page_no}</a>`|페이지 번호가 현재 페이지와 일치하지 않으면 출력|
