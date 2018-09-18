# 2. Network

#### :small_orange_diamond:OSI 7계층
<img src="./images/osi-7-layer.png" width="60%" height="60%">

> - []()

#### :small_orange_diamond:TCP/IP의 개념
<!-- * 네트워크를 상호 연결시켜 정보를 전송할 수 있도록 하는 기능을 가진 다수의 프로토콜이 모여있는 프로토콜 집합
* 인터넷: 데이터 링크 계층을 지원하는 네트워크는 TCP/IP 프로토콜을 이용하여 상호 연결하는 네트워크 -->

#### :small_orange_diamond:TCP와 UDP
* 네트워크 계층 중 **전송 계층에서 사용하는 프로토콜**
* TCP(Transmission Control Protocol)  
    <img src="./images/tcp-virtual-circuit.png" width="60%" height="60%">
    * 인터넷 상에서 데이터를 메세지의 형태(**세그먼트** 라는 블록 단위)로 보내기 위해 IP와 함께 사용하는 프로토콜이다.
    * TCP와 IP를 함께 사용하는데, IP가 데이터의 배달을 처리한다면 TCP는 패킷을 추적 및 관리한다.
    * **연결형 서비스로** 가상 회선 방식을 제공한다.
        * 3-way handshaking과정을 통해 연결을 설정하고, 4-way handshaking을 통해 연결을 해제한다.
    * 흐름제어 및 혼잡제어를 제공한다.
        * 흐름제어
            * 데이터를 송신하는 곳과 수신하는 곳의 데이터 처리 속도를 조절하여 수신자의 버퍼 오버플로우를 방지하는 것
            * 송신하는 곳에서 감당이 안되게 많은 데이터를 빠르게 보내 수신하는 곳에서 문제가 일어나는 것을 막는다.
        * 혼잡제어
            * 네트워크 내의 패킷 수가 넘치게 증가하지 않도록 방지하는 것
            * 정보의 소통량이 과다하면 패킷을 조금만 전송하여 혼잡 붕괴 현상이 일어나는 것을 막는다.
    * 높은 신뢰성을 보장한다.
    * UDP보다 속도가 느리다.
    * 전이중(Full-Duplex), 점대점(Point to Point) 방식이다.
        * 전이중
            * 전송이 양방향으로 동시에 일어날 수 있다.
        * 점대점
            * 각 연결이 정확히 2개의 종단점을 가지고 있다.
        * 멀티캐스팅이나 브로드캐스팅을 지원하지 않는다.
    * 연속성보다 신뢰성있는 전송이 중요할 때에 사용된다.
* UDP(User Datagram Protocol)  
    <img src="./images/udp-datagram.png" width="60%" height="60%">
    * 데이터를 **데이터그램** 단위로 처리하는 프로토콜이다.
    * **비연결형 서비스로** 데이터그램 방식을 제공한다.
        * 연결을 위해 할당되는 논리적인 경로가 없다.
        * 그렇기 때문에 각각의 패킷은 다른 경로로 전송되고, 각각의 패킷은 독립적인 관계를 지니게 된다.
        * 이렇게 데이터를 서로 다른 경로로 독립적으로 처리한다.
    * 정보를 주고 받을 때 정보를 보내거나 받는다는 신호절차를 거치지 않는다.
    * UDP헤더의 CheckSum 필드를 통해 최소한의 오류만 검출한다.
    * 신뢰성이 낮다.
    * TCP보다 속도가 빠르다.
    * 신뢰성보다는 연속성이 중요한 서비스, 예를 들면 실시간 서비스(streaming)에 사용된다.
* 참고
  * UDP와 TCP는 각각 별도의 포트 주소 공간을 관리하므로 같은 포트 번호를 사용해도 무방하다. 즉, 두 프로토콜에서 동일한 포트 번호를 할당해도 서로 다른 포트로 간주한다.
  * 또한 같은 모듈(UDP or TCP) 내에서도 클라이언트 프로그램에서 동시에 여러 커넥션을 확립한 경우에는 서로 다른 포트 번호를 동적으로 할당한다. (동적할당에 사용되는 포트번호는 49,152~65,535이다.)

