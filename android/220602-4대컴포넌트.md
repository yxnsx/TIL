## 4대 컴포넌트
* 안드로이드 앱의 필수적인 기본 구성 요소
* 각 구성 요소는 시스템이나 사용자가 앱에 들어올 수 있는 진입점
* 다른 구성 요소에 종속되는 구성 요소도 있음
* 안드로이드 앱은 `main()` 함수와 같은 단일 진입 지점이 없으므로 필요한 다른 앱의 구성 요소를 시작하여 이를 사용할 수 있음
<br>

#### 4대 컴포넌트의 종류
* `Activity`
* `Service`
* `BroadcastReceiver`
* `ContentProvider`
* 이 중 `Activity`, `Service`, `BroadcastReceiver`는 `Intent`라는 비동기식 메시지를 통해 활성화됨
<br>

---
## Activity
* 사용자와 앱과 상호작용하기 위한 진입점
* 앱이 UI를 그리는 창을 제공
* 한 앱이 다른 앱을 호출할 경우, 앱 전체를 호출하는 것이 아닌 Activity를 호출
* `main()` 메서드를 사용하여 앱을 실행하는 프로그래밍 패러다임과는 달리 Activity 수명주기의 특정 단계에 해당하는 특정 콜백 메서드를 호출하여 Activity를 시작함
* 매니페스트 파일에 `<activity>`로 선언

## Service
* 백그라운드에서 실행되는 구성 요소로, 오랫동안 실행되는 작업을 수행하거나 원격 프로세스를 위한 작업을 수행
* 사용자 인터페이스를 제공하지 않음
* 사용자가 다른 앱으로 전환한 경우에도 계속 실행되며, 앱 구성 요소를 서비스에 바인딩하여 상호작용하고 프로세스간 통신을 위해 사용할 수 있음
* 서비스는 메인 스레드에서 실행되며, 스레드를 직접 생성하지 않고 별도의 프로세스에서 실행되는 것도 아님
* 매니페스트 파일에 `<service>`로 선언

## BroadcastReceiver
* 시스템이 정기적인 사용자 플로우 밖에서 이벤트를 앱에 전달
* 현재 실행되지 않은 앱에도 Broadcast 전달 가능
* publish-subscribe 패턴과 유사한 형태로 안드로이드 시스템과 다른 안드로이드 앱들 간 broadcast message를 주고받을 수 있음
* 앱이 특정 broadcast만 수신하도록 등록할 수 있음
* 매니페스트 파일에 `<receiver>`로 선언

## ContentProvider
* 앱의 파일 시스템, SQLite 데이터베이스 등 영구 저장 위치에 저장 가능한 앱 데이터의 공유형 집합을 관리
* 데이터를 캡슐화하고 데이터 보안을 정의하기 위한 메커니즘 제공
* 데이터베이스에 대한 추상화로 볼 수 있지만, 시스템 설계 관점에서는 URI 구성표로 식별된 데이터 항목에 대한 인터페이스임
* URI를 할당하더라도 앱을 계속 실행할 필요가 없으므로 앱이 종료된 후에도 URI를 유지할 수 있음
* 매니페스트 파일에 `<provider>`로 선언
<br>

---
### 📝 References
* https://developer.android.com/guide/components/fundamentals
* https://developer.android.com/guide/components/activities/intro-activities
* https://developer.android.com/guide/components/services
* https://developer.android.com/guide/components/broadcasts
* https://developer.android.com/guide/topics/providers/content-providers
