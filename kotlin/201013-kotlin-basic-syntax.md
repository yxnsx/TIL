# :fire: Kotlin Basic Syntax
<br>

### :sparkles: Package definition and imports
* 패키지 사양은 소스파일의 맨 위에 위치해야 한다.
```kotlin
package my.demo
import kotlin.text.*
// ...
```
<br>

### :sparkles: Program entry point
* `Kotlin` 애플리케이션의 진입점은 `main` 함수이다.
```kotlin
fun main() {
    println( "Hello World!")
}
```
<br>

### :sparkles: Functions
* 두개의 `Int` 매개변수와 `Int` 리턴 타입이 있는 함수
```kotlin
fun sum(a: Int, b: Int): Int {
    return a + b
}
```
<br>

* 표현식과 타입추론된 리턴 타입이 있는 함수
```kotlin
fun sum(a: Int, b: Int) = a + b
```
<br>

* 의미있는 값을 반환하지 않는 함수
```kotlin
fun printSum(a: Int, b: Int): Unit {
    println("sum of $a and $b is ${a + b}")
}

// `Unit` 리턴 유형은 생략 가능함
fun printSum(a: Int, b: Int) {
    println("sum of $a and $b is ${a + b}")
}
```
<br>

### :sparkles: Variables
* 읽기 전용 지역 변수는 `val`을 사용하여 정의하며, 값은 한 번만 할당할 수 있다.
```kotlin
val a: Int = 1  // 값 즉시 할당
val b = 2       // `Int` 타입추론
val c: Int      // 초기화 값이 제공되지 않은 경우 자료형 필요
c = 3           // 값 지연 할당
```
<br>

* 값의 재할당이 가능한 변수는 `var`을 사용하여 정의한다.
```kotlin
var x = 5 // `Int` 타입추론
x += 1
```
<br>

* 최상위 변수 선언
```kotlin
val PI = 3.14
var x = 0

fun incrementX() { 
    x += 1 
}
```
<br>

### :sparkles: Comments
* `Kotlin`은 한 줄 및 여러 줄(블록) 주석을 지원한다.
```kotlin
// This is an end-of-line comment

/* This is a block comment
   on multiple lines. */
```
<br>

* 여러 줄(블록) 주석의 경우 중첩이 가능하다.
```kotlin
/* The comment starts here
/* contains a nested comment */     
and ends here. */
```
<br>

### :sparkles: String templates
* 문자열 리터럴에는 결과가 문자열에 반영되는 코드 조각인 템플릿 표현식이 포함될 수 있다.
* 템플릿 표현식은 달러 사인(`$`)으로 시작된다.
```kotlin
val i = 10
println("i = $i") // prints "i = 10"

val s = "abc"
println("$s.length is ${s.length}") // prints "abc.length is 3"
```
<br>

### :sparkles: Conditional expressions
```kotlin
fun maxOf(a: Int, b: Int): Int {
    if (a > b) {
        return a
    } else {
        return b
    }
}

// 위의 조건식을 다음과 같이 표현 가능함
fun maxOf(a: Int, b: Int) = if (a > b) a else b
```
<br>

### :sparkles: Nullable values and null checks
* `null` 값이 가능한 경우 반드시 `nullable(?)`을 명시적으로 표시해주어야 한다.
```kotlin
// str이 Int를 지니고 있지 않을 경우 null을 반환
fun parseInt(str: String): Int? {
    // ...
}
```
<br>

* nullable 값을 반환하는 함수
```kotlin
fun printProduct(arg1: String, arg2: String) {
    val x = parseInt(arg1)
    val y = parseInt(arg2)

    // null 체크를 하지 않고 바로 `x * y`로 넘어갈 경우,
    // x 또는 y가 null 값을 지니고 있을 수 있기 때문에 에러가 발생함
    if (x != null && y != null) {
    
        // null 체크 후 x 와 y 값은 자동으로 non-nullable 값으로 캐스팅됨
        println(x * y)
    }
    else {
        println("'$arg1' or '$arg2' is not a number")
    }    
}

// 위의 함수는 다음과 같이 표현 가능함
fun printProduct(arg1: String, arg2: String) {
    val x = parseInt(arg1)
    val y = parseInt(arg2)

    if (x == null) {
        println("Wrong number format in arg1: '$arg1'")
        return
    }
    if (y == null) {
        println("Wrong number format in arg2: '$arg2'")
        return
    }  
    // null 체크 후 x 와 y 값은 자동으로 non-nullable 값으로 캐스팅됨
    println(x * y)
}
```
<br>

### :sparkles: Type checks and automatic casts
* `is` 연산자는 표현식이 타입에 해당하는지 체크한다.
* 변경 불가능한 지역 변수 또는 속성이 특정 타입에 대해 확인된 경우는 타입을 명시할 필요가 없다.
```kotlin
fun getStringLength(obj: Any): Int? {
    if (obj is String) {
        // if문을 분기로, `obj`는 자동으로 `String`으로 캐스팅 됨
        return obj.length
    }

    // 타입 체크 분기 밖에서 `obj`는  여전히 `Any` 타입을 지니고 있음
    return null
}

// 위의 함수는 다음과 같이 표현 가능함
fun getStringLength(obj: Any): Int? {
    if (obj !is String) return null

    // 타입 체크 분기 밖에서 `obj`는 자동으로 `String`으로 캐스팅 됨
    return obj.length
}
```
<br>

### :sparkles: for loop
```kotlin
val items = listOf("apple", "banana", "kiwifruit")
for (item in items) {
    println(item)
}

// 위의 함수는 다음과 같이 표현 가능함
val items = listOf("apple", "banana", "kiwifruit")
for (index in items.indices) {
    println("item at $index is ${items[index]}")
}
```
<br>

### :sparkles: while loop
```kotlin
val items = listOf("apple", "banana", "kiwifruit")
var index = 0
while (index < items.size) {
    println("item at $index is ${items[index]}")
    index++
}
```
<br>

### :sparkles: when expression
```kotlin
fun describe(obj: Any): String = when (obj) {
    1          -> "One"
    "Hello"    -> "Greeting"
    is Long    -> "Long"
    !is String -> "Not a string"
    else       -> "Unknown"
}
```
<br>

### :sparkles: Ranges
* `in` 연산자를 사용해 범위를 바탕으로 숫자를 체크할 수 있다.
```kotlin
// 숫자가 범위 내에 있는 경우
val x = 10
val y = 9
if (x in 1..y+1) {
    println("fits in range")
}

// 숫자가 범위 외에 있는 경우
val list = listOf("a", "b", "c")

if (-1 !in 0..list.lastIndex) {
    println("-1 is out of range")
}
if (list.size !in list.indices) {
    println("list size is out of valid list indices range, too")
}

// 범위 내에서 반복
for (x in 1..5) {
    print(x)
}
```
<br>

### :sparkles: Collections
* 컬렉션을 바탕으로 반복하기
```kotlin
for (item in items) {
    println(item)
}
```
<br>

* `in` 연산자를 사용하여 컬렉션 내에 특정 객체가 포함되어 있는지 확인하기
```kotlin
when {
    "orange" in items -> println("juicy")
    "apple" in items -> println("apple is fine too")
}
```
<br>

* 람다 식을 사용하여 컬랙션 필터링 및 매핑하기
```kotlin
val fruits = listOf("banana", "avocado", "apple", "kiwifruit")
fruits
  .filter { it.startsWith("a") }
  .sortedBy { it }
  .map { it.toUpperCase() }
  .forEach { println(it) }
```
<br>

### :memo: Reference
* https://kotlinlang.org/docs/reference/basic-syntax.html
