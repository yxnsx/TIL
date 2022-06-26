# 7장
## 배열
### 배열 선언
``` java
// 선언 방법
int[] lottoNumbers; // 권장
int lottoNumbers[];

// 배열의 길이 지정
lottoNumbers = new int[7];

// 배열 선언과 동시에 길이를 지정하며 초기화
int[] lottoNumbers = new int[7];

// 배열의 값 지정
lottoNumbers[1] = 15;
```
* 한 가지 타입에 대해 한 변수에 여러 개의 값을 넣을 수 있는 자료구조
* 새 배열 선언시, 배열의 길이를 지정해주어야 함
* 새 배열 선언시, 타입과 배열 변수명 사이에 중괄호 넣는 것을 권장함
* 배열은 참조 자료형이므로, 다른 참조 자료형들과 마찬가지로 `new`를 사용하여 새 객체를 생성해줌
* 배열은 인덱스 0부터 시작함
* 배열에 존재하지 않는 인덱스에 값을 할당하거나 해당 인덱스 값을 참조할 경우 `ArrayIndexOutOfBoundsException`이 발생함
* 배열의 길이를 지정해주지 않고 값을 참조할 경우, `null`을 출력함
<br>

### 배열의 유형 - 기본 자료형 배열 / 참조 자료형 배열
``` java
// 기본 자료형
byteArray[0] = 0; // byte, short, int, long
floatArray[0] = 0.0; // float, double
charArray[0] = [ ]; // 공백(₩u0000) 표시를 위해 대괄호 사용
booleanArray[0] = false;
System.out.println(new byte[0]); // -> [B@14ae5a5 출력

// 참조 자료형
stringArray[0] = "string";
customClassArray[0] = new CustomClass();
System.out.println(new String[0]); // -> [Ljava.lang.String;@1540e19d 출력
```
* 기본 자료형 배열의 경우, 배열의 길이를 지정해주었다면 각 값에 대해 초기화를 하지 않아도 각 자료형의 기본값이 할당됨
* 기본 자료형 배열의 기본값을 출력하면 배열을 나타내는 `[` + 해당 기본 자료형을 나타내는 문자 + @고유번호가 출력됨

| byte | short | int | long | float | double | char | boolean |
| ---- | ----- | --- | ---- | ----- | ------ | ---- | ------- |
| b | S | I | J | F | D | C | Z |

* 참조 자료형 배열의 경우, 각 값을 초기해주지 않는다면 null 값이 할당됨
* 참조 자료형 배열의 기본값을 출력하면 배열을 나타내는 `[` + 해당 배열의 참조 자료형 + @고유번호가 출력됨
<br>

### 중괄호를 이용한 1차원 배열 선언
``` java
int[] lottoNumbers = {5, 12, 23, 25, 38, 41, 2};

int[] lottoNumbers;
lottoNumbers = {5, 12, 23, 25, 38, 41, 2}; // Compile error
```
* 배열을 선언과 함께 초기화하려면 중괄호 안에 넣고자 하는 값들을 `,`로 구분하여 순서대로 나열하면 됨
* 이 방식을 이용하여 두 줄로 초기화하면 컴파일 에러가 발생함
<br>

## 2차원 배열
### 배열 선언
``` java
// 선언 방법
int[][] twoDim; // 권장
int[] twoDim[];
int twoDim[][];

// 배열의 길이 지정 방법 - 1
twoDim = new int[2][3];

// 배열의 길이 지정 방법 - 2
twoDim[0] = new int[2];
twoDim[1] = new int[3];

// 배열 선언과 동시에 길이를 지정하며 초기화
int[][] twoDim = new int[2][3];

// 배열의 값 지정
twoDim[0][2] = 15;
```
* 배열 크기 지정시, 1차원의 배열 길이 지정은 필수적이며 길이를 지정하지 않을 경우 컴파일시 에러가 발생함
<br>

### 중괄호를 이용한 2차원 배열 선언
``` java
int[][] twoDim = {{1, 2}, {3, 4, 5}};

int[][] twoDim;
twoDim = {{1, 2}, {3, 4, 5}}; // Compile error
```
* 배열을 선언과 함께 초기화하려면 중괄호 안에 넣고자 하는 값들을 `,`로 구분하여 순서대로 나열하면 됨
* 이 방식을 이용하여 두 줄로 초기화하면 컴파일 에러가 발생함
<br>

## 배열을 위한 for 루프
``` java
int[][] twoDim = {{1, 2}, {3, 4, 5}};
for (int[] dimArray: twoDim) {
  for (int[] data: dimArray) {
  }
}
  
```
* JDK 5에서 For문에서의 쉬운 `Collection` 활용을 위한 문법이 추가됨
* 배열의 각 데이터를 임시로 담아둘 변수의 이름을 지정하고, 배열의 0번째 인덱스부터 순서대로 해당 변수에 할당되는 방식임
* 배열의 각 값만 다루어야 할 경우엔 위의 for 루프가 유리하고, 인덱스도 함께 필요할 경우엔 기존의 for 루프가 유리함
