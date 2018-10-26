# 8. Spring
**:book: Contents**
* [스프링 프레임워크란](#스프링-프레임워크란)
* [Spring, Spring MVC, Spring Boot의 차이](#spring-spring-mvc-spring-boot의-차이)
* [Container란](#container란)
* [IOC(Inversion of Control, 제어의 역전)란](#ioc란)
* [MVC 패턴이란](#mvc-패턴이란)
* [DI(Dependency Injection, 의존성 주입)란](#di란)
* [AOP(Aspect Oriented Programming)란](#aop란)
* [POJO](#pojo)
* [DAO와 DTO의 차이](#dao와-dto의-차이)
* [Spring JDBC를 이용한 데이터 접근](#spring-jdbc를-이용한-데이터-접근)

---

### 스프링 프레임워크란
* 자바 엔터프라이즈 개발을 편하게 해주는 경량급 오픈소스 애플리케이션 프레임워크
* **Lightweight Java Applicaion Framework**
    * 목표: **POJO 기반의** Enterprise Application 개발을 쉽고 편하게 할 수 있도록 한다.
    * Java Application을 개발하는데 필요한 하부구조(Infrastructure)를 포괄적으로 제공한다.
    * Spring이 하부구조를 처리하기 때문에 개발자는 Application 개발에 집중할 수 있다.
* 간단히 *스프링(Spring)*이라고도 불린다. 
* 동적인 웹 사이트를 개발하기 위한 여러 가지 서비스를 제공한다.
* 대한민국 공공기관의 웹 서비스 개발 시 사용을 권장하고 있는 전자 정부 표준 프레임워크의 기반 기술

> :arrow_double_up:[Top](#8-spring)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#8-spring)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [https://gmlwjd9405.github.io/2018/10/26/spring-framework.html](https://gmlwjd9405.github.io/2018/10/26/spring-framework.html)

### Spring Spring MVC Spring Boot의 차이
> :arrow_double_up:[Top](#8-spring)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#8-spring)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [http://blog.naver.com/PostView.nhn?blogId=sthwin&logNo=221271008423&parentCategoryNo=&categoryNo=50&viewDate=&isShowPopularPosts=true&from=search](http://blog.naver.com/PostView.nhn?blogId=sthwin&logNo=221271008423&parentCategoryNo=&categoryNo=50&viewDate=&isShowPopularPosts=true&from=search)

### Container란
- 컨테이너(Container)는 보통 인스턴스의 생명주기를 관리하며, 생성된 인스턴스들에게 추가적인 기능을 제공하도록하는 것이라 할 수 있다. 다시말해, 컨테이너란 당신이 작성한 코드의 처리과정을 위임받은 독립적인 존재라고 생각하면 된다. 컨테이너는 적절한 설정만 되어있다면 누구의 도움없이도 프로그래머가 작성한 코드를 스스로 참조한 뒤 알아서 객체의 생성과 소멸을 컨트롤해준다.

- Spring 프레임워크는 다른 프레임워크들과 달리 컨테이너 기능을 제공하고 있다. 이와 같은 컨테이너 기능을 제공하는 것이 가능하도록 하는 것이 IoC 패턴이다.

> :arrow_double_up:[Top](#8-spring)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#8-spring)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [http://limmmee.tistory.com/13](http://limmmee.tistory.com/13)
> - [http://wiki.javajigi.net/pages/viewpage.action?pageId=281](http://wiki.javajigi.net/pages/viewpage.action?pageId=281)  

### IoC란
- IoC(Inversion of Control, 제어의 역전)란
    - 객체의 생성에서부터 생명주기의 관리까지 모든 객체에 대한 제어권이 바뀐 것을 의미, 또는 제어 권한을 자신이 아닌 다른 대상에게 위임하는 것이다.
    - 이 방식은 대부분의 프레임워크에서 사용하는 방법으로, 개발자는 필요한 부분을 개발해서 끼워 넣기의 형태로 개발하고 실행하게 된다. 프레임워크가 이러한 구조를 가지기 때문에 개발자는 프레임워크에 필요한 부품을 개발하고 조립하는 방식의 개발을 하게 된다.
    - 이렇게 조립된 코드의 최종 호출은 개발자에 의해서 제어되는 것이 아니라 프레임워크의 내부에서 결정된 대로 이뤄지게 되는데, 이러한 현상을 "제어의 역전"이라고 표현한다.
- Spring에서의 IoC
    - Spring 프레임워크에서 지원하는 Ioc Container는 우리들이 흔히 개발하고 사용해왔던 일반 POJO(Plain Old Java Object)의 생명주기를 관리하며, 생성된 인스턴스들에게 추가적인 기능들을 제공한다.
- 라이브러리와 프레임워크의 차이
    - IoC의 개념이 적용되었나의 차이
    - 라이브러리를 사용하는 애플리케이션 코드는 애플리케이션 흐름을 직접 제어한다. 단지 동작히는 중에 필요한 기능이 있을 때 능동적으로 라이브러리를 시용할 뿐이다.
    - 반면에 프레임워크는 거꾸로 애플리케이션 코드가 프레임워크에 의해 사용된다. 보통 프레임워크 위에 개발한 클래스를 등록해두고, 프레임워크가 흐름을 주도히는 중에 개발자가 만든 애플리케이션 코드를 시용하도록 만드는 방식이다.

> :arrow_double_up:[Top](#8-spring)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#8-spring)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [http://wiki.javajigi.net/pages/viewpage.action?pageId=3664](http://wiki.javajigi.net/pages/viewpage.action?pageId=3664)
> - [http://limmmee.tistory.com/13](http://limmmee.tistory.com/13)
> - [http://wiki.javajigi.net/pages/viewpage.action?pageId=281](http://wiki.javajigi.net/pages/viewpage.action?pageId=281)

### MVC 패턴이란
> :arrow_double_up:[Top](#8-spring)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#8-spring)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### DI란
- DI?
    - Dependency Injection, 의존성 주입
    - Dependency Injection은 Spring 프레임워크에서 지원하는 IoC의 형태이다. 
    - DI는 클래스 사이의 의존관계를 빈 설정 정보를 바탕으로 컨테이너가 자동적으로 연결해주는 것을 말한다. 개발자들은 제어를 담당할 필요없이 빈 설정 파일에 의존관계가 필요하다는 정보만 추가해주면 된다.
        - 컨테이너가 실행 흐름의 주체가 되어 애플리케이션 코드에 의존관계를 주입해주는 것.
- 의존성(Dependency)
    - 현재 객체가 다른 객체와 상호작용(참조)하고 있다면 다른 객체들을 현재 객체의 의존이라 한다.
- 의존성이 위험한 이유
    - 하나의 모듈이 바뀌면 의존한 다른 모듈까지 변경되야 한다.
    - 테스트 가능한 어플을 만들 때 의존성이 있으면 유닛테스트 작성이 어렵다.
    - 유닛테스트의 목적 자체가 다른 모듈로부터 독립적으로 테스트하는 것을 요구한다.
- DI의 특징
    - ‘new’를 사용해 모듈 내에서 다른 모듈을 초기화하지 않으려면 객체 생성은 다른 곳에서 하고, 생성된 객체를 참조하면 된다.
    - 의존성 주입은 Inversion of Control 개념을 바탕으로 한다. 클래스가 외부로부터 의존성을 가져야한다.
- DI가 필요한 이유(DI의 장점)
    - 클래스를 재사용 할 가능성을 높이고, 다른 클래스와 독립적으로 클래스를 테스트 할 수 있다.
    - 비즈니스 로직의 특정 구현이 아닌 클래스를 생성하는데 매우 효과적
- DI의 세가지 방법
    - Contructor Injection : 생성자 삽입
    - Method(Setter) Injection : 메소드 매게 변수 삽입
    - Field Injection : 멤버 변수 삽입

> :arrow_double_up:[Top](#8-spring)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#8-spring)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [http://www.nextree.co.kr/p11247/](http://www.nextree.co.kr/p11247/)
> - [http://wiki.javajigi.net/pages/viewpage.action?pageId=281](http://wiki.javajigi.net/pages/viewpage.action?pageId=281)
> - [http://tony-programming.tistory.com/entry/Dependency-의존성-이란](http://tony-programming.tistory.com/entry/Dependency-의존성-이란) 

### AOP란
* AOP(Aspect Oriented Programming)란

> :arrow_double_up:[Top](#8-spring)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#8-spring)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### POJO
번역하면 '평범한 구식 자바 객체'. 즉 프레임워크 인터페이스나 클래스를 구현하거나 확장하지 않는 단순한 클래스.
- EJB와 엔터프라이즈 서비스
    - EJB(Enterprise JavaBean)
    - 기업업무처리의 IT시스템에 대한 의존도가 높아지면서 시스템이 다뤄야 하는 **비즈니스 로직 자체가 점차 복잡**해지고, 많은 사용자의 처리요구를 빠르게 안정적이면서 확장 가능한 형태로 유지하기위해 필요한 **로우레벨의 기술적인(트랜젝션 처리, 상태관리, 멀티쓰레딩, 리소스풀링, 보안등) 처리**가 요구됐다.
    - EJB의 비전은 **'EJB는 애플리케이션 개발을 쉽게 만들어준다. 애플리케이션 개발자는 로우레벨의 기술들에 관심을 가질 필요도 없다.'** 였지만, 결론적으론 불필요할만큼 **과도한 엔지니어링으로 실패한 대표적인 케이스**가 되었다.
        - 가장 최악의 문제점은 EJB 스펙을 따르는 비즈니스 오브젝트들은 객체지향적인 **특징과 장점을 포기해야했다는 것**이다. EJB 빈은 상속과 다형성등의 혜택을 제대로 누릴 수 없었다.
    - 마틴 파울러는 **EJB와 같은 잘못 설계된 과도한 기술을 피하고, 객체지향 원리에 따라 만들어진 자바 언어의 기본에 충실하게 비즈니스 로직을 구현하는 일명 POJO 방식으로 돌아서야 한다**고 지적했다.
- 특징
    - Java에서 제공하는 API 외에 종속되지 않음
    - 특정 규약, 환경에 종속되지 않음
- 환경에 종속되지 않는 것의 장점
    - 코드의 간결함 (비즈니스 로직과 특정 환경/low 레벨 종속적인 코드를 분리하므로 단순)
    - 비즈니스 로직과 특정 환경이 분리되므로 단순함
    - 자동화 테스트에 유리 (환경 종속적인 코드는 자동화 테스트가 어렵지만, POJO는 테스트가 매우 유연)
    - 객체지향 설계의 자유로운 사용

> :arrow_double_up:[Top](#8-spring)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#8-spring)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [http://limmmee.tistory.com/8?category=654011](http://limmmee.tistory.com/8?category=654011)

### DAO와 DTO의 차이
> :arrow_double_up:[Top](#8-spring)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#8-spring)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### Spring JDBC를 이용한 데이터 접근
> :arrow_double_up:[Top](#8-spring)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#8-spring)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

---

## Reference
> - []()


## :house: [Home](https://github.com/Do-Hee/tech-interview)
