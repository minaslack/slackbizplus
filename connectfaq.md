# 🛠️ Slack Connect Issue Guide

Slack Connect 사용 시의 에러 메세지등에 대해서 조치가 가능한 일반적인 방법을 안내합니다.<br>
본 가이드로 해결이 되지 않는 부분은 /feedback 또는 feedback@slack.com 을 통하여 Slack 피드백팀의 지원을 받으시는 것을 권장합니다.<br>

티켓 접수시 아래와 같은 내용이 준비되면 좋습니다.<br>

1. Slack Connect 를 통해 초대가 되고 있는 채널의 ID<br>
2. 채널을 소유한 조직의 워크스페이스 URL <br>
3. Slack Connect 초대를 보내고 있는 사용자의 email / 초대한 사람의 email <br>
   초대 받는 사람이 Slack Connect 를 연결하고자 하는 워크스페이스의  URL<br>
4. 스크린샷<br>

<style>
  /* ─── [추가] 카테고리 필터 라디오 버튼 숨김 ─── */
  .filter-trigger {
    display: none !important;
  }

  /* ─── [추가] 필터 버튼 바 레이아웃 ─── */
  .filter-bar {
    display: flex;
    justify-content: center;
    gap: 8px;
    margin: 20px auto;
    max-width: 800px;
    flex-wrap: wrap;
  }

  .filter-btn {
    padding: 6px 14px;
    font-size: 12px;
    font-weight: bold;
    border-radius: 20px;
    border: 1px solid #e0e0e0;
    background: #ffffff;
    color: #616061;
    cursor: pointer;
    transition: all 0.2s ease;
  }

  .filter-btn:hover {
    background: #f4f5f7;
  }

  /* ─── [추가] 선택된 필터 버튼 스타일 활성화 (슬랙 테마 색상) ─── */
  #tab-all:checked ~ .filter-bar label[for="tab-all"],
  #tab-auth:checked ~ .filter-bar label[for="tab-auth"],
  #tab-payload:checked ~ .filter-bar label[for="tab-payload"],
  #tab-network:checked ~ .filter-bar label[for="tab-network"],
  #tab-timeout:checked ~ .filter-bar label[for="tab-timeout"],
  #tab-channel:checked ~ .filter-bar label[for="tab-channel"],
  #tab-permission:checked ~ .filter-bar label[for="tab-permission"],
  #tab-size:checked ~ .filter-bar label[for="tab-size"],
  #tab-user:checked ~ .filter-bar label[for="tab-user"] {
    background: #4a154b;
    color: #ffffff;
    border-color: #4a154b;
    box-shadow: 0 2px 8px rgba(74, 21, 75, 0.2);
  }

  /* ─── [추가] 필터링 핵심 로직 ─── */
  #tab-auth:checked ~ .card-grid .grid-item:not(.cat-auth),
  #tab-payload:checked ~ .card-grid .grid-item:not(.cat-payload),
  #tab-network:checked ~ .card-grid .grid-item:not(.cat-network),
  #tab-timeout:checked ~ .card-grid .grid-item:not(.cat-timeout),
  #tab-channel:checked ~ .card-grid .grid-item:not(.cat-channel),
  #tab-permission:checked ~ .card-grid .grid-item:not(.cat-permission),
  #tab-size:checked ~ .card-grid .grid-item:not(.cat-size),
  #tab-user:checked ~ .card-grid .grid-item:not(.cat-user) {
    display: none !important;
  }

  /* ─── 기존 카드 그리드 스타일 ─── */
  .card-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 16px;
    margin: 10px auto 0 auto;
    max-width: 800px;
    align-items: stretch; 
  }
  
  .grid-item {
    display: flex;
    flex-direction: column;
    align-items: flex-start;  
    height: 100%;  
  }

  .focus-trigger {
    display: none !important;
  }

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
    width: 100%;
    min-height: 100px; 
    transition: background-color 0.3s, border-color 0.3s, box-shadow 0.3s;
    overflow: hidden;
  }

  .focus-card:hover {
    border-color: #4a154b;
    box-shadow: 0 6px 15px rgba(0,0,0,0.1);
  }

  .card-body {
    display: flex;
    flex-direction: column;
    flex-grow: 1; 
  }

  /* ─── [수정] 이슈 설명 글자 크기 기존 13px -> 15px (두 단계 업) ─── */
  .card-desc {
    font-size: 15px;
    color: #616061;
    line-height: 1.5;
    margin: 8px 0 0 0;
  }

  .solution-area {
    max-height: 0;
    opacity: 0;
    overflow: hidden;
    transition: max-height 0.3s ease, opacity 0.2s ease, margin-top 0.3s ease;
    box-sizing: border-box;
  }

  .hint-text {
    position: relative;
    margin-top: 0px;  
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

  .focus-trigger:checked + .focus-card {
    border-color: #4a154b;
    background-color: #faf6fa;
    box-shadow: 0 8px 20px rgba(74, 21, 75, 0.1);
  }

  .focus-trigger:checked + .focus-card .solution-area {
    max-height: 600px; 
    opacity: 1;
    margin-top: 14px; 
    padding-top: 14px;
    border-top: 1px dashed #4a154b;
  }

  .focus-trigger:checked + .focus-card .hint-text {
    margin-top: 0px;
  }

  .focus-trigger:checked + .focus-card .hint-text::after {
    content: "카드 접기 △";
  }

  /* ─── [수정] 해결책 박스 내부 본문 글자 크기 기존 13px -> 15px (두 단계 업) ─── */
  .sol-box {
    background: #ffffff;
    border: 1px solid #e9ecef;
    border-left: 4px solid #2eb67d;
    padding: 12px 14px;
    border-radius: 4px;
    margin-bottom: 10px;
    font-size: 15px;
    line-height: 1.6;
    color: #333333;
    text-align: left;
  }

  /* 해결책 제목 크기도 본문 크기에 맞춰 16px로 소폭 조정 */
  .sol-title {
    font-size: 16px;
    color: #4a154b;
    font-weight: bold;
    display: inline-block;
    margin-bottom: 4px;
  }

  @media (max-width: 768px) {
    .grid-item {
      align-items: stretch;
    }
  }
</style>

<input type="radio" id="tab-all" name="cat-filter" class="filter-trigger" checked>
<input type="radio" id="tab-auth" name="cat-filter" class="filter-trigger">
<input type="radio" id="tab-payload" name="cat-filter" class="filter-trigger">
<input type="radio" id="tab-network" name="cat-filter" class="filter-trigger">
<input type="radio" id="tab-timeout" name="cat-filter" class="filter-trigger">
<input type="radio" id="tab-channel" name="cat-filter" class="filter-trigger">
<input type="radio" id="tab-permission" name="cat-filter" class="filter-trigger">
<input type="radio" id="tab-size" name="cat-filter" class="filter-trigger">
<input type="radio" id="tab-user" name="cat-filter" class="filter-trigger">

<div class="filter-bar">
  <label for="tab-all" class="filter-btn">ALL</label>
  <label for="tab-auth" class="filter-btn">AUTH</label>
  <label for="tab-payload" class="filter-btn">PAYLOAD</label>
  <label for="tab-network" class="filter-btn">NETWORK</label>
  <label for="tab-timeout" class="filter-btn">TIMEOUT</label>
  <label for="tab-channel" class="filter-btn">CHANNEL</label>
  <label for="tab-permission" class="filter-btn">PERMISSION</label>
  <label for="tab-size" class="filter-btn">SIZE</label>
  <label for="tab-user" class="filter-btn">USER</label>
</div>

<div class="card-grid">

<div class="grid-item cat-auth">
  <input type="checkbox" id="f1" class="focus-trigger">
  <label for="f1" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #0d47a1; background: #e3f2fd; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 8px;">AUTH</div>
      <div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 16px;">
        <div style="flex: 1;">
          <h3 style="margin: 0 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 invalid_auth 에러</h3>
          <p class="card-desc" style="margin: 0;">슬랙 웹훅이나 API 전송 시 인증 실패 토큰 반환 현상</p>
        </div>
        <div style="flex-shrink: 0;">
          <img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/def830a8-1111-4faf-80ec-e3f495cfa92a" style="max-width: 100%; height: auto;" />
        </div>
      </div>
    </div>
    <div class="hint-text"></div>
    <div class="solution-area">
      <div class="sol-box">
        <span class="sol-title">[해결책] 초대 워크스페이스 플랜 확인</span><br>
        <strong>초대 하고자 하는 사용자의 워크스페이스가 유료플랜인지 확인하세요.</strong><br>
        Slack Connect 는 기본적으로 유료플랜간에 사용이 가능하며, 무료 플랜은 Slack Connect 을 사용할 수 없습니다.<br>
        다만 예외적으로 초대를 보내는 조직이 Ent+ 라면 조직에서 허용하는 경우 무료워크스페이스 조직과 Slack Connect 를 통해 연결할 수 있습니다.
<br>
      </div>
    </div>
  </label>
</div>

<div class="grid-item cat-payload">
  <input type="checkbox" id="f2" class="focus-trigger">
  <label for="f2" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 8px;">PAYLOAD</div>
      <div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 16px;">
        <div style="flex: 1;">
          <h3 style="margin: 0 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 400 Bad Request</h3>
          <p class="card-desc" style="margin: 0;">Block Kit을 구성하여 전송 시 규격이 맞지 않아 거절됨</p>
        </div>
        <div style="flex-shrink: 0;">
          <img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/0dd86bfa-3b7f-4d60-bb8b-35e69ce48fef" style="max-width: 100%; height: auto;" />
        </div>
      </div>
    </div>
    <div class="hint-text"></div>
    <div class="solution-area">
      <div class="sol-box">
        <span class="sol-title">해결책 1. 최상위 fallback 필드 삽입</span><br>
하나의 채널에 250개 이상의 조직이 연결되어있는 경우에는 더이상 연결할 수 없습니다.
      </div>
    </div>
  </label>
</div>

<div class="grid-item cat-network">
  <input type="checkbox" id="f3" class="focus-trigger">
  <label for="f3" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #c62828; background: #ffebee; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 12px;">NETWORK</div>
      <div style="display: flex; flex-direction: row; align-items: flex-start; justify-content: space-between; gap: 24px; width: 100%;">
        <div style="flex: 1; min-width: 0;">
          <h3 style="margin: 0 0 8px 0; font-size: 18px; color: #1d1c1d; word-break: keep-all;">🚨 429 Too Many Requests</h3>
          <p class="card-desc" style="margin: 0; color: #4a4a4a; font-size: 14px; line-height: 1.5; word-break: keep-all;">
            단시간 내 과도한 메시지 발송으로 인한 API 호출 제한 발생
          </p>
        </div>
        <div style="flex-shrink: 0; display: flex; flex-direction: column; gap: 8px; width: 300px; max-width: 45%;">
          <img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/96baa30d-579e-4bd3-b8d3-160e4dc0b8fa" style="width: 100%; height: auto; display: block; border-radius: 4px;" />
          <img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/07f3e7a6-bd7f-4ddd-a098-2245f1343223" style="width: 100%; height: auto; display: block; border-radius: 4px;" />
        </div>
      </div>
    </div>
    <div class="hint-text"></div>
    <div class="solution-area" style="margin-top: 16px;">
      <div class="sol-box">
        <span class="sol-title">해결책 1. 메시지 발송 큐(Queue) 도입</span><br>
        상대방 조직에서 일반 멤버가 Slack Connect 초대를 수락할 수 없도록 설정해 둔 경우이거나 또는 초대 받는 사람이 멤버가 아니고 Guest 인 경우 입니다.<br>
        초대받는 사람이 상대방 조직의 관리자와 확인이 필요합니다.<br>
        임시로 사용가능한 방법으로는 상대방 조직의 관리자를 Slack Connect 로 포스트/초대 가능 권한으로 초대하고, 상대방 조직의 관리자가 직접 해당 멤버를 채널에 초대하는 것입니다.<br>
      </div>
    </div>
  </label>
</div>

<div class="grid-item cat-timeout">
  <input type="checkbox" id="f4" class="focus-trigger">
  <label for="f4" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 8px;">TIMEOUT</div>
      <div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 16px;">
        <div style="flex: 1;">
          <h3 style="margin: 0 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 504 Gateway Timeout</h3>
          <p class="card-desc" style="margin: 0;">슬랙 엔드포인트 응답 지연 혹은 커넥션 풀 고갈 현상</p>
        </div>
        <div style="flex-shrink: 0;">
          <img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/5803f3df-2cf5-4291-b0f5-70c225afc839" style="max-width: 100%; height: auto;" />
        </div>
      </div>
    </div>
    <div class="hint-text"></div>
    <div class="solution-area">
      <div class="sol-box">
        <span class="sol-title">해결책 1. 비동기(Asynchronous) 호출 전환</span><br>
        포스트만 가능한 권한을 가지고 있는 채널에서, 초대링크를 생성한뒤, 또 다른 멤버가 해당 링크를 통해 초대를 수락하는 경우 발생합니다.<br>
포스트만 가능한 권한만 있을 경우 링크를 통해서는 수락할 수 없으며, 채널을 소유한 쪽에서 링크가 아닌 이메일을 지정하여 초대를 해주어야 합니다.<br>
      </div>
    </div>
  </label>
</div>

<div class="grid-item cat-channel">
  <input type="checkbox" id="f5" class="focus-trigger">
  <label for="f5" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #2e7d32; background: #e8f5e9; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 8px;">CHANNEL</div>
      <div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 16px;">
        <div style="flex: 1;">
          <h3 style="margin: 0 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 channel_not_found</h3>
          <p class="card-desc" style="margin: 0;">메시지를 전송하려는 채널 ID가 존재하지 않거나 접근 불가한 상태</p>
        </div>
        <div style="flex-shrink: 0;">
          <img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/8a58c508-87d2-4e1d-95b6-52bff6d900f3" style="max-width: 100%; height: auto;" />
        </div>
      </div>
    </div>
    <div class="hint-text"></div>
    <div class="solution-area">
      <div class="sol-box">
        <span class="sol-title">해결책 1. 봇을 채널에 초대</span><br>
/feedback 또는  feedback@slack.com 을 통해 문의하시기 바랍니다. 
      </div>
    </div>
  </label>
</div>

<div class="grid-item cat-permission">
  <input type="checkbox" id="f6" class="focus-trigger">
  <label for="f6" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #7b1fa2; background: #f3e5f5; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 8px;">PERMISSION</div>
      <div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 16px;">
        <div style="flex: 1;">
          <h3 style="margin: 0 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 not_in_channel</h3>
          <p class="card-desc" style="margin: 0;">봇이 참여하고 있지 않은 공개 채널에 메시지 발송을 시도함</p>
        </div>
        <div style="flex-shrink: 0;">
          <img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/e633e8ba-9785-44dc-a1fd-ea7d75d26bc5" style="max-width: 100%; height: auto;" />
        </div>
      </div>
    </div>
    <div class="hint-text"></div>
    <div class="solution-area">
      <div class="sol-box">
        <span class="sol-title">해결책 1. 자동으로 채널 조인 처리</span><br>
        초대받는 조직에서 Slack Connect 초대 수락시 관리자의 승인이 필요한 경우 입니다. <br>
상대방 조직의 관리자 승인이 되지 않는 상태에서 다시 Slack Connect 초대를 보내는 경우에 발생하는 스크린샷으로, 상대방 조직의 관리자가 승인을 해야 Slack Connect 연결이 됩니다. 초대하는 사용자에게 슬랙 관리자에게 연락하도록 가이드 하시면 됩니다.<br>
      </div>
      <div class="sol-box">
        <span class="sol-title">해결책 2. 수동 채널 추가</span><br>
        해당 공개 채널에 직접 들어가 봇을 멤버로 명시적 추가합니다.
      </div>
    </div>
  </label>
</div>

<div class="grid-item cat-size">
  <input type="checkbox" id="f7" class="focus-trigger">
  <label for="f7" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #00796b; background: #e0f2f1; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 8px;">SIZE</div>
      <div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 16px;">
        <div style="flex: 1;">
          <h3 style="margin: 0 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 msg_too_long</h3>
          <p class="card-desc" style="margin: 0;">슬랙 텍스트 필드의 최대 제한 단위를 초과하는 텍스트 전송</p>
        </div>
        <div style="flex-shrink: 0;">
          <img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/9d0b6594-6a07-4802-ab1d-0609d59a2c60" style="max-width: 100%; height: auto;" />
        </div>
      </div>
    </div>
    <div class="hint-text"></div>
    <div class="solution-area">
      <div class="sol-box">
        <span class="sol-title">해결책 1. 글자 수 청크 분할</span><br>
        Slack Connect 초대는 14일간 유효하며, 이러한 메세지가 발생하는 경우 14일이 지났거나, 또는 초대하는 조직에서 사용자나 관리자가 초대 철회를 한 경우에 발생할 수 있습니다.<br>
새로운 Slack Connect 초대를 보내면 됩니다.<br>
      </div>
      <div class="sol-box">
        <span class="sol-title">해결책 2. 스니펫 업로드 기능 활용</span><br>
        로그나 긴 텍스트 데이터의 경우 메시지 대신 <code>files.upload</code> API를 이용해 파일 형태로 전송합니다.
      </div>
    </div>
  </label>
</div>

<div class="grid-item cat-auth">
  <input type="checkbox" id="f8" class="focus-trigger">
  <label for="f8" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 8px;">AUTH</div>
      <div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 16px;">
        <div style="flex: 1;">
          <h3 style="margin: 0 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 user_not_found</h3>
          <p class="card-desc" style="margin: 0;">DM(다이렉트 메시지) 발송 시 대상 유저 식별자 오류 혹은 탈퇴된 계정</p>
        </div>
        <div style="flex-shrink: 0;">
          <img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/3d2806e7-d48f-4c38-a287-653565e1d297" style="max-width: 100%; height: auto;" />
        </div>
      </div>
    </div>
    <div class="hint-text"></div>
    <div class="solution-area">
      <div class="sol-box">
        <span class="sol-title">해결책 1. 유저 ID 매핑 점검</span><br>
        아래와 같은 시나리오에 발생할 수 있습니다.<br>
초대 받는 쪽이 그리드 환경인데, 다수의 사용자를 초대하는 경우.  조직1 의 사용자 X 가 조직2 의 사용자 A,B 를 초대하는 시나리오 입니다.<br>
User A 는 조직 2의 워크스페이스 AA 의 멤버<br>
User B 는 조직 2의 워크스페이스 BB 의 멤버 <br>
User A 가 워크스페이스 AA 에서 Slack Connect 연결을 먼저 수락하는 경우 User B 는 워크스페이스 AA 의 멤버가 아니기 때문에 수락할 수 없는 경우 입니다.<br>
이 경우 상대방 조직에서 해당 채널을 AA 와 BB 에서 둘다 접근 가능한 멀티워크스페이스 채널로 만들어주거나, 또는 User B 를 워크스페이스 AA 의 멤버로 추가해주어야 합니다.<br>
      </div>
      <div class="sol-box">
        <span class="sol-title">해결책 2. 이메일 기반 검색 연동</span><br>
        유저 ID가 가변적이라면 <code>users.lookupByEmail</code> API를 통해 최신 ID를 매번 조회 후 전송하세요.
      </div>
    </div>
  </label>
</div>

<div class="grid-item cat-auth">
  <input type="checkbox" id="f8" class="focus-trigger">
  <label for="f8" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 8px;">AUTH</div>
      <div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 16px;">
        <div style="flex: 1;">
          <h3 style="margin: 0 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 user_not_found</h3>
          <p class="card-desc" style="margin: 0;">DM(다이렉트 메시지) 발송 시 대상 유저 식별자 오류 혹은 탈퇴된 계정</p>
        </div>
        <div style="flex-shrink: 0;">
          <img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/d13fd43f-bb9e-471b-8873-7f4d9aa2215a" style="max-width: 100%; height: auto;" />
        </div>
      </div>
    </div>
    <div class="hint-text"></div>
    <div class="solution-area">
      <div class="sol-box">
        <span class="sol-title">해결책 1. 유저 ID 매핑 점검</span><br>
        상대방 조직의 멤버 A,B 를 동시에 초대하고 멤버 A 가 먼저 초대를 수락하였으나, 아직 양 조직/워크스페이스의 관리자 승인이 되지 않았을 때 멤버 B 가 초대 링크를 클릭하게 되는 경우 나오는 화면 입니다.<br>
이때 준비되면 본인 추가 버튼을 눌러두면 향후 양 조직/워크스페이스의 관리자 승인이 되었을 때 자동으로 추가됩니다.<br>
</div>
      <div class="sol-box">
        <span class="sol-title">해결책 2. 이메일 기반 검색 연동</span><br>
        유저 ID가 가변적이라면 <code>users.lookupByEmail</code> API를 통해 최신 ID를 매번 조회 후 전송하세요.
      </div>
    </div>
  </label>
</div>

</div>
사본 -  구현 가이드 - Salesforce 채널
Step 1 - Slack과 Salesforce 연결

조직이 이미 Slack을 내부 협업에 사용하는지 여부에 따라 Slack을 Salesforce에 연결하는 단계가 다릅니다.

새 Slack 워크스페이스 만들기

Slack을 아직 사용하지 않는다면 다음 단계를 따라 Salesforce 환경에 연결된 Slack 워크스페이스를 즉시 만드세요. 이미 Slack 워크스페이스 또는 Enterprise Grid 조직이 있다면 다음 섹션으로 건너뛰어 기존 워크스페이스를 Salesforce에 연결하세요.
Salesforce에서:

1. 설정(Setup) 아이콘을 클릭합니다.
2. 빠른 찾기(Quick Find) 박스에서 단계별 Slack 설정(Slack Guided Setup)을 검색하여 선택합니다.
3. Slack 설정 시작(Start Slack Setup) 를 선택합니다.
4. Slack 작업 영역 만들기(Create a Slack workspace)에 시작하기(Get Started)를 클릭합니다.
5. Slack 워크스페이스 이름을 입력한 후 저장(Save)를 클릭합니다.

새 Slack 워크스페이스는 자동으로 Salesforce 환경에 연결됩니다. 기본적으로 Slack은 이메일 주소를 기반으로 사용자 계정을 매핑합니다. Federation ID를 기반으로 매핑하려면 Manage Slack Connection 페이지를 통해 수동으로 연결을 설정할 수 있습니다. Slack 워크스페이스를 탐색하려면 로그인 방법이 담긴 이메일을 받게 됩니다.

레코드 페이지에 Slack 대화 추가(Add Slack conversation to record pages)에 추가(Add)를 클릭


Step 2 - Salesforce 채널용 객체 구성

기록을 위한 Slack 채널(Slack Channels for Records)의 선택한 개체에 Slack 버튼 표시(Show Slack Button on Selected Objects) 토글 활성화
개체별 Slack 활성화의 [+개체 추가]클릭
허용할 개체 검색하여 선택 후, [개체 추가]클릭

단계별 Slack 설정
레코드 페이지에 Slack 대화 추가
이 단계는 완료했습니다 체크


다음으로, Salesforce 채널이 레코드 페이지에 표시되는 방식을 선택할 수 있습니다. 두 가지 옵션이 있습니다:
Lightning 컴포넌트 구현 방법:

1. 각 레코드 페이지에서 Lightning 앱 빌더로 이동
2. 페이지에 "Slack" 컴포넌트를 추가하고 Save를 클릭하여 완료



Step 3 - 사용자에게 Slack 접근 권한 부여

Salesforce 채널에 접근이 필요한 사용자는 Slack 계정이 필요하며, 기존 워크스페이스 사용자 모두에게 이미 접근 권한이 있다면 이 단계를 건너뛸 수 있습니다. 새 워크스페이스 연결 또는 추가 사용자 프로비저닝이 필요한 경우, Salesforce 내부 사용자 자동 프로비저닝이나 Okta 같은 ID 공급자를 활용할 수 있습니다.
Okta를 활용하는 과정을 좀 더 자세히 설명해줄래?

단계별 Slack 설정
사용자에게 Slack에 대한 액세스 권한 자동 부여
[관리]클릭

Slack 연결 관리 
사용자에게 Slack에 대한 액세스 권한 자동 부여
[관리]클릭

팝업에서 [Slack 계정 자동 생성 및 연결] 선택 후 [저장]클릭

사용자에게 Slack 접근 권한을 자동으로 부여하면 해당 사용자들은 Slack 계정을 설정하라는 이메일을 받게 됩니다.
또는 테스트 목적으로 팀원을 수동으로 초대하여 Slack 접근 권한을 부여할 수도 있습니다.


Step 4 - Slack 사용자 초대 (계정 생성)


 [Slack 계정 자동 생성 및 연결]  이메일을 기준으로 자동 연결됨
아닌 경우는 수동으로 연결해 줘야 함

https://slack.com/intl/en-gb/resources/slack-for-admins/salesforce-channels-implementation-guide







