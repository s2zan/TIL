# 본격적으로 API 개발하기
## 미니 트위터 만들기
실습코드 : [app.py](https://github.com/s2zan/TIL/blob/master/python-backend/5-source/app.py)
#### 핵심 기능
* [회원가입](#회원가입)
* 로그인
* [트윗](#300자-제한-트윗-올리기)
* [다른 회원 팔로우 하기](#팔로우)
* [다른 회원 언팔로우 하기](#언팔로우)
* [타임라인](#타임라인)

<br>

### 회원가입
* 필요한 데이터
  * ID
  * name
  * email
  * password
  * Profile

##### request

```http
POST /sign-up HTTP/1.1
Content-Type: application/json
...
{
	"email":"209rrsz@gmail.com",
	"name":"jian",
	"password":"test1234",
	"profile":"study flask"
}
```

##### response

```http
HTTP/1.1 200 OK
content-length: 122
content-type: application/json
...
{
    "email": "209rrsz@gmail.com",
    "id": 1,
    "name": "jian",
    "password": "test1234",
    "profile": "study flask"
}
```

<br>

### 300자 제한 트윗 올리기
* 조건
  
  * 사용자는 300자를 초과하지 않는 글을 올릴 수 있다.
  * 만일 300자를 초과하면 엔드포인트는 400 Bad Request 응답을 보내야 한다.
  * 사용자가 300자 이내의 글을 전송하면 엔ㄷ포인트는 사용자의 글을 저장하고 있어야 한다.
  
* 필요한 데이터

  * ID
  * tweet

##### request

```http
POST /tweet HTTP/1.1
Content-Type: application/json
...
{
	"id":1,
	"tweet":"hello, world"
}
```

##### response

```http
HTTP/1.1 200 OK
content-length: 0
content-type: application/json
...
```

<br>

### 팔로우
* 필요한 데이터

  * ID
  * follow

##### request

```http
POST /follow HTTP/1.1
Content-Type: application/json
...
{
	"id": 1,
	"follow": 2
}
```

##### response

```http
HTTP/1.1 200 OK
content-length: 148
content-type: application/json
...
{
    "email": "209rrsz@gmail.com",
    "follow": [
        2
    ],
    "id": 1,
    "name": "jian",
    "password": "test1234",
    "profile": "study flask"
}
```


<br>

### 언팔로우
* 필요한 데이터

  * ID
  * unfollow
* `user.setdefault('follow', set()).discard(user_id_to_follow)` 에서 `discard`사용하는 이유?
  * `remove` 사용시, 없는 값을 삭제하려고 하면 오류 발생, `discard`의 경우 무시된다.
##### request

```http
POST /unfollow HTTP/1.1
Content-Type: application/json
...
{
	"id": 1,
	"unfollow": 2
}
```

##### response

```http
HTTP/1.1 200 OK
content-length: 139
content-type: application/json
...
{
    "email": "209rrsz@gmail.com",
    "follow": [],
    "id": 1,
    "name": "jian",
    "password": "test1234",
    "profile": "study flask"
}
```

<br>

### 타임라인
* 조건
  
  * 해당 사용자의 트윗과 팔로우하는 사용자들의 트윗을 리턴

* URL에 parameter를 전송하고 싶을때는 `<type:value>` 형식으로 URL 구성한다.

##### request

```http
GET /tweet/1 HTTP/1.1
...
```

##### response

```http
HTTP/1.1 200 OK
content-length: 174
content-type: application/json
...
{
    "timeline": [
        {
            "tweet": "nice to meet you!",
            "user_id": 2
        },
        {
            "tweet": "hello, world",
            "user_id": 1
        }
    ],
    "user_id": 1
}
```
