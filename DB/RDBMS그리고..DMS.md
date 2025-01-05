# DBMS 와 RDBMS의 개념

### 1️⃣ DBMS란?
<hr/>

- DBMS는 DataBase Management System의 약자, 데이터베이스를 관리하는 시스템
- 사용자와 DB사이에서 사용자의 요구에 따라 데이터를 생성, DB를 관리해주는 소프트웨어
- DBMS는 데이터를 계층 또는 탐색 형식으로 저장, 파일 시스템을 사용해 저장하며, 따라서 테이블 간에는 아무런 관계 X
- 데이터에 대한 많은 보안을 제공 X 정규화를 수행 X -> 데이터는 높은 중복성 ㄱㄴ
- Sybase, dbase 및 Microsoft Access 등

### 2️⃣ RDB(Relational DataBase)란?

<hr/>

- RDB는 관계형 데이터 모델에 기초를 둔 데이터 베이스
- 모든 데이터를 2차원의 테이블 형태로 표현한다.


### 3️⃣ RDBMS란?

<hr/>

- RDB를 생성하고 수정하고 관리할 수 있는 소프트웨어
- RDBMS는 Relational DataBase Management System의 약자로 관계형 모델을 기반으로 하는 DBMS 유형
- RDBMS의 테이블은 서로 연관되어 있어 일반 DBMS보다 효율적으로 데이터를 저장, 구성 및 관리 ㄱㄴ
- 정규화를 통해 데이터의 중복성을 최소화, 트랜잭션을 수행하는 것이 더 쉽다
- 데이터의 원자성, 일관성, 격리 및 내구성을 유지, 데이터 무결성을 높임
- MSSQL, MySQL, Oracle

> ※ DBMS와 RDBMS의 관계는? 
<br/> RDBMS는 DBMS의 한 유형이다

### 4️⃣ 관계형 모델이란?

<hr/>

관계형 모델은 실제 세계의 데이터를 '관계' 라는 개념을 사용해서 표현한 데이터 모델
관계형 모델을 이해하는데 가장 중요한 개념은 Relation(관계)

#### 왜 관계형 모델이 중요한가?
- SQL은 관계형 모델을 기반으로 한 질의 언어이지만, 관계형 모델을 충실하게 재현 X. 관계형 모델을 모르고 SQL을 쓰면 제대로 사용할 수 없고 비효율적인 쿼리를 사용하게
- 관계형 모델에 따른 연산이 가장 good. 복잡하고 이상한 SQL문은 가독성도 나쁘고 버그의 원인 ㄱㄴ
- DB 응용 프로그램을 유지보수 할 때도 관계형 모델에 관해서 이해하는 것이 중요

#### Relaction이란?
- Relation은 Heading과 Body로 구성
- Heading은 Attribute가 n개 모인 집합, 이 Attribute는 이름과 데이터 형으로
- Body는 속성값의 집합인 tuple의 집합
- 튜플과 속성은 SQL에서는 row, column이라고..
