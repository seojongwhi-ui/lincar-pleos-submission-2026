# LinCar 제출용 안내

LinCar(린카)는 서로 다른 차로 이동하는 일행이 하나의 여행을 함께하는 느낌을 전하는 차량 동행 앱입니다.

- 실행 방법, 테스트 환경, SDK 버전과 기능 범위: [README.md](README.md)
- 서명된 제출 APK: [GitHub Release](https://github.com/seojongwhi-ui/lincar-pleos-submission-2026/releases/tag/submission-2026-11-15)의 `Team.LinCar_LinCar_release.apk` (로컬 원본: `Team LinCar_LinCar_release.apk`)
- 앱 소스: `:travel-preview` 모듈. 개발 저장소 `demo`의 `19ab254`를 바탕으로 앱 표시 이름을 변경했습니다.
- `:app` 모듈은 Pleos Vehicle SDK 공식 샘플을 보존합니다.

현재 확대 지도는 MapLibre/OpenFreeMap을 사용합니다. 내 차 상태는 Pleos 에뮬레이터의 SDK 신호를 읽고, 다른 차량의 위치와 점수·차량 간 통신·기본 투표는 로컬 시연입니다. OpenAI가 음성에서 투표 안건을 자동 생성하는 기능은 제출 APK에서 동작하지 않습니다.
