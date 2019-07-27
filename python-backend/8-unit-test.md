# unit test

### 테스트 자동화의 중요성

* 메뉴얼 테스트 : 사람이 직접 실행하는 테스트

  * 👍 : 직관적으로. 큰 계획 없이 테스트 가능
  * 👎 : 테스트 실행 속도 느리고 시간 오래 걸림 -> 자주 X, 부정확할 확률

  

* 시스템 테스트 방법 (기능으로 분류)

  * [UI test / End-To-End test](#ui-test-/-end-to-end-test)
  * [integration test](#integration-test)
  * [unit test](#unit-test) ⭐️

<br>

## UI test / End-To-End test

UI(ex. 웹브라우저)를 통해서 테스트

* 👍 : 사용자가 실제로 시스템 사용하는 방식과 동일 -> 확실
* 👎 : 시간이 많이 소요, 프론트 ~ 백엔드 까지 다 실행시키고 연결해야 함, 자동화 까다로움 (셀레니엄 등 프레임워크 사용)

-> 반드시 필요한 테스트지만 비중은 적게(10%)

<br>

## integration test

요청(또는 명령어)을 실행하여 테스트하는 방식

* 👍 : UI test에 비해 자동화 용이
* 👎 : 실제로 시스템 실행해야 함, unit test에 비해 자동화 까다롭고 실행속도 느림

-> 20%

<br>

## unit test

시스템 테스트라기 보다는 코드를 직접 테스트하는 개념

```python
assert plus(1,2) == 3
```

- 👍 : 실행 쉽고 속도 빠름, 디버깅 용이
- 👎 : 전체를 테스트하는데 한계 -> UI test, integration test 로 보완

-> 70%



## pytest

unittest 모듈보다 직관적

#### test_sample.py

```python
def plus(x, y):
  return x + y

def test_plys(): # test_로 시작해야 pytest가 유닛테스트로 인식
  assert plus(1,2) == 3
```

pytest는 별도의 arg가 없으면 현재 디렉터리에 있는 `test_*.py`, `*_test.py` 파일을 찾아 테스트 진행한다. (참고: [pytest를 사용해보자 (1)](https://wkdtjsgur100.github.io/pytest-description-1/)) 

따라서 위의 파일이 있는 경로에서 다음 명령어 실행

```
pytest
```



[실습 코드]()

