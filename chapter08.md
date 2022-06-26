# 8장
## 참조 자료형
* 기본 자료형 8개를 제외한 나머지 타입
  * 기본 자료형 - `byte`, `short`, `int`, `long`, `float`, `double`, `char`, `boolean`
* 기본 자료형과 참조 자료형의 가장 큰 차이는 `new`를 이용하여 객체를 생성하는지 여부임
* 참조 자료형 중 `String`은 예외적으로 `new` 없이 객체 생성이 가능함
<br>

### 참조 자료형의 생성자
``` java
// 매개변수가 없는 경우
public class ReferenceDefault {
  public static void main(String[] args) {
    ReferenceDefalut reference = new ReferenceDefault();
  }
}

// 매개변수가 있는 경우
public class ReferenceString {
  public ReferenceString() {}           // 1 - 매개변수가 없는 경우 호출
  public ReferenceString(String arg) {} // 2 - string 매개변수가 있을 경우 호출
  
  public static void main(String[] args) {
    ReferenceString reference = new ReferenceString();    // 매개변수가 없으므로 overloading을 통해 1 호출
    ReferenceString reference = new ReferenceString("a"); // 매개변수가 있으므로 overloading을 통해 2 호출
  }
}
```
* 생성자는 자바 클래스의 객체 또는 인스턴스를 생성하기 위해 존재함
* 생성자의 리턴 타입은 클래스의 객체이기 때문에 별도의 리턴 타입이 존재하지 않음
* 매개변수가 없는 경우, 기본 생성자는 컴파일 시 자동으로 만들어짐
* 매개변수가 있는 경우, 매개변수를 받을 생성자를 별도로 선언해주어야 함
* 클래스 선언시 인스턴스 변수, 생성자, 메소드 순으로 작성해주는 것이 좋음
* 생성자의 개수에는 제한이 없으나 너무 많으면 관리가 힘들어지므로 꼭 필요한 생성자만 만드는 것이 좋음
* 매개변수의 개수 및 타입에 따라 동일한 메소드 명의 생성자를 각각 생성해 두면 `overloading`을 통해 적절한 생성자를 이용할 수 있음
<br>

### 참조 자료형의 메소드
#### 메소드 종료조건
* `return` 값이 없는 `void` 메소드의 경우, 메소드의 모든 문장이 실행되었을 때
  * `void` 메소드는 메소드명 앞에 `void` 명시
* `return` 값이 있는 메소드의 경우, `return` 문장에 도달했을 때
  * `return` 값이 있는 메소드는 메소드명 앞에 메소드 종료시 반환할 데이터의 자료형 명시
  * `void` 메소드를 `return;`으로 마무리하여 메소드 수행을 종료할 수도 있음
* 예외가 발생했을 때(throw)
<br>

### static
#### static 메소드
* static 메소드를 사용하면 객체 생성 없이 메소드를 호출할 수 있음
* static 메소드는 클래스 변수만 사용할 수 있음
* 클래스 변수는 모든 객체에서 하나의 값을 바라보기 때문에 예상치 못한 상황이 발생할 수 있으므로 신중하게 사용해야 함

#### static 블록
``` java
static {
  // 딱 한 번만 수행할 내용
}
```
* 객체가 생성되면서 딱 한번만 실행되어야 하는 코드가 있을 경우 static 블록을 생성하여 사용함
* 여러 객체가 생성되더라도 한 번만 호출됨
* 클래스 내에 선언되어야 하며, 인스턴스 변수나 클래스 변수와 같이 특정 메소드나 생성자에 속해있어서는 안됨
* static 블록은 여러개를 선언할 수 있으며, 차례로 호출되기 때문에 선언 순서가 중요함
* static 블록 내에서는 static한 것들만 호출할 수 있음
* 생성자가 불리지 않더라도, 클래스에 대한 참조가 발생하자마자 호출됨
<br>

### Pass by value, Pass by reference
#### Pass by value
* 매개변수로 기본 자료형이 전달될 때의 방식
* 매개변수에 해당 값을 복사하여 전달
* 값을 전달받은 메소드에서 해당 값을 변경하더라도 원래의 값은 변하지 않음

#### Pass by reference
* 매개변수로 참조 자료형이 전달될 때의 방식
* 매개변수에 해당 값을 참조하는 주소값 전달
* 값을 전달받은 메소드에서 해당 값을 변경하면 원래의 값도 변경됨
<br>

### 가변인자(varargs)
``` java
public void calculateNumbers(int...numbers) {
  int total = 0;
  for (int number: numbers) {
    total += number;
  }
  System.out.println("Total: " + total);
}
```
* 매개변수의 개수가 유동적일 경우, `타입...변수명`의 형태로 메소드의 매개변수를 선언하여 유동적으로 넘겨줄 수 있음
* 하나의 메소드에서는 한 번만 사용 가능하며, 여러 개의 매개변수가 있을 경우 가장 마지막으로 선언되어야 함
