# 18장
## 1권 정리
### 객체지향 개발 관련 용어
* 클래스 - 상태와 행위를 갖는 기본 단위 / 사물의 단위
* 상태와 행위 - 상태는 클래스나 인스턴스 변수로, 행위는 메소드로 표현
* 캡슐화 - 연관된 상태와 행위를 결정하는 기능을 묶어주는 것 / 정보은닉과 모듈화가 가능하게 해줌
* 메시지 - 메소드에서 다른 메소드를 호출할 때 전달하는 값
* 객체 - 사물의 단위를 나타내는 클래스를 통해 만들어진 각 사물
* 상속 - 부모에 선언된 변수와 메소드에 대한 사용권을 갖는 것
* 다형성 - 같은 부모 클래스에서 파생되었더라도 자식 클래스들의 기능이 각기 다를 수 있다는 것
* Overriding - 부모 클래스에 선언되어 있는 메소드와 선언은 동일하지만 구현이 다른 것
* Overloading - 동일한 이름의 메소드에 대해 매개변수들을 다르게 하는 것
<br>

### Java comment
* 한 줄 주석 - 해당 줄을 실행하지 않도록 할 때 사용
```
// 주석 처리할 내용
```
* 블록 주석 - 여러 줄을 실행하지 않도록 할 때 사용
```
/* 주석 시작
주석 내용
주석 끝 */
```
* javadoc 주석 - API 문서에 설명을 표시할 때 사용
```
/** 주석 시작
주석 내용
주석 끝 */
```
<br>

### Package와 Import
* 패키지 선언시 유의사항
  * 패키지는 package로 시작하며, 하위 패키지로 내려갈 때마다 `.`을 찍어주어야 함
  * 반드시 소스코드의 가장 첫 줄에 존재해야 함
  * 패키지 이름에 자바 예약어가 포함되어서는 안됨
  * 모두 소문자로 구성하는 것이 일반적임
  * 일반적인 패키지는 java나 javax로 시작되어서는 안됨
  * 패키지에 해당하는 폴더에 클래스가 존재하는 것이 일반적임
* Import
  * 다른 패키지에 있는 클래스를 사용하기 위한 문장
  * 다른 클래스에 static으로 선언되어 잇는 접근 가능한 변수를 참조하기 위해서는 import static을 사용해야 함
  * 단일 패키지 내의 모든 클래스를 참조하기 위해서는 `*`을 사용해야 함
<br>

### Java type
* 기본 자료형
  * 초기화시 바로 값 지정 가능
  * 정수형 - byte, short, int, long, char
  * 소수형 - float, double
  * 기타 - boolean
* 참조 자료형
  * 초기화시 일반적으로 new와 생성자를 지정하여 객체 생성
  * 기본 자료형을 제외한 모든 자료형
<br>

### 연산자
* 할당 연산자
* 사칙 연산자
* 대입 연산자
* 단항 연산자
* 비교 연산자
* 조건 논리 연산자
* 논리 연산자
* 삼항 연산자
* Bitwise 연산자
* Bit 이동 연산자
* Bit 대입 연산자
<br>

### 조건문
* if
* if - else
* if - eise if
* switch - case
<br>

### 반복문
* while
* do - whild
* for loop
<br>

### 접근 제어자
* public - 누구나 접근 가능
* protected - 동일 패키지 내 혹은 상속받은 경우 접근 가능
* (package-private) - 동일 패키지 내에 있을 경우 접근 가능
* private - 해당 클래스 내에서만 접근 가능
<br>

### 선언시 사용할 수 있는 제어자
* 접근 제어자 - public, protected, private
* 구현 필요 제어자 - abstract
* 하나의 인스턴스만 허용하는 제어자 - static
* 값 수정 제한 제어자 - final
* strict 소수값 제어자 - strictfp
* Annotation
* 동시 접근 제어자 - synchronized
* 타 언어로 구현되었음을 명시하는 제어자 - native
* 실행 시의 동작 방법을 명시하는 제어자 - transient, volatile

### 클래스
* 자바에서 만든 코드를 관리하는 클래스 파일(.class)이 되는 타입
  * 클래스
  * 인터페이스
  * abstract 클래스
  * enum 클래스
  * annotation 선언 