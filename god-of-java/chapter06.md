# 6장
## 조건문
### if문
``` java
if (point > 90) {
  System.out.println("A");
  
} else if (point > 80) {
  System.out.println("B");
  
} else {
  System.out.println("C");
}
```
* `if` 다음에는 반드시 소괄호를 열고 닫아야 하며, 안에는 `boolean` 형태의 조건이 들어감
* 소괄호 안에 들어가는 조건의 결과가 `true`라면 if문 내부의 문장이 처리됨
* 소괄호 안에 들어가는 조건의 결과가 `false`라면 else if 또는 else문 내부의 문장이 처리됨
* `if` 처리를 할 문장이 하나라면 중괄호를 생략할 수 있지만, 그렇지 않다면 중괄호 안에 처리문장들을 넣어주어야 함
* 하나의 문장만 처리를 해야 할 경우라도 중괄호를 이용하면 코드 가독성이 좋아짐
<br>

### switch문
``` java
switch (numberOfWheel) {
  case 1: 
    System.out.println(numberOfWheel + "One foot bicycle");
    break;
  case 2: 
    System.out.println(numberOfWheel + "Motor cycle or bicycle");
    break;
  case 3: 
    System.out.println(numberOfWheel + "Three wheel car");
    break;
  case 4: 
    System.out.println(numberOfWheel + "Car");
    break;
  defalut:
    System.out.println(numberOfWheel + "Expensive car");
    break;
}
```
* `case`에 해당하는 값이 들어오면 해당 `case`의 문장이 처리되고, `break`가 있을 경우 switch문을 빠져나감
* `defalut` 내의 문장은 조건이 앞의 모든 `case`에 해당하지 않을 경우 또는 `case`문에 `break`가 없어 switch문을 빠져나가지 못했을 경우 실행됨
* switch문에서는 되도록 작은 숫자부터 조건을 증가시켜 가는 것이 좋음
* Java 6까지는 `long`을 제외한 정수와 `Enum`, 몇몇 참조 자료형에서만 사용 가능했으나, Java 7부터는 `String`도 사용할 수 있음
<br>

## 반복문
### while문
``` java
while (loop < 12) {
  loop++;
  if (loop == 12) break;
}
```
* while문 뒤의 소괄호에는 `boolean` 형태의 조건이 들어감
* `break`를 이용하여 실행 중인 while문에서 빠져나갈 수 있음
* `continue`를 이용하여 반복문 조건 검사로 바로 건너뛸 수 있음
* 반복문 사용 시에는 무한 루프를 주의해야 함

### do-while문
``` java
do {
  loop ++;
} while (loop < 12);
```
* do-while문은 한 번은 꼭 실행시키고자 하는 것이 있을 때 사용함
* `while`의 소괄호 뒤에 반드시 세미콜론을 입력해주어야 함
<br>

### for문
``` java
for (int i = 0; i < 12; i++) {
  System.out.println(i);
}
```
* 초기화, 종료조건, 조건값 변경의 세 부분을 세미콜론으로 구분하여 `for` 뒤의 소괄호에 적어주어야 함
* 종료조건 결과가 `true`면 for문 내부의 반복문장이 실행됨
* 종료조건 결과가 `false`면 for문이 종료됨
<br>

### label문
``` java
startLabel;
for (int i = 0; i < 12; i++) {
  for (int j = 0; j < 12; j++) {
      if (j == 4) continue startLabel;
      System.out.println(i + j);
  }
}
```
* 2중 이상으로 구성된 for문이나 while문 등에서 바깥쪽 루프의 시작점으로 이동하고자 할 때 사용함


