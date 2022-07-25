# 16장
## nested class
* 클래스 내에 존재하는 클래스
* 코드를 간단하게 표현하기 위해 사용
* 컴파일 시, 감싸고 있는 클래스 이름 뒤에 `$` 기호를 붙인 후 nested class의 이름이 나옴
  * `OuterOfStatic$StaticNested.class`
<br>

### nested class의 구분
* static class
* inner class
  * local inner class
  * anonymous inner class
<br>

### static nested class
* 한 곳에서만 사용되는 클래스를 묶어 처리하고자 할 때 사용
* 감싸고 있는 클래스 이름 뒤에 `.`을 찍어 호출할 수 있음
* 겉으로 보기에는 유사하지만, 내부적으로 구현이 달라야 할 때 사용
* 감싸고 있는 클래스의 static 변수만 참조 가능
<br>

### inner class
* 캡슐화를 통해 내부 구현을 감주고자 할 때 사용
* 내부 클래스를 감싸고 있는 외부 클래스의 어떤 변수든 접근 가능
* GUI 관련 프로그램을 개발할 때 가장 많이 사용 - 리스너 처리 등
<br>
