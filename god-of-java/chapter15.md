# 15장
## String
* 클래스 중 더하기 연산을 제공하는 클래스는 String 밖에 없음
* String은 `public final`로 선언된 클래스이므로 확장하여 사용할 수 없음
<br>

### String 클래스의 구현 인터페이스
* `Serializable`
  * 구현해야 하는 메소드가 하나도 없는 특이한 인터페이스
  * 이 인터페이스를 구현한다고 선언해 놓으면, 해당 객체를 파일로 저장하거나 다른 서버에 전송 가능한 상태가 됨
* `Comparable`
  * 매개변수로 넘어가는 객체와 현재 객체가 같은지를 비교하는 데에 사용됨
  * int 타입을 리턴하며, 순서상으로 같으면 0, 앞에 있으면 -1, 뒤에 있으면 1을 리턴함
* `CharSequence`
  * 해당 클래스가 문자열을 다루기 위한 클래스라는 것을 명시적으로 나타내는 데에 사용됨
<br>

### String to byte
* String 클래스에서 자주 사용하는 생성자는 매개변수로 byte 배열을 받음
  * `String(byte[] bytes)`
  * `String(byte[] bytes, String charsetName)`
* String 클래스는 문자열 값을 byte 배열로 변환하는 getByte() 메소드를 제공함

| 리턴 타입 | 메소드 이름 및 매개변수 | 설명 |
| ------- | ----------------- | --- |
| byte[] | `getBytes()` | 기본 캐릭터 셋의 byte 배열 생성 |
| byte[] | `getBytes(Charset charset)` | 지정한 캐릭터 셋 객체 타입으로 byte 배열 생성 |
| byte[] | `getBytes(String charsetName)` | 지정한 이름의 캐릭터 셋을 갖는 byte 배열 생성 |

* 캐릭터 셋을 잘 알고 있거나, 같은 프로그램 내에서 문자열을 byte 배열로 변환할 때에는 가장 첫 번째 메소드 사용
* 다른 시스템에서 전달받은 문자열을 byte 배열로 변환할 때에는 두 번째나 세 번째의 메소드 사용
* 표준 캐릭터 셋은 `java.nio.Charset` 클래스 내에 정의되어 있음 - 대부분은 `UTF-16` 사용
* 한글의 경우, byte 배열로 변환할 때 사용하는 캐릭터 셋에 따라 배열의 크기가 달라짐
  * ex) `EUC-KR`은 글자당 2바이트, `UTF-16`은 글자당 3바이트
* 존재하지 않는 캐릭터 셋의 이름을 지정할 경우에는 `UnsupportedEncodingException`이 발생하므로 반드시 `try-catch`로 감싸주거나 throws 구문을 추가해주어야 함
<br>

### 문자열의 길이를 확인하는 메소드
| 리턴 타입 | 메소드 이름 및 매개변수 | 설명 |
| ------- | ----------------- | --- |
| int | `length()` | 문자열의 길이 리턴 |
* 공백도 길이에 포함됨
<br>

### 문자열이 비어있는지 확인하는 메소드
| 리턴 타입 | 메소드 이름 및 매개변수 | 설명 |
| ------- | ----------------- | --- |
| boolean | `isEmpty()` | 문자열이 비어있으면 true 리턴 |
* 공백만으로 구성된 문자열이라도 비어있지 않은 것이므로 false 리턴
<br>

### 문자열이 같은지 비교하는 메소드 
| 리턴 타입 | 메소드 이름 및 매개변수 |
| ------- | ----------------- |
| boolean | `equals(Object anObject)` |
| boolean | `equalsIgnoreCase(String anotherStr)` |
| int | `compareTo(String anotherStr)` |
| int | `compareToIgnoreCase(String str)` |
| boolean | `contentEquals(CharSequence cs)` |
| boolean | `contentEquals(StringBuffer sb)` |
```java
// Case 1
String text1 = "Check value";
String text2 = "Check value";
boolean checkValue = text1 == text2; // true
text1.equals(text2);                 // true

// Case 2
String text1 = "Check value";
String text2 = new String("Check value");
boolean checkValue = text1 == text2; // false
text1.equals(text2);                 // true
```
#### equals()
* 동일한 값을 갖는 객체가 있으면 constant pool에 존재하는 기존 객체의 값을 재사용함
* Case 1과 같이 객체 선언을 할 경우, 기존 객체의 값을 재사용하기 때문에 text1과 text2는 사실상 같은 객체임
* Case 2와 같이 객체 선언을 할 경우, 기존 객체의 값을 재사용하는 대신 new를 통해 별도의 객체를 생성함

