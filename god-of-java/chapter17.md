# 17장
## Annotation
* 클래스나 메소드, 변수 등을 선언할 때 @를 사용하여 표현
* 메타데이터라 불리기도 함
* annotation 관련 클래스들은 `java.lang.annotation` 클래스에 선언되어 있음
* annotation은 enum 클래스와 마찬가지로 상속이 불가능함
* 사용 목적
  * 컴파일러에게 정보 제공
  * 컴파일할 때와 설치(deployment) 시의 작업 지정
  * 실행 중 별도의 처리 제공
* 용도별 분류
  * 제약사항 선언: `@Deprecated`, `@Override`, `@NotNull`
  * 용도 선언: `@Entity`, `@TestCase`, `@WebService`
  * 행위 선언: `@Statefull`, `@Transaction`
  * 처리 선언: `@Column`, `@XmlElement`
<br>

### 미리 정의된 annotation
* `@Override` - 부모 클래스의 메소드를 Override 했다는 것을 명시적으로 선언하기 위해 사용
* `@Deprecated` - 클래스나 메소드가 더 이상 사용되지 않음을 명시적으로 선언하기 위해 사용
* `@SuppressWarnings` - 컴파일러에서 알리는 경고를 무시하기 위해 사용
<br>

### Meta annotation
* annotation을 직접 선언하기 위해 사용하는 annotation
* Meta annotation의 종류
  * `@Target(ElementType.---)` - annotation 적용 대상을 지정하기 위해 사용
    * CONSTRUCTOR: 생성자 선언시
    * FIELD: enum 상수를 포함한 필드 값 선언시
    * LOCAL_VARIABLE: 지역 변수 선언시
    * METHOD: 메소드 선언시
    * PACKAGE: 패키지 선언시
    * PARAMETER: 매개 변수 선언시
    * TYPE: 클래스, 인터페이스, enum 등 선언시
  * `@Retention(RetentionPolicy.---)` - annotation 정보의 유지 기간을 지정하기 위해 사용
    * SOURCE: annotation 정보가 컴파일시 사라짐
    * CLASS: 컴파일러에 의해 클래스 파일의 annotation 정보 참조 가능 / 가상머신에서는 사라짐
    * RUNTIME: 실행시 가상머신에 의해 annotation 정보 참조 가능
  * `@Documented` - annotation 정보가 Javadocs 문서에 포함된다는 것을 나타내기 위해 사용
  * `@Inherited` - 모든 자식 클래스에서 부모 클래스의 annotation 사용이 가능하다는 것을 나타내기 위해 사용
<br>

### Annotation 선언하기
```java
package c.annotation;

import java.lang.annotation.ElemenType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Target;

@Target(ElementType.METHOD)         // Annotation 사용 대상 지정 - @Target((ElementType.METHOD, ElementType.TYPE)) 형태로 여러개 선언 가능
@Retention(RetentionPolicy.RUNTIME) // 실행시 해당 annotation 참조
public @interface UserAnnotation {  // @interface를 선언하여 @UserAnnotation으로 사용 가능
  public int number();              // Annotation 내에 메소드 형태로 선언하여 해당 항목에 대한 타입으로 값 지정 가능
  public String text() default "This is first annotation";
}

// 사용 예시
puvlic class UserAnnotationSample {
  
  @UserAnnotation(number = 0)
  public static void main(String args[]) {
    UserAnnotationSample annotationSample = new UserAnnotationSample()
  }
  
  @UserAnnotation(number = 1, text = "sample")
  public void annotationSample() {
    // ...
  }
}
```
<br>
