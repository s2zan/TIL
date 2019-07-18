# HTTP의 구조 및 핵심 요소

## HTTP

> HyperText Transfer Protocol
웹상에서 서로 다른 서버 간에 하이퍼텍스트 문서(HTML)를 주고받을 수 있도록 만들어진 프로토콜



### 통신 방식

#### HTTP 요청(request)과 응답(response)
클라이언트가 먼저 HTTP 요청을 서버에 보내면, 서버는 요청을 처리한 후 결과에 따른 HTTP 응답을 클라이언트에게 보냄
```python
@app.route("/ping", methods=['GET'])
def ping():
    return "pong"
```
* HTTP 요청 : `/ping` 주소에 GET 요청을 보냄
* HTTP 응답 : `200 OK` 상태 코드와 함께 "pong"이라는 텍스트 보냄
위으 코드에서 문자열만 리턴되는 것 같아 보이지만, Flask가 HTTP 부분을 자동으로 처리해 "pong"을 body로 가지는 HTTP 응답으로 변환시켜준다!
#### stateless
상태가 없다 = 각각의 HTTP 통신은 독립적이며 그 전에 처리된 HTTP 통신에 대해 전혀 알지 못함
* 👍 서버 디자인이 훨씬 간단해지고 효과적
	여러 다른 HTTP 통신간의 진행이나 연결 상태의 처리/저장을 구현 및 관리하지 않아도 됨
* 👎 HTTP 요청을 보낼 때는 해당 요청을 처리하기 위해 필요한 모든 데이터를 매번 포함시켜 요청해야 함
	-> 이를 해결하기 위해 쿠키(cookie, 클라이언트 측에 데이터 저장)나 세션(session, 서버 측에 데이터 저장)등 사용



### HTTP 요청 구조

##### Start Line
```http
GET /test HTTP/1.1
```
다음과 같이 구성

- HTTP 메소드
  - 해당 요청이 의도하는 액션을 정의
  - **GET** / **POST** / PUT / DELETE / OPTIONS 등
- Request target
  - 해당 요청이 전송되는 목표 주소. 위의 경우 `test` 엔드포인트에 보냄을 의미
- HTTP version
  - 해당 요청의 HTTP 버전
  - 1.0 / 1.1 / 2.0

##### Headers

```
Accept: application/json
Accept-Encoding: gzip, deflate
Connection: keep-alive
Content-Length: 83
Content-Type: application/json
Date: Thu, 18 Jul 2019 20:53:12 GMT
Host: XXXXXXXXX.com
User-Agent: HTTPie/0.9.3
```
HTTP 요청 그 자체에 대한 정보가 key - value 로 구성
자주 사용되는 헤더 정보는 다음과 같다.

- **Host** : 요청이 전송되는 target 호스트의 URL 주소
- **User-Agent** : 요청을 보내는 클라이언트에 대한 정보 (웹 브라우저 등)
- **Accept** : 해당 요청이 받을 수 있는 응답의 body 데이터 타입
- **Coonection** : 해당 요청이 끝난 후 클라이언트와 서버가 계속 연결을 유지할 것(keep-alive)인지 끊을 것(close)인지
- **Content-Tyope** : 요청에 포함된 body의 데이터 타입
- **Content-Length** : 요청에 포함된 body의 총 사이즈

참고 : [[HTTP 기초_1] 헤더 (요청(request) 헤더, 응답(response) 헤더)](

##### Body

```
{
	"uid": "qwer1234",
	"status": "happy"
}
```

요청이 전송하는 데이터를 담고 있는 부분

만약 전송하는 데이터가 없다면 body 부분은 비어있음



### HTTP 응답 구조

##### Status Line

```http
HTTP/1.1 404 Not Found
```

다음과 같이 구성

- HTTP version
  - 사용되고 있는 HTTP 버전
- Status Code
  - 응답 상태를 미리 지정되어 있는 숫자 코드로 표시
- Status Text
  - 응답 상태를 간략한 텍스트로 표시

##### Headers

```
Connection: close
Content-Length: 1573
Content-Type: text/html; charset=UTF-8
Date: Thu, 18 Jul 2019 20:53:12 GMT
```

HTTP 요청의 헤더 부분과 동일, 다만 응답에서만 사용되는 헤더 값들이 존재 

##### Body

```
<!DOCTYPE html>
<html lang=en>
	<meta charset=uft-8>
	<title>Error 404 (Not Found)!!!</title>
	<style>
		...................
```

HTTP 요청의 body 부분과 동일



### 자주 사용되는 HTTP 메소드

#### GET

데이터를 서버로부터 요청, 데이터의 변경 사항 없이 단순히 데이터 받아오는 요청 (주로 body가 비어있다)

#### POST

데이터 생성/수정/삭제 요청

#### OPTIONS

주로 특정 엔드포인트에서 허용하는 메소드들이 무엇이 있는지 알고자 하는 요청

응답은 다음과 같다

```http
HTTP/1.0 200 OK

ALLOW: GET, HEAD, OPTIONS
Content-Length: 0
....
```

#### PUT

참고 : [POST vs PUT](https://blog.embian.com/66)

#### DELETE

데이터 삭제 요청



### 자주 사용되는 HTTP Status Code와 Text

#### 200 OK
요청이 성공적으로 처리

#### 301 Moved Permanently
요청을 보낸 엔드포인트의 URL 주소가 바뀌었음을 나타냄
보통 Location 헤더에 해당 엔드포인트의 새로운 주소가 포함

#### 404 Bad Request
잘못된 요청
주로 요청에 포함된 input 값이 잘못 보내졌을 때 사용

#### 401 Unauthorized
요청을 보내는 주체의 신분 확인이 요구될 때 보냄
주로 로그인이 필요한 경우

#### 403 Forbidden
요청을 보내는 주체가 해당 요청에 대한 권한이 없음을 의미

#### 404 Not Found
요청을 보내고자 하는 URI가 존재하지 않음

#### 500 Interneal Server Error
내부 서버 오류 발생



### API 엔드 포인트 아키텍처 패턴

#### RESTful HTTP API

> REpresentational State Transfer

API에서 전송하는 리소스를 URI로 표현하고, 해당 리소스에 행하고자 하는 의도를 HTTP 메소드로 정의하는 방식

Self-Descriptiveness : 엔드포인트의 구조만 보더라도 해당 엔드포인트가 제공하는 리소스와 기능 파악 가능

#### GraphQL

> Graph Query Language

API의 구조가 특정 클라이언트에 맞추어져서 다른 클라이언트에서 사용하기에 적합하지 않게 된다는 REST 방식을 해결하기 위해 도입됨

하나의 엔드포인트에 클라이언트가 필요한 것을 정의해 요청하는 방식

예를 들어, 일반적인 REST 방식에서 아이디가 1인 사용자의 정보와 그의 친구들의 이름 정보를 받아오고자 할때,

```
GET /users/1
GET /users/1/friends
```

와 같이 두번의 HTTP 요청을 보내거나

```
GET /users/1?include=friends.name
```

의 방식으로 HTTP 요청을 보내야 한다.

그러나 GraphQL 방식에서는 한번의 요청으로 처리 가능하다.

```
POST /graphql
{
	user(id: 1){
		name
		age
		friends{
			name
		}
	}
}
```

참고: [GraphQL과 RESTFul API](https://www.holaxprogramming.com/2018/01/20/graphql-vs-restful-api/)