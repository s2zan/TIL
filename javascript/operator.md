# 연산자

## 비교 연산자

`==` 과 `!=` 는 사용하지 말것, 타입을 엄격하게 비교하지 않는다!

<br>

## 논리 연산자

* **truthy** : `true`로 취급되는 값들 
  * falsy 이외의 모든 값
* **falsy** : `false`로 취급되는 값들
  * `false`
  * `null`
  * `undefined`
  * `0`
  * `NaN`
  * `''`

<br>

논리 연산자의 결과는 **Boolean이 아닌 값**일 수 있다!

* OR 연산자

  * truthy한 값을 만나면, 그 값을 출력

    ```javascript
    undefined || 10 || 'a' || NaN // output: 10
    ```

  * 모두 falsy할 경우, 마지막 값을 출력

    ```javascript
    false || null || 0 // output: 0
    ```

* AND 연산자

  * falsy한 값을 만나면, 그 값을 출력
  * 모두 truthy한 경우, 마지막 값을 출력