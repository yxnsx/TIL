# 12장
## Object
* `java.lang.Object` 클래스는 모든 자바 클래스의 부모임
* Object 클래스의 메소드들을 통해 클래스의 기본적인 행동을 정의할 수 있기 때문
* Object 클래스에서 제공하는 메소드의 종류는 객체 처리를 위한 메소드와 스레드를 위한 메소드로 나뉨
<br>

### 객체 처리를 위한 메소드
| 메소드 | 설명 |
| ---- | --- |
| `public String toString()` | 객체를 문자열로 표현하여 리턴 |
| `public boolean equals(Object obj)` | 매개변수로 넘겨받은 객체와 현재 객체가 같은지 확인 |
| `public int hashCode()` | 객체에 대한 해시코드(16진수로 제공되는 객체의 메모리 주소) 값 리턴 |
| `protected Object clone()` | 객체의 복사본을 만들어 리턴 |
| `protected void finalize()` | 현재 객체가 더 이상 쓸모 없을 때 가비지컬렉터에 의해 호출 |
| `public Class<?> getClass()` | 현재 객체의 Class 객체 리턴 |
<br>

#### `public String toString()`
* 객체의 문자열 표현값 리턴
* System.out.println() 메소드에 매개변수로 들어갈 경우 자동 호출됨
* 객체에 대해 더하기 연산을 하는 경우 자동 호출됨
* `DTO`를 사용할 때엔 `toString()` 메소드를 overriding 해놓는 것이 편리함

#### `public boolean equals(Object obj)`
* 값을 비교하는 것이 아닌 주소값을 비교하는 메소드
* 클래스의 인스턴스 변수값들이 같다고 하더라도, 서로 다른 생성자로 객체를 생성했을 경우엔 해시코드가 다르기 때문에 결과값으로 `false`가 출력됨
* 주소값의 비교를 위해 hashCode() 메소드도 Overriding해야 함
* `equals()` 메소드를 Overriding할 때에는 반드시 다섯 가지 조건을 만족해야 함
  * 재귀(reflexive): null이 아닌 x라는 객체의 `x.equals(x)` 결과는 항상 true여야 함
  * 대칭(symmetric): null이 아닌 x와 y라는 객체가 있을 때, `y.equals(x)`가 true를 리턴했다면 `x.equals(y)`도 true를 리턴해야 함
  * 타동적(transitive): null이 아닌 x, y, z가 있을 때, `x.equals(y)`가 true를 리턴하고 `y.equals(z)`가 true를 리턴하면 `z.equals(x)`도 true를 리턴해야 함
  * 일관(consistent): null이 아닌 x와 y가 있을 때, 객체가 변경되지 않은 상황에서는 몇 번을 호출하더라도 `x.equals(y)`의 결과가 항상 true이거나 false여야 함
  * null과의 비교: null이 아닌 x라는 객체의 `x.equals(null)` 결과는 항상 false여야 함

#### `public int hashCode()`
* 객체의 메모리 주소를 16진수로 리턴
* `hashCode()` 메소드를 Overriding할 때에는 세 가지 조건을 만족해야 함
  * 자바 애플리케이션 수행 중 `hashCode()` 메소드가 호출되는 객체의 리턴값은 항상 동일한 int 값이어야 함
  * `equals()`를 사용하여 두 객체를 비교한 결과가 true일 경우, 두 객체의 `hashCode()`의 리턴값이 동일한 int 값이어야 함
  * `equals()`를 사용하여 두 객체를 비교한 결과가 false라고 해서 `hashCode()` 메소드의 리턴값이 달라야 할 필요는 없음<br>다만 서로 다른 int 값을 제공하도록 하면 hashtable의 성능을 향상시키는데 도움이 됨

<br>

### 스레드 처리를 위한 메소드
| 메소드 | 설명 |
| ---- | --- |
| `public void notify()` | 객체의 모니터에 대기하고 있는 단일 스레드를 깨움 |
| `public void notifyAll()` | 객체의 모니터에 대기하고 있는 모든 스레드를 깨움 |
| `public void wait()` | 다른 스레드가 현재 객체의 `notify()` 또는 `notifyAll()` 메소드를 호출할 때까지 스레드가 대기하고 있도록 함 |
| `public void wait(long timeout)` | wait() 메소드와 동일한 기능 제공<br>매개변수 시간을 넘어서면 스레드가 다시 깨어남 |
| `public void wait(long timeout, int nanos)` | `wait()` 메소드와 동일한 기능 제공<br>`wait(timeout)` 메소드보다 자세한 나노초 단위의 시간 설정 가능 |
<br>
