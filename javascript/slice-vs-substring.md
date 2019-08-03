# String.slice() vs String.substring()

```javascript
str.slice(start, end)
str.substring(start, end)
```

#### 공통

* `start === end`라면 빈 문자열 반환
* `end` 생략시 문자열의 끝까지
* `start`과 `end`가  문자열의 길이보다 크면 문자열의 길이가 대신 사용됨

#### slice()

* `start > end`라면 빈 문자열 반환

* 만약 `start` 나 `end`가 음수면, 끝에서 부터 (파이썬처럼…)

  > 1. If `start` is negative: sets char from the end of string, exactly like `substr()` in Firefox. This behavior is observed in both Firefox and IE.
  > 2. If `stop` is negative: sets stop to: `string.length – Math.abs(stop)` (original value), except bounded at 0 (thus, `Math.max(0, string.length + stop)`) as covered in the [ECMA specification](https://www.ecma-international.org/ecma-262/9.0/index.html#sec-string.prototype.slice).

#### substring()

- `start > end`라면 둘을 바꿔줌
- 둘 중 하나가 음수거나 `NaN`이면 `0`을 반환



### 참고

* [What is the difference between String.slice and String.substring?](https://stackoverflow.com/questions/2243824/what-is-the-difference-between-string-slice-and-string-substring)