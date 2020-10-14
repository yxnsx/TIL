# :fire: ViewModel
수명주기를 고려하여 UI 관련 데이터를 저장하고 관리하도록 설계된 <br>
`Android Jetpack`의 라이브러리이다.<br>
액티비티 및 프래그먼트와 같은 UI 컨트롤러가 살아있는 동안 유지된다. <br>
<br>

### :sparkles: ViewModel 사용의 장점
* UI 컨트롤러의 책임을 분리할 수 있다.
* 화면 회전과 같은 UI 구성 변경이 일어나도 데이터를 보존할 수 있다.
* UI 구성 변경시 객체를 다시 생성할 필요가 없으므로 리소스 낭비를 줄일 수 있다.
<br>

### :sparkles: ViewModel 사용을 위한 환경 구축
* build.gradle(Module: app)에서 jvmTarget 및 종속성 선언 추가
```xml
android {
    kotlinOptions {
        jvmTarget = "1.8"
    }
}

dependencies {
    def lifecycle_version = "2.2.0"
    def activity_version = "1.1.0"
    def fragment_version = "1.2.5"

    // ViewModel
    implementation "androidx.lifecycle:lifecycle-viewmodel-ktx:$lifecycle_version"
    
    // activity-ktx (Androidx kotlin 종속 라이브러리)
    // Activity에서 ViewModel을 간단하게 생성하기 위해 추가
    implementation "androidx.activity:activity-ktx:$activity_version"
    
    // fragment-ktx (Androidx kotlin 종속 라이브러리)
    // Fragment에서 ViewModel을 간단하게 생성하기 위해 추가
    implementation "androidx.fragment:fragment-ktx:$fragment_version"

}
```
<br>

### :sparkles: ViewModel 구현 방법
1. ViewModel 클래스를 생성한 후 데이터 및 관련 함수(메소드)를 선언한다. <br>
<sub>* ViewModel은 view, lifeCycle, context 등에 대한 참조를 보유할 수 있는 클래스를 참조해서는 안됨</sub>
  ```kotlin
class MyViewModel : ViewModel() {

    private val users: MutableLiveData<List<User>> by lazy {
        MutableLiveData().also {
            loadUsers()
        }
    }

    fun getUsers(): LiveData<List<User>> {
        return users
    }
    
    private fun loadUsers() {
        // Do an asynchronous operation to fetch users.
    }
}
```
<br>

2. 액티비티 및 프래그먼트와 같은 UI 컨트롤러에서 ViewModel 객체를 생성한다.
  ```kotlin
class MyActivity : AppCompatActivity() {

    // onCreate() 메서드가 호출될 때 ViewModel 객체를 생성
    override fun onCreate(savedInstanceState: Bundle?) {
    
        // build.gradle(Module: app)의 dependencies에 activity-ktx를 추가한 경우,
        // by viewModels()를 통해 간단하게 View Model 생성 가능
        val model: MyViewModel by viewModels()
        
        // 생성된 객체를 통해 ViewModel에 접근
        model.getUsers().observe(this, Observer<List<User>>{ users ->
            // update UI
        })
    }
}
```
<br>

### :sparkles: View Model 의 수명주기
* 액티비티의 경우, onDestroy()가 호출될 때 까지 View Model이 지속된다.
* 프래그먼트의 경우, onDetach()가 호출될 때 까지 View Model이 지속된다.
![viewmodel-lifecycle](https://user-images.githubusercontent.com/47806943/95162896-a14ac500-07e1-11eb-8399-37ba1c8d32d6.png)


### :memo: Reference
* https://developer.android.com/topic/libraries/architecture/viewmodel
