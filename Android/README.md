이 글은 안드로이드 프로젝트를 시작하는 사람들을 위해 작성됨



# 1. 프로젝트 구조

<p align="center">
  <img width="33%" src="res/android_dir_struct.png" />
</p>

 
|이름            | 용도                       |
|----------------|---------------------------|
|build.gradle    | apk 빌드 세팅              |
|settings.gradle | 서브 프로젝트 세팅          |
|.idea           | Intellij IDEA 세팅 디렉토리|
|.gitignore      | git 무시 규칙 파일         |
|gradle          | gradle-wrapper 파일 디렉토리|
| app/build.gradle | 특정 모듈로 정의됨 app 의 특성, manifest 로 정의된 빌드속성위에 override 됨, 종속된 라이브러리 정의 |
|AndroidManifest.xml| 어플라케이션에서 사용되는 activity 목록, 권한, 라이브러리 정의|
<br> 

  

### <center>레이아웃 디렉토리</center>

<p align="center">
  <img src="res/android_res_struct.png" />
</p>


|이름            | 용도     |
|----------------|----------------------|
|res/drawable    | 이미지파일 ( png. jpeg), 9-Patch images ( 늘이기 혹은 반복적으로 사용되는 이미지), xml 로 정의된 이미지|
|res/layout      | 화면을 구성하는 xml 형식의 레이아웃파일, 파일명으로 참조 |
|res/menu  | 메뉴 정의|
|res/mipmap | 앱런처 아이콘 (홈스크린에 표시되는 앱아이콘) |
|res/values | 컬러, 해상도, 문자열, 스타일 등과 같이 반복되어 사용되는 값들이 정의됨 |

# 2. 명명법

안드로이드 프로젝트의 **공식적인** 명명 규칙은 없다. 그러므로 의무적인 사항은 아니다. 하지만 프로젝트 관리차원에서 규칙을 가지고 있는 것은 무엇이 있는지 찾기도 편리하고 특히 프로젝트가 커지면 커질 수록 일관된 규칙속에서 작업해야 효율이 좋을 것이다.

## 2.1 클래스 파일

