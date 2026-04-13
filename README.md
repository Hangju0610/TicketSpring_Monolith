# TicketSpring-Monolith Project
## 대용량 트래픽 및 데이터 정합성 프로젝트

## 프로젝트 Step
### 1. TicketNest Migration 진행
- 기본적인 형태의 Application 구현
- 회원, 예매 도메인 기능 구현
- DB만을 통한 예매 진행

### 2. Monolith 적용
- 도메인 별 적용 진행
- 논리 별 경계를 적용

### 3. 기존 Redis Pub/Sub 구조에서 Kafka Stream 구조로 변경
- 대용량 트래픽에 맞도록 기능 구현
