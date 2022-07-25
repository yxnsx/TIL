# 19장
## 자바에서 사용되는 용어들
* JDK - Java Development Kit
* J2SE - Java 2 Standard Edition
* Java SE - Java Standard Edition
* JRE - Java Runtime Environment (자바 실행을 위한 환경의 집합)
* JVM - Java Virtual Machine (자바 프로그램이 수행되는 프로세스)
* GC - Garbage Collector (JVM 내에서 메모리 관리 수행)
<br>

## 자바 언어의 특징
* 단순하고 객체지향적이며 친숙해야 함 - `It should be "simple, object-oriented and familiar"`
* 견고하고 보안상 안전함 - `It should be "robust and secure"`
* 아키텍처에 중립적이어야 하며 이식성이 높아야 함 - `It should be "architecture-neutral and portable"`
* 높은 성능을 제공해야 함 - `It should execute with "high performance"`
* 인터프리트 언어이며, 스레드를 제공하고, 동적인 언어임 - `It should be "interpreted, threaded, and dynamic"`
<br>

## JIT Compiler
* Just-In-Time
* 인터프리트 방식과 정적 컴파일 방식을 혼합한 방식
  * 인터프리트 방식 - 매번 프로그램을 실행할 때마다 기계어로 변환하는 과정을 수행
  * 정적 컴파일 방식 - 프로그램 실행 전 기계어로 변환하는 과정을 미리 수행
<br>

## HotSpot
* 자바가 시작할 때 알아서 클라이언트 장비인지 서버 장비인지를 확인함
* 확인 기준
  * 2개 이상의 물리적 프로세서 보유 여부
  * 2GB 이상의 물리적 메모리 보유 여부
<br>

### HotSpot client compiler
* CPU 코어가 하나뿐인 사용자를 위해 만들어진 클라이언트 컴파일러
* 애플리케이션 시작 시간을 빠르게 하고, 적은 메모리를 공유하도록 함
<br>

### HotSpot server compiler
* 코어가 많은 장비에서 애플리케이션을 돌리기 위해 만들어진 서버 컴파일러
<br>

## Garbage collector
* Heap 공간에서 객체 관리
* Young GC가 Full GC보다 빠름 - 더 작은 공간이 할당되고, 객체 처리 방식도 다르기 때문

### Minor garbage collection / Young garbage collection
* Eden 영역과 두 개의 Survivor 영역으로 구성
* Eden 영역에서 객체가 생성됨
* Eden 영역이 꽉 차면 살아있는 객체만 Survivor 영역으로 복사되고 다시 Eden 영역을 채우게 됨
* Survivor 영역이 꽉 차면 다른 Survivor 영역으로 객체가 복사됨
* 이와 동시에 Eden 영역의 객체들 중 살아있는 객체만 다시 Survivor 영역으로 복사됨
* Survivor 영역의 둘 중 하나는 반드시 비어 있어야만 함
* 위의 객체들 중 오래 살아있는 객체들은 Old 영역으로 이동함

### Major garbage collection / Full garbage collection
* 지속적으로 이동하다 Old 영역이 꽉 차면 발생하는 Garbage collection

### 오라클 JDK에서 제공하는 GC 방식
* Serial GC
* Parallel Young Generation Collector
* Parallel Old Generation Collector
* Concurrent Mark & Sweep Collector (CMS)
* G1 (Garbage First)
