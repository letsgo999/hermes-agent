# Daily Log

## 2026-09-29

- Hermes Desktop 실행 경로 `apps/desktop/release/win-unpacked`가 사라지고 검증된 `win-unpacked.bak`만 남은 상태를 확인했다.
- 공식 설치기는 기존 Git 작업트리의 로컬 변경과 예약 이름 파일 `NUL` 때문에 자동 스태시 단계에서 실패하는 것으로 진단했다.
- 전체 업데이트나 사용자 상태 백업 없이, 검증된 `win-unpacked.bak`를 정상 경로로 복사하고 시작 메뉴·바탕화면 바로가기를 복구했다.
- `Hermes.exe` 창과 Electron 하위 프로세스, Desktop 백엔드 `127.0.0.1:9203`, 웹 UI 응답, 복구 전후 SHA-256 일치를 확인했다.
- 원본 `win-unpacked.bak`, 설정, 세션, DB 및 기존 Git 변경은 보존했다.

## 2026-10-09

- Desktop 업데이트가 `state.db` 긴급 스냅샷의 60초 제한을 초과해 반복 중단된 원인을 확인했다.
- `D:\HermesUpdateBackups\HERMES-UPD-20261009-01`에 선별 연속성 백업 4,388개 파일(3,669,110,972바이트)을 만들고 해시 매니페스트와 SQLite 11개 DB의 `PRAGMA quick_check`를 검증했다.
- 로컬 커밋은 `refs/hermes-update-backups/diverged-main-20261009-013521-988f1f6e64c1`, 미커밋 변경은 `hermes-update-autostash-20261009-013451`에 보존한 뒤 원격 `main`의 `1e0c7730d791`로 업데이트했다.
- Hermes Agent를 `v0.21.5+3837.g988f1f6.dirty`에서 `v0.21.6+187.g1e0c773.dirty`로 업데이트하고 설정 형식을 v46에서 v50으로 마이그레이션했다.
- Desktop, API, Session Hub, 원격 경계, Tailscale 및 대시보드 응답과 Telegram polling 및 5개 프로필 연결을 확인했다.
- Windows 예약 작업 정의 갱신은 권한 거부로 적용되지 않아 기존 등록을 유지했으며, 권한 설정은 변경하지 않았다.
- 실패한 과거 `state.db.pre-update-emergency-*.partial*` 파일과 유효한 `.bak` 스냅샷은 삭제하지 않고 보존했다.
