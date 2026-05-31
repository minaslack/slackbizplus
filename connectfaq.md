# 🛠️ Slack Connect Issue Guide

Slack Connect 사용 시의 에러 메세지등에 대해서 <strong>조치가 가능한 일반적인 방법</strong>을 안내합니다.<br>
본 가이드로 해결이 되지 않는 부분은 /feedback 또는 feedback@slack.com 을 통하여 Slack 피드백팀의 지원을 받으시는 것을 권장드립니다.<br>

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
  #tab-upgrade:checked ~ .filter-bar label[for="tab-upgrade"],
  #tab-invite:checked ~ .filter-bar label[for="tab-invite"],
  #tab-timeout:checked ~ .filter-bar label[for="tab-timeout"],
  #tab-issue:checked ~ .filter-bar label[for="tab-issue"],
  #tab-permission:checked ~ .filter-bar label[for="tab-permission"] {
    background: #4a154b;
    color: #ffffff;
    border-color: #4a154b;
    box-shadow: 0 2px 8px rgba(74, 21, 75, 0.2);
  }

  /* ─── [추가] 필터링 핵심 로직 ─── */
  #tab-upgrade:checked ~ .card-grid .grid-item:not(.cat-upgrade),
  #tab-invite:checked ~ .card-grid .grid-item:not(.cat-invite),
  #tab-timeout:checked ~ .card-grid .grid-item:not(.cat-timeout),
  #tab-issue:checked ~ .card-grid .grid-item:not(.cat-issue),
  #tab-permission:checked ~ .card-grid .grid-item:not(.cat-permission),
  #tab-ready:checked ~ .card-grid .grid-item:not(.cat-ready) {
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
    font-size: 14px;
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
<input type="radio" id="tab-upgrade" name="cat-filter" class="filter-trigger">
<input type="radio" id="tab-invite" name="cat-filter" class="filter-trigger">
<input type="radio" id="tab-timeout" name="cat-filter" class="filter-trigger">
<input type="radio" id="tab-issue" name="cat-filter" class="filter-trigger">
<input type="radio" id="tab-permission" name="cat-filter" class="filter-trigger">
<input type="radio" id="tab-ready" name="cat-filter" class="filter-trigger">

<div class="filter-bar">
  <label for="tab-all" class="filter-btn">ALL</label>
  <label for="tab-upgrade" class="filter-btn">업그레이드</label>
  <label for="tab-invite" class="filter-btn">초대 수락</label>
  <label for="tab-timeout" class="filter-btn">참여 요청</label>
  <label for="tab-issue" class="filter-btn">문제 발생</label>
  <label for="tab-permission" class="filter-btn">승인 대기</label>
  <label for="tab-ready" class="filter-btn">채널 준비</label>
</div>

<div class="card-grid">

<div class="grid-item cat-upgrade">
  <input type="checkbox" id="f1" class="focus-trigger">
  <label for="f1" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #0d47a1; background: #e3f2fd; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 8px;">업그레이드</div>
      <div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 16px;">
        <div style="flex: 1;">
          <h3 style="margin: 0 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 업그레이드할 준비가 되셨나요?</h3>
          <p class="card-desc" style="margin: 0;">공유 채널은 Slack 유료플랜을 통해 제공받게 될 기능 중 하나에 불과합니다. 초대를 수락하려면, 계정을 업그레이드하세요.</p>
        </div>
        <div style="flex-shrink: 0;">
          <img width="380" height="200" alt="image" src="https://github.com/user-attachments/assets/def830a8-1111-4faf-80ec-e3f495cfa92a" style="max-width: 100%; height: auto;" />
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

<div class="grid-item cat-invite">
  <input type="checkbox" id="f2" class="focus-trigger">
  <label for="f2" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 8px;">초대 수락</div>
      <div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 16px;">
        <div style="flex: 1;">
          <h3 style="margin: 0 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 초대를 수락할 수 없습니다.</h3>
          <p class="card-desc" style="margin: 0;">연결 가능한 조직의 수를 초과하였습니다.</p>
        </div>
        <div style="flex-shrink: 0;">
          <img width="380" height="200" alt="image" src="https://github.com/user-attachments/assets/0dd86bfa-3b7f-4d60-bb8b-35e69ce48fef" style="max-width: 100%; height: auto;" />
        </div>
      </div>
    </div>
    <div class="hint-text"></div>
    <div class="solution-area">
      <div class="sol-box">
하나의 채널에 <b>250개 이상의 조직</b>이 연결되어있는 경우에는 더이상 연결할 수 없습니다.
      </div>
    </div>
  </label>
