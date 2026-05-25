# 🛠️ Slack Connector Issue Tracker

이슈 카드를 클릭하면 해당 카드만 독립적으로 강조되면서, 숨겨져 있던 구체적인 해결책 리스트가 스르륵 나타납니다.

<style>
  .card-grid {
    display: grid;
    /* 한 줄에 정확히 2개씩 배치 (반응형을 원하시면 repeat(auto-fill, minmax(300px, 1fr))로 롤백 가능) */
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
    margin-top: 20px;
    /* stretch를 주어 같은 줄의 카드 높이가 자동으로 같아지도록 설정 */
    align-items: stretch; 
  }
  
  /* 그리드 아이템 wrap (높이 동기화를 위해 중요) */
  .grid-item {
    display: flex;
    flex-direction: column;
  }

  /* 체크박스 숨김 */
  .focus-trigger {
    display: none !important;
  }

  /* 카드 기본 레이아웃 */
  .focus-card {
    position: relative;
    background-color: #ffffff;
    border: 2px solid #e0e0e0;
    border-radius: 12px;
    padding: 16px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.05);
    box-sizing: border-box;
    cursor: pointer;
    display: flex;
    flex-direction: column;
    /* 카드 자체가 부모(grid-item)의 높이를 가득 채우도록 설정 */
    flex: 1; 
    transition: background-color 0.3s, border-color 0.3s, box-shadow 0.3s;
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
    /* 해결책이나 힌트가 아래로 밀리도록 본문 영역이 남은 공간을 채움 */
    flex: 1; 
  }

  /* 설명문 스타일 */
  .card-desc {
    font-size: 13px;
    color: #616061;
    line-height: 1.4;
    margin: 6px 0 0 0;
  }

  /* 기본 상태에서 해결책 영역 숨김 */
  .solution-area {
    max-height: 0;
    opacity: 0;
    overflow: hidden;
    transition: max-height 0.3s ease, opacity 0.2s ease, margin-top 0.3s ease;
    box-sizing: border-box;
  }

  /* ─── 힌트 텍스트 ─── */
  .hint-text {
    position: relative;
    margin-top: 26px;  
    font-size: 12px;
    color: #4a154b;
    font-weight: bold;
    text-align: right;
    line-height: 1.5;
    z-index: 10;
  }

  .hint-text::after {
    content: "해결책 보기 ▽";
  }

  /* ─── 핵심 인터랙션: 클릭(체크) 시 ─── */
  .focus-trigger:checked + .focus-card {
    border-color: #4a154b;
    background-color: #faf6fa;
    box-shadow: 0 8px 20px rgba(74, 21, 75, 0.1);
    overflow: visible;
  }

  /* 해결책 영역 노출 */
  .focus-trigger:checked + .focus-card .solution-area {
    max-height: 500px; 
    opacity: 1;
    margin-top: 15px; 
    padding-top: 15px;
    border-top: 1px dashed #4a154b;
  }

  /* 힌트 텍스트 문구 및 간격 변경 */
  .focus-trigger:checked + .focus-card .hint-text {
    margin-top: 15px;
  }

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

  /* 모바일 대응 (화면이 좁아지면 1줄에 1개씩 보이도록 처리) */
  @media (max-width: 768px) {
    .card-grid {
      grid-template-columns: 1fr;
    }
  }
</style>

