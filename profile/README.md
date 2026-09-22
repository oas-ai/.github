# OAS / oas.ai

OAS(Open Automotive Software Platform)는 차량 데이터 접근부터 안전한 차량 제어까지를 위한 오픈 차량 소프트웨어 플랫폼입니다.

OAS는 Hardware, Transport, Protocol/CAN, Vehicle Adapter, Canonical Vehicle Model, Safety, Application 계층을 분리하는 구조를 지향합니다. 초기 Reference Vehicle은 **Hyundai Palisade 2020 (`HYUNDAI_PALISADE`)**입니다.

현재는 read-only 차량 데이터 경로를 우선 개발합니다. opendbc 기반 Hyundai Palisade 2020 DBC subset에서
속도·가속도·조향·제동·기어·휠 속도·SCC·저빔 상태를 protobuf stream으로 전달하며, HMI는
이 저빔 상태로 자동 라이트/다크 테마를 전환합니다. 값 의미가 실차에서 확인되지 않은 신호는
`raw_signals` diagnostics stream으로만 보존하고 차량 제어에는 사용하지 않습니다.

## 주요 저장소

- [ohayessOS](https://github.com/oas-ai/ohayessOS): 차량 소프트웨어
- [dbc](https://github.com/oas-ai/dbc): 차량 CAN database 정의
- [can](https://github.com/oas-ai/can): CAN 처리 라이브러리
- [car](https://github.com/oas-ai/car): 차량 Adapter와 Canonical Model
- [gateway](https://github.com/oas-ai/gateway): Gateway 및 Hardware 연동
- [simulator](https://github.com/oas-ai/simulator): 차량·CAN 시뮬레이션
- [sdk](https://github.com/oas-ai/sdk): OAS SDK
- [docs](https://github.com/oas-ai/docs): 설계 및 개발 문서

프로젝트는 초기 개발 단계입니다. API, 지원 차량, Safety 및 Vehicle Control 기능은 개발 과정에서 변경될 수 있습니다.

## 로드맵

1. **Palisade 2020 DBC catalog 확장** — 도어·안전벨트·와이퍼·공조·진단 신호를 raw diagnostics로
   추가하고, source revision과 라이선스 provenance를 고정합니다.
2. **Diagnostics HMI** — raw DBC signal의 최신값·관측 시각·bus를 HMI Diagnostics에서
   조회할 수 있게 합니다.
3. **실차 신호 승인** — Canable 수신 로그로 Palisade 2020 연식·시장·트림을 확인하고 enum 의미를
   검증한 신호만 canonical state로 승격합니다.
4. **실차 Linux 통합** — Radxa에서 SocketCAN, systemd supervisor, kiosk/WebView, 부팅·절전·재연결을 검증합니다.
5. **회귀 데이터** — 익명화한 최소 CAN fixture를 decoder·gateway·runtime·HMI E2E에 추가합니다.
6. **차량 제어 준비** — 제어 API는 Safety boundary, 위험 분석, 권한 분리, 실차 검증이 완료된
   뒤에만 별도 단계로 설계합니다. 조향·제동·구동 제어는 현재 범위에 포함하지 않습니다.

구성요소별 상세 상태와 실행 방법은 [docs](https://github.com/oas-ai/docs)에서 관리합니다.
