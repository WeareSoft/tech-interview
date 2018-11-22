# 9. ETC
**:book: Contents**
* [TDD란](#tdd란)
* [웹 브라우저에서 서버로 어떤 페이지를 요청하면 일어나는 일련의 과정을 설명](#웹-브라우저에서-서버로-어떤-페이지를-요청하면-일어나는-일련의-과정을-설명)
* [대칭키와 비대칭키](#대칭키와-비대칭키)
* [컴파일러와 인터프리터](#컴파일러와-인터프리터)
* [분산락](#분산락)
* [프레임워크와 라이브러리의 차이](#프레임워크와-라이브러리의-차이)
* [64bit CPU와 32bit CPU 차이](#64bit-cpu와-32bit-cpu-차이)
* [CVS, SVN, Git](#cvs-svn-git)
* [Git Branch 종류(5가지)](#git-branch-종류)
* [웹 서버(Web Server)와 웹 어플리케이션 서버(WAS)의 차이](#web-server와-was의-차이)
* [애자일 방법론이란](#애자일-방법론이란)
* [Servlet과 JSP](#servlet과-jsp)
* [Memcached와 Redis의 차이](#Memcached와-Redis의-차이)

---

### TDD란
* Test Driven Development
  * 테스트 주도 개발: 테스트가 개발을 이끌어 나간다.
* 구체적인 행동 레벨에서의 TDD의 개념
  * 테스트를 먼저 만들고 테스트를 통과하기 위한 것을 짜는 것 
  * 즉, 만드는 과정에서 우선 테스트를 작성하고 그걸 통과하는 코드를 만들고를 반복하면서 제대로 동작하는지에 대한 피드백을 적극적으로 받는 것이다.
* 추상적인 레벨에서의 TDD의 핵심 개념(중요)
  * 결정과 피드백 사이의 갭에 대한 인식, 더 나아가 결정과 피드백 사이의 갭을 조절하기 위한 테크닉이라고도 할 수 있다.

> :arrow_double_up:[Top](#9-etc)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#9-etc)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [https://gmlwjd9405.github.io/2018/06/03/agile-tdd.html](https://gmlwjd9405.github.io/2018/06/03/agile-tdd.html)

### 웹 브라우저에서 서버로 어떤 페이지를 요청하면 일어나는 일련의 과정을 설명
* Ex. url에 'www.naver.com' 을 입력했다. 일어나는 현상에 대해 아는대로 설명하라.
  * 관련 링크: [http://owlgwang.tistory.com/1](http://owlgwang.tistory.com/1)

> :arrow_double_up:[Top](#9-etc)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#9-etc)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### 대칭키와 비대칭키
> :arrow_double_up:[Top](#9-etc)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#9-etc)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### 컴파일러와 인터프리터
> :arrow_double_up:[Top](#9-etc)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#9-etc)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### 분산락
> :arrow_double_up:[Top](#9-etc)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#9-etc)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### 프레임워크와 라이브러리의 차이
* 프레임워크(Framework)란
    * 소프트웨어의 구체적인 부분에 해당하는 설계와 구현을 재사용이 가능하게끔 일련의 협업화된 형태로 클래스들을 제공하는 것
    * Ex) 자동차의 프레임, 즉 기본적으로 구성하고 있는 뼈대
* 라이브러리(Library)란 
    * 자주 사용되는 로직을 재사용하기 편리하도록 잘 정리한 일련의 코드들의 집합
    * Ex) 자동차의 기능을 하는 부품
> :arrow_double_up:[Top](#9-etc)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#9-etc)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [http://moolgogiheart.tistory.com/87](http://moolgogiheart.tistory.com/87)

### 64bit CPU와 32bit CPU 차이
> :arrow_double_up:[Top](#9-etc)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#9-etc)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### CVS SVN Git
> :arrow_double_up:[Top](#9-etc)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#9-etc)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### Git Branch 종류
1. Master Branch
    * **제품으로 출시될 수 있는 브랜치**
    * 배포(Release) 이력을 관리하기 위해 사용. 즉, 배포 가능한 상태만을 관리한다.
2. Develop Branch
    * **다음 출시 버전을 개발하는 브랜치**
    * 기능 개발을 위한 브랜치들을 병합하기 위해 사용. 즉, 모든 기능이 추가되고 버그가 수정되어 배포 가능한 안정적인 상태라면 develop 브랜치를 ‘master’ 브랜치에 병합(merge)한다. 
    * 평소에는 이 브랜치를 기반으로 개발을 진행한다.
3. Feature branch
    * **기능을 개발하는 브랜치** 
    * feature 브랜치는 새로운 기능 개발 및 버그 수정이 필요할 때마다 ‘develop’ 브랜치로부터 분기한다. feature 브랜치에서의 작업은 기본적으로 공유할 필요가 없기 때문에, 자신의 로컬 저장소에서 관리한다. 
    * 개발이 완료되면 ‘develop’ 브랜치로 병합(merge)하여 다른 사람들과 공유한다.
4. Release Branch
    * **이번 출시 버전을 준비하는 브랜치** 
    * 배포를 위한 전용 브랜치를 사용함으로써 한 팀이 해당 배포를 준비하는 동안 다른 팀은 다음 배포를 위한 기능 개발을 계속할 수 있다. 즉, 딱딱 끊어지는 개발 단계를 정의하기에 아주 좋다. 
    * 예를 들어, ‘이번 주에 버전 1.3 배포를 목표로 한다!’라고 팀 구성원들과 쉽게 소통하고 합의할 수 있다는 말이다.
5. Hotfix Branch
    * **출시 버전에서 발생한 버그를 수정 하는 브랜치** 
    * 배포한 버전에 긴급하게 수정을 해야 할 필요가 있을 경우, ‘master’ 브랜치에서 분기하는 브랜치이다. ‘develop’ 브랜치에서 문제가 되는 부분을 수정하여 배포 가능한 버전을 만들기에는 시간도 많이 소요되고 안정성을 보장하기도 어려우므로 바로 배포가 가능한 ‘master’ 브랜치에서 직접 브랜치를 만들어 필요한 부분만을 수정한 후 다시 ‘master’브랜치에 병합하여 이를 배포해야 하는 것이다. 

> :arrow_double_up:[Top](#9-etc)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#9-etc)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [https://gmlwjd9405.github.io/2018/05/11/types-of-git-branch.html](https://gmlwjd9405.github.io/2018/05/11/types-of-git-branch.html)


### Web Server와 WAS의 차이
* Web Server
    * Web Server의 개념
        * 소프트웨어와 하드웨어로 구분된다.
        * 1) 하드웨어
            * Web 서버가 설치되어 있는 컴퓨터
        * 2) 소프트웨어
            * 웹 브라우저 클라이언트로부터 HTTP 요청을 받아 **정적인 컨텐츠(.html .jpeg .css 등)**를 제공하는 컴퓨터 프로그램
    * Web Server의 기능
        * **HTTP 프로토콜을 기반으로 하여 웹 브라우저의 요청을 서비스 하는 기능**을 담당한다.
        * 요청에 따라 아래의 두 가지 기능 중 적절하게 선택하여 수행한다.
        * 기능 1)
            * 정적인 컨텐츠 제공
            * WAS를 거치지 않고 바로 자원을 제공한다.
        * 기능 2)
            * 동적인 컨텐츠 제공을 위한 요청 전달
            * 클라이언트의 요청(Request)을 WAS에 보내고, WAS가 처리한 결과를 클라이언트에게 전달(응답, Response)한다.
    * Web Server의 예
        * Ex) Apache Server, Nginx, IIS(Windows 전용 Web 서버) 등
* WAS(Web Application Server)
    * WAS의 개념
        * DB 조회나 다양한 로직 처리를 요구하는 **동적인 컨텐츠**를 제공하기 위해 만들어진 Application Server
        * HTTP를 통해 컴퓨터나 장치에 애플리케이션을 수행해주는 미들웨어(소프트웨어 엔진)이다.
        * **"웹 컨테이너(Web Container)" 혹은 "서블릿 컨테이너(Servlet Container)"**라고도 불린다.
            * Container란 JSP, Servlet을 실행시킬 수 있는 소프트웨어를 말한다.
            * 즉, WAS는 JSP, Servlet 구동 환경을 제공한다.
    * WAS의 기능
        * **WAS = Web Server + Web Container**
        * Web Server 기능들을 구조적으로 분리하여 처리하고자하는 목적으로 제시되었다.
            * 분산 트랜잭션, 보안, 메시징, 쓰레드 처리 등의 기능을 처리하는 분산 환경에서 사용된다.
            * 주로 DB 서버와 같이 수행된다. 
    * WAS의 예
        * Ex) Tomcat, JBoss, Jeus, Web Sphere 등

> :arrow_double_up:[Top](#9-etc)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#9-etc)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html](https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html)

### 애자일 방법론이란
> :arrow_double_up:[Top](#9-etc)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#9-etc)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [https://gmlwjd9405.github.io/2018/05/26/what-is-agile.html](https://gmlwjd9405.github.io/2018/05/26/what-is-agile.html)

### Servlet과 JSP
* 기능의 차이는 없고 역할의 차이만 있다. (하는 일은 동일)
* Servlet이란
    * 웹 기반의 요청에 대한 동적인 처리가 가능한 Server Side에서 돌아가는 Java Program 
    * ***Java 코드*** 안에 HTML 코드 (하나의 클래스)
    * 웹 개발을 위해 만든 표준
    * **data processing(Controller)** 에 좋다.
    * 즉 DB와의 통신, Business Logic 호출, 데이터를 읽고 확인하는 작업 등에 유용하다.
    * Servlet이 수정된 경우 Java 코드를 컴파일(.class 파일 생성)한 후 동적인 페이지를 처리하기 때문에 전체 코드를 업데이트하고 다시 컴파일한 후 재배포하는 작업이 필요하다. **(개발 생산성 저하)**
    * 구체적인 내용은 [https://gmlwjd9405.github.io/2018/10/28/servlet.html](https://gmlwjd9405.github.io/2018/10/28/servlet.html) 참고
* JSP란
    * Java 언어를 기반으로 하는 Server Side 스크립트 언어
    * ***HTML 코드*** 안에 Java 코드 
    * Servlet를 보완하고 기술을 확장한 스크립트 방식 표준
        * Servlet의 모든 기능 + 추가적인 기능
        * ![](/images/web/jsp-definition.png)
    * **presentation(View)** 에 좋다. 
    * 즉 요청 결과를 나타내는 HTML 작성하는데 유용하다.
    * JSP가 수정된 경우 재배포할 필요가 없이 WAS가 알아서 처리한다. **(쉬운 배포)**
    * 구체적인 내용은 [https://gmlwjd9405.github.io/2018/11/03/jsp.html](https://gmlwjd9405.github.io/2018/11/03/jsp.html) 참고

> :arrow_double_up:[Top](#9-etc)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#9-etc)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [https://gmlwjd9405.github.io/2018/11/04/servlet-vs-jsp.html](https://gmlwjd9405.github.io/2018/11/04/servlet-vs-jsp.html)

### Memcached와 Redis의 차이
* Memcached
* Redis

> :arrow_double_up:[Top](#9-etc)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#9-etc)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [https://ojava.tistory.com/70](https://ojava.tistory.com/70)

---

## Reference
> - []()


## :house: [Home](https://github.com/Do-Hee/tech-interview)