#### compareTo()
* 보통 정렬을 할 때 사용하며 매개변수로 넘겨준 객체가 알파벳 순으로 앞에 위치하면 양수, 뒤에 위치하면 음수를 리턴함

#### contentEquals()
* 매개변수로 넘어온 `CharSequence`와 `StringBuffer` 객체가 String 객체와 같은지를 비교하는데 사용함
<br>

### 특정 조건에 맞는 문자열이 있는지를 확인하는 메소드
| 리턴 타입 | 메소드 이름 및 매개변수 |
| ------- | ----------------- |
| boolean | startsWith(String prefix) |
| boolean | startsWith(String prefix, int toffset) |
| boolean | endsWith(String suffix) |
| boolean | contains(CharSequence s) |
| boolean | matches(String regex) |
| boolean | regionMatches(boolean ignoreCase, int toffset, String other, int ooffset, int len) |
| boolean | regionMatches(int toffset, String other, int ooffset, int len) |
* 매개변수로 넘어온 값이 문자열에 존재하는지 확인하기 위해서는 `contains()` 메소드를 사용
* `matches()` 메소드는 `contains()` 메소드와 비슷하지만 매개변수로 넘어오는 값이 정규표현식으로 되어 있어야 함
* `regionMatches()` 메소드는 문자열 중 특정 영역이 매개변수로 넘어온 문자열과 동일한지를 확인하는데에 사용됨
* `regionMatches()` 메소드의 매개변수 중 결과가 무조건 false로 나오는 경우
  * `toffset`이 음수일 때
  * `ooffset`이 음수일 때
  * `toffset + len`이 비교대상의 길이보다 클 때
  * `ooffset + len`이 `other` 객체의 길이보다 클 때
  * `ignoreCase`가 true인 경우 - 비교 범위의 문자들을 모두 소문자로 변경한 후, 같은 index의 char가 같을 때
  * `gnoreCase`가 false인 경우 - 비교 범위의 문자들 중 같은 index의 char가 다를 때
<br>

### string 내의 위치를 찾아내는 메소드
* `indexOf()` 메소드를 이용하면 해당 객체의 특정 문자열이나 char가 있는 위치를 알 수 있음
* `indexOf()` 메소드는 문자열의 모든 내용을 다 확인해봐야 한다는 단점이 있음
* 찾고자 하는 문자열이나 char가 없을 경우 -1을 리턴함
* 크게 `indexOf()`와 `lastIndexOf()`로 나눌 수 있음
  * `indexOf()` - 앞(왼쪽)에서부터 문자열이나 char를 찾음
  * `lastIndexOf()` - 뒤(오른쪽)에서부터 문자열이나 char를 찾음
<br>

### string 값의 일부를 추출하는 메소드
#### char 단위의 값을 추출하는 메소드
| 리턴 타입 | 메소드 이름 및 매개변수 | 설명 |
| ------- | ----------------- | --- |
| char | `charAt(int index)` | 특정 위치의 char 값을 리턴
| void | `getChars(int srcBegin, int srcEnd, char[] dst, int dstBegin)` | 매개변수로 넘어온 dst라는 char 배열 내의 srcBegin에서 srcEnd
| int | `codePointAt(int index)` | 특정 위치의 유니코드 값 리턴<br>리턴 값을 char로 형변환하여 char 값을 출력할 수 있음 |
| int | `codePointBefore(int index)` | 특정 위치 앞에 있는 char의 유니코드 값을 리턴 |
| int | `codePointCount(int beginIndex, int endIndex)` | 지정한 범위에 있는 유니코드 개수 리턴 |
| int | `offsetByCodePoints(int index, int codePointOffset)` | 지정된 index부터 offset이 설정된 인텍스 리턴 |
<br>

