# 9장
## 패키지
``` java
package com.javapackage;

public class Package {
  public static void main(String[] args) {
    
  }
}
```
* 클래스들을 구분짓는 폴더와 비슷한 개념
* 클래스들을 분류하지 않으면 이름이 중복되거나 클래스를 혼동하는 일이 발생함
<br>

### 패키지 이름 규칙
| 패키지 시작 이름 | 내용 |
|--------------|-----|
| java | 자바 기본 패키지 (Java 벤더에서 개발) |
| javax | 자바 확짱 패키지 (Java 벤더에서 개발) |
| org | 일반적으로 비영리단체(오픈소스)의 패키지 |
| com | 일반적으로 영리단체의 패키지 |
* 패키지 이름은 모두 소문자로 지정함
* 자바 예약어를 사용해서는 안됨
<br>

### 패키지 선언시의 제약사항
* 소스 내 java 문장 중 가장 첫 줄에 위치해야 함
* 소스 당 하나의 패키지 선언만 존재해야 함
* 패키지 이름과 실제 위치한 폴더의 이름이 같아야 함
* 패키지 이름을 java로 시작해서는 안됨
<br>

### import
``` java
package com.javapackage;

import com.javapackage.sub.Sub; // 특정 클래스만 import
import com.javapackage.sub.*;   // 해당 패키지의 모든 클래스 import
import static com.javapackage.sub.SubStatic.CLASS_NAME;

public class Package {
  public static void main(String[] args) {
    Sub sub = new Sub()
  }
}
```
* 다른 패키지에 있는 클래스에 접근하기 위해서는 해당 클래스의 패키지 경로를 `import`해주어야 함
* `*`를 이용하여 해당 패키지의 모든 클래스를 `import`할 수 있음
* `*`를 이용할 경우, 해당 패키지의 하위 패키지에 속한 클래스들은 `import`되지 않음
* JDK 5부터는 `import static`이 추가되어 static 변수와 메소드를 용이하게 사용할 수 있도록 함
* `import static`을 이용하면 클래스 이름을 통해 접근할 필요 없이 static 변수나 메소드를 사용할 수 있음
* `import`를 하지 않아도 되는 패키지는 `java.lang` 패키지, 같은 패키지가 있음
<br>

## 접근 제어자 (Access modifier)
### 접근 제어자의 종류
|             | 해당 클래스 내 | 동일 패키지 내 | 상속받은 클래스 내 | import한 클래스 내 |
|-------------|-------------|------------|---------------|------------------|
| <b>public</b> | O | O | O | O |
| <b>protected</b> | O | O | O | X |
| <b>(package-private)</b> | O | O | X | X |
| <b>private</b> | O | X | X | X |
* 접근 제어자는 메소드 뿐만 아니라 인스턴스 변수, 클래스 변수, 클래스 선언 등에 사용함
<br>

### 접근 제어자 선언시의 유의점
* public class가 한 파일 내에 2개 이상이 되어서는 안됨
  * 소스 파일의 이름이 public class 이름과 동일해야 하기 때문
