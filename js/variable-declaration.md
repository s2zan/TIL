# 변수 선언

자바스크립트에서 변수를 선언하는 경우 `var`, `let`, `const` 를 사용한다. (정확히는 `const`는 상수 선언이지만)

var | let | const
--- | --- | ---
변수 | 변수 | 상수
function-scoped | block-scoped | block-scoped
재할당O | 재할당O | 재할당X
재선언O | 재선언X | 재선언X

## var

* **함수 스코프**

  var으로 선언된 변수를 scope 내에 가두기 위해서는 함수가 필요, IIFE(immediately-invoked function expression) 사용하기도

  -> var 키워드를 명시하지 않는 변수 선언시 문제 발생

  ```javascript
  (function () { // IIFE
      test = "test";
      console.log(test);
  })();
  
  console.log(test);
  ```

  실행 결과, `test`가 두번 출력된다.  자바스크립트 해석기는 특정 scope에서 var 키워드 없이 선언된 변수를 찾게 되면, 그 변수를 점점 바깥 scope에서 찾는 시도를 한다. 결국 선언을 찾지 못하면 전역 scope 에 선언하기 떄문에 위와 같은 결과 발생

* **변수 명을 재선언해도 문제 X**

  ```javascript
  var score = 50;
  ...
  var score = 100; // 에러 발생하지 않음
  ```

* **hoisting**

  다음과 같은 코드 실행시,

  ```javascript
  console.log(hoistingTest); // 선언되지 않은 변수 -> 에러 발생?
  var hoistingTest = "hello";
  console.log(hoistingTest);
  ```

  에러 발생하지 않고 다음과 같이 출력

  ```
  undefined
  hello
  ```

  이는 `hoistingTest` 변수 선언문을 위로 끌어올려 해석하기 때문이다. 즉, 다음의 코드와 같이 해석한다.

  ```javascript
  var hoistingTest;
  console.log(hoistingTest); // 앞서 선언되었으므로 할당은 안됐지만 문제 없다!
  hoistingTest = "hello";
  console.log(hoistingTest);
  ```

  따라서, hoisting은 개발자가 코드의 실행을 예측하기 어렵게 만든다. 이를 막기위해 `'use strict'` 를 사용하기도

<br>

이러한 `var`의 문제점을 보완하기 위해 `let`과 `const`가 도입

## let, const

* **변수 재선언이 불가능**

* **hosting**

  hoisting 이 발생되지 않는 것이 아닌, **block-scope** 단위로 hoisting 

* `let`: 재할당 O

* `const`: immutable, 재할당 X, 선언과 동시에 할당

  배열, 객체, 함수 등 자료형을 유지하기 위해서도 `const`사용

  ```javascript
  const obj = {txt:"old"};
  obj = "new"; // 에러O, obj가 객체를 유지하게 해줌
  obj.txt = "new"; // 에러X
  ```

<br>

따라서, `let`과 `const`를 사용하자!

<br>

## 참고

* [var, let, const 차이점은?](https://gist.github.com/LeoHeo/7c2a2a6dbcf80becaaa1e61e90091e5d)
* [javascript - var let const 비교설명 (부제:const 객체, const 배열을 사용하는 이유)](https://blog.hanumoka.net/2018/09/21/javascript-20180921-javascript-var-let-const/)