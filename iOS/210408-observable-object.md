# :fire: Observable Object
* 객체에 변화가 있기 전에 알리는 publisher를 지닌 오브젝트

<br>

### :sparkles: 선언 방법
```swift
protocol ObservableObject : AnyObject
```
<br>

### :sparkles: 개요
* 기본적으로  `ObservableObject`는  `@Published` 프로퍼티가 변경되기 전에 변화된 값을 알리는 `objectWillChange`의 publisher를 포함한다.
```swift
class Contact: ObservableObject {
    @Published var name: String
    @Published var age: Int

    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }

    func haveBirthday() -> Int {
        age += 1
        return age
    }
}

let john = Contact(name: "John Appleseed", age: 24)
cancellable = john.objectWillChange
    .sink { _ in
        print("\(john.age) will change")
}
print(john.haveBirthday())
// Prints "24 will change"
// Prints "25"

```
<br>

### :memo: Reference
* https://developer.apple.com/documentation/combine/observableobject
