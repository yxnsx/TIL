# :fire: Swift - The Basics
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
#### :heavy_check_mark: Integer Bounds
* Swift는 8, 16, 32, 64-bit 형식으로 정수를 제공한다.
* `min` 및 `max` 속성을 사용하여 각 정수 유형의 최솟값과 최댓값에 접근할 수 있다.
```swift
let minValue = UInt8.min  // minValue is equal to 0, and is of type UInt8
let maxValue = UInt8.max  // maxValue is equal to 255, and is of type UInt8
```
<br>

#### :heavy_check_mark: Int
* 명시적으로 크기가 지정된 데이터 사용 또는 성능, 메모리 사용량 등 최적화를 위한 작업 등 특별한 경우가 아니라면 Int 정수값을 사용한다.
* 32-bit 플랫폼에서의 Int size = `Int32`
* 64-bit 플랫폼에서의 Int size = `Int64`
<br>

#### :heavy_check_mark: UInt
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
  * 2진법 숫자 - `0b` 접두어 필요
  * 8진법 숫자 - `0o` 접두어 필요
  * 16진법 숫자 - `0x` 접두어 필요
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
  * 2진법 숫자 (2<sup>exp</sup>씩 곱함)
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
#### :heavy_check_mark: Integer Conversion
* 상수 또는 변수에 저장할 수 있는 숫자의 범위는 타입마다 다르기 때문에 타입 변환이 필요하다.
```swift
let twoThousand: UInt16 = 2_000
let one: UInt8 = 1
let twoThousandAndOne = twoThousand + UInt16(one)
```
<br>

#### :heavy_check_mark: Integer and Floating-Point Conversion
```swift
let three = 3
let pointOneFourOneFiveNine = 0.14159
let pi = Double(three) + pointOneFourOneFiveNine // Int -> Double 변환
let integerPi = Int(pi) // Double -> Int 변환
```
<br>

### :sparkles: Type Aliases
* 타입 별칭은 기존 타입의 대체 이름을 정의한다.
* 상황에 따라 더 적절한 이름으로 기존 유형을 참조하는 경우 유용하다.
* 타입 별칭을 정의하면 원래의 이름을 사용할 수 있는 모든 곳에서 별칭을 사용할 수 있다.
```swift
typealias AudioSample = UInt16
var maxAmplitudeFound = AudioSample.min
```
<br>

### :sparkles: Booleans
* Boolean 값은 `true` 또는 `false`만 될 수 있는 logical 값이다.
* 이러한 Boolean 값은 if와 같은 조건문으로 작업할 때 특히 유용하게 활용할 수 있다.
```swift
let orangesAreOrange = true
let turnipsAreDelicious = false

if turnipsAreDelicious {
    print("Mmm, tasty turnips!")
} else {
    print("Eww, turnips are horrible.")
}
```
<br>

### :sparkles: Tuples
* 튜플은 여러 값을 단일 복합 값으로 그룹화한다.
* 튜플은 반환 값이 여러 개인 함수에서 특히 유용하게 사용할 수 있다.
* 튜플 내의 값은 모든 유형이 될 수 있으며, 서로 동일한 유형일 필요는 없다.
```swift
let http404Error = (404, "Not Found")
// http404Error is of type (Int, String), and equals (404, "Not Found")
```
<br>

* 튜플 내의 값은 각각의 상수 또는 변수로 분해할 수 있으며, 다음과 같은 방법으로 각각에 접근할 수 있다.
```swift
let (statusCode, statusMessage) = http404Error

// Prints "The status code is 404"
print("The status code is \(statusCode)")

// Prints "The status message is Not Found"
print("The status message is \(statusMessage)")
```
<br>

* 튜플 내의 값 중 일부만 필요할 경우, 언더스코어(`_`)를 이용하여 불필요한 부분을 무시할 수 있다.
```swift
let (justTheStatusCode, _) = http404Error

// Prints "The status code is 404"
print("The status code is \(justTheStatusCode)")
```
<br>

* 0부터 시작하는 인덱스를 통해 튜플 내의 각 값에 접근할 수도 있다.
```swift
// Prints "The status code is 404"
print("The status code is \(http404Error.0)")

// Prints "The status message is Not Found"
print("The status message is \(http404Error.1)")
```
<br>

