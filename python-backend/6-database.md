# 데이터베이스
## 데이터베이스 시스템

> 데이터를 저장 및 보존하는 시스템

<br>

### 관계형 데이터베이스

`관계형 데이터` 모델에 기초를 둔 데이터베이스 시스템

​	-> `관계형 데이터` : 데이터들이 서로 상호 관련성을 가진 형태로 표현한 데이터

모든 데이터들은 2차원 테이블로 표현

#### 상호 관련성 종류

* one to one / one to many / many to many

#### 정규화 ⭐️

* 동일한 정보들이 불필요하게 중복되어 저장되는 것 방지
* 잘못된 데이터가 저장될 가능성 낮춰줌

#### 트랜잭션

* 일련의 작업들이 마치 하나의 작업처럼 취급 -> 모두 다 성공 or 모두 다 실패
* **ACID** : 트랜잭션 기능을 보장하기 위한 성질
  * **A**tomicity (원자성)
  * **C**onsistemcy (일관성)
  * **I**solation (고립성)
  * **D**urability (지속성)

<br>

### 비관계형 데이터베이스 (NoSQL)

데이터들을 저장하기 전에 정의할 필요 X

스키마나 테이블들의 관계를 미리 구현하지 않고, 데이터가 들어오는 그대로 그냥 저장

Ex) MongoDB, Redis, Cassandra...

<br>

### 관계형 VS 비관계형

* 관계형 데이터베이스 시스템
  * 👍
    * 데이터를 더 효율적이고 체계적으로 저장, 관리
    * 미리 저장할 데이터들의 구조(테이블 스키마)를 정의 -> 데이터 완전성 보장
    * 트랜젝션 기능 제공
  * 👎
    * 테이블 미리 정의 -> 테이블 구조 변화 등에 덜 유연
    * 확장, 분산 저장 어려움 (스케일 업 필요)
* 비관계형 데이턴베이스 시스템
  * 👍
    * 데이터 구조의 변화에 유연
    * 확장 용이
    * 방대한 양의 데이터 저장하는데 유리
  * 👎
    * 데이터 완전성 덜 보장
    * 트랜잭션이 안되거나, 불안정

<br>

## MySQL 설치

참고 : [Homebrew를 이용하여 MYSQL 설치 - MAC](https://devyurim.github.io/data%20base/mysql/2018/08/13/mysql-1.html)

1. Homebrew로 mysql 설치

```
brew install mysql
brew install mysql-client
```

2. root 사용자 비밀번호 설정

```
mysql_secure_installation
```

3. 실행 테스트

```
mysql.server start

mysql.server status

mysql.server stop
```

<br>

## 파이썬 코드 DB 연결

SQLAlchemy 설치

```
pip install sqlalchemy
```

DBAPI (MySQL-Connector) 설치

```
pip install mysql-connector-python
```



[DB 연결 테스트 코드](https://github.com/s2zan/miniter/blob/master/dbtest.py)


