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
 - 게시물 목록 출력
 - [페이지 번호 링크 출력](../print_page_no)
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

## 게시물 목록 출력

목록에는 공지사항 목록과 일반 게시물 목록이 있습니다. 공지사항 목록은 일반 게시물 목록과 달리 항상 표의 윗부분에 출력됩니다.

예제 게시판 스킨의 *list.html*에서는 다음과 같이 `<tbody>` 요소에 공지사항 목록과 일반 게시물 목록을 출력하도록 작성했습니다.

```html
...
<tbody>
    <!-- NOTICE -->
    <tr class="notice" loop="$notice_list=>$no,$document">
        <block loop="$list_config=>$key,$val">
        <td class="notice" cond="$val->type=='no'">
            <block cond="$document_srl==$document->document_srl">&raquo;</block>
            <block cond="$document_srl!=$document->document_srl">{$lang->notice}</block>
        </td>
        <td class="title" cond="$val->type=='title'">
            <a href="{getUrl('document_srl',$document->document_srl, 'listStyle', $listStyle, 'cpage','')}">
                {$document->getTitle()}
            </a>
            <a cond="$document->getCommentCount()" href="{getUrl('document_srl', $document->document_srl)}#comment" class="replyNum" title="Replies">
                [{$document->getCommentCount()}]
            </a>
            <a cond="$document->getTrackbackCount()" href="{getUrl('document_srl', $document->document_srl)}#trackback" class="trackbackNum" title="Trackbacks">
                [{$document->getTrackbackCount()}]
            </a>
        </td>
        <td class="author" cond="$val->type=='nick_name'">{$document->getNickName()}</td>
        <td class="author" cond="$val->type=='user_id'">{$document->getUserID()}</td>
        <td class="author" cond="$val->type=='user_name'">{$document->getUserName()}</td>
        <td class="time" cond="$val->type=='regdate'">{$document->getRegdate('Y.m.d')}</td>
        <td class="time" cond="$val->type=='last_update'">{zdate($document->get('last_update'),'Y.m.d')}</td>
        <td class="lastReply" cond="$val->type=='last_post'">
            <block cond="(int)($document->get('comment_count'))>0">
                <a href="{$document->getPermanentUrl()}#comment" title="Last Reply">
                    {zdate($document->get('last_update'),'Y.m.d')}
                </a>
                <span cond="$document->get('last_updater')">
                    <sub>by</sub>
                    {htmlspecialchars($document->get('last_updater'))}
                </span>
            </block>
            <block cond="(int)($document->get('comment_count'))==0">&nbsp;</block>
        </td>
        <td class="readNum" cond="$val->type=='readed_count'">{$document->get('readed_count')>0?$document->get('readed_count'):'0'}</td>
        <td class="voteNum" cond="$val->type=='voted_count'">{$document->get('voted_count')!=0?$document->get('voted_count'):'0'}</td>
        </block>
    </tr>
    <!-- /NOTICE -->
    <!-- LIST -->
    <tr loop="$document_list=>$no,$document">
        <block loop="$list_config=>$key,$val">
        <td class="no" cond="$val->type=='no'">
            <block cond="$document_srl==$document->document_srl">&raquo;</block>
            <block cond="$document_srl!=$document->document_srl">{$no}</block>
        </td>
        <td class="title" cond="$val->type=='title'">
            <a href="{getUrl('document_srl',$document->document_srl, 'listStyle', $listStyle, 'cpage','')}">
                {$document->getTitle()}
            </a>
            <a cond="$document->getCommentCount()" href="{getUrl('document_srl', $document->document_srl)}#comment" class="replyNum" title="Replies">
                [{$document->getCommentCount()}]
            </a>
            <a cond="$document->getTrackbackCount()" href="{getUrl('document_srl', $document->document_srl)}#trackback" class="trackbackNum" title="Trackbacks">
                [{$document->getTrackbackCount()}]
            </a>
        </td>
        <td class="author" cond="$val->type=='nick_name'">{$document->getNickName()}</td>
        <td class="author" cond="$val->type=='user_id'">{$document->getUserID()}</td>
        <td class="author" cond="$val->type=='user_name'">{$document->getUserName()}</td>
        <td class="time" cond="$val->type=='regdate'">{$document->getRegdate('Y.m.d')}</td>
        <td class="time" cond="$val->type=='last_update'">{zdate($document->get('last_update'),'Y.m.d')}</td>
        <td class="lastReply" cond="$val->type=='last_post'">
            <block cond="(int)($document->get('comment_count'))>0">
                <a href="{$document->getPermanentUrl()}#comment" title="Last Reply">
                    {zdate($document->get('last_update'),'Y.m.d')}
                </a>
                <span cond="$document->get('last_updater')">
                    <sub>by</sub>
                    {htmlspecialchars($document->get('last_updater'))}
                </span>
            </block>
            <block cond="(int)($document->get('comment_count'))==0">&nbsp;</block>
        </td>
        <td class="readNum" cond="$val->type=='readed_count'">{$document->get('readed_count')>0?$document->get('readed_count'):'0'}</td>
        <td class="voteNum" cond="$val->type=='voted_count'">{$document->get('voted_count')!=0?$document->get('voted_count'):'0'}</td>
        </block>
    </tr>
    <!-- /LIST -->
</tbody>
...
```