* 튜플을 정의할 시, 튜플 내의 각 값에 이름을 지정할 수 있다.
* 튜플 내의 각 값에 이름을 지정한 경우, 해당 값에 접근하기 위해 지정한 이름을 이용할 수 있다.
```swift
let http200Status = (statusCode: 200, description: "OK")

// Prints "The status code is 200"
print("The status code is \(http200Status.statusCode)")

// Prints "The status message is OK"
print("The status message is \(http200Status.description)")
```
<br>

### :sparkles: Optionals
* `optinal`은 상수 또는 변수가 "값이 없음"을 지닐 수 있음을 나타낸다.
* `optinal`은 두 가지 상태를 나타낼 수 있다.
  * 값이 있고, 그 값에 접근하기 위해 Optional을 해제할 수 있는 상태
  * 값이 없는 상태
* 스위프트의 `optinal`은 특별한 상수 없이 어떤 타입에도 값이 없음을 나타낼 수 있게 한다.
<br>

```swift
let possibleNumber = "123"
let convertedNumber = Int(possibleNumber)
// convertedNumber is inferred to be of type "Int?", or "optional Int"
```
* 위의 예시에서 `possibleNumber`의 값으로 "Hello, world"등이 지정될 수 있다.
* 이 때, `convertedNumber`에서의 `Int(possibleNumber)` 변환은 실패할 수 있다.
* 이러한 경우를 위해 `convertedNumber`의 값은 `Int?` 또는 `optional Int`로 추론된다.
<br>

#### :heavy_check_mark: nil
* 값이 없는 상태에 `nil`이라는 특정한 값을 할당하여 optional 변수로 지정할 수 있다.
* 기본값을 지정하지 않고 `optional` 변수를 정의할 경우, 변수는 자동으로 `nil` 값으로 설정된다.
```swift
// serverResponseCode contains an actual Int value of 404
var serverResponseCode: Int? = 404

// serverResponseCode now contains no value
serverResponseCode = nil

// surveyAnswer is automatically set to nil
var surveyAnswer: String?
```
<br>

#### :heavy_check_mark: If Statements and Forced Unwrapping
* if문으로 `optinal`과 `nil` 값을 비교해서 `optinal`이 값을 지니고 있는지 알아낼 수 있다.
```swift
if convertedNumber != nil {
    print("convertedNumber has an integer value of \(convertedNumber!).")
}
// Prints "convertedNumber has an integer value of 123."
```
<br>

#### :heavy_check_mark: Optional Binding
* optional binding을 통해 `optinal`이 값을 지니고 있는지 알아낼 수 있다.
* 값이 존재할 경우, 해당 값을 상수 또는 변수로 사용할 수 있다.
```swift
if let actualNumber = Int(possibleNumber) {
    print("The string \"\(possibleNumber)\" has an integer value of \(actualNumber)")
} else {
    print("The string \"\(possibleNumber)\" couldn't be converted to an integer")
}
// Prints "The string "123" has an integer value of 123"
```

#### :heavy_check_mark: Implicitly Unwrapped Optionals
* `optinal` 값이 항상 값을 지니고 있다고 가정할 수 있는 경우, 해당 값에 액세스 할 때마다 값의 유무를 확인할 필요가 없다.
* `optinal`로 선언된 변수 사용시, 해당 변수명 뒤에 느낌표를 넣어 항상 값을 지니고 있음을 나타낼 수 있다.
* 해당 변수 선언시, 자료형 뒤에 느낌표를 넣어 항상 값을 지니고 있음을 나타낼 수 있다.
```swift
let possibleString: String? = "An optional string."
let forcedString: String = possibleString! // requires an exclamation point

let assumedString: String! = "An implicitly unwrapped optional string."
let implicitString: String = assumedString // no need for an exclamation point
```
<br>

