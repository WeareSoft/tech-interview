# 4. Database

#### :small_orange_diamond:데이터베이스 풀

> - []()

#### :small_orange_diamond:정규화(1~3차, BCNF)

#### :small_orange_diamond:트랜잭션(Transaction) 이란
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

> - [http://limkydev.tistory.com/100](http://limkydev.tistory.com/100)
> - [http://coding-factory.tistory.com/226](http://coding-factory.tistory.com/226)
> - [http://yimoyimo.tk/transaction_DI/](http://yimoyimo.tk/transaction_DI/)
> - [https://d2.naver.com/helloworld/407507](https://d2.naver.com/helloworld/407507)

#### :small_orange_diamond:Join

#### :small_orange_diamond:SQL Injection

#### :small_orange_diamond:Index

#### :small_orange_diamond:Statement, PrepareStatement

#### :small_orange_diamond:RDBMS, NoSQL

#### :small_orange_diamond:효과적인 쿼리 저장


---
## Reference
> - []()


## :house: [Home](https://github.com/Do-Hee/tech-interview)
