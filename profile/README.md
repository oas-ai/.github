# OAS / oas.ai

OAS(Open Automotive Software Platform)는 차량 데이터 접근부터 안전한 차량 제어까지를 위한 오픈 차량 소프트웨어 플랫폼입니다.

OAS는 Hardware, Transport, Protocol/CAN, Vehicle Adapter, Canonical Vehicle Model, Safety, Application 계층을 분리하는 구조를 지향합니다. 초기 Reference Vehicle은 **Genesis G80 (RG3, `GENESIS_RG3`)**입니다.

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
