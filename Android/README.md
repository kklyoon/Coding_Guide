이 글은 안드로이드 프로젝트를 시작하는 사람들을 위해 작성됨



안드로이드 프로젝트 구조

안드로이드 스튜디오를 실행하여 프로젝트를 생성하면 다음과 같은 화면 일 것이다.

각각의 역할은 다음과 같다.


 
이름 | 용도
-----|-----
.idea | Intellij IDEA 세팅 디렉토리
.gitignore | git 무시 규칙 파일
gradle | gradle-wrapper 파일 디렉토리
build.gradle | apk 빌드 세팅 
settings.gradle | 서브 프로젝트 세팅



# 프로젝트의 어플리케이션 레벨
AndroidManifest.xml 은 모든 안드로이드 어플리케이션의 필수적인 파일이다.
이 파일은 어플리케이션에서 사용하는 activity 목록, 권한, 라이브러리과 같은 어플리케이션의 특성을 정의한다.

 res/drawable 은 이미지파일 ( png. jpeg), 9-Patch images ( 늘이기 혹은 반복적으로 사용되는 이미지), xml 로 정의된 이미지

 res/layout 은 화면을 구성하는 xml 형식의 레이아웃파일, 파일명으로 참조

 res/menu 메뉴 정의

 res/mipmap 앱런처 아이콘 (홈스크린에 표시되는 앱아이콘)

 res/values 컬러, 해상도, 문자열, 스타일 등과 같이 반복되어 사용되는 값들이 정의됨

build.gradle (Module: app) 특정 모듈로 정의됨 app 의 특성, manifest 로 정의된 빌드속성위에 override 됨, 종속된 라이브러리 정의

# Naming Conventions ( 명명 규칙 )

안드로이드 프로젝트의 **공식적인** 명명 규칙은 없다. 그러니 명명 규칙이 굳이 필요하지는 않지만 나름의 룰을 정해서 프로젝트를 수행하는 것이 나중에 프로젝트 관리차원에서 편리하지 않을까?
의미있는 파일이름은 파일안에 무엇이 있는지 찾는데 좋은 장치이다. 특히 프로젝트가 커지면 커질 수록

## strings.xml
접두어에 layout 명이나 영역을 붙인다. Eg. global_ or error_, etc.
모두 소문자 사용

## colors.xml & dimens.xml
element 당 색을 지정하는 대신 어플리케이션의 color theme 을 정의하자.
비슷하게 dimens.xml 파일에는 어플리케이션의 일반적인 공백이나 사이즈 등을 각 component 마다 지정하는 대신 통일시키자

## Layout Files
각 레이아웃의 용도에 따라 아래와 같이 접두어를 붙이자

Component | Prefix
----------|-----
**Activity** | activity_
**Fragment** | fragment_
**Dialog** | dialog_
**AdapterView item** | item_
**Menu** | menu_
**Partial** | partial_

## Resource IDs
안드로이드에서 다른 레이아웃에 있는 같은 이름의 Resource ID 가 허용된다고 할지라도 각각의 이름을 할당해서 쓰는 것이 좋다.

Element | Prefix
--------|--------
**TextView** | `<layout_name>\_txt\_`
**EditText** | `<layout_name>\_et\_`
**Button** | `<layout_name>\_btn\_`
**Menu** | `<layout_name>\_menu\_`
**ListView** | `<layout_name>\_lv\_`
**RecyclerView** | `<layout_name>\_rv\_`
**ImageView** | `<layout_name>\_img\_`
**LinearLayout** | `<layout_name>\_ll\_`
**FrameLayout** | `<layout_name>\_fl\_`
**ConstraintLayout** | `<layout_name>\_cl\_`


## Drawable Files
Asset Type 에 따라 다음과 같이 접두어를 붙인다.

Asset Type | Prefix
-----------|--------
**Button** | btn_
**Dialog** | dialog_
**Divider** | divider_
**Menu** | menu_
**Icon** | ic_
**Image** | img_

이러한 명명법은 안드로이드 프로젝트를 관리하는데 많은 도움이 될 것이다. 물론 100% 이러한 가이드라인에 따를 필요는 없다. 응용은 각자 알아서

## Libraries
라이브러리 추가하는 세가지 방법
- jar 파일 다운 후 app/libs 디렉토리에 jar 파일 추가
- Android Studio 메뉴에서 "File -> Project -> Structure -> app" 에서 + 버튼, "Module dependency"
- build.gradle 파일에 Dependency 

# Reference
<https://medium.com/@mikelimantara/overview-of-android-project-structure-and-naming-conventions-b08f6d0b7291>
<https://www.supinfo.com/articles/single/4036-android-studio-structure-and-naming-best-practices>
<https://github.com/ribot/android-guidelines/blob/master/project_and_code_guidelines.md>
<https://github.com/futurice/android-best-practices>
<http://blog.smartlogic.io/2013-07-09-organizing-your-android-development-code-structure/>
<https://guides.codepath.com/android/Organizing-your-Source-Files>
<http://www.innofied.com/13-android-development-best-practices/>
