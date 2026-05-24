# 🛠️ Slack Connector Issue Tracker (Card Focus Test)

이슈 카드를 클릭하면 카드가 강조되며 커지고, 숨겨져 있던 구체적인 해결책 리스트가 나타납니다.

<!-- ─── 1. 마크다운에서 동작하는 카드 포커스 핵심 CSS ─── -->
<style>
  /* 기본 그리드 구성 */
  .card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 25px;
    margin-top: 20px;
  }
  
  /* 체크박스는 화면에서 완전히 숨김 */
  .focus-trigger {
    display: none !important;
  }

  /* 카드 기본 레이아웃 및 전환 애니메이션 설정 */
  .focus-card {
    background-color: #ffffff;
    border: 2px solid #e0e0e0;
    border-radius: 14px;
    padding: 24px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.05);
    box-sizing: border-box;
    cursor: pointer;
    display: block;
    transition: all 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
    position: relative;
    z-index: 1;
  }

  /* 마우스 올렸을 때 살짝 뜨는 효과 */
  .focus-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 8px 20px rgba(0,0,0,0.08);
    border-color: #4a154b;
  }

  /* 기본 상태에서 해결책 영역은 보이지 않고 높이가 0임 */
  .solution-area {
    max-height: 0;
    opacity: 0;
    overflow: hidden;
    transition: all 0.4s cubic-bezier(0.25, 0.8, 0.25, 1);
    margin-top: 0;
    padding-top: 0;
    border-top: 1px dashed transparent;
  }

  /* 힌트 문구 */
  .hint-text::after {
    content: "클릭해서 해결책 보기 ▽";
  }

  /* ─── 핵심: 체크박스가 체크되었을 때 (포커스 상태) ─── */
  
  /* 1. 카드가 커지고 위로 떠오르며 테두리가 강조됨 */
  .focus-trigger:checked + .focus-card {
    transform: scale(1.03);
    box-shadow: 0 12px 30px rgba(74, 21, 75, 0.15);
    border-color: #4a154b;
    background-color: #faf6fa; /* 연한 보라색 배경으로 포커스 유도 */
    z-index: 10;
  }

  /* 2. 숨겨져 있던 해결책 영역이 스르륵 펼쳐짐 */
  .focus-trigger:checked + .focus-card .solution-area {
    max-height: 500px; /* 텍스트 양에 맞춰 넉넉하게 지정 */
    opacity: 1;
    margin-top: 15px;
    padding-top: 15px;
    border-top: 1px dashed #4a154b;
  }

  /* 3. 클릭 시 힌트 문구 변경 */
  .focus-trigger:checked + .focus-card .hint-text::after {
    content: "클릭해서 카드 접기 △";
  }

  /* 해결책 개별 박스 스타일 */
  .sol-box {
    background: #ffffff;
    border: 1px solid #e0e0e0;
    border-left: 4px solid #2eb67d; /* 슬랙 그린 포인트 */
    padding: 12px;
    border-radius: 6px;
    margin-bottom: 10px;
    font-size: 13px;
    line-height: 1.5;
    color: #333333;
  }
  .sol-box b {
    color: #4a154b;
  }
</style>

<!-- ─── 2. 카드 콘텐츠 배치 ─── -->
<div class="card-grid">

  <!-- [카드 1] 인증 이슈 -->
  <div>
    <input type="checkbox" id="focus1_trigger" class="focus-trigger">
    <label for="focus1_trigger" class="focus-card">
      <!-- 상단 요약 정보 -->
      <div style="font-weight: bold; color: #0d47a1; background: #e3f2fd; padding: 3px 8px; border-radius: 10px; width: fit-content; font-size: 11px;">AUTH</div>
      <h3 style="margin: 12px 0 8px 0; font-size: 19px; color: #1d1c1d;">🚨 invalid_auth 에러</h3>
      <p style="font-size: 13px; color: #616061; margin-bottom: 12px; line-height: 1.4;">슬랙 웹훅이나 API 전송 시 인증 실패 토큰 반환 현상</p>
      <div class="hint-text" style="text-align: right; font-size: 12px; color: #4a154b; font-weight: bold;"></div>
      <!-- 하단 확장 해결책 영역 -->
      <div class="solution-area">
        <div class="sol-box">
          <b>해결책 A. 토큰 스코프 재검토</b><br>
          봇 토큰에 <code>chat:write</code> 또는 <code>incoming-webhook</code> 권한이 누락되었는지 App 설정 화면에서 확인하세요.
        </div>
        <div class="sol-box">
          <b>해결책 B. 워크스페이스 앱 재인증</b><br>
          앱 권한 스코프(Scope)를 변경한 경우, 반드시 <b>Reinstall to Workspace</b> 버튼을 눌러 다시 연동해야 토큰이 정상 갱신됩니다.
        </div>
      </div>
    </label>
  </div>

  <!-- [카드 2] 페이로드 이슈 -->
  <div>
    <input type="checkbox" id="focus2_trigger" class="focus-trigger">
    <label for="focus2_trigger" class="focus-card">
      <!-- 상단 요약 정보 -->
      <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 3px 8px; border-radius: 10px; width: fit-content; font-size: 11px;">PAYLOAD</div>
      <h3 style="margin: 12px 0 8px 0; font-size: 19px; color: #1d1c1d;">🚨 400 Bad Request</h3>
      <p style="font-size: 13px; color: #616061; margin-bottom: 12px; line-height: 1.4;">Block Kit을 구성하여 전송 시 규격이 맞지 않아 거절됨</p>
      <div class="hint-text" style="text-align: right; font-size: 12px; color: #4a154b; font-weight: bold;"></div>
      <!-- 하단 확장 해결책 영역 -->
      <div class="solution-area">
        <div class="sol-box">
          <b>해결책 A. 최상위 fallback 필드 필수 삽입</b><br>
          <code>blocks</code> 배열 구조를 전송할 때 모바일 알림창 팝업 파싱용 <code>text</code>나 <code>fallback</code> 스트링 필드를 반드시 JSON 최상위에 정의해야 합니다.
        </div>
        <div class="sol-box">
          <b>해결책 B. Block Kit Builder 검증</b><br>
          구조가 너무 복잡하다면 슬랙 공식 웹 도구인 Block Kit Builder에 JSON을 붙여넣어 문법 오류 유무를 실시간으로 체크하세요.
        </div>
      </div>
    </label>
  </div>
</div>
