# 첫 API 개발 시작
## Flask

> micro web framework

##### Flask 설치

```
pip install flask
```

```python
from flask import Flask
app = Flask("test")
```



## ping 엔드포인트 구현

엔드포인트

* API 서버가 제공하는 통신 채널 혹은 접점
* 각 엔드포인트는 고유한 URL 주소를 가지고, 이를 통해 해당 엔드포인트에 접속



[app.py](https://github.com/s2zan/TIL/blob/master/python-backend/3-source/app.py)

```python
from flask import Flask

app = Flask(__name__)


@app.route("/ping", methods=['GET'])
def ping():
    return "pong"
```

`pong`을 response하는 api



##### API 실행하기

```
FLASK_APP=app.py FLASK_DEBUG=1 flask run
```

`FLASK_DEBUG`를 1로 지정하여 디버그 모드를 활성화하면 코드 수정되었을 때 flask 애플리케이션이 자동으로 재시작되어 수정된 코드가 반영된다.

별도 포트를 지정하지 않았으므로, 기본 포트인 5000번에서 실행된다.
