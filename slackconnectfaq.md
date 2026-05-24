# 🛠️ Slack Connector Issue Tracker (Modal Popup Test)

이슈 카드를 클릭하면 화면 중앙에 다이나믹한 팝업창이 뜨며 상세 해결책을 확인할 수 있습니다.

<!-- ─── 1. 마크다운에서 동작하는 중앙 팝업 핵심 CSS ─── -->
<style>
  /* 기본 카드 그리드 */
  .card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 25px;
    margin-top: 20px;
  }
  
  /* 트리거 체크박스 숨김 */
  .popup-trigger {
    display: none !important;
  }

  /* 겉에 보이는 기본 카드 디자인 */
  .base-card {
    background-color: #ffffff;
    border: 2px solid #e0e0e0;
    border-radius: 14px;
    padding: 24px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.05);
    box-sizing: border-box;
    cursor: pointer;
    display: block;
    transition: all 0.25s ease;
  }
  .base-card:hover {
    transform: translateY(-4px);
    border-color: #4a154b;
    box-shadow: 0 8px 20px rgba(0,0,0,0.08);
  }

  /* ─── 여기서부터 팝업(모달) 레이아웃 ─── */
  
  /* 팝업 전체를 감싸는 오버레이 (배경 어둡게 처리) */
  .popup-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.6); /* 뒷 배경 어둡게 */
    backdrop-filter: blur(4px); /* 뒷 배경 블러 효과 */
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 99999; /* 최상단 배치 */
    
    /* 기본 상태는 숨김 및 투명 */
    visibility: hidden;
    opacity: 0;
    transition: all 0.3s ease;
  }

  /* 진짜 한가운데 뜰 팝업창 바디 */
  .popup-content {
    background-color: #ffffff;
    border-radius: 16px;
    width: 90%;
    max-width: 550px;
    padding: 30px;
    box-shadow: 0 20px 40px rgba(0,0,0,0.3);
    box-sizing: border-box;
    position: relative;
    
    /* 기본 상태는 살짝 작아진 상태 (커지면서 나타나게 함) */
    transform: scale(0.85);
    transition: transform 0.3s cubic-bezier(0.34, 1.56, 0.64, 1); /* 통통 튀는 애니메이션 */
  }

  /* 우측 상단 닫기 X 버튼 */
  .close-btn {
    position: absolute;
    top: 15px;
    right: 20px;
    font-size: 24px;
    color: #999;
    cursor: pointer;
    font-weight: bold;
    user-select: none;
  }
  .close-btn:hover {
    color: #333;
  }

  /* ─── 핵심: 체크박스가 켜지면 팝업을 중앙에 띄움 ─── */
  .popup-trigger:checked + .popup-overlay {
    visibility: visible;
    opacity: 1;
  }
  
  /* 팝업창이 커지면서 화면 중앙으로 등장 */
  .popup-trigger:checked + .popup-overlay .popup-content {
    transform: scale(1);
  }

  /* 팝업 내부 해결책 스타일 */
  .sol-box {
    background: #f8f9fa;
    border-left: 4px solid #2eb67d;
    padding: 14px;
    border-radius: 0 8px 8px 0;
    margin-bottom: 12px;
    font-size: 14px;
    line-height: 1.5;
  }
  .sol-box b {
    color: #4a154b;
    display: block;
    margin-bottom: 4px;
  }
</style>

