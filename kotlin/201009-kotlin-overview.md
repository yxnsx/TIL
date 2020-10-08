# :fire: Kotlin
JetBrains 사에서 개발한 프로그래밍 언어로 <br>
2011년부터 개발이 시작되어 2016년에 1.0 정식 버전이 발표되었다. <br>
2017 구글 I/O에서 안드로이드 애플리케이션의 공식 개발 언어로 채택되었다. <br>
<br>

### :sparkles: Kotlin 사용의 장점
* Null safety 언어이다.
* 객체 지향 프로그래밍과 함수형 프로그래밍을 지원한다.
* Java와 100% 호환되므로 Java 애플리케이션이 실행 가능한 환경이라면 Kotlin 애플리케이션도 실행 가능하다.
* 안드로이드 뿐만 아니라 iOS, 백엔드, 웹 애플리케이션을 개발할 수 있는 멀티 플랫폼 개발 언어이다.
<br>

### :sparkles: Kotlin Coding Conventions
#### :heavy_check_mark: 클래스 레이아웃 <br>
* 정렬 순서 <br>
  :one: 속성 선언 및 초기화 블록 <br>
  :two: 보조 생성자 <br>
  :three: 메서드 선언 <br>
  :four: 컴패니언 객체 <br>
  <br>
* 메서드 선언을 알파벳순이나 가시성별로 정렬하거나, 일반 메서드를 확장(상속) 메서드와 분리하지 말아야 한다.
* 위에서 아래로 읽었을 때 무슨 일이 일어나고 있는지 논리적으로 알 수 있도록 관련된 것들을 모아서 작성해야 한다.
<br>

#### :heavy_check_mark: 인터페이스 레이아웃 <br>
* 인터페이스 멤버와 동일한 순서로 유지한다.
<br>

#### :heavy_check_mark: 명명 규칙 <br>
* 패키지 명명 규칙
```kotlin
// 패키지 이름은 항상 소문자이며 밑줄을 사용하지 않는다.
org.example.project

// 여러 단어를 사용해야 하는 경우, 이어 적거나 camelCase를 사용한다.
org.example.myproject
org.example.myProject // android studio에서는 권장 X
```
<br>

* 파일명 명명 규칙
```kotlin
// PascalCase로 작성하며 .kt 확장자로 끝난다.
// Kotlin 파일에 단일 클래스만 포함된 경우, 파일명은 클래스의 이름과 동일해야 한다.
// 파일에 여러 클래스 또는 최상위 선언만 포함된 경우, 파일의 내용을 설명하는 이름을 지정한다.

// Bar.kt - 클래스 이름과 동일한 파일명
class Bar { ... }
fun Runnable.toBar(): Bar = // …

// Map.kt - 파일의 내용을 설명하는 파일명
fun <T, O> Set<T>.map(func: (T) -> O): List<O> = // …
fun <T, O> List<T>.map(func: (T) -> O): List<O> = // …
```
<br>

* 기타 명명 규칙
```kotlin
// [클래스, 오브젝트, 인터페이스]
// PascalCase로 작성하며, 일반적으로 명사 또는 명사 구문이다.
open class DeclarationProcessor { /*...*/ }
object EmptyDeclarationProcessor : DeclarationProcessor() { /*...*/ }

// [함수]
// camelCase로 작성하며, 일반적으로 동사 또는 동사 구문이다.
fun processDeclarations() { /*...*/ }
var declarationCount = 1

// [상수]
// 변경 불가능한 const, val 등의 상수는 UPPER_SNAKE_CASE로 작성한다.
const val MAX_COUNT = 8
val USER_NAME_FIELD = "UserName"

// [변수]
// 동작 또는 변경 가능한 데이터가 있는 객체를 보유하는 최상위 속성 또는 객체 속성의 이름은 camelCase로 작성한다.
val variable = "var"
val nonConstScalar = "non-const"
val mutableCollection: MutableSet = HashSet()
val mutableElements = listOf(mutableInstance)
val mutableValues = mapOf("Alice" to mutableInstance, "Bob" to mutableInstance2)
val logger = Logger.getLogger(MyClass::class.java.name)
val nonEmptyArray = arrayOf("these", "can", "change")
```
<br>

### :memo: Reference
* https://kotlinlang.org/docs/reference/
* https://developer.android.com/kotlin/style-guide
