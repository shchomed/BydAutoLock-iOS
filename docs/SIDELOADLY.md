# 개인 아이폰 설치 (무료 Apple 계정 + Sideloadly)

1. 변경 파일을 GitHub 저장소에 올립니다.
2. Actions → **Build iPhone IPA (Sideloadly)** → **Run workflow**를 실행합니다. main에 앱 변경을 올려도 자동 실행됩니다.
3. 성공한 실행의 Artifacts에서 **BydAutoLock-Sideloadly**를 다운로드하고 ZIP을 풉니다.
4. Windows에서 Sideloadly를 열고 아이폰을 연결한 뒤 기기에서 컴퓨터를 신뢰합니다.
5. **BydAutoLock-Sideloadly.ipa**를 선택하고 본인의 Apple 계정으로 서명·설치합니다. 필요한 경우 아이폰의 개발자 모드와 개발자 앱 신뢰를 설정합니다.

Apple 계정 암호나 인증서를 GitHub Secrets에 등록할 필요가 없습니다. GitHub는 서명 없는 IPA만 만들고 Sideloadly가 서명합니다.

무료 계정으로 설치한 앱은 7일마다 재서명이 필요합니다. Sideloadly 자동 갱신을 설정하거나 같은 계정과 번들 ID로 다시 설치하세요.

이 빌드는 iPhone 앱만 포함합니다. 워치 앱, 위젯, App Group 권한은 제외되며 위젯 공유 저장도 비활성화됩니다. 기존 전체 앱 프로젝트 설정은 유지됩니다. 최소 iOS 버전은 기존 앱과 같은 15.0입니다.

빌드 설정은 `project.sideload.yml`, 자동화는 `.github/workflows/ios-sideload.yml`에 있습니다. XcodeGen으로 기본 설정을 불러온 후 확장 앱 의존성을 교체하고 Sideload 스킴만 빌드합니다.

참고: https://sideloadly.io/faq
