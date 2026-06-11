# Polymorph Status

[![Uptime CI](https://github.com/polym-team/polymorph-upptime/workflows/Uptime%20CI/badge.svg)](https://github.com/polym-team/polymorph-upptime/actions/workflows/uptime.yml)
[![Response Time CI](https://github.com/polym-team/polymorph-upptime/workflows/Response%20Time%20CI/badge.svg)](https://github.com/polym-team/polymorph-upptime/actions/workflows/response-time.yml)
[![Graphs CI](https://github.com/polym-team/polymorph-upptime/workflows/Graphs%20CI/badge.svg)](https://github.com/polym-team/polymorph-upptime/actions/workflows/graphs.yml)
[![Static Site CI](https://github.com/polym-team/polymorph-upptime/workflows/Static%20Site%20CI/badge.svg)](https://github.com/polym-team/polymorph-upptime/actions/workflows/site.yml)
[![Summary CI](https://github.com/polym-team/polymorph-upptime/workflows/Summary%20CI/badge.svg)](https://github.com/polym-team/polymorph-upptime/actions/workflows/summary.yml)

[Upptime](https://upptime.js.org)으로 운영되는 Polymorph 서비스 상태 페이지입니다.
GitHub Actions가 5분마다 각 엔드포인트를 체크하고, 결과는 이 저장소의 git history와 GitHub Pages 상태 페이지에 자동 반영됩니다.

## 상태 페이지

- [📈 Live Status](https://polym-team.github.io/polymorph-upptime)

## 동작 원리

- `.upptimerc.yml` — 모니터링 대상 사이트 목록 (편집 대상)
- `.github/workflows/uptime.yml` — 5분마다 cron으로 사이트 체크 → `history/`에 commit
- `.github/workflows/site.yml` — 상태 페이지 빌드 후 `gh-pages` 브랜치로 배포
- `.github/workflows/summary.yml` — 이 README의 상태 표 자동 갱신
- 다운 감지 시 → GitHub Issue 자동 생성, 복구 시 자동 close

## 운영 메모

- 모니터링 대상 추가/수정은 `.upptimerc.yml`만 편집하면 됩니다. push 시 `Setup CI`가 자동으로 워크플로우/페이지를 재구성합니다.
- 워크플로우가 commit/issue를 만들려면 저장소 Settings → Actions → "Read and write permissions" 활성화 필요.
- 상태 페이지는 Settings → Pages → Source를 `gh-pages` 브랜치로 설정.

<!--start: status pages-->
<!--end: status pages-->
