# 게시판 스킨 만들기

- [게시판 스킨이란](../../01_about_board_skin)
- [게시판 모듈 설치](../../02_install_board_module)
 - [쉬운 설치](../../02_install_board_module/autoinstall)
 - [소스 파일 업로드](../../02_install_board_module/upload_sources)
- [게시판 스킨의 위치와 필수 파일](../)
 - [게시판 스킨의 위치 확인](../confirm_directory)
 - 게시판 스킨 필수 파일
- [게시판 스킨 정보 작성](../../04_write_board_skin_info)
- [게시판 생성 및 스킨 적용](../../05_make_board_n_apply_skin)
- [게시판 헤더/푸터 작성](../../06_write_header_n_footer)
 - [헤더 작성](../../06_write_header_n_footer/write_header)
 - [푸터 작성](../../06_write_header_n_footer/write_footer)
- [목록 페이지 작성](../../07_write_list_page)
 - [_header.html, _footer.html 포함(include)](../../07_write_list_page/include_header_n_footer)
 - [게시물이 없을 때 메시지 출력](../../07_write_list_page/show_message_when_no_document)
 - [게시물 목록을 표로 작성](../../07_write_list_page/listing_documents)
 - [게시물 목록 헤더 출력](../../07_write_list_page/print_list_header)
 - [게시물 목록 출력](../../07_write_list_page/print_list)
 - [페이지 번호 링크 출력](../../07_write_list_page/print_page_no)
 - [쓰기 버튼 출력](../../07_write_list_page/print_write_btn)
 - [게시판 검색 입력 양식 출력](../../07_write_list_page/print_search_form)
 - [게시판 목록 화면 출력 결과 확인](../../07_write_list_page/confirm_print_list)
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

## 게시판 스킨 필수 파일

게시판 스킨을 만들려면 다음과 같은 필수 파일이 필요합니다.

|파일|설명|비고|
|---|---|---|
|skin.xml|게시판 스킨 정보|파일 이름 변경할 수 없음|
|list.html|게시물 목록|파일 이름 변경할 수 없음|
|write_form.html|게시물 쓰기 양식|파일 이름 변경할 수 없음|
|delete_form.html|게시물 삭제 양식|파일 이름 변경할 수 없음|
|comment_form.html|댓글 쓰기 양식|파일 이름 변경할 수 없음|
|delete_comment_form.html|댓글 삭제 양식|파일 이름 변경할 수 없음|
|delete_trackback_form.html|엮인글 삭제 양식|파일 이름 변경할 수 없음|
|input_password_form.html|비밀번호 입력 양식|파일 이름 변경할 수 없음|
|message.html|알림 메시지|파일 이름 변경할 수 없음|
|_header.html|게시판 헤더 출력|다른 페이지에 포함(include)됨|
|_footer.html|게시판 푸터 출력|다른 페이지에 포함(include)됨|
|_read.html|게시물 읽기 페이지 출력|다른 페이지에 포함(include)됨|
|_comment.html|댓글 출력|다른 페이지에 포함(include)됨|
|_trackback.html|엮인글 출력|다른 페이지에 포함(include)됨|
|user_board.css|게시판 스킨 스타일시트|&nbsp;|
