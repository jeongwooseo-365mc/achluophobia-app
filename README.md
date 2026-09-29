# 아클루오포비아 앱

게임 사이트(https://nee.n-e.kr/school/client/)를 여는 앱 껍데기입니다.

- **Windows:** Tauri (WebView2)
- **Android:** Capacitor

게임 본체는 사이트에 있어서, 게임을 고쳐도 앱을 다시 빌드할 필요가 없습니다.

## 게임 파일을 앱 안에 넣지 않는 이유

InfinityFree 서버는 브라우저가 아닌 요청에 보안 확인 페이지를 돌려줍니다. 그래서 파일을 앱에 넣으면 로그인과 저장 API를 쓸 수 없습니다. 앱이 사이트를 직접 열면 브라우저와 똑같이 동작합니다.

## 빌드

GitHub에 푸시하면 Actions가 자동으로 빌드합니다. 워크플로 파일은 `.github/workflows/build.yml`입니다.

- **Windows 설치파일:** `windows-installer` → `Achluophobia_x.y.z_x64-setup.exe`
- **안드로이드:** `android-apk` → `achluophobia.apk`
  - 디버그 서명이라 직접 설치(사이드로드)만 됩니다.
  - 플레이스토어에 올리려면 릴리스 키로 서명해야 합니다.
- **Releases:** `v1.0.1`처럼 태그를 푸시하면 두 파일이 Releases에도 올라갑니다.

## 파일 구성

| 경로 | 내용 |
|---|---|
| `src-tauri/` | Windows 앱 (`tauri.conf.json`에 창 크기와 사이트 주소) |
| `android/` | 안드로이드 프로젝트 (`MainActivity.java`에 화면 꺼짐 방지와 전체 화면) |
| `capacitor.config.json` | 안드로이드 앱 이름, 패키지 id, 사이트 주소 |
| `icon.png`, `assets/` | 아이콘과 스플래시 원본 |
| `web/` | 사이트에 연결할 수 없을 때 보이는 화면 |

아이콘을 바꾸려면 `icon.png`와 `assets/icon-only.png`를 교체한 뒤 `npm run icons`를 실행하세요.
