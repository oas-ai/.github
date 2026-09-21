# OAS 기여 가이드

OAS 기여에 관심을 가져주셔서 감사합니다. 문서, 테스트, 버그 수정, 차량 지원과 기능 제안은 모두 소중한 기여입니다.

## 기본 원칙

- 문서, Issue, Pull Request 설명 및 코드 주석은 한국어로 작성합니다. 식별자·파일명·API field는 영어를 사용합니다.
- 각 저장소는 독립적으로 Semantic Versioning을 사용합니다. 초기 개발 버전은 `0.x.x`입니다.
- 새 소프트웨어는 Apache License 2.0 정책을 따르되, LICENSE 파일은 각 코드 저장소에서 관리합니다.

## 개발 흐름

기본 branch는 `main`이며 `develop` branch는 사용하지 않습니다. `main`에 직접 push하지 말고 다음 흐름을 사용합니다.

```
feature branch → Pull Request → CI → Review → Squash Merge → main
```

branch는 `feat/`, `fix/`, `refactor/`, `docs/`, `test/`, `chore/` prefix를 사용합니다. 예: `feat/genesis-rg3`, `fix/rg3-wheel-speed`.

Commit은 Conventional Commits 형식을 사용합니다.

```
<type>(<scope>): <description>
```

허용 type은 `feat`, `fix`, `docs`, `test`, `refactor`, `perf`, `build`, `ci`, `chore`입니다. description은 한국어로 작성할 수 있습니다.

## Pull Request

1. 관련 Issue가 있으면 연결합니다.
2. 변경에 맞는 테스트를 추가하거나 갱신하고 로컬에서 통과시킵니다.
3. Formatter, linter, type check와 CI를 통과시킵니다.
4. Public API, 문서, 버전 영향과 Breaking Change 여부를 검토합니다.
5. Review 후 Squash Merge를 기본으로 사용합니다.

Breaking Change는 영향 범위, migration 방법, 버전 변경 계획을 Pull Request에 명확히 기록합니다.

## Vehicle 및 Safety 변경

차량 상태 읽기, CAN/CAN FD, Gateway, Vehicle Control 또는 Safety에 영향을 주는 변경은 대상 Platform과 capability를 명시하고 안전 영향을 검토해야 합니다. Application이 Raw CAN TX를 직접 수행하는 구조를 추가하지 마세요. 기본 제어 경로는 `Application → VehicleControl → SafetyModel → Manufacturer Controller → CAN TX`입니다.

Platform ID는 `MANUFACTURER_PLATFORM` 형식(예: `GENESIS_RG3`)을 사용하며, 연식·트림·ADAS 옵션은 capability metadata로 관리합니다. 내부 계산은 SI 단위를 기본으로 하고, OEM CAN signal은 DBC, parser, manufacturer adapter를 거쳐 Canonical Model로 변환합니다.

상세 Coding Convention은 향후 `oas-ai/docs/engineering/`에서 관리합니다.
