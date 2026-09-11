# 동물왕국 출시 문서 초안

기준: animal-border `feat/game-feedback-settings` / `991b71b` (2026-09-11 확인).
사이트 형식: 이 저장소의 `0to99/privacy-policy.html`, `0to99/support.html`.

추가한 문서:
- `animal-kingdom/privacy-policy.html`: 한국어 및 영어 전문. 초안임을 표시한다.
- `animal-kingdom/support.html`: 문의·오류 제보·서버 기록 삭제 안내.

공개 경로 (출시 전 초안으로 공개):
- https://sidus-network.github.io/animal-kingdom/privacy-policy.html
- https://sidus-network.github.io/animal-kingdom/support.html

## 코드와 대조한 사항

- 계정·서버 랭킹·인앱결제는 현재 비활성/미구현. 계정 삭제 기능이 있다고 쓰지 않는다.
- 자체 분석은 `app/src/telemetry.js`: 참가자 코드도 서버에 전송된다.
- `worker/index.js`: 서버 수신 시각과 접속 국가 추가. 별도 `feat/privacy-retention` 브랜치에서 신규 기록의 KV TTL을 90일로 설정했다. 운영 배포 및 기존 기록의 만료 전환은 아직 수행하지 않았다.
- `app/src/ads.js`: Google Mobile Ads 전면/리워드 광고. 현재 테스트 ID.
- Firebase Analytics는 현재 앱에 없음. 기존 0to99 문구를 복사하지 않는다.
- `reminder-driver.js`: 로컬 일일 알림, 서버 push token 요청 없음.
- `App.js`의 reset은 서버 로그·참가자 코드·모든 설정을 지우지 않음.
- 문의메일은 사용자 결정에 따라 sidus.network+support@gmail.com으로 통일.
  앱 및 기존 웹 문의메일도 `feat/privacy-retention`에서 변경했다.
  개인정보 URL은 사이트 공개 후 Workers /privacy에서 Sidus 페이지로 전환한다.

## 정식 시행 전에 확정할 사항

1. 문의메일은 확정. 스토어의 개발자/운영 주체 표기를 실제 등록 정보와 대조한다.
2. 원본 플레이 기록은 서버 수신 후 90일로 확정. 신규 기록 TTL 변경을 운영 배포하고,
   기존 KV 키에는 최초 수신 시각 + 90일의 절대 만료 시각을 설정한다. 이미 지난 기록은 삭제한다.
   전환 작업 시점부터 90일을 다시 주지 않는다. 내보낸 원본 사본에도 같은 기준을 적용한다.
   기존 기록 전환과 삭제 요청 대응 절차를 검증한 뒤 정책을 정식 시행한다.
3. 글로벌 출시, 한국어·영어 및 한국·영어권 우선으로 결정. 목표 이용자는 청소년으로 결정하며 어린이는 대상에서 제외한다.
   구체적인 배포 국가, 최소 이용 연령과 광고 동의/추적 구성은 추가 확정한다. 현재 앱에는 이를 근거로
   '광고 식별자 미수집', '필요한 동의 모두 획득', '아동 데이터 수집 없음'을 단정할 근거가 없다.
   필요한 지역별 고지 및 국외 처리 상세를 확정된 운영 정보에 맞춘다.
4. 배포할 Android/iOS SDK 버전 및 광고 설정을 기준으로 Google Play 데이터 보안·
   App Store 개인정보 답변을 작성한다. 광고 SDK가 처리하는 정보도 포함한다.
5. 위 결정을 반영하고 초안 표시를 제거한 뒤 시행일을 확정한다.
6. 사이트를 공개하고 URL을 확인한 뒤 앱 Settings 문의메일·개인정보 링크를 연결한다.
   기존 `mockup/privacy.html`도 오래된 문구를 남기지 않도록 정리한다.

앱 메일·신규 기록 TTL 코드와 문서 초안을 수정했다. 운영 서버는 아직 배포하지 않았다. 사이트는 초안 표시를 유지한 채 main 병합으로 공개한다.
이용약관이나 결제/계정 정책은 현재 앱에 없는 기능을 가정하여 추가하지 않았다.

## 참고한 공식 자료

2026-09-11 조회. 아래 광고 문서는 최신 SDK 기준이므로 실제 출시 SDK와 대조한다.
- Google Mobile Ads Android: https://developers.google.com/admob/android/privacy/play-data-disclosure
- Google Mobile Ads iOS: https://developers.google.com/admob/ios/privacy/data-disclosure
- Google Play User Data: https://support.google.com/googleplay/android-developer/answer/10144311

검증: HTML 구문 구조, 한국어/영어 구역, 내부 링크와 HTTP 응답. 법적 적합성 또는
실제 삭제 운영을 검증한 것으로 취급하지 않는다.

## 대상 연령 결정 및 남은 구현

- 사용자 결정: 이번 출시는 청소년만을 목표 이용자로 한다. 어린이를 대상으로 포함하지 않는다.
- 이 결정은 성인 이용을 기술적으로 차단하라는 요구로 해석하지 않는다.
- 정확한 최소 이용 연령은 우선 출시 국가별 요건과 광고 SDK 설정을 대조하여 정한다.
- 연령 확인, 광고·분석 초기화 시점 및 필요한 미성년자 보호 설정은 아직 구현 완료로 간주하지 않는다.
- 스토어 콘텐츠 등급과 실제 목표 연령은 다르다. 그래픽, 마케팅, 실제 이용자 등을 함께 고려한다.
- King 약관은 기본 만 13세 이상 및 해당 지역 법률을 전제로 한다. 이를 한국에서 동일한 최소 연령이 확인된 것으로 해석하지 않는다.
- 어린이를 주요 대상에 포함하면 광고와 자체 분석의 수집 항목·연령별 처리·필요한 보호자 동의를 구현하고 검증해야 한다.
- 글로벌 목표라도 영어권 각국의 요건이 같지는 않다. 우선 국가 목록은 별도 확정한다.

공식 근거 (2026-09-11 조회):
- King 약관: https://www.king.com/termsandconditions/
- 한국 개인정보 보호법 제22조의2: https://www.law.go.kr/lsLinkCommonInfo.do?chrClsCd=010202&lsJoLnkSeq=1029334761
- 미국 COPPA: https://www.ftc.gov/legal-library/browse/rules/childrens-online-privacy-protection-rule-coppa
- Google Play Families: https://support.google.com/googleplay/android-developer/answer/9893335?hl=en
- Apple Kids Category: https://developer.apple.com/app-store/review/guidelines/#kids-category
