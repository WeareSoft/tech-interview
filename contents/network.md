# 2. Network

#### :small_orange_diamond:OSI 7계층

> - []()

#### :small_orange_diamond:TCP와 UDP
* 네트워크 계층 중 전송 계층에서 사용하는 프로토콜
* TCP(Transmission Control Protocol)
    <img src="./images/tcp-virtual-circuit.png" width="70%" height="70%">
    * 인터넷 상에서 데이터를 메세지의 형태로 보내기 위해 IP와 함께 사용하는 프로토콜이다.
    * TCP와 IP를 함께 사용하는데, IP가 데이터의 배달을 처리한다면 TCP는 패킷을 추적 및 관리한다.
    * 연결형 서비스로 가상 회선 방식을 제공한다.
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
    <img src="./images/udp-datagram.png" width="70%" height="70%">
    * 데이터를 데이터그램 단위로 처리하는 프로토콜이다.
    * 비연결형 서비스로 데이터그램 방식을 제공한다.
        * 연결을 위해 할당되는 논리적인 경로가 없다.
        * 그렇기 때문에 각각의 패킷은 다른 경로로 전송되고, 각각의 패킷은 독립적인 관계를 지니게 된다.
        * 이렇게 데이터를 서로 다른 경로로 독립적으로 처리한다.
    * 정보를 주고 받을 때 정보를 보내거나 받는다는 신호절차를 거치지 않는다.
    * UDP헤더의 CheckSum 필드를 통해 최소한의 오류만 검출한다.
    * 신뢰성이 낮다.
    * TCP보다 속도가 빠르다.
    * 신뢰성보다는 연속성이 중요한 서비스, 예를 들면 실시간 서비스(streaming)에 사용된다.

> - [http://mangkyu.tistory.com/15](http://mangkyu.tistory.com/15)

#### :small_orange_diamond:TCP 3-way-handshake, 4-way-handshake

#### :small_orange_diamond:HTTP

#### :small_orange_diamond:GET, POST

#### :small_orange_diamond:쿠키, 세션

#### :small_orange_diamond:HTTPS

#### :small_orange_diamond:DNS

#### :small_orange_diamond:REST


---
## Reference
> - []()


## :house: [Home](https://github.com/Do-Hee/tech-interview)
