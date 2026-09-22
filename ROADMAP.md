# OAS Roadmap

조직 프로필의 로드맵을 구현 단위로 관리한다. 완료 여부는 실차 승인과 분리하며, DBC만으로
확인된 값은 read-only raw diagnostics에 머문다.

## Vehicle data

- Genesis G80 DBC raw catalog: body, seatbelt, wiper, climate, diagnostics
- Raw signal의 HMI Diagnostics 조회
- 실차 CAN capture 기반 signal enum 승인
- 승인된 신호의 canonical `VehicleState` 승격
- 익명화 fixture와 decoder/gateway/HMI 회귀 E2E

## Target hardware

- Radxa Linux image와 SocketCAN interface 구성
- gateway/runtime/HMI systemd supervisor 배포
- kiosk/WebView 부팅·절전·gateway 재연결 검증
- 실제 차량에서 테마·기어·미디어 안전 정책 검증

## Safety

- read-only와 command 권한의 프로세스·API 분리
- 차량 제어 명령별 위험 분석과 fail-safe 설계
- 실차 검증이 끝나기 전 조향·제동·구동 제어를 배포하지 않음
