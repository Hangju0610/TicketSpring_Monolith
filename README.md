# TicketSpring-Monolith Project
## 대용량 트래픽 및 데이터 정합성 프로젝트

## 프로젝트 Step
### 1. 하네스 엔지니어링 적용기
- Claude.md, Agent.md 파일을 통한 하네스 엔지니어링 적용
- docs 작성을 통해 ADR, 아키텍처, PRD 문서화 진행
- rules, conventions, guidelines 문서화 진행
- **우선 빠르게 작성하고, TicketNest Migration을 진행하면서 점진적 발전을 해간다.**

### 2. TicketNest Migration 진행
- 기본적인 형태의 Application 구현
- 회원, 예매 도메인 기능 구현
- DB만을 통한 예매 진행
- Redis zset, Kafka를 점진적 적용하여 대용량 트래픽 및 데이터 정합성 문제 해결

### 3. Monolith 적용
- 계층별 아키텍처 형태 -> 도메인별 기능 구현
- Monolith를 적용하여 도메인 별 영역 경계 설정
