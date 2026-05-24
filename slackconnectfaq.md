# 🛠️ Slack Connector Issue Tracker

프로젝트 중 발생하는 슬랙 커넥터 이슈와 해결책 모음입니다. 항목을 클릭하면 다수의 해결책을 확인할 수 있습니다.

---

## 🔐 인증 및 보안 (Auth)

<details>
<summary><b>🚨 invalid_auth 에러 발생 (클릭하여 해결책 보기 ↻)</b></summary>
<br>

> 💡 **해결책 1. 토큰 스코프 재검토**
> 봇 토큰에 `chat:write` 또는 `incoming-webhook` 권한이 누락되었는지 Slack App 설정 화면에서 확인하세요.

> 💡 **해결책 2. 워크스페이스 앱 재인증**
> 앱 권한 스코프(Scope)를 변경한 경우, 반드시 **Reinstall to Workspace** 버튼을 눌러 다시 연동해야 토큰이 정상 갱신됩니다.

</details>

---

## 📦 데이터 규격 (Payload)

<details>
<summary><b>🚨 400 Bad Request (missing_text_or_fallback) (클릭하여 해결책 보기 ↻)</b></summary>
<br>

> 💡 **해결책 1. 최상위 fallback 필드 필수 삽입**
> `blocks` 배열 구조를 전송할 때 모바일 알림창 팝업 파싱용 `text`나 `fallback` 스트링 필드를 반드시 JSON 최상위에 정의해야 합니다.

> 💡 **해결책 2. Block Kit Builder 검증**
> 구조가 너무 복잡하다면 슬랙 공식 웹 도구인 [Block Kit Builder](https://app.slack.com/block-kit-builder)에 JSON을 붙여넣어 문법 오류 유무를 실시간으로 체크하세요.

</details>

---

## 🌐 네트워크 및 제한 (Network)

<details>
<summary><b>🚨 HTTP 429 Too Many Requests 에러 (클릭하여 해결책 보기 ↻)</b></summary>
<br>

> 💡 **해결책 1. 요청 큐(Queue) 체계 도입**
> 초당 1회 스로틀링(Tier 3 기본 규격) 기준을 맞추기 위해 인메모리 큐나 Redis Queue를 이용해 발송 속도를 제어합니다.

> 💡 **해결책 2. Retry-After 헤더 파싱**
> 429 에러 응답 시 함께 넘어오는 `Retry-After` 헤더 값을 읽어, 해당 초(seconds)만큼 대기(Backoff) 후 재시도 하도록 로직을 보완합니다.

</details>
