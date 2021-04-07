# :fire: Core Data
* 오프라인 사용을 위해 애플리케이션의 영구적인 데이터를 저장하고, 임시 데이터를 캐시하여 실행 취소를 지원하기 위한 프레임워크
* 데이터 모델 편집기를 통해 데이터의 유형과 관계를 정의하고 각 클래스 정의를 생성한다.
* 런타임에 객체 인스턴스를 관리하여 여러 기능을 제공한다.
<br>

### :sparkles: 제공 기능
####  Persistence
* Core Data는 객체를 저장소에 매핑하기 위한 세부적인 정보를 추상화한다.
* 이를 통해 Swift 또는 Objective-C가 데이터베이스를 직접 관리하지 않고도 데이터를 저장하기 쉽도록 한다.
<br>

#### Undo and Redo of Individual or Batched Changes
* Core Data의 undo manager는 변경 사항을 추적한다.
* 추적한 변경사항은 개별적으로, 그룹화하여, 또는 모든 것을 한 번에 되돌릴 수 있다.
* 이러한 기능을 통해 실행 취소 또는 재실행 기능을 앱에서 보다 쉽게 지원할 수 있다.
<br>

#### Background Data Tasks
* JSON을 객체로 파싱하는 등 잠재적으로 UI-blocking을 하는 백그라운드 데이터 작업에서 결과를 캐시하거나 저장하여 서버 왕복을 줄일 수 있다.
<br>

#### View Synchronization
* 테이블 및 컬렉션 뷰에 대한 데이터 소스를 제공하여 뷰와 데이터를 동기화 상태로 유지하는데에 도움을 준다.
<br>

#### Versioning and Migration
* 데이터 모델의 버전을 관리하고 앱이 발전함에 따라 유저 데이터를 마이그레이션하는 메커니즘을 포함한다.
<br>

### :memo: Reference
* https://developer.apple.com/documentation/coredata/
