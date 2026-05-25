# 🛠️ Slack Connector Issue Tracker

이슈 카드를 클릭하면 해당 카드만 독립적으로 강조되면서, 숨겨져 있던 구체적인 해결책 리스트가 스르륵 나타납니다.

<style>
  .card-grid {
    display: grid;
    /* 한 줄에 정확히 2개씩 배치 */
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
    margin-top: 20px;
    /* [수정] stretch를 유지하여 부모(.grid-item)들의 높이는 유지하되, 내부 정렬로 카드 높이를 제어합니다. */
    align-items: stretch; 
  }
  
  /* 그리드 아이템 wrap */
  .grid-item {
    display: flex;
    flex-direction: column;
    /* [수정] 카드가 펼쳐질 때 옆 카드는 상단에 붙어 본래 높이를 유지하도록 flex-start 설정 */
    align-items: flex-start;  
    height: 100%;  
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
    /* [수정] 무조건 부모 높이를 채우던 flex-grow: 1; 을 제거하고 너비가 100%가 되도록 변경 */
    width: 100%;
    min-height: 140px; 
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
    flex-grow: 1; 
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
    margin-top: 20px;  
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
    /* 모바일에서는 각 카드가 가로를 꽉 채우도록 설정 */
    .grid-item {
      align-items: stretch;
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
          채널 이름(예: #general) 대신 <code>C0...</code>로 시작하는 고유 채널 ID를 정확히 입력했는지 확인하세요.
        </div>
      </div>
    </label>
  </div>

  <div class="grid-item">
    <input type="checkbox" id="f6" class="focus-trigger">
    <label for="f6" class="focus-card">
      <div class="card-body">
        <div style="font-weight: bold; color: #7b1fa2; background: #f3e5f5; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">PERMISSION</div>
        <h3 style="margin: 8px 0 4px 0; font-size: 16px; color: #1d1c1d;">🚨 not_in_channel</h3>
        <p class="card-desc">봇이 참여하고 있지 않은 공개 채널에 메시지 발송을 시도함</p>
      </div>
      <div class="hint-text"></div>
      <div class="solution-area">
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 1. 자동으로 채널 조인 처리</b><br>
          메시지 전송 전에 <code>conversations.join</code> API를 호출하여 봇을 채널에 먼저 입장시킵니다.
        </div>
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 2. 수동 채널 추가</b><br>
          해당 공개 채널에 직접 들어가 봇을 멤버로 명시적 추가합니다.
        </div>
      </div>
    </label>
  </div>

  <div class="grid-item">
    <input type="checkbox" id="f7" class="focus-trigger">
    <label for="f7" class="focus-card">
      <div class="card-body">
        <div style="font-weight: bold; color: #00796b; background: #e0f2f1; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">SIZE</div>
        <h3 style="margin: 8px 0 4px 0; font-size: 16px; color: #1d1c1d;">🚨 msg_too_long</h3>
        <p class="card-desc">슬랙 텍스트 필드의 최대 제한 단위를 초과하는 텍스트 전송</p>
      </div>
      <div class="hint-text"></div>
      <div class="solution-area">
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 1. 글자 수 청크 분할</b><br>
          텍스트 본문이 4,000자를 넘지 않도록 코드가 자동으로 문자열을 분할(Chunking)해 순차 전송하게 합니다.
        </div>
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 2. 스니펫 업로드 기능 활용</b><br>
          로그나 긴 텍스트 데이터의 경우 메시지 대신 <code>files.upload</code> API를 이용해 파일 형태로 전송합니다.
        </div>
      </div>
    </label>
  </div>

  <div class="grid-item">
    <input type="checkbox" id="f8" class="focus-trigger">
    <label for="f8" class="focus-card">
      <div class="card-body">
        <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px;">USER</div>
        <h3 style="margin: 8px 0 4px 0; font-size: 16px; color: #1d1c1d;">🚨 user_not_found</h3>
        <p class="card-desc">DM(다이렉트 메시지) 발송 시 대상 유저 식별자 오류 혹은 탈퇴된 계정</p>
      </div>
      <div class="hint-text"></div>
      <div class="solution-area">
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 1. 유저 ID 매핑 점검</b><br>
          디스플레이 네임(이름)이 아닌, <code>U</code>로 시작하는 고유 유저 ID(예: U123456)를 사용했는지 검증하세요.
        </div>
        <div class="sol-box">
          <b style="color: #4a154b;">해결책 2. 이메일 기반 검색 연동</b><br>
          유저 ID가 가변적이라면 <code>users.lookupByEmail</code> API를 통해 최신 ID를 매번 조회 후 전송하세요.
        </div>
      </div>
    </label>
  </div>

</div>
