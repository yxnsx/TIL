# LiveData
`Android Jetpack의 일부` <br><br>
LiveData는 앱 구성 요소의 수명주기를 인식하고 <br>
활성 수명주기 상태에 있는 앱 구성 요소의 observer만 업데이트하는 데이터 홀더 클래스이다. <br>
<sub>* LiveData Observer는 수명주기가 `STARTED` 또는 `RESUMED` 상태인 경우 활성 상태로 간주함</sub><br>
<br>

### LiveData 사용의 장점
* LiveData는 Observer pattern을 바탕으로 수명주기 상태 변경을 인식하고 자동으로 관리한다.
* LiveData Observer는 Lifecycle 객체에 바인딩되며, 관련 수명주기가 파괴되면 스스로 정리하여 메모리 누수가 없다.
* 수명주기가 비활성화 되었다가 다시 활성화 될 때 항상 최신 데이터를 수신한다.
<br>

### LiveData 구현 방법
1. ViewModel 클래스 내에 특정 데이터를 보관할 LiveData 객체를 생성한다.
```kotlin
class NameViewModel : ViewModel() {

    // currentName이라는 이름의 MutableLiveData 객체 생성
    val currentName: MutableLiveData<String> by lazy {
        MutableLiveData<String>()
    }
}
```
<br>

2. 액티비티 또는 프래그먼트와 같은 UI 컨트롤러 내에 Observer 객체를 만든다.
```kotlin
class NameActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
		
        // UI를 업데이트하는 Observer 객체 생성
        val nameObserver = Observer<String> { newName ->
		
            // UI 업데이트
            nameTextView.text = newName
        }
    }
}
```
<br>

3. LifecycleOwner 객체를 참조하는 observe() 메서드를 사용하여 LiveData 객체에 Observer 객체를 구독시킨다.
```kotlin
class NameActivity : AppCompatActivity() {

    // 뷰모델 객체 생성
    private val model: NameViewModel by viewModels()

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
		
        val nameObserver = Observer<String> { newName ->
            nameTextView.text = newName
        }

        // 뷰모델의 LiveData인 currentName에 observe() 메서드를 사용해 Observer 객체 구독
        model.currentName.observe(this, nameObserver)
    }
}
```
<br>

4. MutableLiveData 클래스의 setValue(T) 또는 postValue(T) 메서드를 이용해 LiveData에 저장된 값을 업데이트한다.
```kotlin
class NameActivity : AppCompatActivity() {

    private val model: NameViewModel by viewModels()

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
		
        val binding: ActivityMainBinding = DataBindingUtil.setContentView(
            this, R.layout.activity_main)
			
        val nameObserver = Observer<String> { newName ->
            nameTextView.text = newName
        }

        model.currentName.observe(this, nameObserver)
		
        binding.button.setOnClickListener {
            val anotherName = "John Doe"
			
            // 뷰모델의 LiveData인 currentName의 값 업데이트
            model.currentName.setValue(anotherName)
        }
    }
}
```
<br>

### :memo: Reference
* https://developer.android.com/topic/libraries/architecture/livedata
