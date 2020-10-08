# :fire: DataBinding
프로그래밍 방식이 아닌 선언적 형식을 사용하여 <br>
레이아웃의 UI 구성 요소를 앱의 데이터 소스에 바인딩 할 수 있는 <br>
`Android Jetpack`의 라이브러리 <br>
<br>

### :sparkles: DataBinding 사용의 장점
* 액티비티에서 UI 호출을 제거하여 코드를 더 간단하고 쉽게 유지 및 관리할 수 있다.
* 앱의 성능을 개선하고 메모리 누수 및 널 포인터 예외를 방지하는 데에 도움이 될 수 있다.
* 기본 데이터 소스가 변경될 때, UI 새로고침에 대해 걱정할 필요가 없다.
* Data Binding 라이브러리와 함께 AAC를 사용하여 UI 개발을 더욱 단순화할 수 있다.
<br>

### :sparkles: DataBinding 지원 조건
* Android 4.0(API 레벨 14) 이상을 실행하는 기기
* Android Gradle Plugin 1.5.0 이상 <br>
<sub>* build.gradle(Project)의 dependencies에 정의되어 있음</sub>
<br>

### :sparkles: DataBinding 사용을 위한 환경 구축
* build.gradle(Module: app)에서 빌드 옵션 활성화
```xml
android {
    ...
    buildFeatures {
      dataBinding true
    }
}
```
<br>

### :sparkles: DataBinding 구현 방법

#### * 레이아웃 xml 파일에 Data Binding을 적용해 바인딩 클래스 생성하기
1. xml 파일의 루트 레이아웃을 `<layout>` 태그로 감싼다.
  ```xml
<?xml version="1.0" encoding="utf-8"?>
<layout xmlns:android="http://schemas.android.com/apk/res/android">
  
    <LinearLayout>
        ...
    </LinearLayout>
    
</layout>
```
<br>

2. 레이아웃의 뷰에 연결할 변수가 있을 경우, `<data>`태그와 `<variable>`태그를 이용해 변수를 선언한다.
  ```xml
<?xml version="1.0" encoding="utf-8"?>
<layout xmlns:android="http://schemas.android.com/apk/res/android">
  
    <data>
        <variable
            name="user"
            type="com.example.User" />
    </data>
    
        <LinearLayout>
            ...
        </LinearLayout>
</layout>
```
<br>

3. `@{}` 구문을 이용하여 레이아웃 컴포넌트에 변수를 할당한다.
  ```xml
<?xml version="1.0" encoding="utf-8"?>
<layout xmlns:android="http://schemas.android.com/apk/res/android">
    <data>
        <variable
            name="user"
            type="com.example.User" />
    </data>
        <LinearLayout
            android:orientation="vertical"
            android:layout_width="match_parent"
            android:layout_height="match_parent">
          
            <TextView android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:text="@{user.firstName}"/>
          
        </LinearLayout>
</layout>
```
<br>

* 레이아웃 xml 파일에 Data Binding을 적용하면 각 레이아웃 파일에 대해 바인딩 클래스가 생성된다.
* 생성되는 바인딩 클래스의 이름은 'Pascal 표기법으로 변환된 xml 파일의 이름' + 'Binding'이다. <br>
<sub>* `activity_main.xml` -> `ActivityMainBinding`</sub>
* 레이아웃 컴포넌트에 변수를 할당하지 않고, findViewById()의 호출을 대체하는 용도로만 사용할 경우엔 <br>
Data Binding 대신 View Binding을 사용하는 것이 권장된다.
<br>

#### * 생성된 바인딩 클래스를 바탕으로 바인딩 객체 만들기
```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    
        // 방법 1 - LayoutInflater 이용
        val binding: ActivityMainBinding = DataBindingUtil.setContentView(
            this, R.layout.activity_main)
        
        // 방법 2 - ViewGroup 이용
        val binding: MyLayoutBinding = MyLayoutBinding.inflate(
            getLayoutInflater(), viewGroup, false)

        binding.user = User("Test", "User")
}
```
* 바인딩 클래스는 layout inflating 시에 객체화하는 것이 권장된다.
* 바인딩 객체는 레이아웃의 뷰에 대한 모든 바인딩을 보유하고, 값을 할당할 수 있다.
<br>

### :memo: Reference
* https://developer.android.com/topic/libraries/data-binding
