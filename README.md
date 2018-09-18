# tech-interview

**기술 면접 대비를 위한 기본 개념을 정리하는 Repository 입니다.**
> :star: 내용에 오류가 있거나 추가할 내용이 있다면 Pull Request를 통해서 알려주시면 감사하겠습니다.
> <br> :star: Star나 Watching를 통한 많은 관심 부탁드립니다. :)

**:book: Contents**
1. Data Structure
2. Network
3. Operating System
4. Database
5. Design Pattern
6. Algorithm
7. Java
8. Spring
9. ETC

---

## 1. Data Structure
:arrow_forward: [답변 내용](/contents/datastructure.md)
* Array
* LinkedList
* Stack
* Queue
* Tree
* Binary Heap
* Red-Black Tree
* B+ Tree
* HashTable
* Graph

## 2. Network
:arrow_forward: [답변 내용](/contents/network.md)
* OSI 7계층
* TCP/IP의 개념
* TCP와 UDP
* TCP와 UDP의 헤더 분석
* TCP의 3-way-handshake, 4-way-handshake
  * Q. TCP의 연결 설정 과정(3단계)과 연결 종료 과정(4단계)이 단계가 차이나는 이유?
  * Q. 만약 Server에서 FIN 플래그를 전송하기 전에 전송한 패킷이 Routing 지연이나 패킷 유실로 인한 재전송 등으로 인해 FIN 패킷보다 늦게 도착하는 상황이 발생하면 어떻게 될까?
  * Q. 초기 Sequence Number인 ISN을 0부터 시작하지 않고 난수를 생성해서 설정하는 이유?
* HTTP, HTTPS
* GET, POST
* 쿠키, 세션
* DNS
* REST와 RESTful의 개념
* 소켓(Socket)이란
* Socket.io와 WebSocket의 차이

## 3. Operating System
:arrow_forward: [답변 내용](/contents/os.md)
* 프로세스와 스레드의 차이(Process vs Thread)
* 멀티 프로세스 대신 멀티 스레드를 사용하는 이유?
* Thread-safe
* 동기화 객체의 종류
* 뮤텍스와 세마포어의 차이
* 스케줄러
* 동기, 비동기
* 프로세스 동기화
* 메모리 관리 전략
* 가상 메모리
* 캐시의 지역성
* 교착상태(데드락)의 개념과 조건
* 사용자 수준 스레드, 커널 수준 스레드
* 외부 단편화와 내부 단편화
* Context Switching
* Swapping

## 4. Database
:arrow_forward: [답변 내용](/contents/db.md)
* 데이터베이스 풀
* 정규화(1~3차, BCNF)
* 트랜잭션(Transaction) 이란
* 트랜잭션 격리 수준(Transaction Isolation Level)
* Join
* SQL injection
* Index
* Statement, PrepareStatement
* RDBMS, NoSQL
* 효과적인 쿼리 저장
* Replication
* 파티셔닝(Partitioning)
* 샤딩(Sharding)

## 5. Design Pattern
:arrow_forward: [답변 내용](/contents/designpattern.md)
* 디자인 패턴의 개념과 종류
* Singleton 패턴
* Strategy 패턴
* Template Method 패턴
* Factory Method 패턴
* MVC1, MVC2 패턴

## 6. Algorithm :pushpin: [관련 링크](https://github.com/Do-Hee/algorithm-study)
:arrow_forward: [답변 내용](/contents/algorithm.md)
* BigO
* DFS와 BFS의 차이
* Fibonacci에서의 세 가지(Recursion, Dynamic Programming, 반복) 방식에 대한 시간, 공간복잡도 차이
* Quick Sort


## 7. Java
:arrow_forward: [답변 내용](/contents/java.md)
* java 프로그래밍이란
* java와 c/c++의 차이점
* java 언어의 장단점
* java의 접근 제어자의 종류와 특징
* OOP의 4가지 특징
* OOP의 5대 원칙 (SOLID)
* 객체지향 프로그래밍과 절차지향 프로그래밍의 차이
* 객체지향(Object-Oriented)이란
* java의 non-static 멤버와 static 멤버의 차이
* java의 final 키워드 (final/finally/finalize)
* java의 제네릭(Generic)과 c++의 템플릿(Template)의 차이
* java의 가비지 컬렉션(Garbage Collection) 처리 방법
* 객체 직렬화(Serialization)와 역직렬화(Deserialization)란 무엇인가
* 클래스, 객체, 인스턴스의 차이
* 객체(Object)란 무엇인가
* 오버로딩과 오버라이딩의 차이(Overloading vs Overriding)
* Call by Reference와 Call by Value의 차이
* 인터페이스와 추상 클래스의 차이(Interface vs Abstract Class)
* JVM 구조
* Java Collections Framework
* java Map 인터페이스 구현체의 종류
* java Set 인터페이스 구현체의 종류
* java List 인터페이스 구현체의 종류
* Wrapper class
* Annotation
* String, StringBuilder, StringBuffer
* 동기화와 비동기화의 차이(Syncronous vs Asyncronous)
* java에서 '=='와 'Equals()'의 차이
* java의 리플렉션(Reflection) 이란


## 8. Spring
:arrow_forward: [답변 내용](/contents/spring.md)
* IOC
* DI
* AOP
* POJO
* DAO, DTO
* MVC

## 9. ETC
:arrow_forward: [답변 내용](/contents/etc.md)
* TDD란
* 웹 브라우저에서 서버로 어떤 페이지를 요청하면 일어나는 일련의 과정을 설명
  * Ex. url에 'www.naver.com' 을 입력했다. 일어나는 현상에 대해 아는대로 설명하라.
* 대칭키, 비대칭키
* 컴파일러, 인터프리터
* 분산락
* 프레임워크와 라이브러리의 차이
* 64bit, 32bit 차이

---

# Reference
* https://github.com/jojoldu/junior-recruit-scheduler/blob/master/README.md
* https://github.com/JaeYeopHan/Interview_Question_for_Beginner
* https://github.com/KimHunJin/Study-Book/tree/master/interview
* https://trello.com/b/BWtpfywH/%EC%8B%A0%EC%9E%85-%EA%B0%9C%EB%B0%9C%EC%9E%90-%EA%B8%B0%EC%88%A0%EB%A9%B4%EC%A0%91
* https://github.com/NESOY/Back-end-Developer-Interview-Questions
