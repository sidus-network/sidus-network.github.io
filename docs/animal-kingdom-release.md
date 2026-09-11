# 동물왕국 출시 문서 초안

기준: animal-border `feat/game-feedback-settings` / `991b71b` (2026-09-11 확인).
사이트 형식: 이 저장소의 `0to99/privacy-policy.html`, `0to99/support.html`.

추가한 문서:
- `animal-kingdom/privacy-policy.html`: 한국어 및 영어 전문. 초안임을 표시한다.
- `animal-kingdom/support.html`: 문의·오류 제보·서버 기록 삭제 안내.

향후 공개 경로 (현재 배포한 주소가 아님):
- https://sidus-network.github.io/animal-kingdom/privacy-policy.html
- https://sidus-network.github.io/animal-kingdom/support.html

## 코드와 대조한 사항

- 계정·서버 랭킹·인앱결제는 현재 비활성/미구현. 계정 삭제 기능이 있다고 쓰지 않는다.
- 자체 분석은 `app/src/telemetry.js`: 참가자 코드도 서버에 전송된다.
- `worker/index.js`: 서버 수신 시각과 접속 국가 추가, KV 저장에 expiration/TTL 없음.
- `app/src/ads.js`: Google Mobile Ads 전면/리워드 광고. 현재 테스트 ID.
- Firebase Analytics는 현재 앱에 없음. 기존 0to99 문구를 복사하지 않는다.
- `reminder-driver.js`: 로컬 일일 알림, 서버 push token 요청 없음.
- `App.js`의 reset은 서버 로그·참가자 코드·모든 설정을 지우지 않음.
- 현재 앱의 문의메일은 metallseajelly@gmail.com, 개인정보 URL은 Workers /privacy.
  이번 Sidus 초안의 메일은 기존 Sidus 페이지 기준 sidus.network+support@gmail.com.
  사용자의 메일 결정 후 앱·문서 양쪽을 일치시켜야 한다.

## 공개 전에 확정할 사항

1. 문의 메일과 스토어의 개발자/운영 주체 표기를 확정한다.
2. 원본 플레이 기록 보관 기간과 삭제 절차를 정한다. 현재 TTL이 없으므로
   임의로 '90일/1년 후 자동 삭제'라고 쓰지 않았다. 기간을 정하면 실제 서버 처리도 함께 바꾼다.
3. 출시 대상 연령·국가와 광고 동의/추적 구성을 확정한다. 현재 앱에는 이를 근거로
   '광고 식별자 미수집', '필요한 동의 모두 획득', '아동 데이터 수집 없음'을 단정할 근거가 없다.
   필요한 지역별 고지 및 국외 처리 상세를 확정된 운영 정보에 맞춘다.
4. 배포할 Android/iOS SDK 버전 및 광고 설정을 기준으로 Google Play 데이터 보안·
   App Store 개인정보 답변을 작성한다. 광고 SDK가 처리하는 정보도 포함한다.
5. 위 결정을 반영하고 초안 표시를 제거한 뒤 시행일을 확정한다.
6. 사이트를 공개하고 URL을 확인한 뒤 앱 Settings 문의메일·개인정보 링크를 연결한다.
   기존 `mockup/privacy.html`도 오래된 문구를 남기지 않도록 정리한다.

개인정보·고객지원 페이지 초안만 작성했으며 앱 코드, 운영 서버, 사이트 공개 상태는 변경하지 않았다.
이용약관이나 결제/계정 정책은 현재 앱에 없는 기능을 가정하여 추가하지 않았다.

## 참고한 공식 자료

2026-09-11 조회. 아래 광고 문서는 최신 SDK 기준이므로 실제 출시 SDK와 대조한다.
- Google Mobile Ads Android: https://developers.google.com/admob/android/privacy/play-data-disclosure
- Google Mobile Ads iOS: https://developers.google.com/admob/ios/privacy/data-disclosure
- Google Play User Data: https://support.google.com/googleplay/android-developer/answer/10144311

검증: HTML 구문 구조, 한국어/영어 구역, 내부 링크와 HTTP 응답. 법적 적합성 또는
실제 삭제 운영을 검증한 것으로 취급하지 않는다.
