# == vs ===

js에서 `==`과 `===`은 비슷하지만 전혀 다른 의미를 갖는다.

<br>

### Equal Operator `==`, `!=`

* Equality를 비교

* 피연산자들을 먼저 서로 비교할 수 있는 형태로 변환
* 즉, **값**이 같은지 판단

```javascript
254 == '254'  // true
true == 1  // true
undefined == null  // true
'abc' == new String('abc')  // true
null == false  // false
'true' == true  // false
true == 2  // false
```

<br>

### Strict Equal Operator `===`, `!==`

* 형변환 하지 않고 연산
* 즉, **값**과 **타입**이 정확하게 같은지 판단

```javascript
123 === '123'  // false
true === 1  // false
undefined === null  // false
'abc' = new String('abc')  // false
```

<br>

`===` 과 `!==`  사용을 권장!!

### 참고

* [JavaScript 동치연산자 ==와 ===의 차이점](https://hyunseob.github.io/2015/07/30/diffrence-between-equality-and-identity-in-javascript/)