<div class="card-grid">

  <div class="grid-item">
    <input type="checkbox" id="f1" class="focus-trigger">
    <label for="f1" class="focus-card">
      <div class="card-body">
        <div style="font-weight: bold; color: #0d47a1; background: #e3f2fd; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">AUTH</div>
        <h3 style="margin: 8px 0 4px 0; font-size: 16px; color: #1d1c1d;">🚨 invalid_auth 에러</h3>
        <p class="card-desc">슬랙 웹훅이나 API 전송 시 인증 실패 토큰 반환 현상</p>
      </div>
      <div class="hint-text"></div>
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

  <div class="grid-item">
    <input type="checkbox" id="f2" class="focus-trigger">
    <label for="f2" class="focus-card">
      <div class="card-body">
        <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">PAYLOAD</div>
        <h3 style="margin: 8px 0 4px 0; font-size: 16px; color: #1d1c1d;">🚨 400 Bad Request</h3>
        <p class="card-desc">Block Kit을 구성하여 전송 시 규격이 맞지 않아 거절됨</p>
      </div>
      <div class="hint-text"></div>
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

  <div class="grid-item">
    <input type="checkbox" id="f3" class="focus-trigger">
    <label for="f3" class="focus-card">
      <div class="card-body">
        <div style="font-weight: bold; color: #c62828; background: #ffebee; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">NETWORK</div>
        <h3 style="margin: 8px 0 4px 0; font-size: 16px; color: #1d1c1d;">🚨 429 Too Many Requests</h3>
        <p class="card-desc">단시간 내 과도한 메시지 발송으로 인한 API 호출 제한 발생</p>
      </div>
      <div class="hint-text"></div>
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

  <div class="grid-item">
    <input type="checkbox" id="f4" class="focus-trigger">
    <label for="f4" class="focus-card">
      <div class="card-body">
        <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">TIMEOUT</div>
        <h3 style="margin: 8px 0 4px 0; font-size: 16px; color: #1d1c1d;">🚨 504 Gateway Timeout</h3>
        <p class="card-desc">슬랙 엔드포인트 응답 지연 혹은 커넥션 풀 고갈 현상</p>
      </div>
      <div class="hint-text"></div>
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

  <div class="grid-item">
    <input type="checkbox" id="f5" class="focus-trigger">
    <label for="f5" class="focus-card">
      <div class="card-body">
        <div style="font-weight: bold; color: #2e7d32; background: #e8f5e9; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">CHANNEL</div>
        <h3 style="margin: 8px 0 4px 0; font-size: 16px; color: #1d1c1d;">🚨 channel_not_found</h3>
        <p class="card-desc">메시지를 전송하려는 채널 ID가 존재하지 않거나 접근 불가한 상태</p>
      </div>
      <div class="hint-text"></div>
      <div class="solution-area">
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 1. 봇을 채널에 초대</b><br>
          비공개 채널의 경우, 슬랙 대화창에 <code>/invite @봇이름</code>을 입력하여 명시적으로 초대해야 합니다.
        </div>
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 2. 채널 ID 검증</b><br>
          채널 이름(예: #general) 대신 <code>C0123456789</code> 형태의 고유 채널 고유 ID를 사용했는지 확인하세요.
        </div>
      </div>
    </label>
  </div>

  <div class="grid-item">
    <input type="checkbox" id="f6" class="focus-trigger">
    <label for="f6" class="focus-card">
      <div class="card-body">
        <div style="font-weight: bold; color: #37474f; background: #eceff1; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">WEBHOOK</div>
        <h3 style="margin: 8px 0 4px 0; font-size: 16px; color: #1d1c1d;">🚨 404 Missing Verification</h3>
        <p class="card-desc">Incoming Webhook URL이 유효하지 않거나 삭제된 상태</p>
      </div>
      <div class="hint-text"></div>
      <div class="solution-area">
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 1. 웹훅 URL 활성화 확인</b><br>
          Slack App 설정 페이지에서 해당 Webhook URL이 여전히 활성화 상태인지(Active) 점검하세요.
        </div>
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 2. 재생성 및 주소 교체</b><br>
          웹훅을 생성한 사용자가 워크스페이스를 나간 경우 비활성화되므로, 새로운 웹훅을 생성해 교체합니다.
        </div>
      </div>
    </label>
  </div>

  <div class="grid-item">
    <input type="checkbox" id="f7" class="focus-trigger">
    <label for="f7" class="focus-card">
      <div class="card-body">
        <div style="font-weight: bold; color: #6a1b9a; background: #f3e5f5; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">ESCAPING</div>
        <h3 style="margin: 8px 0 4px 0; font-size: 16px; color: #1d1c1d;">🚨 알림 멘션 및 링크 깨짐</h3>
        <p class="card-desc">메시지 내부의 유저 ID 멘션(@)이나 하이퍼링크가 정상적으로 변환되지 않는 현상</p>
      </div>
      <div class="hint-text"></div>
      <div class="solution-area">
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 1. 슬랙 전용 멘션 문법 준수</b><br>
          유저 멘션은 일반 텍스트 대신 <code>&lt;@U12345678&gt;</code> 형태로 감싸서 발송해야 합니다.
        </div>
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 2. 특수문자 이스케이프</b><br>
          메시지 내에 포함된 <code>&amp;</code>, <code>&lt;</code>, <code>&gt;</code> 문자들을 각각 HTML Entity 형태로 변환 처리하세요.
        </div>
      </div>
    </label>
  </div>

  <div class="grid-item">
    <input type="checkbox" id="f8" class="focus-trigger">
    <label for="f8" class="focus-card">
      <div class="card-body">
        <div style="font-weight: bold; color: #00838f; background: #e0f7fa; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">FILE API</div>
        <h3 style="margin: 8px 0 4px 0; font-size: 16px; color: #1d1c1d;">🚨 files.upload 중단 에러</h3>
        <p class="card-desc">기존 파일 업로드 API 호출 시 에러가 나거나 전송이 실패하는 현상</p>
      </div>
      <div class="hint-text"></div>
      <div class="solution-area">
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 1. 신규 V2 API 메서드로 전환</b><br>
          Deprecated된 <code>files.upload</code> 대신, 새로운 방식인 <code>files.getUploadURLExternal</code> 및 <code>files.completeUploadExternal</code> 조합으로 마이그레이션하세요.
        </div>
      </div>
    </label>
  </div>

</div>
