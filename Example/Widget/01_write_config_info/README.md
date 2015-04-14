# 위젯 예제

- [위젯](../)
 - config/info.xml 작성
 - [위젯 클래스 개발](../02_develop_widget_class)
 - [확장 변수 사용](../03_use_extra_vars)

## config/info.xml 작성

`info.xml` 파일은 위젯 제작자와 버전, 기타 설정 변수에 관한 정보를 저장합니다. 다음과 같이 작성합니다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<widget version="0.2">
   <title xml:lang="en">Widget title</title>
   <description xml:lang="en">Widget description</description>
   <version>Widget version</version>
   <date>Widget creation date</date>
   <author email_address="..." link="...">
       <name xml:lang="en">Author name</name>
   </author>
   <extra_vars>
       <var id="extensionVariableName">
           <name xml:lang="en">Extension variable name</name>
           <type>Type of extension variable: text | textarea | select | select-multi-order | mid | mid-list | menu </type>
       </var>
   </extra_vars>
</widget>
```
