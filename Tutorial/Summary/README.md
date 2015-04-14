# 개요

XE core는 개발자들이 원하는 웹 애플리케이션을 만드는 기반이 되는 프레임워크입니다. XE core는 회원 관리, 문서/댓글뿐만 아니라 DBMS의 종류와 상관없이 데이터를 관리할 수 있는 기능도 제공합니다. XE 자체가 MVC(Model-View-Controller) 구조로 되어 있어 완벽한 SoC(Separation of Concerns)를 구현할 수 있습니다.  

XE 애플리케이션으로 유입되는 모든 요청은 index.php에서 처리합니다. 이 페이지는 요청 컨텍스트를 초기화하고 적절한 모듈을 찾아서 클라이언트(브라우저)로 응답을 보내는 역할을 담당합니다.  

XE의 기능 대부분이 모듈로 이루어져 있습니다. XE는 요청이 들어오면 모듈 이름과 액션 이름(없으면 기본값 사용)을 기준으로 어떤 모듈을 사용할지 정합니다. 예를 들어 관리자 페이지를 표시하려면 URL은 `index.php?module=admin&act=dispBoardAdminContent`가 됩니다.