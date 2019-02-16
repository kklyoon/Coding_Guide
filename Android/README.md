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
