<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>슬랙 커넥터 이슈 해결 가이드 (카드 뒤집기 완벽 수정본)</title>
  <style>
    /* 기본 스타일 리셋 */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    body {
      background-color: #f5f7fb;
      color: #333;
      padding: 40px 20px;
    }
    .container {
      max-width: 1200px;
      margin: 0 auto;
    }
    header {
      text-align: center;
      margin-bottom: 40px;
    }
    header h1 {
      font-size: 2.2rem;
      color: #4a154b;
      margin-bottom: 10px;
    }
    header p {
      color: #666;
    }
    /* 카테고리 필터 스타일 */
    .filter-container {
      display: flex;
      justify-content: center;
      gap: 10px;
      margin-bottom: 40px;
      flex-wrap: wrap;
    }
    .filter-btn {
      background-color: #fff;
      border: 2px solid #e0e0e0;
      padding: 10px 20px;
      border-radius: 30px;
      cursor: pointer;
      font-weight: 600;
      transition: all 0.2s ease;
    }
    .filter-btn:hover, .filter-btn.active {
      background-color: #4a154b;
      border-color: #4a154b;
      color: #fff;
    }
    /* 카드 그리드 레이아웃 */
    .card-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
      gap: 30px;
    }
    /* ─── 카드 뒤집기 애니메이션 ─── */
    .card-scene {
      height: 380px;
      perspective: 1000px; /* 3D 효과 */
    }
    .card {
      width: 100%;
      height: 100%;
      position: relative;
      transform-style: preserve-3d;
      transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
      cursor: pointer;
    }
    /* 뒤집기 클래스 활성화 상태 */
    .card.is-flipped {
      transform: rotateY(180deg);
    }
    .card-face {
      position: absolute;
      width: 100%;
      height: 100%;
      backface-visibility: hidden; /* 뒷면 가리기 */
      border-radius: 16px;
      padding: 24px;
      box-shadow: 0 4px 15px rgba(0,0,0,0.05);
      display: flex;
      flex-direction: column;
      border: 1px solid rgba(0,0,0,0.08);
    }
    /* 앞면 스타일 */
    .card-front {
      background-color: #ffffff;
      justify-content: space-between;
    }
    .badge {
      align-self: flex-start;
      padding: 4px 12px;
      border-radius: 12px;
      font-size: 0.75rem;
      font-weight: bold;
    }
    .badge.auth { background-color: #e3f2fd; color: #0d47a1; }
    .badge.payload { background-color: #fff3e0; color: #e65100; }
    .badge.network { background-color: #ffebee; color: #c62828; }
    .issue-title {
      font-size: 1.25rem;
      margin-top: 15px;
      color: #1d1c1d;
      line-height: 1.4;
    }
    .issue-desc {
      font-size: 0.9rem;
      color: #616061;
      margin-top: 10px;
      flex-grow: 1;
    }
    .flip-hint {
      text-align: right;
      font-size: 0.8rem;
      color: #4a154b;
      font-weight: bold;
    }
    /* 뒷면 스타일 */
    .card-back {
      background-color: #2c102e;
      color: #ffffff;
      transform: rotateY(180deg);
      overflow-y: auto;
    }
    .back-title {
      font-size: 1.05rem;
      border-bottom: 1px solid rgba(255,255,255,0.2);
      padding-bottom: 8px;
      margin-bottom: 15px;
      color: #ecb22e;
    }
    .solution-item {
      background: rgba(255, 255, 255, 0.08);
      border-left: 4px solid #2eb67d;
      padding: 10px 12px;
      border-radius: 0 8px 8px 0;
      margin-bottom: 12px;
      font-size: 0.88rem;
      line-height: 1.4;
    }
    .solution-item strong {
      color: #36c5f0;
      display: block;
      margin-bottom: 4px;
    }
    .solution-item code {
      background: rgba(0,0,0,0.3);
      padding: 2px 6px;
      border-radius: 4px;
      font-family: monospace;
      font-size: 0.8rem;
    }
    .back-hint {
      text-align: center;
      font-size: 0.75rem;
      color: rgba(255,255,255,0.5);
      margin-top: auto;
      padding-top: 10px;
    }
    .card-scene.hidden {
      display: none;
    }
  </style>
</head>
<body>
<div class="container">
  <header>
    <h1>Slack Connector Issue Tracker</h1>
    <p>이슈 카드를 클릭하면 다수의 해결책(Solution) 명세를 확인할 수 있습니다.</p>
  </header>
  <!-- 카테고리 필터 버튼 -->
  <div class="filter-container">
    <button class="filter-btn active" data-filter="all">전체 보기</button>
    <button class="filter-btn" data-filter="auth">인증/보안 (Auth)</button>
    <button class="filter-btn" data-filter="payload">데이터 규격 (Payload)</button>
    <button class="filter-btn" data-filter="network">네트워크/제한 (Network)</button>
  </div>
  <!-- 카드 리스트 레이아웃 -->
  <div class="card-grid" id="cardGrid">
        <!-- 카드 1: 인증 에러 -->
    <div class="card-scene" data-category="auth">
      <div class="card">
        <div class="card-face card-front">
          <span class="badge auth">Auth</span>
          <h2 class="issue-title">🚨 invalid_auth 에러 발생</h2>
          <p class="issue-desc">슬랙 API 또는 웹훅 호출 시 인증 관련 실패 토큰 응답이 떨어지며 메시지 전송이 거부되는 현상.</p>
          <div class="flip-hint">클릭해서 해결책 보기 ↻</div>
        </div>
        <div class="card-face card-back">
          <h2 class="back-title">💡 복수 해결 방안</h2>
          <div class="solution-item">
            <strong>해결책 1. 토큰 스코프 재검토</strong>
            봇 토큰에 <code>chat:write</code> 또는 <code>incoming-webhook</code> 권한이 누락되었는지 App 설정에서 확인하세요.
          </div>
          <div class="solution-item">
            <strong>해결책 2. 워크스페이스 재인증</strong>
            앱 권한 스코프를 변경한 경우, 반드시 <b>Reinstall to Workspace</b> 버튼을 눌러 다시 연동해야 토큰이 갱신됩니다.
          </div>
          <div class="back-hint">다시 클릭하면 돌아갑니다</div>
        </div>
      </div>
    </div>
    <!-- 카드 2: 페이로드 규격 에러 -->
    <div class="card-scene" data-category="payload">
      <div class="card">
        <div class="card-face card-front">
          <span class="badge payload">Payload</span>
          <h2 class="issue-title">🚨 400 Bad Request (missing_text_or_fallback)</h2>
          <p class="issue-desc">블록 키트(Block Kit)를 구성하여 전송할 때 슬랙 서버 측에서 형식이 올바르지 않다며 거절하는 케이스.</p>
          <div class="flip-hint">클릭해서 해결책 보기 ↻</div>
        </div>
        <div class="card-face card-back">
          <h2 class="back-title">💡 복수 해결 방안</h2>
          <div class="solution-item">
            <strong>해결책 1. 최상위 fallback 필드 삽입</strong>
            <code>blocks</code> 배열을 보낼 때 알림창 파싱용 <code>text</code>나 <code>fallback</code> 스트링 필드를 반드시 최상위에 정의해야 합니다.
          </div>
          <div class="solution-item">
            <strong>해결책 2. Block Kit Builder 검증</strong>
            슬랙 공식 웹 도구인 Block Kit Builder에 JSON 구조를 붙여넣어 마크다운 문법 오류 유무를 체크하세요.
          </div>
          <div class="back-hint">다시 클릭하면 돌아갑니다</div>
        </div>
      </div>
    </div>
    <!-- 카드 3: 네트워크 레이트 리밋 에러 -->
    <div class="card-scene" data-category="network">
      <div class="card">
        <div class="card-face card-front">
          <span class="badge network">Network</span>
          <h2 class="issue-title">🚨 HTTP 429 Too Many Requests</h2>
          <p class="issue-desc">단시간 내에 특정 채널 혹은 앱 내부에서 너무 많은 메시지 API를 발송하여 API 호출 제한에 걸리는 현상.</p>
          <div class="flip-hint">클릭해서 해결책 보기 ↻</div>
        </div>
        <div class="card-face card-back">
          <h2 class="back-title">💡 복수 해결 방안</h2>
          <div class="solution-item">
            <strong>해결책 1. 요청 큐(Queue) 체계 도입</strong>
            초당 1회 스로틀링(Tier 3 기본 규격) 기준을 맞추기 위해 인메모리 큐나 Redis Queue를 이용해 발송 속도를 제어합니다.
          </div>
          <div class="solution-item">
            <strong>해결책 2. Retry-After 헤더 파싱</strong>
            429 에러 응답 시 함께 넘어오는 <code>Retry-After</code> 헤더 값을 읽어, 해당 초(seconds)만큼 대기(Backoff) 후 재시도 하도록 로직을 작성합니다.
          </div>
          <div class="back-hint">다시 클릭하면 돌아갑니다</div>
        </div>
      </div>
    </div>
  </div>
</div>
<script>
  // [수정 완료] 인라인 에러 유발 코드 완전 제거 후 안정적인 리스너 방식으로 변경
  const allCards = document.querySelectorAll('.card');
    allCards.forEach(card => {
    card.addEventListener('click', () => {
      card.classList.toggle('is-flipped');
    });
  });
  // 카테고리 필터링 로직
  const filterButtons = document.querySelectorAll('.filter-btn');
  const cardScenes = document.querySelectorAll('.card-scene');
  filterButtons.forEach(button => {
    button.addEventListener('click', () => {
      filterButtons.forEach(btn => btn.classList.remove('active'));
      button.classList.add('active');
      const filterValue = button.getAttribute('data-filter');
      cardScenes.forEach(scene => {
        const innerCard = scene.querySelector('.card');
        if (innerCard.classList.contains('is-flipped')) {
          innerCard.classList.remove('is-flipped');
        }
        if (filterValue === 'all' || scene.getAttribute('data-category') === filterValue) {
          scene.classList.remove('hidden');
        } else {
          scene.classList.add('hidden');
        }
      });
    });
  });
</script>
</body>
</html>
