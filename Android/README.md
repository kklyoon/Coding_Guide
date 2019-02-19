이 글은 안드로이드 프로젝트를 시작하는 사람들을 위해 작성됨



안드로이드 프로젝트 구조

안드로이드 스튜디오를 실행하여 프로젝트를 생성하면 다음과 같은 화면 일 것이다.

각각의 역할은 다음과 같다.


<center><img src="res/android_dir_struct.png" width="50%" height="50%"></center>
 
|이름            | 용도                       |
|----------------|---------------------------|
|build.gradle    | apk 빌드 세팅              |
|settings.gradle | 서브 프로젝트 세팅          |
|.idea           | Intellij IDEA 세팅 디렉토리|
|.gitignore      | git 무시 규칙 파일         |
|gradle          | gradle-wrapper 파일 디렉토리|



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
**TextView** | `<layout_name>_txt_`
**EditText** | `<layout_name>_et_`
**Button** | `<layout_name>_btn_`
**Menu** | `<layout_name>_menu_`
**ListView** | `<layout_name>_lv_`
**RecyclerView** | `<layout_name>_rv_`
**ImageView** | `<layout_name>_img_`
**LinearLayout** | `<layout_name>_ll_`
**FrameLayout** | `<layout_name>_fl_`
**ConstraintLayout** | `<layout_name>_cl_`


## Drawable Files
Asset Type 에 따라 다음과 같이 접두어를 붙인다.

Asset Type | Prefix | Example
-----------|--------|---------
**Button** | `btn_` | `btn_send.png`
**Dialog** | `dialog_` | `dialog_top.png`
**Divider** | `divider_` | `divider_horizontal.png`
**Menu** | `menu_` | `menu_submenu_bg.png`
**Icon** | `ic_` | `ic_start.png`
**Image** | `img_` | `img_sample.png`
**Action bar** | `ab_` | `ab_stacked.png`
**Notification** | `notification_` | `notification_bg.png`
**Tabs** | `tab_` | `tab_pressed.png`

아이콘도 종류에 따라서 다음과 같이 나눈다.

| Asset Type                      | Prefix             | Example                      |
| --------------------------------| ----------------   | ---------------------------- |
| Icons                           | `ic_`              | `ic_star.png`                |
| Launcher icons                  | `ic_launcher`      | `ic_launcher_calendar.png`   |
| Menu icons and Action Bar icons | `ic_menu`          | `ic_menu_archive.png`        |
| Status bar icons                | `ic_stat_notify`   | `ic_stat_notify_msg.png`     |
| Tab icons                       | `ic_tab`           | `ic_tab_recent.png`          |
| Dialog icons                    | `ic_dialog`        | `ic_dialog_info.png`         |

selector 도 다음과 같이 나눈다.

| State	       | Suffix          | Example                     |
|--------------|-----------------|-----------------------------|
| Normal       | `_normal`       | `btn_order_normal.9.png`    |
| Pressed      | `_pressed`      | `btn_order_pressed.9.png`   |
| Focused      | `_focused`      | `btn_order_focused.9.png`   |
| Disabled     | `_disabled`     | `btn_order_disabled.9.png`  |
| Selected     | `_selected`     | `btn_order_selected.9.png`  |




## Libraries
라이브러리 추가하는 세가지 방법
- jar 파일 다운 후 app/libs 디렉토리에 jar 파일 추가
- Android Studio 메뉴에서 "File -> Project -> Structure -> app" 에서 + 버튼, "Module dependency"
- build.gradle 파일에 Dependency 

# Reference

<https://developer.android.com/studio/build/>

<https://medium.com/@mikelimantara/overview-of-android-project-structure-and-naming-conventions-b08f6d0b7291>

<https://www.supinfo.com/articles/single/4036-android-studio-structure-and-naming-best-practices>

<https://github.com/ribot/android-guidelines/blob/master/project_and_code_guidelines.md>

<https://github.com/futurice/android-best-practices>

<http://blog.smartlogic.io/2013-07-09-organizing-your-android-development-code-structure/>

<https://guides.codepath.com/android/Organizing-your-Source-Files>

<http://www.innofied.com/13-android-development-best-practices/>
