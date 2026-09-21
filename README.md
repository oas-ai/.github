# OAS GitHub Organization 설정

이 저장소는 `oas-ai` Organization 전체에 적용되는 공통 GitHub 정책, Contributor Guide, Issue/PR Template, 재사용 가능한 CI Workflow 및 Workflow Template을 관리합니다.

상세한 설계·Engineering Standard는 향후 [oas-ai/docs](https://github.com/oas-ai/docs) 저장소에서 관리합니다.

## 구성

- `profile/`: Organization Profile
- `.github/ISSUE_TEMPLATE/`: 공통 Issue Form
- `.github/workflows/`: 다른 저장소가 호출하는 재사용 Workflow
- `workflow-templates/`: 새 저장소에서 사용할 얇은 CI wrapper

각 코드 저장소의 LICENSE와 실제 CI 적용 여부는 해당 저장소에서 별도로 관리합니다.
