# 🛠️ Slack Connector Issue Tracker

이슈 카드를 클릭하면 카드가 강조되면서, 아래로 숨겨져 있던 구체적인 해결책 리스트가 스르륵 나타납니다.

<!-- ─── 깃허브 마크다운 친화적 카드 포커스 CSS (에러 없음) ─── -->
<style>
  .card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 20px;
    margin-top: 20px;
  }
  
  /* 체크박스 숨김 */
  .focus-trigger {
    display: none !important;
  }

  /* 카드 기본 레이아웃 (정적 문서 흐름을 깨지 않아 안전함) */
  .focus-card {
    background-color: #ffffff;
    border: 2px solid #e0e0e0;
    border-radius: 12px;
    padding: 20px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.05);
    box-sizing: border-box;
    cursor: pointer;
    display: block;
    transition: all 0.3s ease;
  }

  .focus-card:hover {
    border-color: #4a154b;
    box-shadow: 0 6px 15px rgba(0,0,0,0.1);
  }

  /* 기본 상태에서 해결책 영역 숨김 */
  .solution-area {
    max-height: 0;
    opacity: 0;
    overflow: hidden;
    transition: all 0.3s ease;
  }

  .hint-text::after {
    content: "클릭해서 해결책 보기 ▽";
  }

  /* ─── 핵심 인터랙션: 클릭(체크) 시 확장 및 강조 ─── */
  .focus-trigger:checked + .focus-card {
    border-color: #4a154b;
    background-color: #faf6fa; /* 연한 보라색 톤으로 포커스 */
    box-shadow: 0 8px 20px rgba(74, 21, 75, 0.1);
  }

  /* 해결책 영역 노출 */
  .focus-trigger:checked + .focus-card .solution-area {
    max-height: 400px; 
    opacity: 1;
    margin-top: 15px;
    padding-top: 15px;
    border-top: 1px dashed #4a154b;
  }

  /* 힌트 텍스트 변경 */
  .focus-trigger:checked + .focus-card .hint-text::after {
    content: "클릭해서 카드 접기 △";
  }

  /* 해결책 내용 상자 */
  .sol-box {
    background: #ffffff;
    border: 1px solid #e9ecef;
    border-left: 4px solid #2eb67d;
    padding: 10px 12px;
    border-radius: 4px;
    margin-bottom: 8px;
    font-size: 13px;
    line-height: 1.5;
    color: #333333;
  }
</style>

<!-- ─── 카드 콘텐츠 ─── -->
<div class="card-grid">
  <!-- 카드 1: 인증 이슈 -->
  <div>
    <input type="checkbox" id="f1" class="focus-trigger">
    <label for="f1" class="focus-card">
      <div style="font-weight: bold; color: #0d47a1; background: #e3f2fd; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">AUTH</div>
      <h3 style="margin: 10px 0 6px 0; font-size: 18px; color: #1d1c1d;">🚨 invalid_auth 에러</h3>
      <p style="font-size: 13px; color: #616061; margin-bottom: 10px;">슬랙 웹훅이나 API 전송 시 인증 실패 토큰 반환 현상</p>
      <div class="hint-text" style="text-align: right; font-size: 12px; color: #4a154b; font-weight: bold;"></div>
            <!-- 클릭 시 펼쳐지는 영역 -->
      <div class="solution-area">
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 1. 토큰 스코프 재검토</b>
          봇 토큰에 <code>chat:write</code> 권한이 누락되었는지 확인하세요.
        </div>
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 2. 워크스페이스 앱 재인증</b>
          스코프 변경 후 <b>Reinstall to Workspace</b>를 진행해야 토큰이 갱신됩니다.
        </div>
      </div>
    </label>
  </div>
  <!-- 카드 2: 페이로드 이슈 -->
  <div>
    <input type="checkbox" id="f2" class="focus-trigger">
    <label for="f2" class="focus-card">
      <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">PAYLOAD</div>
      <h3 style="margin: 10px 0 6px 0; font-size: 18px; color: #1d1c1d;">🚨 400 Bad Request</h3>
      <p style="font-size: 13px; color: #616061; margin-bottom: 10px;">Block Kit을 구성하여 전송 시 규격이 맞지 않아 거절됨</p>
      <div class="hint-text" style="text-align: right; font-size: 12px; color: #4a154b; font-weight: bold;"></div>
            <!-- 클릭 시 펼쳐지는 영역 -->
      <div class="solution-area">
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 1. 최상위 fallback 필드 삽입</b>
          <code>blocks</code> 전송 시 최상위 <code>text</code> 필드를 누락했는지 확인하세요.
        </div>
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 2. 공식 빌더 검증</b>
          Block Kit Builder 도구에 JSON을 붙여넣어 문법 오류를 체크하세요.
        </div>
      </div>
    </label>
  </div>

</div>
