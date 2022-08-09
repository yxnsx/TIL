# 22장
## Collection
* java.util 패키지에 선언되어있는 인터페이스

| 자료구조 | Collection 구현 여부 |
| ------ | ----------------- |
| Set | O |
| List | O |
| Queue | O |
| Map | X 

### Java의 자료구조
* Set
  * HashSet
    * LinkedHashSet
  * TreeSet
* List
  * ArrayList
  * LinkedList
* Queue
  * LinkedList
  * PriorityQueue
* Map
  * HashMap
    * LinkedHashMap
  * TreeMap

### List
* 순서가 있는 목록
* `ArrayList`, `Vector`, `Stack`, `LinkedList`
* `ArrayList` - Non thread safe
* `Vector` - Thread safe
* `Stack` - `Vector`를 확장하여 구현함

#### ArrayList
* 생성자
  * `ArrayList()` - 10개의 저장 공간을 지닌 ArrayList 생성
  * `ArrayList(Collection<? extends E> c)` - `c`가 저장된 ArrayList 생성
  * `ArrayList(int initialCapacity)` - `initialCapacity`개의 저장공간을 지닌 ArrayList 생성
* Shallow copy: 다른 객체에 원본 객체의 주소 값 할당
* Deep copy: 객체의 값 자체를 다른 객체에 할당하여 복제된 객체 값의 변경이 원본 객체에 영향을 미치지 못함
