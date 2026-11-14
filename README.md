# LinCar (린카)

서로 다른 차로 함께 여행하는 사람들이 출발부터 도착까지 같은 여정을 느끼도록 돕는 차량 동행 앱입니다.

## 실행 방법

1. [제출용 Release](https://github.com/seojongwhi-ui/lincar-pleos-submission-2026/releases/tag/submission-2026-11-15)에서 APK를 내려받습니다. GitHub가 파일명 공백을 점으로 바꾸므로 Release에는 `Team.LinCar_LinCar_release.apk`로 표시됩니다.
2. Pleos Connect-S 에뮬레이터를 실행하고 APK를 설치합니다. 이 환경의 운전자 사용자 ID는 10입니다.
   ```powershell
   adb install --user 10 "Team.LinCar_LinCar_release.apk"
   ```
3. 에뮬레이터 앱 목록에서 **LinCar** 앱을 눌러 실행합니다. 하단 GNB에 직접 고정한 경우에는 그 아이콘으로도 실행할 수 있습니다.

기존 디버그 빌드가 설치되어 있으면 서명이 달라 업데이트 설치가 거부될 수 있습니다. 이 경우 `adb uninstall com.contest.travel.preview`로 제거한 뒤 제출 APK를 설치합니다. 제거하면 기존 앱의 로컬 데이터도 삭제됩니다.

## 테스트 환경 및 설정

- 확인 환경: Pleos Connect **2.1.0**, Connect-S, Android **14**, 화면 **2560 × 1440**.
- Vehicle Service **2.3.22**. 앱의 차량 연동 의존성: Vehicle SDK **2.3.2**, NaviHelper **3.0.5**, SpeechToText **3.3.1**, FusedLocation **1.1.3**.
- 에뮬레이터의 Virtual Console에서 주차·주행 상태와 차량 이동을 시연합니다. 주행 중 일부 조작은 안전 제한 화면으로 전환됩니다.
- 현재 확대 지도는 MapLibre와 OpenFreeMap 타일을 사용하며 인터넷 연결이 필요합니다. 네이버 지도 키나 GitHub Secret 없이 표시됩니다. 네이버 Maps SDK Client ID는 추후 네이버 지도로 전환할 때 루트의 추적되지 않는 `local.properties`에 `NAVER_MAP_CLIENT_ID`로 설정합니다. Directions 연결은 아직 구현되지 않았고, 해당 Client Secret은 APK에 넣지 않습니다.
- 투표 화면의 기본 안건과 선택 결과는 로컬 시연입니다. 현재 release APK에는 OpenAI API 키가 없으며, 음성에서 AI가 새 투표 안건을 자동 생성하는 기능은 동작하지 않습니다. 저장소의 `tools/openai_poll_bridge.py`와 **텍스트로 AI 투표 시험** 버튼은 추후 연동을 위한 실험용 코드입니다. API 키와 서명 키는 저장소에 포함하지 않습니다.
- 다른 차량의 위치·점수와 차량 간 공유는 현재 에뮬레이터 시연 데이터입니다. 마이크로 남긴 음성은 이 기기에서 녹음·저장·재생할 수 있지만 차량 간 실시간 서버 연결이나 음성 전송은 포함하지 않습니다.

## 소스 코드

앱은 `:travel-preview` 모듈입니다. `:app`은 Pleos 공식 Vehicle SDK 샘플을 유지한 모듈입니다. JDK 17과 Android SDK 35를 설치한 뒤 Windows에서는 다음 명령으로 디버그 빌드를 만들 수 있습니다.

```powershell
.\gradlew.bat :travel-preview:assembleDebug
```

이 제출 저장소는 개발 저장소 `demo` 브랜치의 커밋 `19ab254`를 바탕으로 만든 소스 스냅샷입니다.

## APK 위치

서명된 release APK는 용량이 100MB를 넘어 저장소 파일 대신 [GitHub Releases](https://github.com/seojongwhi-ui/lincar-pleos-submission-2026/releases/tag/submission-2026-11-15)에 첨부했습니다. 로컬 원본 파일명은 `Team LinCar_LinCar_release.apk`이고, GitHub 다운로드 파일명은 `Team.LinCar_LinCar_release.apk`입니다.
