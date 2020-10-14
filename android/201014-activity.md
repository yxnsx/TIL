# :fire: Activity
* 액티비티는 앱이 UI를 그리는 창을 제공한다.
* 앱과 사용자의 상호작용을 위한 진입점 역할을 하는 기본 요소이다.
* 대부분의 앱은 여러 액티비티로 구성되며, 각 액티비티는 다양한 활동을 위해 또 다른 액티비티를 시작할 수 있다.
* 액티비티를 사용하려면 앱의 매니페스트에 액티비티에 대한 정보를 선언해야 한다.
<br>

### :sparkles: Manifest에 Activity 선언하기
* 액티비티는 `<activity>` 태그를 이용해 선언한다.
* `<activity>` 태그의 필수 속성은 `android:name` 이다.
* `<activity>` 태그는 `<application>` 태그의 하위에 위치해야 한다.
* `<activity>` 태그는 `<intent-filter>`, `<meta-data>`, `<layout>` 태그를 포함할 수 있다.

```xml
<manifest ... >
    <application ... >
        <activity android:name=".ExampleActivity" />
            ...
    </application ... >
    ...
</manifest >
```
<br>

### :sparkles: Activity 라이프 사이클
* 사용자가 앱을 사용하는 동안 액티비티 인스턴스는 라이프 사이클 내에서 서로 다른 상태로 전환된다.
* `Activity` 클래스는 이러한 라이프 사이클 관리를 위한 여러 콜백 메서드를 제공한다.
* 각 콜백 메서드는 상태 변화에 적합한 특정 작업을 실행할 수 있도록 한다.
* 이를 통해 적시에 알맞은 작업을 하고 적절하게 전환을 처리하면 앱의 안정적 기능이 가능하다.
<br>

![activity_lifecycle (1)](https://user-images.githubusercontent.com/47806943/95963247-67fa0100-0e42-11eb-9a4c-995eca2ccc06.png)
<br>
<br>

### :sparkles: Activity 라이프 사이클의 콜백 메서드
1. **`onCreate()`**
  * 각 액티비티의 필수 구현 요소이다.
  * 액티비티가 생성될 때 처음으로 호출되는 메서드이다.
  * `onCreate()` 메서드 내에서는 액티비티의 전체 수명주기 동안 한 번만 발생해야 하는 <br> 
  뷰 생성, 리스트에 데이터 바인딩, 클래스 변수의 인스턴스화 등의 시작 로직을 수행한다.
<br>

2. **`onStart()`**
  * `onStart()`가 호출되면 액티비티는 사용자에게 표시된다.
  * 이 때 앱은 액티비티를 포그라운드에 보내 사용자와 상호작용할 수 있도록 준비한다.
  * `onStart()` 메서드 내에서는 앱이 UI를 관리하는 코드를 초기화한다.
<br>

3. **`onResume()`**
  * `onResume()`이 호출되면 액티비티는 사용자와 상호작용할 수 있다.
  * 어떤 이벤트가 발생하여 액티비티에서 포커스가 떠나기 전까지 액티비티는 이 상태에 머무른다.
  * `onResume()` 메서드 내에서는 액티비티가 포그라운드에서 사용자에게 보여지는 동안 실행해야 하는 <br>
  모든 기능을 활성화할 수 있다.
<br>

4. **`onPause()`**
  * `onPause()`이 호출되면 액티비티는 더 이상 포그라운드에 있지 않은 상태이다.
  * `onPause()` 메서드 내에서는 시스템 리소스, 센서 핸들(ex. GPS) 또는 배터리 수명에 영향을 미칠 수 있는 <br>
  모든 리소스를 해제할 수 있다.
  * 사용자가 멀티윈도우 모드일 경우, 일시중지된 액티비티가 여전히 보여지는 상태일 수 있으므로 <br>
  UI 관련 리소스 및 작업을 완전히 해제하거나 조정할 때에는 `onPause()` 대신 `onStop()`을 사용하는 것이 좋다.
  * `onPause()` 메서드는 아주 잠깐 실행되므로 데이터 저장, 네트워크 호출, 데이터베이스 트랜잭션 등을 <br>
  실행해서는 안되며 이러한 부하가 큰 종료 작업은 `onStop()` 내에서 실행해야 한다.
<br>

5. **`onStop()`**
  * `onStop()` 메서드는 액티비티의 실행이 완료되어 종료될 시점에 호출된다.
  * `onStop()` 메서드가 호출된 이후, 시스템은 메모리 관리를 위해 해당 액티비티를 소멸시킬 수 있다.
  * `onStop()` 메서드 내에서는 앱이 사용자에게 보여지지 않는 동안 필요하지 않은 <br>
  애니메이션, 세밀한 위치 업데이트 등의 리소스를 해제하거나 조정한다.
  * 또한 데이터 저장 등의 CPU를 비교적 많이 소모하는 종료 작업을 실행해야 한다.
<br>

6. **`onDestroy()`**
  * `onDestroy()` 메서드는 액티비티가 수신하는 마지막 수명주기 콜백으로, 액티비티가 소멸되기 전에 호출된다.
  * `onDestroy()` 메서드 내에서는 이전의 콜백에서 해제되지 않은 모든 리소스를 해제해야 한다.
<br>

### :sparkles: Activity의 Tasks와 Back Stack
![](https://developer.android.com/images/fundamentals/diagram_backstack.png)
* 새 액티비티가 시작되면 이전 액티비티는 백 스택에서 새 액티비티의 아래에 중지된 상태로 보존된다.
* 액티비티의 스택은 재정렬이 불가하며, `LIFO(Last In First Out, 후입선출)` 구조로 작동한다.
<br>

![](https://developer.android.com/images/fundamentals/diagram_multiple_instances.png)
* 사용자가 이미 스택에 존재하는 액티비티를 다시 시작하도록 한 경우에는 액티비티의 이전 인스턴스가 <br>
맨 위로 오는 것이 아닌 액티비티의 새 인스턴스가 생성되어 스택으로 푸시된다.
* 이렇게 단일 액티비티가 여러 번 인스턴스화 되지 않도록 하기 위해서는 매니페스트 파일에서 <br> 
`<activity>` 요소의 `launchMode` 속성을 지정하거나 액티비티에 인텐트 플래그 설정을 해주어야 한다.
<br>

### :memo: Reference
* https://developer.android.com/guide/components/activities/intro-activities
* https://developer.android.com/guide/components/activities/activity-lifecycle
* https://developer.android.com/guide/components/activities/tasks-and-back-stack
