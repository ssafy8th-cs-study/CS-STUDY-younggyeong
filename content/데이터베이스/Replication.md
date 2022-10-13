# Replication
두개 이상의 DBMS 시스템을 마스터/슬레이브 로 나누어 동일한 데이터를 저장하는 방식이다. 즉 DB 이중화 혹은 복제라고 한다.

<br>

![image](https://user-images.githubusercontent.com/54929520/195526650-7ae3fec2-a50d-44c3-bd23-61c6e4cc7f2e.png)  
처음에는 하나의 서버와 하나의 DB만을 구성하게 된다.

하지만 사용자가 계속해서 증가하면 DB는 쿼리를 처리하기에 힘든 상황이 올때 Replication을 사용한다.

<br>

![image](https://user-images.githubusercontent.com/54929520/195526889-addde606-b476-4dd8-a33b-69805a05bdc1.png)

슬레이브 DB는 쿼리의 대부분을 차지하는 Select 연산만을 수행하게 하고 마스터 DB에는 데이터의 수정사항만 반영(Insert, Update, Delete)하고 Replication하여 슬레이브 DB에 데이터를 복사한다.

## Replication 방법
### 로그기반 복제
웹 서버로부터 데이터 등록/수정/삭제 요청 시 바이너리 로그를 생성하여 SLAVE 서버로 비동기적으로 전송한다.
SLAVE DB는 MASTER DB로부터 전달받은 바이너리 로그를 데이터로 반영한다.

1. Statement Based : sql문장을 그대로 복사하여 실행한다.
2. Row Based : sql에 따라 변경된 라인만 기록하는 방식이다.
3. Mixed : 기본적으로 Statement Based로 진행하며 필요에 따라 Row Based 방식을 사용한다.

![image](https://user-images.githubusercontent.com/54929520/195529882-9c408655-52cb-408c-a411-aca6856af0dc.png)
1. 클라이언트(Application)에서 Commit 을 수행한다.
2. Connection Thead 는 스토리지 엔진에게 해당 트랜잭션에 대한 Prepare(Commit 준비)를 수행한다.
3. Commit 을 수행하기 전에 먼저 Binary Log 에 변경사항을 기록한다.
스토리지 엔진에게 트랜잭션 Commit 을 수행한다.
4. Master Thread 는 시간에 구애받지 않고(비동기적으로) Binary Log 를 읽어서 Slave 로 전송한다.
5. Slave 의 I/O Thread 는 Master 로부터 수신한 변경 데이터를 Relay Log 에 기록한다. (기록하는 방식은 Master 의 Binary Log 와 동일하다)
6. Slave 의 SQL Thread 는 Relay Log 에 기록된 변경 데이터를 읽어서 스토리지 엔진에 적용한다.


## 단점 
Slave DB는 비동기방식으로 Master DB와 동기화하기 때문에 일관성 있는 결과를 얻지 못할 수 있음.
Master DB가 동작하지 않으면 복구 및 대처가 까다롭다.
