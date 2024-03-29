# 13장
## 인터페이스와 추상 클래스
### 인터페이스
* 개발 방법론의 일반적인 절차: 분석 → 설계 → 개발 및 테스트 → 시스템 릴리즈
* 사용 목적 1) 설계 단계에서 인터페이스를 만들어두면 어떤 메소드들이 있어야 하는지를 미리 정의해둘 수 있음
* 사용 목적 2) 외부에 노출될 요소를 정의해 놓고자 할 때 사용되기도 함
* 몸통 없이 메소드만 선언하므로 선언과 구현을 구분할 수 있고, 실제 개발할 때에는 기능 구현에 집중할 수 있음
* 인터페이스를 구현할 경우, 인터페이스에 정의한 메소드들의 몸통을 만들어 주어야 함
* 소스 파일 이름과 클래스 파일 이름만 보면 인터페이스인지 클래스인지 알 수 없기 때문에 클래스 이름 앞에 I를 붙이는 등 표준을 정함
* DAO(Data Access Object) 패턴이 가장 일반적 - DBMS 종류에 상관없이 원하는 값을 요청하고 응답을 받을 수 있게 해줌
* 인터페이스 내에는 static이나 final 메소드가 선언되어 있으면 안됨
<br>

### 추상 클래스
* 추상 클래스는 자바에서 마음대로 초기화하고 실행할 수 없도록 되어있음
* 추상 클래스를 구현해놓은 클래스로 초기화 및 실행이 가능함
* 공통적인 기능을 미리 구현해놓기 위해 사용함
* 내부에 추상 메소드가 하나 이상 있을 경우, 반드시 추상 클래스로 선언되어야 함
* 추상 클래스 내에는 static이나 final 메소드가 선언되어 있어도 됨
<br>

### 인터페이스와 추상 클래스, 클래스의 차이
|   | 인터페이스 | 추상 클래스 | 클래스 |
| - | ------- | -------- | ----- |
| 선언시 사용하는 예약어 | interface | abstract class | class |
| 미구현된 메소드 포함 가능 여부 | 가능(필수) | 가능 | 불가 |
| 구현된 메소드 포함 가능 여부 | 불가 | 가능 | 가능(필수) |
| static 메소드 포함 가능 여부 | 불가 | 가능 | 가능 |
| final 메소드 포함 가능 여부 | 불가 | 가능 | 가능 |
| 상속 가능 여부 | 불가 | 가능 | 가능 |
| 구현 가능 여부 | 가능 | 불가 | 불가 |
<br>

## final
* 클래스, 메소드, 변수에 선언 가능
* final class
  * ex) `public final class FinalClass { }`
  * 클래스가 final로 선언되어 있을 경우, 상속을 해줄 수 없음
  * 클래스가 final이라고 해서 그 안의 인스턴스 변수나 클래스 변수가 final인 것은 아님
  * 더 이상 확장해서는 안되는 클래스, 누군가 해당 클래스를 상속받아 내용을 변경해서는 안되는 클래스 선언시 사용
* final method
  * ex) `public final void printLog(String data) { }`  
  * 메소드가 final로 선언되어 있을 경우, Overriding이 불가능함
  * 메소드를 누군가 변경하지 못하도록 하기 위해 사용
* final variable
  * ex) `final int instanceVariable = 1;`
  * 변수가 final로 선언되어 있을 경우, 값의 변경이 불가능함
  * 인스턴스 변수가 final로 선언된 경우, 변수 선언과 동시에 값을 할당해주어야 함
  * 매개 변수나 지역 변수가 final로 선언된 경우, 선언과 동시에 초기화할 필요는 없음
  * 변수의 값이 변하지 않도록 하기 위해 사용
<br>

## enum
* 상수로만 구성된 클래스에 enum 선언을 추가하여 객체가 상수의 집합이라는 것을 명시적으로 나타낼 수 있음
* 상수를 선언만 해둘 수도 있고 상수에 값을 지정할 수도 있으나, 값을 동적으로 할당하는 것을 불가능함
* enum 클래스의 생성자는 접근 제어자로 `package-private`이나 `private`만 사용할 수 있음
* 일반 클래스와 마찬가지로 컴파일할 때 자동으로 생성자를 만들어 줌
* enum 클래스의 무조건 `java.lang.Enum` 클래스의 상속을 받음
* Object 클래스의 메소드를 모두 사용할 수 있으나, 그 중 4개의 메소드는 Overriding이 불가능함
  * Overrinding 불가 메소드 - `clone()`, `finalize()`, `hashCode()`, `equals()`
<br>

### enum 클래스에 선언되어 있는 메소드
| 메소드 | 내용 |
| ---- | --- |
| compareTo(E e) | 매개변수로 넘어온 enum 타입과의 순서 차이 리턴<br>매개변수로 넘기는 상수 기준으로 앞에 있으면 음수(-), 뒤에 있으면 양수(+)를 리턴함 |
| getDeclaringClass() | 클래스 타입의 enum 리턴 |
| name() | 상수의 이름 리턴 |
| ordinal() | 상수의 순서 리턴 |
| valueOf(Class<T> enumType, String name) | static 메소드<br> 첫 번째 매개변수로는 클래스 타입의 enum, 두 번째 매개변수로는 상수의 이름을 넘겨주면 됨 |
<br>
  
