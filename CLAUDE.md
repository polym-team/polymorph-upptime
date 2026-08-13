# CLAUDE.md — polymorph-upptime

[Upptime](https://upptime.js.org) 기반 상태 페이지. GitHub Actions 가 5분마다 `.upptimerc.yml` 의
`sites` 를 체크해 `history/` 에 커밋하고, `gh-pages` 브랜치로 상태 페이지를 배포합니다.
클러스터·Cloudflare 가 죽어도 GitHub Pages 가 살아 있으면 이 페이지는 동작합니다 — 그게 이
저장소를 클러스터 밖에 두는 이유입니다.

- 상태 페이지: https://polym-team.github.io/polymorph-upptime/
- 배지·요약 JSON: `api/<슬러그>/uptime.json` (main 브랜치에 자동 커밋됨)
- 슬러그는 `sites[].name` 을 슬러그화한 값입니다 → **이름을 바꾸면 히스토리 경로가 끊깁니다.**

## `sites` 의 앱 블록은 생성물입니다 (직접 편집 금지)

`polymorph-app` 의 각 앱은 `apps/<app>/polymorph.config.json` 에서 자기 감시 여부를 선언합니다
(`uptime`, 표시 이름은 `uptimeName`). 그 설정이 감시 대상의 정본이고, 이 파일의 다음 마커 사이는
거기서 생성됩니다:

```yaml
sites:
  # >>> polymorph-app 앱 (생성됨 — pnpm sync:upptime)
  ...          # ← 이 안은 손으로 고치지 말 것
  # <<< polymorph-app 앱
  - name: ArgoCD   # ← 마커 밖은 수동 관리 영역 (앱이 아닌 대상)
```

갱신 절차:

```bash
cd ../polymorph-app
pnpm sync:upptime            # 이 저장소의 .upptimerc.yml 앱 블록을 갱신
pnpm sync:upptime -- --check # 동기화가 필요한지만 검사

cd ../polymorph-upptime      # 변경분을 여기서 커밋·푸시
```

앱 목록을 이 파일에서 직접 고치면 다음 동기화 때 덮어써집니다. **감시 대상을 바꾸려면
`polymorph-app` 쪽 앱 설정을 고치세요.**

## 마커 밖(수동 관리) 대상

앱이 아니라 `polymorph-app` 설정에 없는 것들입니다 — 여기서 직접 관리합니다:

| 대상 | 비고 |
|---|---|
| `Official Website (www)` | `www` 리다이렉트 확인용 |
| `ArgoCD` | 인증 필요 → `expectedStatusCodes` 로 200/302/401 허용 |
| `Verdaccio (npm)` | 동일 |

## 그 외 설정

`status-website`(제목·소개문·네비), `assignees`(인시던트 담당), `i18n`(한국어 라벨)은 이 저장소에서
직접 관리합니다. 상세 옵션은 [Upptime 문서](https://upptime.js.org/docs/configuration) 참조.
