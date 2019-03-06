# 8. JavaScript
**:book: Contents**
* [JavaScript Event Loop](#javascript-event-loop)
* [Hoisting](#hoisting)
* [Closure](#closure)
* [this](#this)
* [Promise](#promise)
* [Async/Await](#async-await)

---

### JavaScript Event Loop

> :arrow_double_up:[Top](#8-javascript)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#8-javascript)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - []()

### Hoisting
- Hoisting(끌어올리다.)
    - Hoisting이란 선언한 함수와 변수를 해석기가 가장 상단에 있는 것처럼 인식한다.
    - js 해석기는 코드의 라인 순서와 관계 없이 **함수 선언식**(함수 표현식 X)과 **변수**를 위한 메모리 공간을 먼저 확보한다.
    - 따라서, `function a()`와 `var`는 코드의 최상단으로 끌어 올려진 것(hoisted)처럼 보인다.
 ```js
 function willbeoverridden() {
     return 10;
 }
 willbeoverridden(); // 5
 function willbeoverridden() {
     return 5;
 }
 ```
 ```js
 /* 예시 */
 var sum = 5;
 sum = sum + i;
 function sumAllNumbers() {
     // ...
 }
 var i = 10;

 /* js 해석기에 따른 순서 재조정 결과 */
 // #1 - 함수 선언식과 변수 선언을 hoisting
 var sum;
 function sumAllNumbers() {
     // ...
 }
 var i;
 // #2 - 변수 대입 및 할당
 sum = 5;
 sum = sum + i;
 i = 10;
 ```
 
> :arrow_double_up:[Top](#8-javascript)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#8-javascript)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - []()

### Closure

> :arrow_double_up:[Top](#8-javascript)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#8-javascript)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - []()

### this

> :arrow_double_up:[Top](#8-javascript)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#8-javascript)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - []()

### Promise

> :arrow_double_up:[Top](#8-javascript)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#8-javascript)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - []()

### Async Await

> :arrow_double_up:[Top](#8-javascript)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#8-javascript)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - []()

---

## Reference
> - []()


## :house: [Home](https://github.com/WeareSoft/tech-interview)