클래스 명은 [UpperCamelCase](http://en.wikipedia.org/wiki/CamelCase) 를 따른다. Android component 에 해당되는 클래스는 파일명 끝에 component 이름을 명시한다. 예) `SignInActivity`, `SignInFragment`, `ImageUploaderService`, `ChangePasswordDialog`

## 2.2 리소스 파일

리소스 파일은 소문자와 언더바로 구성 

### 2.2.1 Drawable Files

Asset Type 에 따라 다음과 같이 접두어를 붙인다.

Asset Type      | Prefix          | Example
-----------     |--------         |---------
**Button**      | `btn_`          | `btn_send.png`
**Dialog**      | `dialog_`       | `dialog_top.png`
**Divider**     | `divider_`      | `divider_horizontal.png`
**Menu**        | `menu_`         | `menu_submenu_bg.png`
**Icon**        | `ic_`           | `ic_start.png`
**Image**       | `img_`          | `img_sample.png`
**Action bar**  | `ab_`           | `ab_stacked.png`
**Notification**| `notification_` | `notification_bg.png`
**Tabs**        | `tab_`          | `tab_pressed.png`

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

### 2.2.2 Layout Files

레이아웃 파일은 안드로이드 컴포넌트 이름이 앞으로 오게 만든다. 예를 들어 `SignInActivity` 를 만든다 치면 레이아웃 파일 이름은 `activity_sign_in.xml`.


| Component        | Class Name             | Layout Name                   |
| ---------------- | ---------------------- | ----------------------------- |
| Activity         | `UserProfileActivity`  | `activity_user_profile.xml`   |
| Fragment         | `SignUpFragment`       | `fragment_sign_up.xml`        |
| Dialog           | `ChangePasswordDialog` | `dialog_change_password.xml`  |
| AdapterView item | ---                    | `item_person.xml`             |
| Partial layout   | ---                    | `partial_stats_bar.xml`       |

약간 다른 경우로 'Adapter' 를 만들 때 'ListView' 를 만든다면 layout 파일은 'item_' 으로 시작하게 된다.

이러한 규칙은 모든 레이아웃에 적용될 수는 없다. 예를 들어 다른 레이아웃의 일부분을 파일로 만들었을 때는 'partial_' 이라는 이름을 붙여주는 것이 맞다.

### 2.2.3 Menu files

레이아웃파일과 비슷하다. `UserActivity` 에서 쓰이는 메뉴파일이라면 `activity_user.xml` 라고 만든다. 이미 'menu' 디렉토리에 존재하기 때문에 굳이 'menu' 라는 이름을 붙이지 않아도 된다. 


### 2.2.4 Values files

다음과 같이 복수형으로 파일이름을 만든다. ->  `strings.xml`, `styles.xml`, `colors.xml`, `dimens.xml`, `attrs.xml`


## 2.3 Resource IDs
안드로이드에서 다른 레이아웃에 있는 같은 이름의 Resource ID 가 허용된다고 할지라도 각각의 이름을 할당해서 쓰는 것이 좋다. __소문자_언더바__ 사용

Element              | Prefix               | 혹은
--------             |--------              |--------
**TextView**         | `<layout_name>_txt_` |`tv_<layout_name>`
**EditText**         | `<layout_name>_et_`  |`et_<layout_name>`
**Button**           | `<layout_name>_btn_` |`btn_<layout_name>`
**Menu**             | `<layout_name>_menu_`|`menu_<layout_name>`
**ListView**         | `<layout_name>_lv_`  |`lv_<layout_name>`
**RecyclerView**     | `<layout_name>_rv_`  |`rv_<layout_name>`
**ImageView**        | `<layout_name>_img_` |`iv_<layout_name>`
**LinearLayout**     | `<layout_name>_ll_`  |`ll_<layout_name>`
**FrameLayout**      | `<layout_name>_fl_`  |`fl_<layout_name>`
**ConstraintLayout** | `<layout_name>_cl_`  |`cl_<layout_name>`

## 2.4 문자열


문자열 이름은 문자열의 카테고리에 따라서 접두어를 붙있다. 


| Prefix             | Description                           |
| -----------------  | --------------------------------------|
| `error_`             | An error message                      |
| `msg_`               | A regular information message         |
| `title_`             | A title, i.e. a dialog title          |
| `action_`            | An action such as "Save" or "Create"  |


## 2.5 스타일과 테마

리소스와는 달리 스타일은  __UpperCamelCase__ 로 명명

## 2.6 레이아웃 Attribute 순서

일반적인 규칙의 attribute 순서는

1. View Id
2. Style
3. Layout width and layout height
4. Other layout attributes, sorted alphabetically
5. Remaining attributes, sorted alphabetically



# 3. Code guidelines

## 3.1 Java 언어
### 3.1.1 예외처리 무시하지 않기

__Bad__
```java
void setServerPort(String value) {
    try {
        serverPort = Integer.parseInt(value);
    } catch (NumberFormatException e) { }
}
```

> _당신의 코드가 에러처리를 안해도 된다든가 처리하는데 중요하지 않다고 생각할 수 있지만, 위와 같은 예외를 무시하면 언젠가 다른 사람이(혹은 당신이) 곤란을 겪게 될 것이다. 모든 예외를 원칙적으로 다뤄야하고 구체적인 방법은 사례에 따라 달라진다._ - ([Android code style guidelines](https://source.android.com/source/code-style.html))

수정된 코드는 __[여기](https://source.android.com/source/code-style.html#dont-ignore-exceptions)__

### 3.1.2 generic exception 처리하지 마라

```java
try {
    someComplicatedIOFunction();        // may throw IOException
    someComplicatedParsingFunction();   // may throw ParsingException
    someComplicatedSecurityFunction();  // may throw SecurityException
    // phew, made it all the way
} catch (Exception e) {                 // I'll just catch all exceptions
    handleError();                      // with one generic handler!
}
```

이유와 수정된 코드는 __[여기](https://source.android.com/source/code-style.html#dont-catch-generic-exception)__ 참고 


### 3.1.3 finalizers 사용하지 마라


> _우리는 finalizer를 사용하지 않는다. finalizer 는 언제 불릴지 혹은 불려지기는 할지에 대한 보장이 없다. 대부분의 경우 예외처리만 잘하면 필요없다. 정말 필요하다면 'close()' 메서드같은 것을 정의하고 메서드가 정확히 언제 불려지는지 문서화 하라. `InputStream`을 예로 들면 finalizer 에서 짧은 로그를 찍는건 나쁘진 않지만 로그가 넘쳐나지 않는 이상 꼭 필요한 것은 아니다._- ([Android code style guidelines](https://source.android.com/source/code-style.html#dont-use-finalizers))


### 3.1.4 import 정확하게 하기 

This is bad: `import foo.*;`

This is good: `import foo.Bar;`

[여기참고](https://source.android.com/source/code-style.html#fully-qualify-imports)

## 3.2 Java style rules

### 3.2.1 Fields definition and naming

 __파일 상단__ 에 정의 되어야 하는 것들과 명명법


* Private, non-static 은 __m__ 으로 시작.
* Private, static 은  __s__ 로 시작.
* 다른 것들은 소문자로 시작.
* Static final (상수) 언더바와 대문자(ALL_CAPS_WITH_UNDERSCORES).

Example:

```java
public class MyClass {
    public static final int SOME_CONSTANT = 42;
    public int publicField;
    private static MyClass sSingleton;
    int mPackagePrivate;
    private int mPrivate;
    protected int mProtected;
}
```

### 3.2.3 단어와 약어 다루기

|| Good           | Bad            |
|-----| -------------- | -------------- |
|클래스| `XmlHttpRequest` | `XMLHTTPRequest` |
|메서드| `getCustomerId`  | `getCustomerID`  |
|변수  | `String url`     | `String URL`     |
|     | `long id`        | `long ID`        |

### 3.2.4 공백과 들여쓰기 사용

블럭에서는  __4 칸__ 들여쓰기:

```java
if (x == 1) {
    x++;
}
```

한 라인일 경우  __8 칸__ 들여쓰기:

```java
Instrument i =
        someLongExpression(that, wouldNotFit, on, one, line);
```

### 3.2.5 standard brace style

standard brace style 은 다음과 같은것

```java
class MyClass {
    int func() {
        if (something) {
            // ...
        } else if (somethingElse) {
            // ...
        } else {
            // ...
        }
    }
}
```

조건과 실행을 한라인에 할 수 있으면 다음과 같이 한다.e.g.


```java
if (condition) body();
```

This is __bad__:

```java
if (condition)
    body();  // bad!
```

### 3.2.6 Annotations

#### 3.2.6.1 Annotations 활용


안드로이드 스타일 가이드에 따르면, 표준 활용은 Java 에 미리 정의되어 있다.

* `@Override`: @Override annotation 은 부모클래스에 있는 메서드를 구현하거나 정의할 때 __반드시 사용되어야__ 하는 annotation 이다. 예를 들어 클래스에서 @inheritdocs Javadoc tag 를 사용했다면 (인터페이스말고), 부모클래스의 메서드에 반드시 @Overrides 를 사용해야한다.

* `@SuppressWarnings`: The @SuppressWarnings annotation warning 을 도저히 없앨 수 없는 상황에서 사용.

annotation 에 대한 자세한 가이드라인은  [여기](http://source.android.com/source/code-style.html#use-standard-java-annotations).

#### 3.2.6.2 Annotations 스타일

__클래스, 메서드, 생성자__

annotations 이 클래스, 매서드, 생성자 등에 적용될 때 , documatation 블럭 뒤에 오는 것들은 __한 줄씩__ 표기해야한다. 

```java
/* This is the documentation block about the class */
@AnnotationA
@AnnotationB
public class MyAnnotatedClass { }
```

__Fields__

annotation 을 멤버에게 쓸 때는 한줄에 모두 표기해야한다.

```java
@Nullable @Mock DataManager mDataManager;
```

### 3.2.7 변수 범위 제한

> _지역 변수의 범위는 최소한으로 제한해야한다. 그렇게 함으로써 코드의 가독성과 유지관리성을 높이고 에러 가능성을 줄일 수 있다._

> _지역 변수는 사용하는 시점에 선언되어야 한다. 대부분의 지역 변수에는 초기화가 포함되어야 한다. 아직 지역 변수를 초기화 하기에 충분한 정보가 없다면 정보가 있을 때까지 선언을 미뤄야 한다._ - ([Android code style guidelines](https://source.android.com/source/code-style.html#limit-variable-scope))


### 3.2.8 import 순서

안드로이드 스튜디오를 사용하고 있다면 이미 이러한 규칙을 따르고 있으니 걱정할 필요없다.

import 순서:

1. Android imports
2. Imports from third parties (com, junit, net, org)
3. java and javax
4. Same project imports

To exactly match the IDE settings, the imports should be:
IDE 세팅과 맞추려면 

* 알파벳 순서로, 소문자 앞에 대문자 (e.g. a 앞에 Z).
* 그룹마다 줄바꿈으로 구분해주기 (android, com, junit, net, org, java, javax)

더 많은 정보는 [여기](https://source.android.com/source/code-style.html#limit-variable-scope)

### 3.2.9 로깅 가이드

로그 출력용 `Log` 클래스를 사용할 때 다음과 같이 이슈를 분리할 수 있다.

* `Log.v(String tag, String msg)` (verbose)
* `Log.d(String tag, String msg)` (debug)
* `Log.i(String tag, String msg)` (information)
* `Log.w(String tag, String msg)` (warning)
* `Log.e(String tag, String msg)` (error)

일반적으로 클래스 이름을 `static final` 로 선언해서 다음과 같이 사용할 수 있다.

```java
public class MyClass {
    private static final String TAG = MyClass.class.getSimpleName();

    public myMethod() {
        Log.e(TAG, "My error message");
    }
}
```

VERBOSE 과 디버그 로그는 __릴리즈 빌드에선 disable__ 되어야 한다. Infomation, Warning, Error 로그도 마찬가지로 diable 하는걸 추천하지만 릴리즈 빌드의 이슈관리에 사용하고 싶으면 enable 시킬 수 있다. enable 할 때는 민감한 정보(email address, user ID 같은)를 노출시키지 않도록 한다.

디버그 빌드일 때만 사용하려면 다음과 같이

```java
if (BuildConfig.DEBUG) Log.d(TAG, "The value of x is " + x);
```

### 3.2.10 클래스 멤버 순서

정해진 법칙은 없지만 유지보수와 가독성 차원에서의 __논리적, 일관성__ 을 지키려면 다음과 같은 순서를 추천한다.

1. 상수
2. 멤버변수
3. 생성자
4. Override methods and callbacks (public or private)
5. Public methods
6. Private methods
7. Inner classes or interfaces

Example:

```java
public class MainActivity extends Activity {

    private static final String TAG = MainActivity.class.getSimpleName();

    private String mTitle;
    private TextView mTextViewTitle;

    @Override
    public void onCreate() {
        ...
    }

    public void setTitle(String title) {
    	mTitle = title;
    }

    private void setUpView() {
        ...
    }

    static class AnInnerClass {

    }

}
```

만약 클래스가 Activity나 Fragment 같이 __Android component__ 를 상속받고 있다면 __component의 lifecycle__ 이 좋은 예가 될 수 있다. 예를 들어 `onCreate()`, `onDestroy()`, `onPause()`, `onResume()` 등을 구현하려면 다음과 같은 순서로

```java
public class MainActivity extends Activity {

	//Order matches Activity lifecycle
    @Override
    public void onCreate() {}

    @Override
    public void onResume() {}

    @Override
    public void onPause() {}

    @Override
    public void onDestroy() {}

}
```

### 3.2.11 메서드의 파라미터 순서

안드로이드 프로그래밍을 할 때 `Context` 를 받는 경우가 많다. 이 경우 __Context__ 파라미터를 첫번째로 해야한다.

반대로 __callback__ 을 받을 때는 __마지막 파라미터__ 로 받아야 한다.

Examples:

```java
// Context always goes first
public User loadUser(Context context, int userId);

// Callbacks always go last
public void loadUserAsync(Context context, int userId, UserCallback callback);
```

### 3.2.13 상수문자열 명명, 값

안드로이드에서 `SharedPreferences`, `Bundle`, `Intent` 등은 key-value 를 짝으로 쓰는 것들이다. 여기엔 상수 문자열이 많이 쓰인다.

이러한 component 를 쓸때 반드시 `static final`로 선언해서 사용해야 한다. 
아래와 같은 접두사를 사용하면 좋다.


| Element            | Field Name Prefix |
| -----------------  | ----------------- |
| SharedPreferences  | `PREF_`             |
| Bundle             | `BUNDLE_`           |
| Fragment Arguments | `ARGUMENT_`         |
| Intent Extra       | `EXTRA_`            |
| Intent Action      | `ACTION_`           |


Fragment 에서 전달 값 `Fragment.getArguments()` 을 받아올 때 Bundle 로 받아온다. 일반적인 사용이기 따문에 다른 접두사를 붙여 정의된다.

Example:

```java
// Note the value of the field is the same as the name to avoid duplication issues
static final String PREF_EMAIL = "PREF_EMAIL";
static final String BUNDLE_AGE = "BUNDLE_AGE";
static final String ARGUMENT_USER_ID = "ARGUMENT_USER_ID";

// Intent-related items use full package name as value
static final String EXTRA_SURNAME = "com.myapp.extras.EXTRA_SURNAME";
static final String ACTION_OPEN_USER = "com.myapp.action.ACTION_OPEN_USER";
```

### 3.2.14 Fragment 와 Activity 의 전달인자

`Intent` 와 `Bundle` 을 통해 `Activity` 혹은 `Fragment` 에 데이터를 넘길 때 키값은 위에 언급한 바와 같이 작성되어야 한다.

`Activity`,  `Fragment`가 전달인자를 받을 때 `Intent`와 `Fragment`형으로 만들어진 `public static` 메서드를 통해 전달되어야 한다. 

Activity 의 경우 `getStartIntent()`에서 불릴 때:

```java
public static Intent getStartIntent(Context context, User user) {
	Intent intent = new Intent(context, ThisActivity.class);
	intent.putParcelableExtra(EXTRA_USER, user);
	return intent;
}
```

Fragment 의 경우 `newInstance()` 로 전달인자를 사용하여 Fragment 의 생성을 처리할 때:

```java
public static UserFragment newInstance(User user) {
	UserFragment fragment = new UserFragment();
	Bundle args = new Bundle();
	args.putParcelable(ARGUMENT_USER, user);
	fragment.setArguments(args)
	return fragment;
}
```

__Note 1__: 이런 메서드는 `onCreate()` 위에 있어야 한다..

__Note 2__: 위에서 언급한 바와 같이, 클래스 밖에서는 알 수 없도록 extras 와 전달인자의 key 값은 `private` 이어야 한다. 


### 3.2.15 줄 길이 제한

코드는 __100글자__ 를 넘어서는 안된다. 더 길다면 두가지 옵션이 있다.

* 지역변수와 메서드를 풀어써라
* 자동 줄 바꿈 사용

100글자를 넘어도 되는 __두가지 예외__ 가 있다.

* Lines that are not possible to split, e.g. long URLs in comments.
* 라인을 나눌 수 없을 때, e.g. 주석의 긴 URL
* `package` 나 `import` 

#### 3.2.15.1 자동 줄바꿈 전략

정확한 공식은 없다. 하지만 상식적인 수준에서 몇가지 규칙은 있다.

__연산자 앞에서 끊기__

```java
int longName = anotherVeryLongVariable + anEvenLongerOne - thisRidiculousLongOne
        + theFinalOne;
```

__대입 연산자는 예외__

```java
int longName =
        anotherVeryLongVariable + anEvenLongerOne - thisRidiculousLongOne + theFinalOne;
```

__메서드 체인의 경우__

빌더 패턴같은 메서드 체인의 경우 `.` 앞에서 끊는다.

```java
Picasso.with(context).load("http://ribot.co.uk/images/sexyjoe.jpg").into(imageView);
```

```java
Picasso.with(context)
        .load("http://ribot.co.uk/images/sexyjoe.jpg")
        .into(imageView);
```

__긴 매개변수의 경우__

매개변수가 많거나 길거나 할 땐 `,` 뒤에서 끊는다.

```java
loadPicture(context, "http://ribot.co.uk/images/sexyjoe.jpg", mImageViewProfilePicture, clickListener, "Title of the picture");
```

```java
loadPicture(context,
        "http://ribot.co.uk/images/sexyjoe.jpg",
        mImageViewProfilePicture,
        clickListener,
        "Title of the picture");
```

### 3.2.16 RxJava chains styling


`.` 앞에서 끊는다.

```java
public Observable<Location> syncLocations() {
    return mDatabaseHelper.getAllLocations()
            .concatMap(new Func1<Location, Observable<? extends Location>>() {
                @Override
                 public Observable<? extends Location> call(Location location) {
                     return mRetrofitService.getLocation(location.id);
                 }
            })
            .retry(new Func2<Integer, Throwable, Boolean>() {
                 @Override
                 public Boolean call(Integer numRetries, Throwable throwable) {
                     return throwable instanceof RetrofitError;
                 }
            });
}
```

## 3.3 XML style rules

### 3.3.1 Use self closing tags

When an XML element doesn't have any contents, you __must__ use self closing tags.

This is good:

```xml
<TextView
	android:id="@+id/text_view_profile"
	android:layout_width="wrap_content"
	android:layout_height="wrap_content" />
```

This is __bad__ :

```xml
<!-- Don\'t do this! -->
<TextView
    android:id="@+id/text_view_profile"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content" >
</TextView>
```

## 3.4 Tests style rules

### 3.4.1 Unit tests


테스트 클래스는 테스트할 타겟 클래스와 이름을 맞춰야한다. 접미사 `Test` 를 넣고. 예를 들어 `DatabaseHelper` 를 테스트 한다면 `DatabaseHelperTest` 라고 명명한다.

테스트 메서드는 `@Test` annotation 을 붙이고 테스트할 메서드이름과 메서드의 원래상태 혹은 예상결과를 붙여서 명명한다.

* Template: `@Test void methodNamePreconditionExpectedBehaviour()`
* Example: `@Test void signInWithEmptyEmailFails()`

메서드의 원래상태나 예상결과가 명확하지 않을 때는 안붙여도 된다. ( 이 때는 맘데로 하라는듯)

어떤 클래스는 많은 양의 메서드를 포함하고 있고 각 메서드마다 몇개씩의 테스트가 필요하다. 이런 경우에는 테스트 클래스를 여러개로 나누는걸 추천한다. 예를 들어 `DataManager` 가 많은 메서드를 가지고 있다치면 `DataManagerSignInTest`, `DataManagerLoadUsersTest` 등으로 테스트 클래스를 나눌수 있다. 일반적인 테스트가 어떻게 나뉘는지는  [여기](https://en.wikipedia.org/wiki/Test_fixture)를 참고하라

### 3.4.2 Espresso tests

Espresso 테스트는 보통 Activity 를 타겟으로 한다. 그래서 보통 `SignInActivityTest` 이런 식으로 명명한다.

체인 메서드는 다음과 같이 사용한다.

```java
onView(withId(R.id.view))
        .perform(scrollTo())
        .check(matches(isDisplayed()))
```

# 4. Reference

* <https://developer.android.com/studio/build/>
* <https://medium.com/@mikelimantara/overview-of-android-project-structure-and-naming-conventions-b08f6d0b7291>
* <https://www.supinfo.com/articles/single/4036-android-studio-structure-and-naming-best-practices>
* <https://github.com/ribot/android-guidelines/blob/master/project_and_code_guidelines.md>

============================= (일단 여기까지 취합)

* <https://github.com/futurice/android-best-practices>
* <http://blog.smartlogic.io/2013-07-09-organizing-your-android-development-code-structure/>
* <https://guides.codepath.com/android/Organizing-your-Source-Files>
* <http://www.innofied.com/13-android-development-best-practices/>
* <https://source.android.com/setup/contribute/code-style>
