# 28장
## 네트워크 프로그래밍
* OSI 7 layer 중 자바에서 활용하는 대표적인 레이어
  * 애플리케이션 레이어 - HTTP, FTP, Telnet, ...
  * 트랜스포트 레이어 - TCP, UDP, ...
  * 네트워크 레이어 - IP, ...
  * 링크 레이어 - Device driver, ...

### TCP/UDP
* TCP - Transmission Control Protocol
  * 연결 기반 프로토콜
  * 상대방이 데이터를 받았는지를 확실히 보장함
  * UDP에 비해 고비용이며 느리고 무거움
* UDP - User Datagram Protocol
  * 상대방이 데이터를 받았는지를 보장하지 못함
  * TCP에 비해 저비용이며 빠르고 가벼움

### Port
* 일반적인 웹 애플리케이션의 포트 번호 - :80
* SSL을 이용한 안전한 통신을 위한 포트 번호 - :443
* 위와 같이 정해져있는 포트 값(0~1023)은 다른 용도로 사용하지 않는 것이 좋음
* 포트는 16비트로 구성되어 있으며, 1024~65,535의 범위 내 다른 값들은 임의로 사용할 수 있음

## TCP 통신 - Socket
* 자바에서의 TCP 통신을 수행하기 위해 사용하는 클래스
* 데이터를 보내는 쪽(보통 클라이언트)에서 Socket 객체를 생성하여 사용함
* 데이터를 받는 쪽(보통 서버)에서는 요청에 대해 ServerSocket 클래스에서 생성하여 전달한 Socket 객체를 이용하여 데이터를 처리함
* 원격에 있는 장비와의 연결 상태를 보관하고 있음

### Socket의 생성자
| 생성자 | 설명 |
| ---- | --- |
| ServerSocket() | 서버 소켓 객체만 생성 |
| ServerSocket(int port) | 지정된 포트를 사용하는 서버 소켓을 생성 |
| ServerSocket(int port, int backlog) | 지정된 포트와 backlog 개수를 가지는 소켓을 생성 |
| ServerSocket(int port, int backlog, InetAddress bindAddr) | 지정된 포트와 backlog 개수를 가지는 소켓을 생성하며, bindAddr에 있는 주소에서의 접근만을 허용 |

* backlog는 큐의 개수를 의미 (= 최대 연결 대기 개수)
* backlog의 값을 지정하지 않을 경우 기본값은 50임
* bindAddr은 특정 주소에서만 접근 가능하도록 지정할 때 사용
* ServerSocket 생성자는 `accept()` 메소드를 이용해 연결 작업을 해주어야 함
* `close()`를 해주지 않는다면 계속 대기 상태로 유지됨
* 데이터가 EXIT이라면 더 이상 대기하지 않고 프로그램을 종료함

### Socket의 메소드
| 리턴타입 | 메소드 | 설명 |
| ------ | ---- | --- |
| void | close() | 소켓 연결을 종료 |
| int | getSoTimeout() | 타임아웃 시간 리턴 |
| void | setSoTimeout(int timeout) | 타임아웃 설정 |

### Socket의 예외
* `java.net.BindException` - `Address already in use`
  * 서버를 띄워 놓고 또 띄웠을 떄 발생
  * 이미 지정된 port 번호를 사용하고 있기 떄문에 동일한 port 번호를 사용할 수 없음
* `java.net.ConnectException` - `Connection refused`
  * 서버를 띄워 놓지 않고 클라이언트 프로그램만 수행했을 때 발생

## UDP 통신 - Datagram
* DatagramSocket 객체를 통해 보내는 역할과 받는 역할 모두를 수행할 수 있음
* TCP 통신에서처럼 스트림 객체를 사용하는 대신, DatagramPacket이라는 클래스를 사용함

### Datagram의 생성자
| 생성자 | 설명 |
| ---- | --- |
| DatagramSocket() | 소켓 객체 생성 후 사용 가능한 포트로 대기 |
| DatagramSocket(DatagramSocketImpl impl) | 사용자가 지정한 SocketImpl 객체를 사용하여 소켓 객체만 생성 |
| DatagramSocket(int port) | 소켓 객체 생성 후 지정된 port로 대기 |
| DatagramSocket(int port, InetAddress address) | 소켓 객체 생성 후 address와 port를 사용하는 서버에 연결 |
| DatagramSocket(SocketAddress address) | 소켓 객체 생성 후 address에 지정된 서버로 연결 |

### Datagram의 메소드
| 리턴타입 | 메소드 | 설명 |
| ------ | ---- | --- |
| void | close() | 데이터그램 연결을 종료 |
| void | receive(DatagramPacket packet) | 메소드 호출시 요청을 대기하고, 데이터를 받았을 경우 packet 객체에 데이터 저장 |
| void | send(DatagramPacket packet) | packet 데이터 전송 |

### DatagramPacket의 생성자
* `DatagramPacket(byte[] buf, int length)` - 유일하게 데이터를 받기 위한 객체를 생성하는 생성자
* `byte[] buf` - 전송되는 데이터
* `offset` - 전송되는 byte[]의 첫 위치
* `length` -  데이터의 크기

### DatagramPacket의 메소드
* `getData()` - 전송받은 데이터를 byte[]로 리턴
* `getLength()` - 전송받은 데이터의 크기를 int 타입으로 리턴
