# 위젯 예제

- 위젯
 - [config/info.xml 작성](./01_write_config_info)
 - [위젯 클래스 개발](./02_develop_widget_class)
 - [확장 변수 사용](./03_use_extra_vars)

위젯은 화면에서 데이터를 출력하는 데 사용되는 컴포넌트입니다. 위젯은 최신 글과 회원 정보 같은 기존 모듈이나 외부 API로부터 추출한 데이터와 함께 연동할 수 있습니다. 위젯은 모든 종류의 페이지에 추가할 수 있으며 레이아웃에 직접 추가할 수도 있습니다. 위젯을 통해 출력되는 콘텐츠를 쉽게 커스터마이즈할 수 있습니다.

위젯은 관리자가 수동으로 페이지 모듈에 입력하고 `<img />` 요소에 저장합니다. 출력할 웹 페이지를 호출할 때 `widgetController::triggerWidgetCompile()` 트리거가 `widgetproc()`를 사용해서 `<img />` 요소의 코드를 실행하고 올바른 HTML 코드로 변환합니다.