#### char 배열의 값을 string으로 변환하는 메소드
| 리턴 타입 | 메소드 이름 및 매개변수 | 설명 |
| ------- | ----------------- | --- |
| static String | `copyValueOf(char[] data)` | char 배열에 있는 값을 문자열로 변환 |
| static String | `copyValueOf(char[] data, int offset, int count)` | char 배열에 있는 값 중, offset에서 count 개수만큼만 문자열로 변환 |
<br>

#### String 값을 char 배열로 변환하는 메소드
| 리턴 타입 | 메소드 이름 및 매개변수 | 설명 |
| ------- | ----------------- | --- |
| char[] | `toCharArray()` | 문자열을 char 배열로 변환하는 메소드 |
<br>

#### 문자열의 일부 값을 잘라내는 메소드
| 리턴 타입 | 메소드 이름 및 매개변수 | 설명 |
| ------- | ----------------- | --- |
| String | `substring(int beginIndex)` | beginIndex부터 끝까지 대상 문자열을 잘라 리턴 |
| String | `substring(int beginIndex, int endIndex)` | beginIndex에서부터 endIndex까지 대상 문자열을 잘라 리턴 |
| CharSequence | `subSequence(int beginIndex, int endIndex)` | beginIndex에서부터 endIndex까지 대상 문자열을 잘라 리턴 |
* `indexOf()` 메소드와 더불어 가장 많이 사용하는 메소드 중 하나임
<br>

#### 문자열을 여러 개의 String 배열로 나누는 메소드
| 리턴 타입 | 메소드 이름 및 매개변수 | 설명 |
| ------- | ----------------- | --- |
| String[] | `split(String regex)` | regex에 있는 정규 표현식에 맞추어 문자열을 잘라 리턴 |
| String[] | `split(String regex, int limit)` | regex에 있는 정규 표현식에 맞추어 문자열을 잘라 리턴<br>이 때, 리턴되는 String 배열의 크기가 limit보다 커서는 안됨 | ㅣ
* 정규 표현식을 이용하여 문자열을 나누려 하는 경우, `split()` 메소드를 사용하는 것이 편리함
* 특정 string을 이용하여 문자열을 나누려 하는 경우, StringTokenizer를 사용하는 것이 편리함
<br>

### String 값을 바꾸는 메소드
#### 문자열을 합치는 메소드 / 공백을 없애는 메소드
| 리턴 타입 | 메소드 이름 및 매개변수 | 설명 |
| ------- | ----------------- | --- |
| String | concat(String str) | 매개변수로 받은 str을 기존 문자열이 우측에 붙인 새로운 문자열 객체를 생성하여 리턴 |
| String | trim() | 문자열의 맨 앞과 맨 뒤에 있는 공백들을 제거한 문자열 객체 리턴 |
* `trim()` 메소드의 경우, 문자열이 공백만으로 이루어져 있는지, 공백을 제외한 값이 포함되어있는지 확인하기에 용이함
<br>

#### 내용을 교체하는 메소드
| 리턴 타입 | 메소드 이름 및 매개변수 | 설명 |
| ------- | ----------------- | --- |
| String | replace(char oldChar, char newChar) | oldChar의 값을 newChar로 대치 |
| String | replace(CharSequence target, CharSequence replacement) | target과 같은 값을 replacement로 대치 |
| String | replaceAll(String regex, String replacement) | regex의 정규 표현식에 포함되는 모든 내용을 replacement로 대치 |
| String | replaceFirst(String regex, String replacement) | regex의 정규 표현식에 포함되는 첫 번째 내용을 replacement로 대치 |
<br>

#### 특정 형식에 맞춰 값을 치환하는 메소드
