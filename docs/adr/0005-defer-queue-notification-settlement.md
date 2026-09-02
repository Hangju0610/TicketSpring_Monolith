# ADR-0005: Queue/Notification/Settlement 도메인 보류

## Status
Accepted

## Context
초기 도메인 목록(`User`, `Product`, `Payment`, `Booking`)을 검토하는 과정에서 다음 세 가지가 누락되어 있다는 지적이 있었다.

**질문 1 (Queue)**: README 로드맵에 "Redis Pub/Sub → Kafka Stream" 전환이 명시되어 있는데, 이는 보통 오픈런 티켓팅의 대기열/줄서기 기능에서 나오는 요구사항이다. 대기열 도메인을 1차 구현에 포함할지.

**질문 2 (Notification)**: C4 관계에 있는 "정보·결과 제공"이 API 응답만을 의미하는지, 예매 확정·대기열 순서 도래·결제 실패 같은 비동기 알림(이메일/SMS/푸시)까지 포함하는지. 알림 도메인을 지금 모델링에 포함할지.

**질문 3 (Settlement)**: 고객 결제(`Payment`)와 별개로, 주최자(`Provider`)에게 정산(수수료 차감, 정산 주기)해주는 기능을 `Payment` 안에 넣을지 별도 도메인으로 뺄지.

## Decision
세 도메인 모두 1차 구현 범위에서 제외하고 이후 단계로 미룬다.

- **Queue**: 1차 구현 이후, 대용량 트래픽 대응(Redis Pub/Sub → Kafka Stream 전환)과 함께 설계한다.
- **Notification**: 1차 범위는 결제·예매 기능에 집중하고, 알림은 이후 추가한다.
- **Settlement**: `Payment`는 "고객 결제/환불/PG 연동"으로 좁게 유지하고, 정산은 배치성이며 정합성 요구가 결제와 다르므로 별도 도메인으로 나중에 설계한다.

## Consequences
- 1차 구현 스코프가 `User`, `Auth`, `Provider`, `Product`, `Inventory`, `Booking`, `Payment`로 명확해진다.
- 세 도메인의 필요성 자체는 인지하고 있으므로, 이후 로드맵([도메인 모델](../architecture/domain-model.md) 문서의 "보류" 표)에 반영해두었다.
