# Results

## 1. 실험 요약
- 저장소: app-blackhole-observatory
- 커밋 해시: 9a343ed
- 실험 일시: 2026-05-20T15:33:54.420Z -> 2026-05-20T15:34:01.881Z
- 담당자: ai-webgpu-lab
- 실험 유형: `integration`
- 상태: `success`

## 2. 질문
- 하나의 앱 surface에서 blackhole preset review와 renderer selection을 함께 검증할 수 있는가
- graphics 성능 지표와 blackhole observatory telemetry가 같은 앱 결과 문서에 함께 남는가
- 실제 renderer/physics/provider 연결 전 blackhole app protocol을 고정할 수 있는가

## 3. 실행 환경
### 브라우저
- 이름: Chrome
- 버전: 147.0.7727.15

### 운영체제
- OS: Linux
- 버전: unknown

### 디바이스
- 장치명: Linux x86_64
- device class: `desktop-high`
- CPU: 16 threads
- 메모리: 32 GB
- 전원 상태: `unknown`

### GPU / 실행 모드
- adapter: navigator.gpu available
- backend: `browser-fixture`
- fallback triggered: `false`
- worker mode: `hybrid`
- cache state: `warm`
- required features: ["shader-f16","timestamp-query"]
- limits snapshot: {"maxTextureDimension2D":8192,"maxBindGroups":4}

## 4. 워크로드 정의
- 시나리오 이름: Blackhole Observatory
- 입력 프로필: widefield-balanced
- 데이터 크기: preset=m87-horizon-v1; winner=kerr-science-engine; observatory_score=0.928; checksum=0.98241; automation=playwright-chromium, preset=m87-horizon-v1; winner=kerr-science-engine; observatory_score=0.928; checksum=0.98241; realAdapter=fallback(manifest fetch failed for https://ai-webgpu-lab.github.io/app-blackhole-observatory/manifests/observatory-v1.json); automation=playwright-chromium
- dataset: -
- model_id 또는 renderer: kerr-science-engine
- 양자화/정밀도: -
- resolution: -
- context_tokens: -
- output_tokens: -

## 5. 측정 지표
### 공통
- time_to_interactive_ms: 745.8 ~ 810.8 ms
- init_ms: 53 ms
- success_rate: 1
- peak_memory_note: 32 GB reported by browser
- error_type: -

### Graphics / Blackhole
- avg_fps: 58.9
- p95_frametime_ms: 20.7 ms
- scene_load_ms: 53 ms
- ray_steps: 128
- photon_ring_radius_px: 96 px
- lensing_arc_pct: 0.87
- geodesic_checksum: 0.9824
- renderer_consensus_score: 0.93
- science_alignment_score: 0.99

## 6. 결과 표
| Run | Scenario | Backend | Cache | Mean | P95 | Notes |
|---|---|---:|---:|---:|---:|---|
| 1 | Blackhole Observatory | browser-fixture | warm | 58.9 | 20.7 | renderer=kerr-science-engine, science=0.99, score=0.93 |
| 2 | Blackhole Observatory | browser-fixture | warm | 58.9 | 20.7 | renderer=kerr-science-engine, science=0.99, score=0.93 |

## 7. 관찰
- blackhole observatory demo는 avg_fps=58.9, renderer_consensus_score=0.93로 기록됐다.
- 앱 surface가 preset telemetry, photon ring metric, renderer selection 결과를 같은 결과 문서에 남긴다.
- playwright-chromium로 수집된 automation baseline이며 headless=true, browser=Chromium 147.0.7727.15.
- 실제 runtime/model/renderer 교체 전 deterministic harness 결과이므로, 절대 성능보다 보고 경로와 재현성 확인에 우선 의미가 있다.

## 8. Real Adapter vs Deterministic
- adapter: real=not-connected (no real adapter registered — falling back to deterministic), deterministic=deterministic-observatory
- avg_fps: real=58.9, deterministic=58.9, delta=0
- frame_ms: real=20.7 ms, deterministic=20.7 ms, delta=0 ms

## 9. 결론
- blackhole observatory demo가 generic probe를 벗어나 integrated preset-to-renderer surface와 첫 raw result를 갖게 됐다.
- 다음 단계는 deterministic preset/leaderboard 대신 실제 three.js, Kerr engine, raw WebGPU renderer 및 asset loading path를 같은 app protocol에 연결하는 것이다.
- 내부 데모 승격을 위해 camera controls, preset gallery, annotation overlays, capture/export UX 메모를 추가로 기록해야 한다.

## 10. 첨부
- 스크린샷: ./reports/screenshots/01-blackhole-observatory.png, ./reports/screenshots/02-blackhole-observatory-real-surface.png
- 로그 파일: ./reports/logs/01-blackhole-observatory.log, ./reports/logs/02-blackhole-observatory-real-surface.log
- raw json: ./reports/raw/01-blackhole-observatory.json, ./reports/raw/02-blackhole-observatory-real-surface.json
- 배포 URL: https://ai-webgpu-lab.github.io/app-blackhole-observatory/
- 관련 이슈/PR: -
