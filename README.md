### 이용권 만료
```mermaid
sequenceDiagram
    participant Batch
    participant DB
    Batch->>DB: 이용권 조회
    activate DB
    DB->>Batch: 이용권 응답
    deactivate DB
    Batch->>DB: 만료 상태 변경
```

### 이용권 일괄 지급
```mermaid
sequenceDiagram
    actor User
    participant DB
    participant Batch
    User->>DB: 일괄 지급요청

    Batch->>DB: 일괄 지급 조회
    activate DB
    DB->>Batch: 일괄 지급 응답
    deactivate DB
    Batch->>DB: 해당 사용자 추가
```

### 수업 전 알림
```mermaid
sequenceDiagram
    participant Batch
    participant DB
    participant Messenger
    Batch->>DB: 예약 조회
    activate DB
    DB->>Batch: 예약 응답
    deactivate DB
    Batch->>DB: 알림 대상 추가
    
    Batch->>DB: 알림 대상 조회
    activate DB
    DB->>Batch: 알림 대상 응답
    deactivate DB
    Batch->>Messenger: 알림 요청
    activate Messenger
    Messenger->>Batch: 알림 응답
    deactivate Messenger
```

### 수업 후 이용권 차감
```mermaid
sequenceDiagram
    participant Batch
    participant DB
    Batch->>DB: 예약된 수업, 사용자 조회
    activate DB
    DB->>Batch: 예약된 수업, 사용자 응답
    deactivate DB
    Batch->>DB: 사용자 별 이용권 차감
```

## Environments
* OpenJDK 18.0.1
* Spring Boot 2.7.3
* Gradle
* MySQL (Docker)
* JPA
* lombok
* ModelMapper
 
