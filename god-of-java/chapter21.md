# 21장
## Generic
* 타입 형 변환시 발생 가능한 문제점을 컴파일 시점에 체크하기 위한 타입
* 제네릭 타입의 이름
  * E: 요소
  * K: 키
  * N: 숫자
  * T: 타입
  * V: 값
  * S, U, V: 두 번쨰, 세 번쨰, 네 번째 선언 타입

### Wildcard
* <?>의 형태로 선언
* 정해져 있지 않은 형태의 제네릭 타입을 받고 싶을 때 사용
* 메소드의 매개변수로만 사용하는 것이 좋음

### Bounded wildcard
* <? extends Type>의 형태로 선언
* 해당 타입을 상속한 클래스만 적용 가능
* 값 할당이 불가하므로 조회용 매개변수로만 사용해야 함

### Generic method
```java
public <T> void genericMethod(WildcardGeneric<T> generic, T addValue){
    generic.setWildcard(addValue);
		T value = generic.getWildcard();
		System.out.println(value);
}

// Generic 타입이 여러개일 경우
public <S,T extends Car> void multiGenericMethod(WildcardGeneric<T> generic, T addValue, S another) {
    // ...
}
```