</div>

<div class="grid-item cat-invite">
  <input type="checkbox" id="f3" class="focus-trigger">
  <label for="f3" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 12px;">초대 수락</div>
      <div style="display: flex; flex-direction: row; align-items: flex-start; justify-content: space-between; gap: 24px; width: 100%;">
        <div style="flex: 1; min-width: 0;">
          <h3 style="margin: 0 0 8px 0; font-size: 18px; color: #1d1c1d; word-break: keep-all;">🚨 Slack Connect 초대를 수락할 수 없음</h3>
          <p class="card-desc" style="margin: 0; color: #4a4a4a; font-size: 14px; line-height: 1.5; word-break: keep-all;">
            관리자가 Slack Connect 초대를 수락하는 데 필요한 권한을 공유하지 않았습니다. 관리자에게 지원을 요청할 수 있습니다.<br>
            <br>
            또는 UI상에서 [수락]버튼이 grey out 처리된 경우
          </p>
        </div>
        <div style="flex-shrink: 0; display: flex; flex-direction: column; gap: 8px; width: 300px; max-width: 45%;">
          <img width="380" height="200" alt="image" src="https://github.com/user-attachments/assets/96baa30d-579e-4bd3-b8d3-160e4dc0b8fa" style="width: 100%; height: auto; display: block; border-radius: 4px;" />
          <img width="380" height="200" alt="image" src="https://github.com/user-attachments/assets/07f3e7a6-bd7f-4ddd-a098-2245f1343223" style="width: 100%; height: auto; display: block; border-radius: 4px;" />
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
      <div style="font-weight: bold; color: #78281F; background: #F9EBEA; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 8px;">참여 요청</div>
      <div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 16px;">
        <div style="flex: 1;">
          <h3 style="margin: 0 0 4px 0; font-size: 17px; color: #1d1c1d;">🚨 이 채널에 참여하도록 요청해야 합니다.</h3>
          <p class="card-desc" style="margin: 0;">누군가 이 채널을 고객님과 공유하려고 하지만 개인 정보 보호 설정에서 고객님의 참여를 허용하지 않는 것 같습니다.<br></p>
        </div>
        <div style="flex-shrink: 0;">
          <img width="350" height="200" alt="image" src="https://github.com/user-attachments/assets/5803f3df-2cf5-4291-b0f5-70c225afc839" style="max-width: 100%; height: auto;" />
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

<div class="grid-item cat-issue">
  <input type="checkbox" id="f5" class="focus-trigger">
  <label for="f5" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #2e7d32; background: #e8f5e9; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 8px;">문제 발생</div>
      <div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 16px;">
        <div style="flex: 1;">
          <h3 style="margin: 0 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 문제가 발생했습니다.</h3>
          <p class="card-desc" style="margin: 0;">Something went wrong<br>If the problem persists, please drop us a line.</p>
        </div>
        <div style="flex-shrink: 0;">
          <img width="380" height="200" alt="image" src="https://github.com/user-attachments/assets/8a58c508-87d2-4e1d-95b6-52bff6d900f3" style="max-width: 100%; height: auto;" />
        </div>
      </div>
    </div>
    <div class="hint-text"></div>
    <div class="solution-area">
      <div class="sol-box">
/feedback 또는 feedback@slack.com 을 통해 문의하시기 바랍니다.
      </div>
    </div>
  </label>
</div>

<div class="grid-item cat-permission">
  <input type="checkbox" id="f6" class="focus-trigger">
  <label for="f6" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #7b1fa2; background: #f3e5f5; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 8px;">승인 대기</div>
      <div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 16px;">
        <div style="flex: 1;">
          <h3 style="margin: 0 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 관리자 승인 대기 중</h3>
          <p class="card-desc" style="margin: 0;">채널에 가입하기 위한 이 초대를 이미 수락했습니다. 채널은 내 조직 관리자 중 한 명의 승인만 받으면 됩니다. 채널이 연계되면 Slack으로 알림 메시지가 표시됩니다.</p>
        </div>
        <div style="flex-shrink: 0;">
          <img width="380" height="200" alt="image" src="https://github.com/user-attachments/assets/e633e8ba-9785-44dc-a1fd-ea7d75d26bc5" style="max-width: 100%; height: auto;" />
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
    </div>
  </label>
</div>

