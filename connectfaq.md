# 🛠️ Slack Connector Issue Tracker

이슈 카드를 클릭하면 해당 카드만 독립적으로 강조되면서, 숨겨져 있던 구체적인 해결책 리스트가 스르륵 나타납니다.

<style>
  .card-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
    gap: 20px;
    margin-top: 20px;
    align-items: start; 
  }
  
  /* 체크박스 숨김 */
  .focus-trigger {
    display: none !important;
  }

  /* 카드 기본 레이아웃 */
  .focus-card {
    background-color: #ffffff;
    border: 2px solid #e0e0e0;
    border-radius: 12px;
    padding: 20px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.05);
    box-sizing: border-box;
    cursor: pointer;
    display: flex;
    flex-direction: column;
    transition: all 0.3s ease;
    
    /* 열리기 전 카드의 고정 높이 */
    height: 200px; 
    overflow: hidden;
  }

  .focus-card:hover {
    border-color: #4a154b;
    box-shadow: 0 6px 15px rgba(0,0,0,0.1);
  }

  /* 카드 내부 텍스트 영역 */
  .card-body {
    display: flex;
    flex-direction: column;
    height: 100%;
  }

  /* 설명문 스타일 */
  .card-desc {
    font-size: 13px;
    color: #616061;
    line-height: 1.4;
    margin: 0;
  }

  /* 기본 상태에서 해결책 영역 숨김 */
  .solution-area {
    max-height: 0;
    opacity: 0;
    overflow: hidden;
    transition: all 0.3s ease;
    box-sizing: border-box;
  }

  /* ─── 변경된 힌트 텍스트: absolute를 제거하고 마진으로 위치 조절 ─── */
  .hint-text {
    margin-top: auto; /* 설명글 아래쪽, 카드 바닥 쪽에 자연스럽게 밀착 */
    font-size: 12px;
    color: #4a154b;
    font-weight: bold;
    text-align: right;
    line-height: 1.5;
  }

  .hint-text::after {
    content: "해결책 보기 ▽";
  }

  /* ─── 핵심 인터랙션: 클릭(체크) 시 높이 해제 및 확장 ─── */
  .focus-trigger:checked + .focus-card {
    border-color: #4a154b;
    background-color: #faf6fa;
    box-shadow: 0 8px 20px rgba(74, 21, 75, 0.1);
    height: auto; /* 고정 높이 해제 */
    overflow: visible;
  }

  /* 해결책 영역 노출 */
  .focus-trigger:checked + .focus-card .solution-area {
    max-height: 500px; 
    opacity: 1;
    margin-top: 15px; /* 힌트 텍스트와의 자연스러운 간격 */
    padding-top: 15px;
    border-top: 1px dashed #4a154b; /* 구분선 역할 (---) */
  }

  /* 펼쳐졌을 때 힌트 텍스트 마진 조정 (해결책 위쪽으로 바짝 붙도록) */
  .focus-trigger:checked + .focus-card .hint-text {
    margin-top: 12px; 
  }

  /* 힌트 텍스트 변경 */
  .focus-trigger:checked + .focus-card .hint-text::after {
    content: "카드 접기 △";
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
    text-align: left;
  }
</style>

<div class="card-grid">

  <div>
    <input type="checkbox" id="f1" class="focus-trigger">
    <label for="f1" class="focus-card">
      <div class="card-body">
        <div style="font-weight: bold; color: #0d47a1; background: #e3f2fd; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">AUTH</div>
        <h3 style="margin: 8px 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 invalid_auth 에러</h3>
        <p class="card-desc">슬랙 웹훅이나 API 전송 시 인증 실패 토큰 반환 현상</p>
        <div class="hint-text"></div>
      </div>
      <div class="solution-area">
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 1. 토큰 스코프 재검토</b><br>
          봇 토큰에 <code>chat:write</code> 권한이 누락되었는지 확인하세요.
        </div>
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 2. 워크스페이스 앱 재인증</b><br>
          스코프 변경 후 <b>Reinstall to Workspace</b>를 진행해야 토큰이 갱신됩니다.
        </div>
      </div>
    </label>
  </div>

  <div>
    <input type="checkbox" id="f2" class="focus-trigger">
    <label for="f2" class="focus-card">
      <div class="card-body">
        <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">PAYLOAD</div>
        <h3 style="margin: 8px 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 400 Bad Request</h3>
        <p class="card-desc">Block Kit을 구성하여 전송 시 규격이 맞지 않아 거절됨</p>
        <div class="hint-text"></div>
      </div>
      <div class="solution-area">
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 1. 최상위 fallback 필드 삽입</b><br>
          <code>blocks</code> 전송 시 최상위 <code>text</code> 필드를 누락했는지 확인하세요.
        </div>
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 2. 공식 빌더 검증</b><br>
          Block Kit Builder 도구에 JSON을 붙여넣어 문법 오류를 체크하세요.
        </div>
      </div>
    </label>
  </div>

  <div>
    <input type="checkbox" id="f3" class="focus-trigger">
    <label for="f3" class="focus-card">
      <div class="card-body">
        <div style="font-weight: bold; color: #c62828; background: #ffebee; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">NETWORK</div>
        <h3 style="margin: 8px 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 429 Too Many Requests</h3>
        <p class="card-desc">단시간 내 과도한 메시지 발송으로 인한 API 호출 제한 발생</p>
        <div class="hint-text"></div>
      </div>
      <div class="solution-area">
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 1. 메시지 발송 큐(Queue) 도입</b><br>
          인메모리 큐나 Redis를 사용해 초당 1회 스로틀링 기준을 맞추도록 제어합니다.
        </div>
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 2. Retry-After 헤더 활용</b><br>
          429 에러 응답 헤더의 <code>Retry-After</code> 값만큼 대기 후 재시도 로직을 태웁니다.
        </div>
      </div>
    </label>
  </div>

  <div>
    <input type="checkbox" id="f4" class="focus-trigger">
    <label for="f4" class="focus-card">
      <div class="card-body">
        <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">TIMEOUT</div>
        <h3 style="margin: 8px 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 504 Gateway Timeout</h3>
        <p class="card-desc">슬랙 엔드포인트 응답 지연 혹은 커넥션 풀 고갈 현상</p>
        <div class="hint-text"></div>
      </div>
      <div class="solution-area">
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 1. 비동기(Asynchronous) 호출 전환</b><br>
          요청을 보낸 후 응답을 대기하지 않고, 웹훅을 Event-Driven 방식으로 비동기 처리합니다.
        </div>
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 2. HTTP 커넥션 타임아웃 튜닝</b><br>
          클라이언트 측의 Connect Timeout 설정을 3~5초 내외로 지정해 무한 대기를 방지합니다.
        </div>
      </div>
    </label>
  </div>

</div>
