# 4. Database
**:book: Contents**
* [데이터베이스 풀](#데이터베이스-풀)
* [정규화(1차 2차 3차 BCNF)](#정규화-1차-2차-3차-BCNF)
* [트랜잭션(Transaction) 이란](#트랜잭션이란)
* [트랜잭션 격리 수준(Transaction Isolation Level)](#트랜잭션-격리-수준)
* [Join](#join)
* [SQL injection](#sql-injection)
* [Index란](#index란)
* [Statement와 PrepareStatement](#statement와-preparestatement)
* [RDBMS와 NoSQL](#rdbms와-noSQL)
* [효과적인 쿼리 저장](#효과적인-쿼리-저장)
* [옵티마이저(Optimizer)란](#옵티마이저란)
* [Replication](#replication)
* [파티셔닝(Partitioning)](#파티셔닝)
* [샤딩(Sharding)](#샤딩)
* [객체 관계 매핑(Object-relational mapping, ORM)이란](#ORM이란)
* [java JDBC](#java-jdbc)

---

### 데이터베이스 풀
> :arrow_double_up:[Top](#4-database)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#4-database)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### 정규화 1차 2차 3차 BCNF
> :arrow_double_up:[Top](#4-database)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#4-database)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### 트랜잭션이란
* 트랜잭션(Transaction) 이란
    * 데이터베이스의 상태를 변환시키는 하나의 논리적인 작업 단위를 구성하는 연산들의 집합이다.
        * 예를들어, A계좌에서 B계좌로 일정 금액을 이체한다고 가정하자.
          1. A계좌의 잔액을 확인한다.
          2. A계좌의 금액에서 이체할 금액을 빼고 다시 저장한다.
          3. B계좌의 잔액을 확인한다.
          4. B계좌의 금액에서 이체할 금액을 더하고 다시 저장한다.
        * 이러한 과정들이 모두 합쳐져 계좌이체라는 하나의 작업단위를 구성한다.
    * 하나의 트랜잭션은 Commit 되거나 Rollback 된다.
        * Commit 연산
            * 한개의 논리적 단위(트랜잭션)에 대한 작업이 성공적으로 끝나 데이터베이스가 다시 일관된 상태에 있을 때, 이 트랜잭션이 행한 갱신 연산이 완료된 것을 트랜잭션 관리자에게 알려주는 연산이다.
        * Rollback 연산
            * 하나의 트랜잭션 처리가 비정상적으로 종료되어 데이터베이스의 일관성을 깨뜨렸을 때, 이 트랜잭션의 일부가 정상적으로 처리되었더라도 트랜잭션의 원자성을 구현하기 위해 이 트랜잭션이 행한 모든 연산을 취소(Undo)하는 연산이다.
            * Rollback 시에는 해당 트랜잭션을 재시작하거나 폐기한다.
    * 데이터베이스 응용 프로그램은 트랜잭션들의 집합으로 정의 할 수 있다.
* 트랜잭션의 성질(ACID)
    * 원자성(Atomicity), All or nothing
        * 트랜잭션의 모든 연산들은 정상적으로 수행 완료되거나 아니면 전혀 어떠한 연산도 수행되지 않은 상태를 보장해야 한다.
    * 일관성(Consistency)
        * 트랜잭션 완료 후에도 데이터베이스가 일관된 상태로 유지되어야 한다.
    * 독립성(Isolation)
        * 하나의 트랜잭션이 실행하는 도중에 변경한 데이터는 이 트랜잭션이 완료될 때까지 다른 트랜잭션이 참조하지 못한다.
    * 지속성(Durability)
        * 성공적으로 수행된 트랜잭션은 영원히 반영되어야 한다.
* 트랜잭션의 필요성
    * 현금 인출기를 작동하는 도중에 기계오류나 정전 등과 같은 예기치 않은 상황이 발생하여 카드가 나오지 않거나 기계가 멈추는 경우
    * 각각 다른 지점의 은행에서 동시에 인출할 때, 하나의 지점이 다른 지점에서 저장한 잔액을 덮어 쓰는 경우
    * 위와 같은 상황이 발생되지 않도록 방지하기 위해, 즉, 트랜잭션의 성질인 ACID를 제공받기위해 트랜잭션을 사용한다.
* 트랜잭션의 상태  
    <img src="./images/transaction-status.png" width="70%" height="70%">
    * 활동(Active)
        * 트랜잭션이 실행 중에 있는 상태, 연산들이 정상적으로 실행 중인 상태
    * 장애(Failed)
        * 트랜잭션이 실행에 오류가 발생하여 중단된 상태
    * 철회(Aborted)
        * 트랜잭션이 비정상적으로 종료되어 Rollback 연산을 수행한 상태
    * 부분 완료(Partially Committed)
        * 트랜잭션이 마지막 연산까지 실행했지만, Commit 연산이 실행되기 직전의 상태
    * 완료(Committed)
        * 트랜잭션이 성공적으로 종료되어 Commit 연산을 실행한 후의 상태

> :arrow_double_up:[Top](#4-database)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#4-database)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [http://limkydev.tistory.com/100](http://limkydev.tistory.com/100)
> - [http://coding-factory.tistory.com/226](http://coding-factory.tistory.com/226)
> - [http://yimoyimo.tk/transaction_DI/](http://yimoyimo.tk/transaction_DI/)
> - [https://d2.naver.com/helloworld/407507](https://d2.naver.com/helloworld/407507)

### 트랜잭션-격리-수준
* Isolation Level 이란?
    * 트랜잭션에서 일관성이 없는 데이터를 허용하도록 하는 수준
* Isolation Level 의 필요성
    * 데이터베이스는 ACID 같이 트랜잭션이 원자적이면서도 독립적인 수행을 하도록 한다.
    * 그래서 Locking 이라는 개념이 등장한다.
        * 트랜잭션이 DB를 다루는 동안 다른 트랜잭션이 관여하지 못하게 막는 것
    * 하지만 무조건적인 Locking으로 동시에 수행되는 많은 트랜잭션들을 순서대로 처리하는 방식으로 구현되면 DB의 성능은 떨어지게 된다.
    * 반대로 응답성을 높이기 위해 Locking 범위를 줄인다면 잘못된 값이 처리 될 여지가 있다.
    * 그래서 최대한 효율적인 Locking 방법이 필요하다.
* Isolation Level 의 종류
    1. Read Uncommitted (레벨 0)
        * SELECT 문장이 수행되는 동안 해당 데이터에 Shared Lock이 걸리지 않는 Level
        * 트랜잭션에 처리중인 혹은 아직 커밋되지 않은 데이터를 다른 트랜잭션이 읽는 것을 허용한다.
        * 따라서, 어떤 사용자가 A라는 데이터를 B라는 데이터로 변경하는 동안 다른 사용자는 아직 완료되지 않은(Uncommitted 혹은 Dirty) 트랜잭션이지만 변경된 데이터인 B를 읽을 수 있다.
        * 데이터베이스의 일관성을 유지할 수 없다.
    2. Read Committed (레벨 1)
        * SELECT 문장이 수행되는 동안 해당 데이터에 Shared Lock이 걸리는 Level
        * 트랜잭션이 수행되는 동안 다른 트랜잭션이 접근할 수 없어 대기하게 된다.
        * Commit이 이루어진 트랜잭션만 조회할 수 있다.
        * 따라서, 어떤 사용자가 A라는 데이터를 B라는 데이터로 변경하는 동안 다른 사용자는 해당 데이터에 접근할 수 없다.
        * SQL Server가 Default로 사용하는 Isolation Level
    3. Repeatable Read (레벨 2)
        * 트랜잭션이 완료될 때까지 SELECT 문장이 사용하는 모든 데이터에 Shared Lock이 걸리는 Level
        * 트랜잭션이 범위 내에서 조회한 데이터의 내용이 항상 동일함을 보장한다.
        * 따라서, 다른 사용자는 그 영역에 해당되는 데이터에 대한 수정이 불가능하다.
    4. Serializable (레벨 3)
        * 트랜잭션이 완료될 때까지 SELECT 문장이 사용하는 모든 데이터에 Shared Lock이 걸리는 Level
        * 완벽한 읽기 일관성 모드를 제공한다.
        * 따라서, 다른 사용자는 그 영역에 해당되는 데이터에 대한 수정 및 입력이 불가능하다.
    * Isolation level 조정은 동시성이 증가되는데 반해 데이터 무결성에 문제가 발생할 수 있고, 데이터의 무결성을 유지하는 데 반해 동시성이 떨어질 수 있다.
    * 레벨이 높아질수록 비용이 높아진다.
* 낮은 단계의 Isolation Level 이용시 발생하는 현상  
    <img src="./images/isolation-level.png" width="70%" height="70%">
    * Dirty Read
        * 커밋되지 않은 수정 중인 데이터를 다른 트랜잭션에서 읽을 수 있도록 허용할 때 발생하는 현상
        * 어떤 트랜잭션에서 아직 실행이 끝난지 않은 다른 트랜잭션에 의한 변경 사항을 보게 되는 되는 경우
    * Non-Repeatable Read
        * 한 트랜잭션에서 같은 쿼리를 두 번 수행할 때 그 사이에 다른 트랜잭션이 값을 수정 또는 삭제함으로써 두 쿼리의 결과가 상이하게 나타나는 비 일관성 현상
    * Phantom Read
        * 한 트랜잭션 안에서 일정 범위의 레코드를 두 번 이상 읽을 때, 첫 번째 쿼리에서 없던 레코드가 두 번째 쿼리에서 나타나는 현상
        * 이는 트랜잭션 도중 새로운 레코드가 삽입되는 것을 허용하기 때문에 나타난다.

> :arrow_double_up:[Top](#4-database)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#4-database)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [http://hundredin.net/2012/07/26/isolation-level/](http://hundredin.net/2012/07/26/isolation-level/)
> - [http://egloos.zum.com/ljlave/v/1530887](http://egloos.zum.com/ljlave/v/1530887)

### Join
> :arrow_double_up:[Top](#4-database)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#4-database)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### SQL Injection
> :arrow_double_up:[Top](#4-database)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#4-database)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### Index
> :arrow_double_up:[Top](#4-database)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#4-database)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### Statement와 PrepareStatement
> :arrow_double_up:[Top](#4-database)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#4-database)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### RDBMS와 NoSQL
> :arrow_double_up:[Top](#4-database)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#4-database)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### 효과적인 쿼리 저장
> :arrow_double_up:[Top](#4-database)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#4-database)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### 옵티마이저란
> :arrow_double_up:[Top](#4-database)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#4-database)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### Replication
> :arrow_double_up:[Top](#4-database)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#4-database)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### 파티셔닝
* 배경
  * 서비스의 크기가 점점 커지고 DB에 저장하는 데이터의 규모 또한 대용량화 되면서, 기존에 사용하는 DB 시스템의 **용량(storage)의 한계와 성능(performance)의 저하** 를 가져오게 되었다.
  * 즉, VLDB(Very Large DBMS)와 같이 하나의 DBMS에 너무 큰 table이 들어가면서 용량과 성능 측면에서 많은 이슈가 발생하게 되었고, 이런 이슈를 해결하기 위한 방법으로 table을 '파티션(partition)'이라는 작은 단위로 나누어 관리하는 **'파티셔닝(Partitioning)'기법** 이 나타나게 되었다.
* 파티셔닝의 개념
  * **큰 table이나 index를, 관리하기 쉬운 partition이라는 작은 단위로 물리적으로 분할하는 것을 의미한다.**
    * 물리적인 데이터 분할이 있더라도, DB에 접근하는 application의 입장에서는 이를 인식하지 못한다.
  * '파티셔닝(Partitioning)'기법을 통해 소프트웨어적으로 데이터베이스를 분산 처리하여 성능이 저하되는 것을 방지하고 관리를 보다 수월하게 할 수 있게 되었다.
* 파티셔닝의 목적
  1. 성능(Performance)
      * 특정 DML과 Query의 성능을 향상시킨다.
      * 주로 대용량 Data WRITE 환경에서 효율적이다.
      * 특히, Full Scan에서 데이터 Access의 범위를 줄여 성능 향상을 가져온다.
      * 많은 INSERT가 있는 OLTP 시스템에서 INSERT 작업을 작은 단위인 partition들로 분산시켜 경합을 줄인다.
  2. 가용성(Availability)
      * 물리적인 파티셔닝으로 인해 전체 데이터의 훼손 가능성이 줄어들고 데이터 가용성이 향상된다.
      * 각 분할 영역(partition별로)을 독립적으로 백업하고 복구할 수 있다.
      * table의 partition 단위로 Disk I/O을 분산하여 경합을 줄이기 때문에 UPDATE 성능을 향상시킨다.
  3. 관리용이성(Manageability)
      * 큰 table들을 제거하여 관리를 쉽게 해준다.
* 파티셔닝의 장점
  * 관리적 측면 : partition 단위 백업, 추가, 삭제, 변경
    * 전체 데이터를 손실할 가능성이 줄어들어 데이터 가용성이 향상된다.
    * partition별로 백업 및 복구가 가능하다.
    * partition 단위로 I/O 분산이 가능하여 UPDATE 성능을 향상시킨다.
  * 성능적 측면 : partition 단위 조회 및 DML수행
    * 데이터 전체 검색 시 필요한 부분만 탐색해 성능이 증가한다.
    * 즉, Full Scan에서 데이터 Access의 범위를 줄여 성능 향상을 가져온다.
    * 필요한 데이터만 빠르게 조회할 수 있기 때문에 쿼리 자체가 가볍다.
* 파티셔닝의 단점
  * table간 JOIN에 대한 비용이 증가한다.
  * table과 index를 별도로 파티셔닝할 수 없다.
    * table과 index를 같이 파티셔닝해야 한다.
* 파티셔닝의 종류
  1. 수평(horizontal) 파티셔닝
      * **샤딩(Sharding)** 과 동일한 개념
  2. 수직(vertical) 파티셔닝
  <img src="./images/types-of-partitioning.png">
* 파티셔닝의 분할 기준
  1. 범위 분할 (range partitioning)
  2. 목록 분할 (list partitioning)
  3. 해시 분할 (hash partitioning)
  4. 합성 분할 (composite partitioning)
  <img src="./images/partitioning.png" width="70%" height="70%">

> :arrow_double_up:[Top](#4-database)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#4-database)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [https://gmlwjd9405.github.io/2018/09/24/db-partitioning.html](https://gmlwjd9405.github.io/2018/09/24/db-partitioning.html)
> - [https://nesoy.github.io/articles/2018-02/Database-Partitioning](https://nesoy.github.io/articles/2018-02/Database-Partitioning)

### 샤딩
  <!-- * 샤딩은 물리적으로 다른 데이터베이스에 데이터를 수평 분할 방식으로 분산 저장하고 조회하는 방법을 말한다.
샤딩은 주로 키값(해쉬값 또는 특정 컬럼값)을 이용하여 테이블들의 데이터 자체를 나눠서 분산저장하거나, 특정 분류기준을 가지고(저장 데이터 종류-유저, 일반데이터 등) 테이블을 분류하여 저장하는 것
샤딩은 수평 파티션과 동일한 개념이다.
sharding == horizontal partitioning

'주민' 테이블이 여러 DB에 있을 때, 서현동 주민에 대한 정보는 A DB에, 정자동 주민에 대한 정보는 B DB에 저장되도록 하는 방식을 말한다. 여러 데이터베이스를 대상으로 작업해야 하기 때문에 경우에 따라서는 기능에 제약이 있을 수 있고(JOIN 연산 등) 일관성(consistency)과 복제(replication) 등에서 불리한 점이 많다. 예전의 샤딩은 애플리케이션 서버 레벨에서 구현하는 경우가 많았다. 최근에는 이를 플랫폼 차원에서 제공하려는 시도가 많다. 크게 분류하면 Hibernate Shards와 같이 애플리케이션 서버에서 동작하는 형태, CUBRID SHARD, Spock Proxy, Gizzard와 같이 미들티어(middle tier)로 동작하는 형태, nStore나 MongoDB와 같이 데이터베이스 자체에서 샤딩 기능을 제공하는 형태로 나누어볼 수 있다. -->

> :arrow_double_up:[Top](#4-database)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#4-database)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [http://mongodb.citsoft.net/?page_id=225#comment-91922](http://mongodb.citsoft.net/?page_id=225#comment-91922)
> - [https://d2.naver.com/helloworld/14822](https://d2.naver.com/helloworld/14822)

### ORM이란

> :arrow_double_up:[Top](#4-database)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#4-database)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### java JDBC

> :arrow_double_up:[Top](#4-database)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#4-database)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

---

## Reference
> - []()


## :house: [Home](https://github.com/Do-Hee/tech-interview)