위 코드에서 사용된 템플릿 문법과 변수는 다음과 같습니다.

|XE 템플릿 문법/변수|설명|
|---|---|
|`<tr class="notice" loop="$notice_list=>$no,$document">`|공지 게시물 목록 행을 반복|
|`<tr loop="$document_list=>$no,$document">`|일반 게시물 목록 행을 반복|
|`<block loop="$list_config=>$key,$val">`|게시물 표시 항목 열을 반복|
|`<block cond="$document_srl==$document->document_srl">&raquo;</block>`|게시물의 고유 번호와 현재 페이지 게시물의 고유 번호가 일치하면 오른쪽 이중 꺾은 괄호(>>) 출력|
|`<block cond="$document_srl!=$document->document_srl">{$lang->notice}</block>`|게시물의 고유 번호와 현재 페이지 게시물의 고유 번호가 일치하지 않으면 **공지** 출력|
|`<block cond="$document_srl!=$document->document_srl">{$no}</block>`|게시물의 고유 번호와 현재 페이지 게시물의 고유 번호가 일치하지 않으면 **게시물 번호** 출력|
|`<td class="title" cond="$val->type=='title'">`|게시물 제목 셀|
|`<a href="{getUrl('document_srl',$document->document_srl, 'listStyle', $listStyle, 'cpage','')}">...</a>`|게시물 링크|
|`{$document->getTitle()}`|게시물 제목 출력|
|`<a cond="$document->getCommentCount()" href="{getUrl('document_srl', $document->document_srl)}#comment" class="replyNum" title="Replies">[...]</a>`|게시물 댓글 링크|
|`{$document->getCommentCount()}`|게시물 댓글 수|
|`<a cond="$document->getTrackbackCount()" href="{getUrl('document_srl', $document->document_srl)}#trackback" class="trackbackNum" title="Trackbacks">[...]</a>`|게시물 엮인글 링크|
|`{$document->getTrackbackCount()}`|게시물 엮인글 수|
|`<td class="author" cond="$val->type=='nick_name'">{$document->getNickName()}</td>`|닉네임|
|`<td class="author" cond="$val->type=='user_id'">{$document->getUserID()}</td>`|아이디|
|`<td class="author" cond="$val->type=='user_name'">{$document->getUserName()}</td>`|이름|
|`<td class="time" cond="$val->type=='regdate'">{$document->getRegdate('Y.m.d')}</td>`|날짜|
|`<td class="time" cond="$val->type=='last_update'">{zdate($document->get('last_update'),'Y.m.d')}</td>`|최종 수정일|
|`<td class="lastReply" cond="$val->type=='last_post'">...</td>`|최종 글|
|`<block cond="(int)($document->get('comment_count'))>0">...</block>`|댓글이 하나 이상이면 출력|
|`<block cond="(int)($document->get('comment_count'))==0">...</block>`|댓글이 없으면 출력|
|`<a href="{$document->getPermanentUrl()}#comment" title="Last Reply">{zdate($document->get('last_update'),'Y.m.d')}</a>`|최종 댓글 날짜 + 링크|
|`<span cond="$document->get('last_updater')">...</span>`|최종 댓글 작성자|
|`<td class="readNum" cond="$val->type=='readed_count'">...</td>`|조회 수|
|`<td class="voteNum" cond="$val->type=='voted_count'">...</td>`|추천 수|

> 일반 게시물 목록의 출력 개수는 XE 관리자 페이지의 고급 > 설치된 모듈 > 게시판에서 수정할 모듈 오른쪽의 설정을 클릭하고 *게시판 정보 > 기본* 탭에서 목록 수를 설정하여 변경할 수 있습니다. 기본값은 20입니다.
