# ADR-0001: Provider 도메인 분리

## Status
Accepted

## Context
[System Context](../architecture/c4-context.md)에서 고객과 관리자(주최자)는 서로 다른 책임(조회·예매 vs 공연·좌석·일정 등록·관리)을 가진 별개의 Person으로 구분되어 있었다.

**질문**: 관리자를 `User` 도메인 안에 role 플래그로 넣을지, 별도 도메인으로 분리할지.

## Decision
별도 도메인으로 분리한다.

권한/책임이 근본적으로 다른 액터를 하나의 애그리거트에 role로 욱여넣으면 권한 체크 로직이 지저분해진다는 이유였다.

이름은 최초 `Organizer`/`Admin`으로 제안했으나, [ADR-0004](./0004-keep-generic-product-naming.md)에서 `Product`를 범용 명칭으로 유지하기로 하면서 이름 체계를 맞추기 위해 최종적으로 `Provider`로 명명했다 (콘서트 주최자 전용 뉘앙스인 `Organizer`는 향후 숙소 호스트·항공사가 붙을 때 맞지 않는다는 이유).

## Consequences
- 현재는 공연 주최자만 다루지만, 향후 숙박·항공 등 다른 판매자 유형도 `Provider` 도메인으로 편입 가능.
- `Provider`의 인증은 [ADR-0003](./0003-separate-and-unify-auth-domain.md)에서 `User`와 동일한 `Auth` 도메인을 공유하기로 결정.
