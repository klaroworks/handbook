# Klaro Forge는 어떻게 작동하나

Forge는 코드 생성기가 아니라 AI 산출물의 납품을 통제하는 곳입니다. 레거시 전환을 에이전트가 수행하고, 반영 전에 검토·테스트·승인 기록을 남깁니다.

<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/klaroworks/handbook/main/assets/forge-dark.png">
    <img src="https://raw.githubusercontent.com/klaroworks/handbook/main/assets/forge-light.png" alt="분석 → 전환 → Evidence → Approval → 납품" width="100%">
  </picture>
</div>

## "컴파일 성공"으로 끝내지 않는다

Evidence 엔진이 컴파일과 정적 점검, SQL Diff, 기준 입출력 비교를 설명 가능한 근거로 묶습니다. 빌드가 통과했다는 사실만으로는 정확성을 보장하지 못하기 때문입니다.

## 승인 리스크를 구조로 줄인다

TA·AA·QA·PM의 승인 이력을 산출물과 함께 남깁니다. 규제 산업의 구매 조건인 "누가 어떤 근거로 승인했는가"에 답하기 위해서입니다.

## 사람은 결정, AI는 수행

에이전트의 실행 범위를 두 축으로 정합니다. 자율성(supervised · bounded · autonomous)과 검토 정책(always · risk_based · evidence_gated)입니다. 변경 요청 피드백은 이전 출력을 덮어쓰지 않고 이어 붙입니다(append-only). 수동 작업도 같은 승인 게이트를 지나므로, 원장과 승인 흐름이 한결같습니다.

## LLM을 직접 부르지 않는다

Forge 본체는 모델을 직접 호출하지 않고 에이전트 런타임에 위임합니다. 계획은 구조화 출력, 실행은 저장소 도구, 검증은 결정론 게이트로 나눕니다. 모델은 교체 가능한 부품으로 둡니다.


## 제품 사양

| 항목 | 내용 |
|---|---|
| **자동화 대상** | 레거시 전환(프레임워크·언어 현대화), EOS 대응, 기간계 마이그레이션 |
| **핵심 엔진** | 전환 AI 에이전트(분석·변환·검증) · 소스 복잡도 지도 · 패턴 목록화·후보 생성·규칙 보정 루프 |
| **검증 방식** | Evidence 엔진 — 컴파일 · 정적 점검 · SQL Diff · 기준 입출력 비교 |
| **승인 체계** | TA·AA·QA·PM 단계별 승인 이력, 산출물과 함께 보존 |
| **산출물** | 전환 코드 · 검증 근거 리포트 · 승인 준비 보고서 |
| **배포 형태** | 고객 환경 내 실행 — 소스가 외부로 나가지 않는 구조 |
| **거버넌스** | 전 과정 감사 로그 · 승인 워크플로 (Hub 공통 거버넌스 스택) |
| **연동** | SI 파트너 납품 도구 라이선스(연간 계약형) |