<div class="grid-item cat-invite">
  <input type="checkbox" id="f7" class="focus-trigger">
  <label for="f7" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 8px;">초대 수락</div>
      <div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 16px;">
        <div style="flex: 1;">
          <h3 style="margin: 0 0 4px 0; font-size: 16px; color: #1d1c1d;">🚨 이 Slack Connect 초대를 수락할 수 없음</h3>
          <p class="card-desc" style="margin: 0;">Slack Connect 초대는 14일 동안만 활성화됩니다. 14일이 되지 않은 경우 발송인이 초대를 취소했을 수 있습니다.</p>
        </div>
        <div style="flex-shrink: 0;">
          <img width="340" height="200" alt="image" src="https://github.com/user-attachments/assets/9d0b6594-6a07-4802-ab1d-0609d59a2c60" style="max-width: 100%; height: auto;" />
        </div>
      </div>
    </div>
    <div class="hint-text"></div>
    <div class="solution-area">
      <div class="sol-box">
        Slack Connect 초대는 14일간 유효하며, 이러한 메세지가 발생하는 경우 14일이 지났거나, 또는 초대하는 조직에서 사용자나 관리자가 초대 철회를 한 경우에 발생할 수 있습니다.<br>
<b>새로운 Slack Connect 초대를 보내면 됩니다.</b><br>
      </div>
    </div>
  </label>
</div>

<div class="grid-item cat-invite">
  <input type="checkbox" id="f8" class="focus-trigger">
  <label for="f8" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #e65100; background: #fff3e0; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 8px;">초대 수락</div>
      <div style="display: flex; align-items: flex-start; justify-content: space-between; gap: 16px;">
        <div style="flex: 1;">
          <h3 style="margin: 0 0 4px 0; font-size: 18px; color: #1d1c1d;">🚨 초대를 수락할 수 없습니다.</h3>
          <p class="card-desc" style="margin: 0;">팀에서 고객님이 액세스할 수 없는 워크스페이스에 이 채널을 추가한 것 같습니다.</p>
        </div>
        <div style="flex-shrink: 0;">
          <img width="350" height="200" alt="image" src="https://github.com/user-attachments/assets/3d2806e7-d48f-4c38-a287-653565e1d297" style="max-width: 100%; height: auto;" />
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
    </div>
  </label>
</div>

<div class="grid-item cat-ready">
  <input type="checkbox" id="f9" class="focus-trigger">
  <label for="f9" class="focus-card">
    <div class="card-body">
      <div style="font-weight: bold; color: #7D6608; background: #FEF9E7; padding: 2px 6px; border-radius: 8px; width: fit-content; font-size: 11px; margin-bottom: 12px;">채널 준비</div>
      <div style="display: flex; flex-direction: row; align-items: flex-start; justify-content: space-between; gap: 24px; width: 100%;">
        <div style="flex: 1; min-width: 0;">
          <h3 style="margin: 0 0 8px 0; font-size: 18px; color: #1d1c1d; word-break: keep-all;">🚨 채널이 곧 준비됩니다.</h3>
          <p class="card-desc" style="margin: 0; color: #4a4a4a; font-size: 14px; line-height: 1.5; word-break: keep-all;">
            이 채널은 계속 진행하기 전에 관리자의 승인을 받아야합니다. 원하는 경우, 준비가 됐을 때 고객님을 추가해드릴 수 있습니다.
          </p>
        </div>
        <div style="flex-shrink: 0; display: flex; flex-direction: column; gap: 8px; width: 300px; max-width: 45%;">
          <img width="380" height="200" alt="image" src="https://github.com/user-attachments/assets/d13fd43f-bb9e-471b-8873-7f4d9aa2215a" style="width: 100%; height: auto; display: block; border-radius: 4px;" />
          <img width="380" height="200" alt="image" src="https://github.com/user-attachments/assets/f6e2e707-c35b-4536-9f8f-2b403f3a2837" style="width: 100%; height: auto; display: block; border-radius: 4px;" />
        </div>
      </div>
    </div>
    <div class="hint-text"></div>
    <div class="solution-area" style="margin-top: 16px;">
      <div class="sol-box">
        <span class="sol-title">해결책 1. 유저 ID 매핑 점검</span><br>
        상대방 조직의 멤버 A,B 를 동시에 초대하고 멤버 A 가 먼저 초대를 수락하였으나, 아직 양 조직/워크스페이스의 관리자 승인이 되지 않았을 때 멤버 B 가 초대 링크를 클릭하게 되는 경우 나오는 화면 입니다.<br>
        이때 준비되면 본인 추가 버튼을 눌러두면 향후 양 조직/워크스페이스의 관리자 승인이 되었을 때 자동으로 추가됩니다.<br>
      </div>
    </div>
  </label>
</div>
</div>
