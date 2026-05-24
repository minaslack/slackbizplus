# 🛠️ Slack Connector Issue Tracker (Card Flip Test)

카드를 클릭하면 자바스크립트 없이 3D로 뒤집히며 여러 해결책이 나타납니다.

<!-- ─── 1. 마크다운에서 동작하는 카드 뒤집기 핵심 CSS ─── -->
<style>
  /* 기본 그리드 구성 */
  .card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 20px;
    margin-top: 20px;
  }
  
  /* 체크박스는 화면에서 완전히 숨김 */
  .flip-trigger {
    display: none !important;
  }

  /* 3D 회전 무대 세팅 */
  .card-scene {
    height: 350px;
    perspective: 1000px;
  }

  /* 진짜 카드 박스 (라벨 태그로 만들어 클릭 인식) */
  .flip-card {
    width: 100%;
    height: 100%;
    position: relative;
    transform-style: preserve-3d;
    transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
    cursor: pointer;
    display: block; /* 마크다운 내 영역 확보 */
  }

  /* 핵심: 체크박스가 체크되면 카드를 180도 회전 시킴 */
  .flip-trigger:checked + .card-scene .flip-card {
    transform: rotateY(180deg);
  }

  /* 카드 앞/뒷면 공통 레이아웃 */
  .card-face {
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
    border-radius: 14px;
    padding: 20px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
  }

  /* 카드 앞면 디자인 */
  .card-front {
    background-color: #ffffff;
    border: 2px solid #e0e0e0;
    justify-content: space-between;
  }

  /* 카드 뒷면 디자인 (슬랙 보라색 테마) */
  .card-back {
    background-color: #4a154b;
    color: #ffffff;
    transform: rotateY(180deg);
    overflow-y: auto;
    border: 2px solid #4a154b;
  }

  /* 뒷면 내부의 해결책 박스 스타일 */
  .sol-box {
    background: rgba(255,255,255,0.15);
    border-left: 4px solid #2eb67d;
    padding: 8px 10px;
    border-radius: 4px;
    margin-bottom: 10px;
    font-size: 13px;
    line-height: 1.4;
  }
</style>

<!-- ─── 2. 카드 콘텐츠 배치 ─── -->
<div class="card-grid">

  <!-- [카드 1] 인증 이슈 -->
  <div>
    <!-- 체크박스와 라벨의 ID를 매칭시켜 클릭 이벤트 구현 -->
    <input type="checkbox" id="card1_trigger" class="flip-trigger">
    <div class="card-scene">
      <label for="card1_trigger" class="flip-card">
        <!-- 앞면 -->
        <div class="card-face card-front">
          <div style="font-weight: bold; color: #0d47a1; background: #e3f2fd; padding: 3px 8px; border-radius: 10px; width: fit-content; font-size: 11px;">AUTH</div>
          <h3 style="margin: 10px 0; font-size: 18px; color: #1d1c1d;">🚨 invalid_auth 에러</h3>
          <p style="font-size: 13px; color: #616061; flex-grow: 1;">슬랙 웹훅이나 API 전송 시 인증 실패 토큰 반환 현상</p>
          <div style="text-align: right; font-size: 12px; color: #e01e5a; font-weight: bold;">클릭해서 뒤집기 ↻</div>
        </div>
        <!-- 뒷면 -->
        <div class="card-face card-back">
          <h4 style="color: #ecb22e; margin-bottom: 12px; border-bottom: 1px solid rgba(255,255,255,0.2); padding-bottom: 5px;">💡 해결책 리스트</h4>
          <div class="sol-box">
            <b>1. 스코프 재검토:</b> App 설정에서 <code>chat:write</code> 권한 누락 여부 확인
          </div>
          <div class="sol-box">
            <b>2. 워크스페이스 재인증:</b> 스코프 변경 후 <b>Reinstall App</b> 진행 필수
          </div>
        </div>
      </label>
    </div>
  </div>

  <!-- [카드 2] 페이로드 이슈 -->
  <div>
    <input type="checkbox" id="card2_trigger" class="flip-trigger">
    <div class="card-scene">
      <label for="card2_trigger" class="flip-card">
        <!-- 앞면 -->
        <div class="card-face card-front">
          <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 3px 8px; border-radius: 10px; width: fit-content; font-size: 11px;">PAYLOAD</div>
          <h3 style="margin: 10px 0; font-size: 18px; color: #1d1c1d;">🚨 400 Bad Request</h3>
          <p style="font-size: 13px; color: #616061; flex-grow: 1;">Block Kit을 구성하여 전송 시 규격이 맞지 않아 거절됨</p>
          <div style="text-align: right; font-size: 12px; color: #e01e5a; font-weight: bold;">클릭해서 뒤집기 ↻</div>
        </div>
        <!-- 뒷면 -->
        <div class="card-face card-back">
          <h4 style="color: #ecb22e; margin-bottom: 12px; border-bottom: 1px solid rgba(255,255,255,0.2); padding-bottom: 5px;">💡 해결책 리스트</h4>
          <div class="sol-box">
            <b>1. fallback 필드 삽입:</b> <code>blocks</code> 전송 시 최상위 <code>text</code> 필드도 필수 포함
          </div>
          <div class="sol-box">
            <b>2. 공식 빌더 사용:</b> Block Kit Builder 도구로 JSON 구조 선제 검증
          </div>
        </div>
      </label>
    </div>
  </div>

</div>
