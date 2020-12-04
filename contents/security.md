# 9. Security
**:book: Contents**

- [대칭키와 비대칭키 차이](#대칭키와-비대칭키-차이)
- [패스워드 암호화 방법](#패스워드-암호화-방법)
- [SQL Injection 공격](#sql-injection-공격)
- [CSRF 공격](#csrf-공격)
- [XSS 공격](#xss-공격)
- [OAuth](#oauth)

---

### 대칭키와 비대칭키 차이 
1. 대칭키 암호화 방식 (비밀키 암호화 방식)
- 개념 
    - 하나의 비밀키를 이용한 암호화 방식 
2. 비대칭키 암호화 방식 (공개키 암호화 방식)
- 개념 
    - 공개키(public)와 개인키(private)를 이용한 암호화 방식 
- 종류 
    1. 공개키로 암호화
        - 암호로서 효용성
    2. 개인키로 암호화
        - 공인인증체계에 사용하는 전자서명법
        
    <!-- - 암호화, 복호화시킬 수 있는 서로 다른 키 2개가 존재하는데 이 두 개의 키는 서로 1번 키로 암호화하면 반드시 2번키로만 복호화할 수 있고 2번 키로 암호화하면 반드시 1번키로만 복호화할 수 있는 룰이 있는 것이다.
    - 그 중에서 하나 키는 모두에게 공개키로 공개키 저장소에 등록해놓고 그 누구에게도 알려주지않고 개인(서버)만 알고 있는 개인키를 서버가 소유해서 통신하는 방식 -->
<!-- - 예시 
    - A와 B가 존재하고 A와 B 둘다 공개키와 비밀키를 소유하고 있다.
    - A가 평문을 B에게 보내고자 할 때 A는 B의 공개키를 가져와 암호화하여 전달한다.
    - B는 전달받은 암호문(B의 공개키로 암호화된 평문)을 B의 비밀키로 복호화 하여 평문을 얻는다.
    - 반대로 B 또한 A에게 평문을 전달할 때 A의 공개키를 사용하면 된다. -->
  
> :arrow_double_up:[Top](#9-security)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#9-security)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - [http://blog.naver.com/PostView.nhn?blogId=mr100do&logNo=60144936458](http://blog.naver.com/PostView.nhn?blogId=mr100do&logNo=60144936458)
> - [http://cryptocat.tistory.com/3](http://cryptocat.tistory.com/3)

### 패스워드 암호화 방법 
1. 단순 텍스트(plain text)
2. 단방향 해시 함수(one-way hash function)의 다이제스트(digest)
    * 수학적인 연산을 통해 원본 메시지를 변환하여 암호화된 메시지인 다이제스트를 생성한다. 
    * 원본 메시지를 알면 암호화된 메시지를 구하기는 쉽지만 암호화된 메시지로는 원본 메시지를 구할 수 없어야 하며 이를 '단방향성'이라고 한다.
    * 패스워드가 "hunter2"라면 이 문자열을 흔히 사용하는 해시 알고리즘인 "SHA-256"으로 인코딩
    * avalanche 효과
        * 대부분의 해시 함수는 입력 값의 일부가 변경되었을 때 다이제스트가 완전히 달라지도록 설계되어 있다. 
        * "hunter3"라는 값의 SHA-256 다이제스트는 아래와 같으며 위의 "hunter2"와는 완전히 달라진 것을 확인할 수 있다.
    * 단방향 해시 함수의 문제점
        * 1. 인식 가능성(recognizability)
            * "레인보우 공격(rainbow attack)"
            * 공격자가 전처리(pre-computing)된 다이제스트를 가능한 한 많이 확보한 다음 이를 탈취한 다이제스트와 비교해 원본 메시지를 찾아내거나 동일한 효과의 메시지를 찾을 수 있다.
        * 2. 속도(speed)
            * 해시 함수는 짧은 시간에 데이터를 검색하기 위해 설계된 것
            * 해시 함수의 빠른 처리 속도로 인해 공격자는 매우 빠른 속도로 임의의 문자열의 다이제스트와 해킹할 대상의 다이제스트를 비교할 수 있다
3. 솔팅(salting)
    * 솔트(salt)
        * 단방향 해시 함수에서 다이제스트를 생성할 때 추가되는 바이트 단위의 임의의 문자열
    * 솔팅(salting)
        * 이 원본 메시지에 문자열을 추가하여 다이제스트를 생성하는 것
        * 솔트 + 원본 메시지(패스워드) = 다이제스트
    * 사용자별로 다른 솔트를 사용한다면 동일한 패스워드를 사용하는 사용자의 다이제스트가 다르게 생성되어 인식 가능성 문제가 크게 개선된다.
    * 솔트와 패스워드의 다이제스트를 데이터베이스에 저장하고, 사용자가 로그인할 때 입력한 패스워드를 해시하여 일치 여부를 확인할 수 있다. 
    * 이 방법을 사용할 때에는 모든 패스워드가 고유의 솔트를 갖고 솔트의 길이는 32바이트 이상이어야 솔트와 다이제스트를 추측하기 어렵다.
4. 키 스트레칭(key stretching)
    * 여러 단계의 해시 함수를 적용하여 다이제스트를 생성하는 과정
    * 잘 설계된 패스워드 저장 시스템에서는 하나의 다이제스트를 생성할 때 어느 정도(일반적인 장비에서 0.2초 이상)의 시간이 소요되게 설정한다.
        * "억지 기법 공격(brute-force attack)"으로 패스워드를 추측하는 데 많은 시간이 소요되도록 하기 위한 것
    * 솔팅과 키 스트레칭으로 구성된 암호화 시스템을 구현하려고 한다면 이미 검증된 암호화 시스템을 사용할 것을 권장한다. 

<!-- * 참고) 안전한 패스워드 저장
    * 취약한 암호화 알고리즘(해시 함수)인 "SHA-1"
        * MD5, SHA-1, SHA-256, SHA-512 등의 해시 함수는 메시지 인증과 무결성 체크를 위한 것이다. 
        * 이것을 패스워드 인증을 위해 사용하면 인식 가능성과 빠른 처리 속도에 기인하는 취약점이 존재한다.
    * 해결법
        * 1. Adaptive Key Derivation Functions
            * 다이제스트를 생성할 때 솔팅과 키 스트레칭을 반복하며 솔트와 패스워드 외에도 입력 값을 추가하여 공격자가 쉽게 다이제스트를 유추할 수 없도록 하고 보안의 강도를 선택 -->

> :arrow_double_up:[Top](#9-security)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#9-security)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - [https://d2.naver.com/helloworld/318732](https://d2.naver.com/helloworld/318732)

### SQL Injection 공격
* 개념 
    * SQL 삽입공격은 웹에플리케이션에 대해서 가해지는 가장 흔한 공격 기법 중의 하나로 에플리케이션의 허점을 이용해서 데이터베이스를 비정상적으로 조작하는 기법
* 방어 방법 
    * mysql_real_escape_string을 사용하는 것만으로도 많은 공격을 차단할 수 있다.

> :arrow_double_up:[Top](#9-security)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#9-security)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - []()

### CSRF 공격
* 개념 
    * Cross-site request forgery, CSRF, XSRF, 사이트 간 요청 위조
    * 일단 사용자가 웹사이트에 로그인한 상태에서 사이트 간 요청 위조 공격 코드가 삽입된 페이지를 열면, 공격 대상이 되는 웹사이트는 위조된 공격 명령이 믿을 수 있는 사용자로부터 발송된 것으로 판단하게 되어 공격에 노출된다.
* 방어 방법 
    * XSS와 마찬가지로, 입력 필터링은 중요한 문제입니다.
    * 모든 민감한 동작에 필수로 요구되는 확인 절차가 항상 수행되도록 합니다.
    * 민감한 동작에 사용되는 쿠키는 짧은 수명만 갖도록 합니다.
* **[참고]** XSS vs CSRF
    * 사이트 간 스크립팅(XSS)을 이용한 공격이 사용자가 특정 웹사이트를 신용하는 점을 노린 것이라면, 
    * 사이트간 요청 위조(CSRF)는 특정 웹사이트가 사용자의 웹 브라우저를 신용하는 상태를 노린 것이다. 

> :arrow_double_up:[Top](#9-security)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#9-security)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - [https://developer.mozilla.org/ko/docs/Web/HTTP/Cookies](https://developer.mozilla.org/ko/docs/Web/HTTP/Cookies)

### XSS 공격 
* 개념 
    * Cross-site 스크립팅 공격, 사이트 간 스크립팅 공격
    * 사용자가 입력한 정보를 출력할 때 스크립트가 실행되도록 하는 공격기법
    * 웹사이트 관리자가 아닌 이가 웹 페이지에 악성 스크립트를 삽입할 수 있는 취약점이다.
    * 이 취약점은 웹 애플리케이션이 사용자로부터 입력 받은 값을 제대로 검사하지 않고 사용할 경우 나타난다. 
    * 이 취약점으로 해커가 사용자의 정보(쿠키, 세션 등)를 탈취하거나, 자동으로 비정상적인 기능을 수행하게 할 수 있다.
        * 누군가가 중간에서 사용자의 세션 아이디를 훔친다면 그 사용자처럼 로그인할 수 있게 된다.
* 방어 방법 
    * htmlspecialchars 사용
        * 이 함수는 html 코드를 해석하지 않고 화면에 그대로 출력하도록 변환
    * 쿠키는 XSS 공격과 CSRF 공격 등에 취약하기 때문에 
        * 쿠키 속성 HttpOnly 옵션을 활성화한다.
            * HttpOnly: true를 주면 자바스크립트를 통해서 쿠키 값에 접근할 수 없다.
            * XSS 공격 방지
        * 세션 옵션 Secure을 활성화
            * HTTPS에서만 쿠키가 전송된다. (즉, HTTPS에서만 세션 정보를 주고받을 수 있다.)
            * XSS 공격 방지
        * 쿠키를 사용하는 요청은 서버 단에서 검증하는 로직을 꼭 마련해두는 것이 좋다.
        * HTTPS를 이용해서 통신 하는 것이 좋다.

> :arrow_double_up:[Top](#9-security)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#9-security)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - []()

### OAuth
#### OAuth 개념
- 사용자가 어떤 애플리케이션을 이용할 때, 비밀번호를 입력하지 않고 OAuth를 제공하는 애플리케이션의 계정 정보를 공유하여 접근 권한을 부여할 수 있는 수단
- OAuth가 사용되기 전에는 보안이 취약한 구조
  - 각 애플리케이션이나 웹 사이트마다 개별적인 인증 방식으로 아이디와 비밀번호를 사용하여 로그인
- OAuth는 제각각인 인증방식을 표준화한 것
- 인증을 공유하는 애플리케이션끼리는 별도 인증과정 불필요
- '인증(Authentication)' 프로토콜이 아닌 **'인가(Authorization)' 프로토콜**
  - 인증 : 접근 가능함을 확인하는 과정
  - 인가 : 허가, 접근 권한을 관리
  - 사용자의 확인(인증) 과정을 통해 권한을 부여(인가)

#### OAuth 관련 용어
- 사용자
  - '서비스 제공자'와 '소비자'를 사용하는 계정을 가지고있는 개인
- 서비스 제공자
  - OAuth를 통한 접근을 지원하는 애플리케이션(Open API 제공 서비스)
  - 대표적으로 구글, 네이버, 카카오, 페이스북 등
- 소비자
  - Open API를 사용하여 개발된 OAuth를 사용하여 '서비스 제공자'에게 접근하는 애플리케이션
- 소비자 비밀번호
  - '서비스 제공자'에서 소비자가 자신임을 인증하는 키
- 요청 토큰
  - '소비자'가 '사용자'의 접근 권한을 인증받기 위해 필요한 정보
  - 이후 '접근 토큰'으로 변경
- 접근 토큰
  - 인증 후에 '사용자'가 '서비스 제공자'가 아닌 '소비자'를 통해 보호된 자원에 접근하기 위한 키를 포함한 값

#### 과정
- '소비자'와 '서비스 제공자' 간에 OAuth 과정 진행
1. 소비자가 서비스 제공자에게 '요청 토큰'을 요청
2. 서비스 제공자가 소비자에게 '요청 토큰' 발급
3. 소비자가 사용자를 서비스 제공자에게 이동시키고, 이 과정에서 사용자 인증 수행(인증, Authentication)
4. 사용자 인증 후, 서비스 제공자가 사용자를 소비자로 이동
5. 소비자가 '접근 토큰' 요청
6. 서비스 제공자가 '접근 토큰' 발급(권한 부여, Authorization)
7. 소비자는 '접근 토큰'을 사용하여 사용자 정보에 접근 가능

> :arrow_double_up:[Top](#9-security)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#9-security)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - [OAuth](https://ko.wikipedia.org/wiki/OAuth)


---

## Reference
> - []()


## :house: [Home](https://github.com/WeareSoft/tech-interview)