### :sparkles: Error Handling
* 실행 중 프로그램에서 나타나는 문제의 에러 상황에 따라 응답할 때 사용한다.
* 에러 처리는 내재하는 실패 원인을 판별하고, 필요한 경우 프로그램의 다른 부분으로 해당 에러를 전달할 수 있다.
* 에러 상황을 마주한 함수는 에러를 `throws`하고, 해당 함수의 호출자는 에러를 잡아내고 적절하게 응답할 수 있다.
* 이러한 함수는 에러를 `throws`할 수 있다는 것을 나타내기 위해 `throws` 키워드를 포함해야 한다.
```swift
func canThrowAnError() throws {
    // this function may or may not throw an error
}
```
<br>

* swift는 `catch`절에 의해 처리될 때까지 해당 범위 내에서 자동으로 에러를 전달한다.
* `do`문은 에러를 하나 이상의 `catch`절로 전파하는 새 구간을 생성한다.
```swift
do {
    try canThrowAnError()
    // no error was thrown
} catch {
    // an error was thrown
}
```
<br>

```swift
func makeASandwich() throws {
    // ...
}

do {
    try makeASandwich()
    eatASandwich()
} catch SandwichError.outOfCleanDishes {
    washDishes()
} catch SandwichError.missingIngredients(let ingredients) {
    buyGroceries(ingredients)
}
```
* 위의 예에서 `makeASandwich()` 함수는 깨끗한 접시가 없을 경우 또는 재료가 빠졌을 경우 에러를 발생시킨다.
* 아무런 에러도 발생하지 않았을 경우,`eatASandwich()` 함수가 호출된다.
* `do`문으로 감싸인 함수 호출에서는 어떠한 에러라도 `catch`절로 전달된다.
* 에러가 발생했고 해당 에러가 `SandwichError.outOfCleanDishes`와 일치할 경우, `washDishes()` 함수가 호출된다.
* 에러가 발생했고 해당 에러가 `SandwichError.missingIngredients`와 일치할 경우, `catch` 패턴에 의해 캡쳐된 `[String]` 값과 함께 `buyGroceries(_:)` 함수가 호출된다.
<br>

### :sparkles: Assertions and Preconditions
#### :heavy_check_mark: Debugging with Assertions
* swift의 표준 라이브러리에서 `assert(_:_:file:line:)`를 호출하여 assertion을 작성할 수 있다.
* 결과가 `true`일 경우, 코드 실행이 계속된다.
* 결과가 `false`일 경우, assertion에 실패하여 프로그램이 종료된다.
* `true` 또는 `false`를 판별할 수 있는 표현식과 결과가 `false`일 경우 보여질 메시지를 이 함수에 전달한다.
```swift
let age = -3
assert(age >= 0, "A person's age can't be less than zero.")
// This assertion fails because -3 isn't >= 0.
```
<br> 

* 단순히 조건만을 반복할 경우에는 메시지를 생략할 수 있다.
```swift
assert(age >= 0)
```
<br> 

* 조건을 이미 확인한 경우, `assertionFailure(_:file:line:)`함수를 호출하여 assertion이 실패했는지 알릴 수 있다.
```
if age > 10 {
    print("You can ride the roller-coaster or the ferris wheel.")
} else if age >= 0 {
    print("You can ride the ferris wheel.")
} else {
    assertionFailure("A person's age can't be less than zero.")
}
```
<br>

#### :heavy_check_mark: Enforcing Preconditions
* 조건이 `false`가 될 가능성이 있을 경우 precondition을 사용하지만, 코드가 계속 실행되기 위해서는 반드시 `true`여야 한다.
* 어떠한 값이 범위를 벗어나지는 않는지, 함수에 유효한 값이 전달되는지를 체크하기 위해 precondition을 사용한다.
* ` precondition(_:_:file:line:)` 함수를 호출하여 precondition을 작성할 수 있다.
* `true` 또는 `false`를 판별할 수 있는 표현식과 결과가 `false`일 경우 보여질 메시지를 이 함수에 전달한다.
* `preconditionFailure(_:file:line:)`함수를 호출하여 precondition이 실패했는지 알릴 수 있다.
```swift
let age = -3
assert(age >= 0, "A person's age can't be less than zero.")
// This assertion fails because -3 isn't >= 0.
```
<br>

### :memo: Reference
* https://docs.swift.org/swift-book/LanguageGuide/TheBasics.html
