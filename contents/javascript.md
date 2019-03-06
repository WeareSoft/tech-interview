# 8. JavaScript
**:book: Contents**
* [JavaScript Event Loop](#javascript-event-loop)
* [함수 선언식과 함수 표현식](#함수-선언식과-함수-표현식)
* [변수 선언 방식 const와 let](#변수-선언-방식-const와-let)
* [화살표 함수](#화살표-함수)
* [향상된 객체 리터럴](#향상된-객체-리터럴)
* [Modules](#modules)
* [Destructuring](#destructuring)
* [Spread Operator](#spread-operator)
* [Hoisting](#hoisting)
* [Closure](#closure)
* [this](#this)
* [Promise](#promise)
* [Async/Await](#async-await)

---

### JavaScript Event Loop

> :arrow_double_up:[Top](#8-javascript)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#8-javascript)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - []()

### 함수 선언식과 함수 표현식
- 함수 
```js
// function statement
function sum() {
    return 10 + 20;
}
```
- 함수 표현식
```js
// function expression (; 존재)
var sum = function () {
    return 10 + 20;
};
 ```
 
 > :arrow_double_up:[Top](#8-javascript)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#8-javascript)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - []()

### 변수 선언 방식 const와 let
- 블록 단위 `{}`로 변수의 범위가 제한되었음
 ```js
 let sum = 0;
 for (let i=1; i<=5; i++) {
     sum = sum + i;
 }
 console.log(sum); // 10
 console.log(i); // Uncaught ReferenceError: i is not defined
 ```
- `const`
    - 한번 선언한 값에 대해서 변경할 수 없음(상수 개념)
 ```js
 /* 예시 */
 const a = 10;
 a = 20; // Uncaught TypeError: Assignment to constant variable

 /* [주의!] 하지만, 객체나 배열의 내부는 변경할 수 있다. */
 const a = {};
 a.num = 10;
 console.log(a); // {num: 10}

 const b = [];
 b.push(20);
 console.log(b); // [20]
 ```
- `let`
    - 한번 선언한 값에 대해서 다시 선언할 수 없음(메모리에 할당하면 다시 할당하지 못함), 변경은 가능 
- 간단한 scope 예시
 ```js
 function f() {
     {
        let x;
        {
            // 새로운 블록 안에 새로운 x의 스코프가 생김
            const x = "sneaky";
            x = "foo"; // 위에 이미 const로 x를 선언했으므로 다시 값을 대입하면 Error
        }
        // 이전 블록 범위로 돌아왔기 때문에 'let x'에 해당하는 메모리에 값을 대입
        x = "bar";
        let x = "inner"; // SyntaxError: Identifier 'x' has already been declared
     }
 }
 ```
 
 > :arrow_double_up:[Top](#8-javascript)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#8-javascript)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - []()
 
### 화살표 함수 
- **Arrow Function**, Fat Arrow
- 함수를 정의할 때 `function`이라는 키워드를 사용하지 않고 `=>`로 대체
- 흔히 사용하는 **콜백 함수**의 문법을 간결화
```js
// ES5 함수 정의 방식 (function expression)
var sum = function (a, b) {
   return a + b;
};

// ES6 함수 정의 방식
var sum = (a, b) => {
   return a + b;
}
sum (10, 20);
```
```js
/* 화살표 함수 사용 예시 */

var arr = ["a", "b", "c"];
// ES5
arr.forEach(function(value){ // 익명 함수
   console.log(value); // a, b, c
});
// ES6
arr.forEach(value => console.log(value)); // a, b, c
```

> :arrow_double_up:[Top](#8-javascript)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#8-javascript)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - []()

### 향상된 객체 리터럴 
- **Enhanced Object Literals**
- 객체의 속성을 메서드로 사용할 때 `function`예약어를 생략하고 생성 가능
```js
// 객체 
var dictionary = {
   words: 100, 
   /* 속성 메서드: 속성에 function을 연결 */
   // ES5
   lookup: function() {
       console.log("find words");
   },
   // ES6 - ': funtion' 생략 
   lookup() {
       console.log("find words");
   }
};
```
- 객체의 속성명과 값 명이 동일할 때 아래와 같이 축약 가능
```js
var figures = 10;
var dictionary = {
   // figures: figures,
   figures
};
```

> :arrow_double_up:[Top](#8-javascript)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#8-javascript)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - []()

### Modules 
- **자바스크립트 모듈화 방법**
- 자바스크립트 모듈(특정 기능을 수행하는 한 단위) 로더 라이브러리(AMD, Commons JS)기능을 js언어 자체에서 지원
- 모듈화 하는 이유
    - 재사용성
    - 변수 scope 충돌 방지
    - 안정성있는 코딩 가능
    - Modules: lib에서 지원하던 것을 언어 차원에서 지원함으로써 개발자들의 수고를 덜어줌
- 호출되기 전까지는 코드 실행과 동작을 하지 않는 특징이 있음
```js
// libs/math.js
export function sum(x, y) {
   return x + y;
}
export var pi = 3.141592;

// main.js
import {sum} from libs/math.js;
sum(1, 2);
```
- `defualt` export
    - 하나의 파일에서 하나만 export 할 수 있다.
    - encapsulation으로 모듈화
    - 다른 파일에서 가져다가 사용할 때 원하는 이름을 설정하여 사용할 수 있다.
```js
// util.js
export default function(x) {
   return console.log(x);
}
// main.js
import util from `util.js`;
console.log(util); // function(x) {return console.log(x);}
```

> :arrow_double_up:[Top](#8-javascript)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#8-javascript)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - []()
   
### Destructuring
- **디스트럭처링 (Destructuring)**

> :arrow_double_up:[Top](#8-javascript)    :leftwards_arrow_with_hook:[Back](https://github.com/WeareSoft/tech-interview#8-javascript)    :information_source:[Home](https://github.com/WeareSoft/tech-interview#tech-interview)
> - []()

### Spread Operator
- **전개 연산자 (Spread Operator)**

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
