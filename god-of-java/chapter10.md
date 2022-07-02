# 10장
## 상속

``` java
package com.inheritance;

// Parent.java
public class Parent {
  public parent() {
    
  }
}

// Child.java
public class Child extends Parent {
  public child() {
    
  }
}
```
* 확장을 통해 부모 클래스에 `public` 및 `protected`로 선언되어 잇는 모든 변수와 메소드를 자신의 것처럼 사용할 수 있음
* UML의 클래스 다이어그램에서 `Child -▷ Parent`로 표현하여 상속 관계를 나타낼 수 있음
* 부모 클래스에서 상속을 위해 할 작업은 기본 생성자를 만들어두는 것 외에 별도로 없음
* 자식 클래스의 생성자가 호출되면, 자동으로 부모 클래스의 매개변수 없는 생성자가 실행됨
* 자바에서는 다중 상속이 불가능함
<br>

### 상속과 생성자
``` java
package com.inheritance;

// Parent.java
public class Parent {
  public parent(String name) {
    
  }
}

// Child.java
public class Child extends Parent {
  public child() {
    System.out.println("Child"); // 에러 - 부모 클래스의 생성자로 넘어갈 매개변수가 없어, 에러 발생
    super("Child");              // 해결 - super()를 통해 부모 클래스의 생성자로 "Child" 전달
  }
}
```
* 부모 클래스에 매개변수가 있는 생성자만 있을 경우, 기본 생성자가 없다는 에러가 발생함
  * 부모 클래스에 매개변수가 없는 기본 생성자를 설정해주거나,
  * 자식 클래스에서 `super()`를 사용하여 부모 클래스의 생성자를 명시적으로 지정해주어야 함
  * `super()`는 반드시 자식 클래스 생성자의 가장 첫 줄에 선언되어야 함
  * 자식 클래스 생성자에서 `super()`를 명시적으로 지정하지 않을 경우, 컴파일시 자동으로 `super()`가 추가됨
* 부모 클래스에 생성자가 여러개 있고 `super()`로 생성자를 호출하여 null 값을 넘겨줄 경우, 어떤 생성자로 값이 전달되어야 할지 모호함
  * `super()`를 사용하여 생성자를 호출할 때에는 모호한 null값 보다는 생성자의 기본 타입을 넘겨주는 것이 좋음
<br>

### 메소드 overriding
``` java
package com.inheritance;

// Parent.java
public class Parent {
  public parent(String name) {
    
  }
}

// Child.java
public class Child extends Parent {
  public child() {
    System.out.println("Child"); // 에러 - 부모 클래스의 생성자로 넘어갈 매개변수가 없어, 에러 발생
    super("Child");              // 해결 - super()를 통해 부모 클래스의 생성자로 "Child" 전달
  }
}
```
* 부모 클래스에 선언되어 있는 메소드와 동일한 메소드를 자식 클래스에 선언해서 사용하는 것
* 접근 제어자, 리턴 타입, 메소드 이름, 매개변수 타입 및 개수가 모두 동일해야만 메소드 overriding이라고 함

### 참조 자료형의 형 변환
### 다형성 (Polymorphism)
### 자식 클래스