<!-- ─── 2. 카드 및 팝업 콘텐츠 배치 ─── -->
<div class="card-grid">

  <!-- [카드 1] 인증 이슈 -->
  <div>
    <!-- 1) 카드 클릭용 트리거 체크박스 -->
    <input type="checkbox" id="pop1_trigger" class="popup-trigger">
    
    <!-- 2) 오버레이 및 팝업 본문 (체크박스가 켜지면 보임) -->
    <div class="popup-overlay">
      <div class="popup-content">
        <!-- 닫기 버튼: 라벨을 한 번 더 눌러 체크박스를 해제하는 원리 -->
        <label for="pop1_trigger" class="close-btn">&times;</label>
        
        <div style="font-weight: bold; color: #0d47a1; background: #e3f2fd; padding: 3px 8px; border-radius: 10px; width: fit-content; font-size: 11px; margin-bottom: 10px;">AUTH</div>
        <h3 style="font-size: 22px; color: #1d1c1d; margin-bottom: 20px; padding-right: 30px;">🚨 invalid_auth 에러 해결책</h3>
        
        <div class="sol-box">
          <b>해결책 1. 토큰 스코프 재검토</b>
          봇 토큰에 <code>chat:write</code> 또는 <code>incoming-webhook</code> 권한이 누락되었는지 Slack App 설정 화면에서 확인하세요.
        </div>
        <div class="sol-box">
          <b>해결책 2. 워크스페이스 앱 재인증</b>
          앱 권한 스코프(Scope)를 변경한 경우, 반드시 <b>Reinstall to Workspace</b> 버튼을 눌러 다시 연동해야 토큰이 정상 갱신됩니다.
        </div>
      </div>
    </div>

    <!-- 3) 화면에 항상 떠있는 기본 카드 상태 -->
    <label for="pop1_trigger" class="base-card">
      <div style="font-weight: bold; color: #0d47a1; background: #e3f2fd; padding: 3px 8px; border-radius: 10px; width: fit-content; font-size: 11px;">AUTH</div>
      <h3 style="margin: 12px 0 8px 0; font-size: 18px; color: #1d1c1d;">🚨 invalid_auth 에러</h3>
      <p style="font-size: 13px; color: #616061; line-height: 1.4; margin-bottom: 10px;">슬랙 웹훅이나 API 전송 시 인증 실패 토큰 반환 현상</p>
      <div style="text-align: right; font-size: 12px; color: #4a154b; font-weight: bold;">자세히 보기 →</div>
    </label>
  </div>

  <!-- [카드 2] 페이로드 이슈 -->
  <div>
    <input type="checkbox" id="pop2_trigger" class="popup-trigger">
    
    <div class="popup-overlay">
      <div class="popup-content">
        <label for="pop2_trigger" class="close-btn">&times;</label>
        
        <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 3px 8px; border-radius: 10px; width: fit-content; font-size: 11px; margin-bottom: 10px;">PAYLOAD</div>
        <h3 style="font-size: 22px; color: #1d1c1d; margin-bottom: 20px; padding-right: 30px;">🚨 400 Bad Request 해결책</h3>
        
        <div class="sol-box">
          <b>해결책 1. 최상위 fallback 필드 필수 삽입</b>
          <code>blocks</code> 배열 구조를 전송할 때 모바일 알림창 팝업 파싱용 <code>text</code>나 <code>fallback</code> 스트링 필드를 반드시 JSON 최상위에 정의해야 합니다.
        </div>
        <div class="sol-box">
          <b>해결책 2. Block Kit Builder 검증</b>
          구조가 너무 복잡하다면 슬랙 공식 웹 도구인 Block Kit Builder에 JSON을 붙여넣어 문법 오류 유무를 실시간으로 체크하세요.
        </div>
      </div>
    </div>

    <label for="pop2_trigger" class="base-card">
      <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 3px 8px; border-radius: 10px; width: fit-content; font-size: 11px;">PAYLOAD</div>
      <h3 style="margin: 12px 0 8px 0; font-size: 18px; color: #1d1c1d;">🚨 400 Bad Request</h3>
      <p style="font-size: 13px; color: #616061; line-height: 1.4; margin-bottom: 10px;">Block Kit을 구성하여 전송 시 규격이 맞지 않아 거절됨</p>
      <div style="text-align: right; font-size: 12px; color: #4a154b; font-weight: bold;">자세히 보기 →</div>
    </label>
  </div>

</div>
