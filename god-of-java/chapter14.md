# 14장
## 예외
* There is no rule has no exception.
* 예상한 일 및 예상치 못한 일이 발생하면 예외(`Exception`)라는 것을 던짐
* 예외가 발생하면 첫 줄에는 어떤 예외가 발생했는지 출력되고, 그 다음 줄부터는 `at`으로 시작하는 스택 트레이스가 출력됨
* 모든 예외의 부모 클래스는 `java.lang.Exception` 클래스임
* 예외 처리 - 예외 발생을 미리 예견하고 안전장치를 하는 것
<br>

### `try-catch` / `finally`
```java
public void arrayOutOfBoundsTryCatch() {
  int[] intArray = new int[5];
  try {
    System.out.println(intArray[5]);
                       
  } catch (ArrayIndexOutOfBoundsException e) {
    System.err.println(intArray.length);
    
  } catch (Exception e) {
    System.err.println("Exception occured");
    
  } finally {
    
  }
}
```
* `try` 뒤에 중괄호로 예외가 발생하는 문장들을 묶어주고 `catch` 괄호 안에 예외 처리를 구현함
* `try` 블록 내에서 예외가 발생하면 그 이후 문장은 실행되지 않고 바로 `catch` 블록으로 넘어감
* 오류가 발생하는 부분에서는 `System.err` 사용을 생활화하는 것이 좋음
* `catch` 블록은 여러개 만들 수 있으며, `catch` 블록의 순서는 매우 중요함
* 부모 예외 클래스가 이미 `catch`를 했을 경우, 자식 클래스가 예외를 처리할 기회가 없으므로 `Exception` 클래스로 `catch`하는 것은 가장 마지막에 있을 것을 권장함
* `finally` 블록은 예외 발생 여부와 상관없이 실행되며 코드의 중복을 피하기 위해 반드시 필요햠
<br>

### 예외의 종류
* `error`
  * 자바 프로그램 밖에서 발생한 예외
  * 프로세스에 영향을 줌 (프로그램이 멈춤)
* `runtime exception` 또는 `unchecked exception`
  * 자바 프로그램 내에서 발생한 예외
  * 예외가 발생할 것을 미리 감지하지 못했을 때 발생함
  * 컴파일시에 체크되지 않기 때문에 `unchecked exception`이라고도 불림
* `checked exception`
  * 위의 둘을 제외한 모든 예외
<br>

### `java.lang.Throwable`
* `exception`과 `error`의 공통 부모 클래스
* `Throwable`에 선언되어 있는 생성자
  * `Throwable()`
  * `Throwable(String message)`
  * `Throwable(String message, Throwable cause)`
  * `Throwable(Throwable cause)`
* `Throwable`에 선언되어 있고, `exception`에서 Overriding한 메소드 중 가장 많이 사용되는 메소드
  * `getMessage()` - string 형태의 예외 메시지 제공
  * `toString()` - 예외 클래스 이름을 포함한 더 자세한 string 형태의 예외 메시지 제공
  * `printStackTrace()` - 첫 줄에는 예외 메시지, 두 번째 줄부터는 예외 발생 메소드들의 호출 관계 출력
<br>

### `throws`
```java
// Case 1
public void throwException(int number) {
  try {
    if (number > 12) {
      throw new Exception("Number is over than 12");
    }
    System.err.println("Number is " + number);
                       
  } catch (Exception e) {
    e.printStackTrace();
  }
}

// Case 2
public void throwsException(int number) throws NullPointerException, Exception {
  if (number > 12) {
    throw new Exception("Number is over than 12");
  }
  System.out.println("Number is " + number);
}
```
* `throw`를 이용하여 예외를 던질 수 있음
* Case 2와 같이 메소드에 `throws` 선언을 할 경우, 해당 메소드에서 발생한 예외는 이를 호출한 메소드로 전달됨
* `throws` 선언된 메소드 내에는 `try-catch` 블록이 없어도 되지만, 이를 호출하는 곳에서 `try-catch` 처리를 해주어야 함
<br>

### Custom exception
* 예외 클래스는 `Throwable`이나 그 자식 클래스를 상속받아 임의로 만들 수 있음
* exception 처리를 위한 클래스라면 `java.lang.Exception` 클래스를 상속받는 것이 좋음
<br>

### 자바 예외 처리 전략
* 예외를 처리할 때에는 표준을 정하고 진행해야 함
* Custom exception 정의시 반드시 `try-catch`로 묶어줄 필요가 있을 경우라면 `Exception` 클래스 확장을 권장함
* Custom exception 정의시 실행 중 예외 발생 확률이 높은 경우라면 `RuntimeException` 클래스 확장을 권장함
* `catch` 블록을 비워두면 예외 분석이 어려워지므로 꼭 로그 등의 처리를 해주어야 함
