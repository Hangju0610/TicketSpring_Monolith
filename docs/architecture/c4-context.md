# C4 Model - Level 1: System Context

TicketSpring의 최상위 System Context 다이어그램입니다. 고객, 관리자(주최자), 결제 대행사(PG)와 TicketSpring 시스템 간의 관계를 나타냅니다.

```mermaid
flowchart TB
    classDef person fill:#08427b,stroke:#052e51,color:#fff
    classDef system fill:#1168bd,stroke:#0b4884,color:#fff,font-weight:bold
    classDef external fill:#8a8a8a,stroke:#666666,color:#fff

    customer["<b>고객</b><br/>[Person]<br/>공연 정보를 조회하고<br/>티켓을 예매하는 사용자"]:::person
    admin["<b>관리자 (주최자)</b><br/>[Person]<br/>공연 정보와 좌석·일정을<br/>등록·관리하는 운영자"]:::person
    ticketSpring["<b>TicketSpring</b><br/>[Software System]<br/>공연 정보 제공, 좌석 예매<br/>및 결제를 처리하는 시스템"]:::system
    pg["<b>결제 대행사 (PG)</b><br/>[External System]<br/>카드/간편결제 등 실제<br/>결제 승인을 처리하는 시스템"]:::external

    customer <-->|"공연 조회·예매 요청 / 공연 정보·예매 결과 제공"| ticketSpring
    admin -->|"공연·좌석·일정 등록/관리"| ticketSpring
    ticketSpring <-->|"결제 요청 / 승인·실패 결과 통지"| pg
```

## 구성 요소

| 구분 | 이름 | 책임 |
|---|---|---|
| Person | 고객 | 공연 정보를 조회한다 / 티켓을 예약한다 (좌석 정보, 날짜 등) |
| Person | 관리자 (주최자) | 공연 정보를 등록한다 / 좌석·일정을 관리한다 |
| Software System | TicketSpring | 공연 정보를 조회해서 고객에게 제공한다 / 티켓 예매 및 결제 진행 |
| External System | 결제 대행사 (PG) | 결제 승인을 처리한다 / 결제 결과를 TicketSpring에 통지한다 |
