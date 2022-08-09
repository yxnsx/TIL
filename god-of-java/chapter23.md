# 23장 (Collection - Set/Queue)
## Set
* 순서가 없음
* 값의 중복 방지 및 값 포함 여부를 확인하는 것이 주 용도
* Set을 구현한 주요 클래스로는 `HashSet`, `TreeSet`, `LinkedHashSet`이 있음

### HashSet
* 순서가 필요하지 않은 데이터를 해시 테이블에 저장함
* Set 중 가장 성능이 좋음
* 저장된 순서대로 출력되지 않음
* HashSet이 구현한 인터페이스
  * `Serializable` - 원격 객체 전송 및 파일 저장이 가능함을 지정
  * `Clonable` - 객체 복제가 가능함을 지정
  * `Iterable` - 객체의 foreach 문장 사용이 가능함을 지정
  * `Collection` - 여러 개의 객체를 하나의 객체에 담아 처리할 때의 메소드 지정
  * `Set` - 셋 데이터를 처리하는 것과 관련된 메소드 지정
* 생성자
  * `HashSet()` - 데이터를 저장할 수 있는 16개의 공간과 0.75의 로드 팩터를 갖는 객체 생성
  * `HashSet(Collection<? extends E> c)` - `c`의 데이터를 HashSet에 담음
  * `HashSet(int initialCapacity)` - `initialCapacity`만큼의 데이터 저장 공간과 0.75의 로드 팩터를 갖는 객체 생성
  * `HashSet(int initialCapacity, float loadFactor)` - `initialCapacity`만큼의 데이터 저장 공간과 `loadFactor` 만큼의 로드 팩터를 갖는 객체 생성
* 로드 팩터: 데이터의 개수 / 저장공간
  * `데이터의 개수 > 로드 팩터`
    * 저장 공간의 크기가 증가되어 해시 재정리 작업(refresh)를 해야만 함
    * 성능에 영향
  * 로드 팩터 값이 커질수록 저장 공간은 넉넉해지지만, 데이터를 찾는 시간은 증가함

#### TreeSet
* 저장된 데이터의 값에 따라 정렬되는 Set
* red-black이라는 트리 타입으로 값이 저장됨
* HashSet보단 성능이 약간 느림

#### LinkedHashSet
* 저장된 순서에 따라 값이 정렬되는 Set
* 연결된 목록 타입으로 구현된 해시 테이블에 데이터가 저장됨
* 성능이 가장 나쁨

### LinkedList
* 배열의 중간 데이터가 지속적으로 추가 및 삭제될 경우, 메모리 공간 측면에서 배열보다 유리
* `List`도 되고 `Queue`도 되는 클래스
* `Deque` 인터페이스도 구현하므로 맨 앞과 끝의 데이터를 쉽게 처리 가능

## Queue
* FIFO
* 사용자의 요청을 들어온 순서대로 처리할 때 사용