> - [http://mangkyu.tistory.com/15](http://mangkyu.tistory.com/15)
> - [http://ddooooki.tistory.com/21](http://ddooooki.tistory.com/21)

#### :small_orange_diamond:TCP와 UDP의 헤더 분석

> - [https://idchowto.com/?p=18352](https://idchowto.com/?p=18352)
> - [https://m.blog.naver.com/PostView.nhn?blogId=koromoon&logNo=120162515270&proxyReferer=https%3A%2F%2Fwww.google.co.kr%2F](https://m.blog.naver.com/PostView.nhn?blogId=koromoon&logNo=120162515270&proxyReferer=https%3A%2F%2Fwww.google.co.kr%2F)

#### :small_orange_diamond:TCP의 3-way-handshake, 4-way-handshake
* TCP는 장치들 사이에 논리적인 접속을 성립(establish)하기 위하여 연결을 설정하여 **신뢰성을 보장하는 연결형 서비스** 이다.
* 3-way handshake 란
  * TCP 통신을 이용하여 데이터를 전송하기 위해 네트워크 **연결을 설정(Connection Establish)** 하는 과정
  * 즉, TCP/IP 프로토콜을 이용해서 통신을 하는 응용 프로그램이 데이터를 전송하기 전에 먼저 정확한 전송을 보장하기 위해 상대방 컴퓨터와 사전에 세션을 수립하는 과정을 의미한다.
  * <img src="./images/3-way-handshaking.png" width="60%" height="60%">
    * 양쪽 모두 데이터를 전송할 준비가 되었다는 것을 보장하고, 실제로 데이터 전달이 시작하기 전에 한 쪽이 다른 쪽이 준비되었다는 것을 알 수 있도록 한다.
    * A 프로세스(Client)가 B 프로세스(Server)에 연결을 요청
    1. A -> B: SYN
      * 접속 요청 프로세스 A가 연결 요청 메시지 전송 (SYN)
      * 송신자가 최초로 데이터를 전송할 때 Sequence Number를 임의의 랜덤 숫자로 지정하고, SYN 플래그 비트를 1로 설정한 세그먼트를 전송한다.
      * PORT 상태 - B: LISTEN, A: CLOSED
    2. B -> A: SYN + ACK
      * 접속 요청을 받은 프로세스 B가 요청을 수락했으며, 접속 요청 프로세스인 A도 포트를 열어 달라는 메시지 전송 (SYN + ACK)
      * 수신자는 Acknowledgement Number 필드를 (Sequence Number + 1)로 지정하고, SYN과 ACK 플래그 비트를 1로 설정한 세그먼트를 전송한다.
      * PORT 상태 - B: SYN_RCV, A: CLOSED
    3. A -> B: ACK
      * PORT 상태 - B: SYN_RCV, A: ESTABLISHED
      * 마지막으로 접속 요청 프로세스 A가 수락 확인을 보내 연결을 맺음 (ACK)
      * 이때, 전송할 데이터가 있으면 이 단계에서 데이터를 전송할 수 있다.
      * PORT 상태 - B: ESTABLISHED, A: ESTABLISHED
* 4-way handshake 란
  * TCP의 **연결을 해제(Connection Termination)** 하는 과정
  * <img src="./images/4-way-handshaking.png" width="60%" height="60%">
    * A 프로세스(Client)가 B 프로세스(Server)에 연결 해제를 요청
    1. A -> B: FIN
      * 프로세스 A가 연결을 종료하겠다는 FIN 플래그를 전송
      * 프로세스 B가 FIN 플래그로 응답하기 전까지 연결을 계속 유지
    2. B -> A: ACK
      * 프로세스 B는 일단 확인 메시지를 보내고 자신의 통신이 끝날 때까지 기다린다. (이 상태가 TIME_WAIT 상태)
      * 수신자는 Acknowledgement Number 필드를 (Sequence Number + 1)로 지정하고, ACK 플래그 비트를 1로 설정한 세그먼트를 전송한다.
      * 그리고 자신이 전송할 데이터가 남아있다면 이어서 계속 전송한다.
    3. B -> A: FIN
      * 프로세스 B가 통신이 끝났으면 연결 종료 요청에 합의한다는 의미로 프로세스 A에게 FIN 플래그를 전송
    4. A -> B: ACK
      * 프로세스 A는 확인했다는 메시지를 전송
* 참고 - ***포트(PORT) 상태 정보***
  * CLOSED: 포트가 닫힌 상태
  * LISTEN: 포트가 열린 상태로 연결 요청 대기 중
  * SYN_RCV: SYNC 요청을 받고 상대방의 응답을 기다리는 중
  * ESTABLISHED: 포트 연결 상태
* 참고 - ***플래그 정보***
  * TCP Header에는 CONTROL BIT(플래그 비트, 6bit)가 존재하며, 각각의 bit는 "URG-ACK-PSH-RST-SYN-FIN"의 의미를 가진다.
  * 즉, 해당 위치의 bit가 1이면 해당 패킷이 어떠한 내용을 담고 있는 패킷인지를 나타낸다.
  * SYN(Synchronize Sequence Number)
    * 연결 설정. Sequence Number를 랜덤으로 설정하여 세션을 연결하는 데 사용하며, 초기에 Sequence Number를 전송한다.
    * 000010
  * ACK(Acknowledgement)
    * 응답 확인. 패킷을 받았다는 것을 의미한다.
    * Acknowledgement Number 필드가 유효한지를 나타낸다.
    * 양단 프로세스가 쉬지 않고 데이터를 전송한다고 가정하면 최초 연결 설정 과정에서 전송되는 첫 번째 세그먼트를 제외한 모든 세그먼트의 ACK 비트는 1로 지정된다고 생각할 수 있다.
    * 010000
  * FIN(Finish)
    * 연결 해제. 세션 연결을 종료시킬 때 사용되며, 더 이상 전송할 데이터가 없음을 의미한다.
    * 000001

> - [http://needjarvis.tistory.com/157](http://needjarvis.tistory.com/157)
> - [http://hyeonstorage.tistory.com/286](http://hyeonstorage.tistory.com/286)

#### :question:TCP 관련 질문 1
* Q. TCP의 연결 설정 과정(3단계)과 연결 종료 과정(4단계)이 단계가 차이나는 이유?
  * A. Client가 데이터 전송을 마쳤다고 하더라도 Server는 아직 보낼 데이터가 남아있을 수 있기 때문에 일단 FIN에 대한 ACK만 보내고, 데이터를 모두 전송한 후에 자신도 FIN 메시지를 보내기 때문이다.
  * [관련 Reference](http://ddooooki.tistory.com/21)

#### :question:TCP 관련 질문 2
* Q. 만약 Server에서 FIN 플래그를 전송하기 전에 전송한 패킷이 Routing 지연이나 패킷 유실로 인한 재전송 등으로 인해 FIN 패킷보다 늦게 도착하는 상황이 발생하면 어떻게 될까?
  * A. 이러한 현상에 대비하여 Client는 Server로부터 FIN 플래그를 수신하더라도 일정시간(Default: 240sec)동안 세션을 남겨 놓고 잉여 패킷을 기다리는 과정을 거친다. (TIME_WAIT 과정)
  * [관련 Reference]((http://mindnet.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-22%ED%8E%B8-TCP-3-WayHandshake-4-WayHandshake)

#### :question:TCP 관련 질문 3
* Q. 초기 Sequence Number인 ISN을 0부터 시작하지 않고 난수를 생성해서 설정하는 이유?
  * A. Connection을 맺을 때 사용하는 포트(Port)는 유한 범위 내에서 사용하고 시간이 지남에 따라 재사용된다. 따라서 두 통신 호스트가 과거에 사용된 포트 번호 쌍을 사용하는 가능성이 존재한다. 서버 측에서는 패킷의 SYN을 보고 패킷을 구분하게 되는데 난수가 아닌 순처적인 Number가 전송된다면 이전의 Connection으로부터 오는 패킷으로 인식할 수 있다. 이런 문제가 발생할 가능성을 줄이기 위해서 난수로 ISN을 설정한다.
  * [관련 Reference](http://asfirstalways.tistory.com/356)

#### :small_orange_diamond:HTTP, HTTPS

#### :small_orange_diamond:GET, POST

#### :small_orange_diamond:쿠키, 세션

#### :small_orange_diamond:DNS

#### :small_orange_diamond:REST와 RESTful의 개념

#### :small_orange_diamond:소켓(Socket)이란
<!-- * 소켓(Socket)은 TCP/IP를 이용하는 API로 소프트웨어로 작성된 통신의 접속점이다. -->


#### :small_orange_diamond:Socket.io와 WebSocket의 차이

> - [https://d2.naver.com/helloworld/1336](https://d2.naver.com/helloworld/1336)


---
## Reference
> - []()


## :house: [Home](https://github.com/Do-Hee/tech-interview)
