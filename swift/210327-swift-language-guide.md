# :fire: Swift Language Guide
<br>

### :sparkles: Constants and Variables
* 상수는 `let` 키워드로 선언하고, 변수는 `var` 키워드로 선언한다.
* 상수의 값은 한 번 설정되면 변경할 수 없지만, 변수는 다른 값으로 변경할 수 있다.
* 상수와 변수는 사용하기 전, 선언이 우선되어야 한다.
```swift
let maximumNumberOfLoginAttempts = 10 // 상수
var currentLoginAttempt = 0 // 변수

var x = 0.0, y = 0.0, z = 0.0 // 여러 상수 또는 변수를 쉼표로 구분하여 한 줄에 선언할 수 있다.
```
<br>

### :sparkles: Type Annotations
* 상수 또는 변수가 저장할 수 있는 값의 유형을 명확히하기 위해 사용한다.
* 상수 또는 변수 이름 뒤에 콜론, 공백, 타입을 차례로 선언한다.
* 초기값이 지정되지 않은 경우, Type Annotations으로 타입을 선언한다.
* 초기값이 지정된 경우, Type Annotations으로 타입이 선언되어 있지 않아도 타입 추론이 가능하다.
```swift
var welcomeMessage: String
var red, green, blue: Double // 한 줄에 선언한 변수들에 동일한 유형의 타입을 정의할 수 있다.
```
<br>

### :sparkles: Naming Constants and Variables
* 상수 및 변수의 이름은 유니코드 문자를 포함한 거의 모든 문자를 포함할 수 있다.
```swift
let π = 3.14159 // 가능
let 你好 = "你好世界" // 가능
let 🐶🐮 = "dogcow" // 가능
```
<br>

* 상수 및 변수 이름에는 공백 문자, 수학 기호, 화살표, 개인용 유니코드 스칼라 값 등이 포함될 수 없다.
```swift
let s pace = "space" // 불가능
let space = "space"  // 가능
```
<br>

* 상수 및 변수 이름이 숫자로 시작되어서는 안된다.
```swift
let 1one = 1 // 불가능
let one1 = 1 // 가능
```
<br>

* `where`, `func` 등 스위프트 키워드와 동일한 이름으로 상수 및 변수의 이름을 지정해야 할 경우, 백틱(<code>`</code>)으로 묶어주어야 한다.
```swift
let where = "where"   // 불가능
let `where` = "where" // 가능
```
<br>

### :sparkles: Comment
* 한 줄 주석은 두 개의 슬래시(`//`)로 시작한다.
```swift
// This is a comment.
```
<br>

* 여러 줄 주석은 슬래시와 별표(`/*`)로 시작하고 별표와 슬래시(`*/`)로 끝난다.
```swift
/* This is also a comment
but is written over multiple lines. */
```
<br>

* 여러 줄 주석은 중첩 사용이 가능하다.
```swift
/* This is the start of the first multiline comment.
 /* This is the second, nested multiline comment. */
This is the end of the first multiline comment. */
```
<br>

### :sparkles: Semicolons
* Swift는 코드의 각 명령문 뒤에 세미콜론(`;`)을 작성할 필요가 없다.
* 다만, 한 줄에 여러 개의 개별문을 작성하기 위해서는 세미콜론이 필요하다.
```swift
let cat = "🐱"; print(cat)
```
<br>

### :sparkles: Integers
* Integer Bounds
  * Swift는 8, 16, 32, 64-bit 형식으로 정수를 제공한다.
  * `min` 및 `max` 속성을 사용하여 각 정수 유형의 최솟값과 최댓값에 접근할 수 있다.
```swift
let minValue = UInt8.min  // minValue is equal to 0, and is of type UInt8
let maxValue = UInt8.max  // maxValue is equal to 255, and is of type UInt8
```
<br>

* Int
  * 명시적으로 크기가 지정된 데이터 사용 또는 성능, 메모리 사용량 등 최적화를 위한 작업 등 특별한 경우가 아니라면 Int 정수값을 사용한다.
  * 32-bit 플랫폼에서의 Int size = `Int32`
  * 64-bit 플랫폼에서의 Int size = `Int64`
<br>

* UInt
  * 부호 없는 정수 유형(0, 양수)만 제공한다.
  * 32-bit 플랫폼에서의 UInt size = `UInt32`
  * 64-bit 플랫폼에서의 UInt size = `UInt64`
<br>

### :sparkles: Floating-Point Numbers
* 부동 소수점 타입은 정수 타입보다 훨씬 더 넓은 범위의 값을 나타낼 수 있다.
* Swift는 두 종류의 부동 소수점 타입을 제공한다.
  * 32-bit 부동 소수점 숫자 = `Float`
  * 64-bit 부동 소수점 숫자 = `Double`
<br>

### :sparkles: Numeric Literals
* 정수 리터럴은 다음과 같이 작성할 수 있다.
  * 10진법 숫자 - 접두어 필요 없음
  * 2진법 숫자 - 0b 접두어 필요
  * 8진법 숫자 - 0o 접두어 필요
  * 16진법 숫자 - 0x 접두어 필요
```swift
let decimalInteger = 17
let binaryInteger = 0b10001   // 2진법으로 나타낸 17
let octalInteger = 0o21       // 8진법으로 나타낸 17
let hexadecimalInteger = 0x11 // 16진법으로 나타낸 17
```
<br>

* 부동 소수점 리터럴은 지수를 지닐 수 있다.
  * 10진법 숫자 (10<sup>exp</sup>씩 곱함)
    * 1.25e2 = 1.25 x 10<sup>2</sup> = 125.0
    * 1.25e-2 = 1.25 x 10<sup>-2</sup> = 0.0125
  * 2진법 숫자
    * 0xFp2 = 15 x 2<sup>2</sup> = 60.0
    * 0xFp-2 = 15 x 2<sup>-2</sup> = 3.75
```swift
let decimalDouble = 12.1875     // = 12.1875
let exponentDouble = 1.21875e1  // = 12.1875
let hexadecimalDouble = 0xC.3p0 // = 12.1875
```
<br>

* 숫자 리터럴은 쉽게 읽을 수 있도록 추가적인 형식을 포함할 수 있다.
* 정수와 부동 소수점 모두 0으로 채울 수 있으며, 밑줄을 포함할 수 있다.
* 이러한 형식은 리터럴의 기본 값에 영향을 주지 않는다.
```swift
let paddedDouble = 000123.456
let oneMillion = 1_000_000
let justOverOneMillion = 1_000_000.000_000_1
```
<br>

### :sparkles: Numeric Type Conversion
* Integer Conversion
  * 상수 또는 변수에 저장할 수 있는 숫자의 범위는 타입마다 다르기 때문에 타입 변환이 필요하다.
```swift
let twoThousand: UInt16 = 2_000
let one: UInt8 = 1
let twoThousandAndOne = twoThousand + UInt16(one)
```
<br>

* Integer and Floating-Point Conversion
```swift
let three = 3
let pointOneFourOneFiveNine = 0.14159
let pi = Double(three) + pointOneFourOneFiveNine // Int -> Double 변환
let integerPi = Int(pi) // Double -> Int 변환
```
<br>

### :memo: Reference
* https://kotlinlang.org/docs/reference/basic-syntax.html
