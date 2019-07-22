# 인증

사용자의 신원을 확인하는 절차

ex) 로그인

### api상에서의 절차

1. 사용자 가입 절차 진행 -> 아이디, 비밀번호 생성 (미니터 API의 경우 sign-up 엔드포인트)
2. 아이디와 비밀번호 DB에 저장
   - 이때 비밀번호는 암호화
3. 사용자 로그인시 본인의 아이디와 비밀번호 입력
4. 사용자가 입력한 비밀번호를 암호화한 후, 그 갑을 이미 암호화되어 DB에 저장된 비밀번호와 비교
5. 비밀번호 일치하면 로그인 성공
6. 로그인에 성공하면 백엔드 API 서버는 `access token`을 프론트엔드 or 클라이언트에게 전송
7. 프론트엔드 서버는 로그인 성공 후 다음부터는 해당 사용자의 `access token`을 첨부해서 request를 서버에 전송함으로써 매번 로그인하지 않아도 되도록 함

<br>

## 사용자 비밀번호 암호화

##### WHY?

- 외부의 해킹 공격에 의해 DB가 노출되었을 경우에 대비
- 내부 인력에 의해 DB가 노출되었을 경우에 대비

### 단방향 해시 함수 (one-way hash function) 

- 비밀번호 암호화시 일반적으로 사용

- 단방향성 : 복호화를 할 수 없음

- **애벌런시 효과(avalanche effect)**

  - 원본 값과 해시 값 사이에 직접적인 연관성이나 패턴이 없도록 하여 원본 값을 추론하는 것을 어렵게 만듦

- 파이썬의 `hashlib` 모듈

  ```python
  import hashlib
  m = hashlib.sha256()
  m.update(b"test password")
  m.hexdigest()
  ```

<br>

그러나, 취약점 존재

- rainbow attack : 가장 널리 사용되는 단방향 해시 알고리즘 해킹 방법
  - 미리 해시 값들을 계산해 놓은 테이블인 rainbow table을 생성, 해시 함수 값을 역추적해 본래 값을 찾아냄
  - 즉, 복호화 방식 X, 미리 암호화해둔 조합들을 매칭하는 방식

보완하기 위한 방법

- salting
  - 실제 비밀번호 이외에 추가적으로 랜덤 데이터를 더해 해시값을 계산
- key stretching
  - 단방향 해시 값을 계산한 후, 그 해시 값을 또 해시하고, 또 해시하고….. -> 알고리즘 실행 속도를 낮춰줌

이들을 구현한 해시함수 중 가장 널리 사용되는 bcrypt

<br>

### bcrypt

```python
import bcrypt
bcrypt.hashpw(b"secrete password", bcrypt.gensalt()).
```

<br>

## access token

HTTP는 stateless, 이로 인해 생기는 이슈 중 하나 : 인증 절차

현재의 통신에서 이전에 이미 인증이 진행됐는지 알지 못하기 때문

따라서, 로그인 정보를 담고 있는 `access token`을 요청에 첨부해서 보냄

### JWT (JSON Web Token)

- JSON 데이터를 token으로 변환하는 방식
- 왜 굳이 토큰으로 변환?
  - 단순 JSON 데이터를 사용하면 해킹 가능성의 문제가 발생
  - 데이터 전송 기능 외에 검증의 기능도, 서버 자신이 생성한 JWT인지 확인할 수 있는 기능 제공

#### JWT 구조

일반적으로, 다음과 같은 형태

```
xxxxxx.yyyyy.zzzzzzz
```

**x**: header, **y**: payload, **Z**: signature

"."으로 분리

- **header**

  - 토큰 타입 (JWT)
  - 사용되는 해시 알고리즘

- **payload**

  - 실제로 서버간에 전송하고자 하는 데이터

    (Base64URL 코드화 -> 암호화가 아니므로 누구나 복원 가능, 민감한 정보 넣지 않을 것)

- **signature**

  - JWT가 원본 그대로라는 것을 확인할 때 사용되는 부분

    Base64URL 코드화된 header와 payload, 그리고 JWT secret을 헤더에 지정된 암호알고리즘으로 암호화하여 전송(복호화 가능)

    API 서버는 전송받은 JWT의 signature 부분을 복호화하여 서버에서 생성한 JWT가 맞는지 확인



#### pyJWT

파이썬 JWT 라이브러리

```python
import jwt
data_to_encode = {'some': 'payload'}
encryption_secret = 'secret'
algorithm = 'HS256'
encoded = jwt.encode(data_to_encode, encryption_secret, algorithm=algorithm)
decoded = jwt.decode(encoded, encryption_secret, algorithm=algorithm)
```