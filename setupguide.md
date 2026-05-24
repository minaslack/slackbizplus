# 관리자 기본 설정

<div style="display: flex; gap: 20px; margin-bottom: 20px; flex-wrap: wrap;">
  
  <div style="flex: 1; min-width: 250px; border: 2px solid #e1e4e8; padding: 24px; border-radius: 12px; background: #ffffff; display: flex; flex-direction: column; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
    <h4 style="margin: 0 0 15px 0; color: #1a1f23;">⚙️ 워크스페이스 기본 설정</h4>
    <div style="font-size: 0.9em; color: #586069; line-height: 1.6; margin-bottom: 20px;">
      <p style="margin: 4px 0;">• 워크스페이스 이름 및 URL</p>
      <p style="margin: 4px 0;">• 워크스페이스 아이콘</p>
      <p style="margin: 4px 0;">• 워크스페이스 언어</p>
    </div>
    <a href="javascript:void(0);" onclick="document.getElementById('basic-setup-section').scrollIntoView({behavior: 'smooth'});" style="margin-top: auto; color: #0366d6; font-size: 0.9em; font-weight: bold; text-decoration: none; border-top: 1px solid #f1f3f5; padding-top: 15px; cursor: pointer;">설정하러 가기 →</a>
  </div>

  <div style="flex: 1; min-width: 250px; border: 2px solid #e1e4e8; padding: 24px; border-radius: 12px; background: #ffffff; display: flex; flex-direction: column; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
    <h4 style="margin: 0 0 15px 0; color: #1a1f23;">👥 멤버 관리 및 접근 권한</h4>
    <div style="font-size: 0.9em; color: #586069; line-height: 1.6; margin-bottom: 20px;">
      <p style="margin: 4px 0;">• 승인된 이메일 도메인 허용</p>
      <p style="margin: 4px 0;">• 기본 채널</p>
      <p style="margin: 4px 0;">• 새 사용자 알림</p>
      <p style="margin: 4px 0;">• 이름 지침 표시</p>
      <p style="margin: 4px 0;">• 이메일 표시</p>
      <p style="margin: 4px 0;">• Slack Connect 멤버 프로필</p>
    </div>
    <a href="javascript:void(0);" onclick="document.getElementById('member-setup-section').scrollIntoView({behavior: 'smooth'});" style="margin-top: auto; color: #0366d6; font-size: 0.9em; font-weight: bold; text-decoration: none; border-top: 1px solid #f1f3f5; padding-top: 15px; cursor: pointer;">설정하러 가기 →</a>
  </div>
  
</div>

<div style="display: flex; gap: 20px; margin-bottom: 30px; flex-wrap: wrap;">
  
  <div style="flex: 1; min-width: 250px; border: 2px solid #e1e4e8; padding: 24px; border-radius: 12px; background: #ffffff; display: flex; flex-direction: column; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
    <h4 style="margin: 0 0 15px 0; color: #1a1f23;">🚀 사용자 경험 및 기능</h4>
    <div style="font-size: 0.9em; color: #586069; line-height: 1.6; margin-bottom: 20px;">
      <p style="margin: 4px 0;">• GIF 첨부</p>
      <p style="margin: 4px 0;">• 방해 금지</p>
      <p style="margin: 4px 0;">• 채널 참여 및 나가기 메시지</p>
      <p style="margin: 4px 0;">• 모바일 사용량</p>
      <p style="margin: 4px 0;">• 캔버스</p>
      <p style="margin: 4px 0;">• 워크플로 내보내기</p>
    </div>
    <a href="javascript:void(0);" onclick="document.getElementById('experience-setup-section').scrollIntoView({behavior: 'smooth'});" style="margin-top: auto; color: #0366d6; font-size: 0.9em; font-weight: bold; text-decoration: none; border-top: 1px solid #f1f3f5; padding-top: 15px; cursor: pointer;">설정하러 가기 →</a>
  </div>

  <div style="flex: 1; min-width: 250px; border: 2px solid #e1e4e8; padding: 24px; border-radius: 12px; background: #ffffff; display: flex; flex-direction: column; box-shadow: 0 2px 5px rgba(0,0,0,0.05);">
    <h4 style="margin: 0 0 15px 0; color: #1a1f23;">📦 데이터 보관 정책</h4>
    <div style="font-size: 0.9em; color: #586069; line-height: 1.6; margin-bottom: 20px;">
      <p style="margin: 4px 0;">• 데이터 보존</p>
      <p style="margin: 4px 0;">• 파일 내역</p>
      <p style="margin: 4px 0;">• 캔버스 및 리스트 내역</p>
    </div>
    <a href="javascript:void(0);" onclick="document.getElementById('data-setup-section').scrollIntoView({behavior: 'smooth'});" style="margin-top: auto; color: #0366d6; font-size: 0.9em; font-weight: bold; text-decoration: none; border-top: 1px solid #f1f3f5; padding-top: 15px; cursor: pointer;">설정하러 가기 →</a>
  </div>
</div>

<hr style="border: 0; height: 1px; background: #e1e4e8; margin: 40px 0;">

<div id="basic-setup-section" style="padding-top: 20px; margin-bottom: 40px;">
  <h2 style="color: #1a1f23; border-left: 4px solid #0366d6; padding-left: 15px;">📍 워크스페이스 기본 설정</h2>
  <ul style="line-height: 2.0; list-style-type: disc; padding-left: 20px;">
    <li>
      <span style="font-size: 1.15rem;">
        <strong>워크스페이스 이름 및 URL</strong>: 워크스페이스의 이름과 접속 주소(URL)를 설정합니다.
      </span>
    </li>
        <div style="background-color: #F3E5F5; border-left: 5px solid #8E44AD; padding: 15px; margin: 10px 0; border-radius: 4px;">
  <span style="color: #6A1B9A; font-weight: bold;">:pushpin: 의미 있는 워크스페이스 이름과 URL을 설정하십시오. 이는 귀하의 회사, 부서, 팀 및/또는 프로젝트를 반영해야 합니다. 
</span>
</div>
    <img width="1251" alt="image" src="https://github.com/user-attachments/assets/29937071-dd2d-4173-9621-00ff6927a682" style="margin: 10px 0;" />
    <li>
      <span style="font-size: 1.15rem;">
        <strong>워크스페이스 아이콘</strong>: 팀의 정체성을 나타내는 이미지를 업로드합니다.
      </span>
    </li>
    <img width="888" alt="image" src="https://github.com/user-attachments/assets/90d42690-e24f-4b1f-81be-2f4ca52dddbb" style="margin: 10px 0;" />
    <img width="970" alt="image" src="https://github.com/user-attachments/assets/9c68d2ba-b98a-456e-9345-0da738c6bfd1" style="margin: 10px 0;" />
    <li>
      <span style="font-size: 1.15rem;">
        <strong>워크스페이스 언어</strong>: 시스템 알림, Slackbot 메시지 및 가입 이메일에 적용됩니다. <b>한국어</b>로 바꿔서 편리하게 사용하세요!!
      </span>
    </li>
    <img width="885" alt="image" src="https://github.com/user-attachments/assets/e2dfb747-62e8-4b9d-8a9d-373632554661" style="margin: 10px 0;" />
  </ul>
</div>

<div id="member-setup-section" style="padding-top: 20px; margin-bottom: 40px;">
  <h2 style="color: #1a1f23; border-left: 4px solid #0366d6; padding-left: 15px;">📍 멤버 관리 및 접근 권한</h2>
  <ul style="line-height: 2.0; list-style-type: disc; padding-left: 20px;">
    <li><span style="font-size: 1.15rem;"><strong>승인된 이메일 도메인 허용</strong>: 특정 도메인 이메일 소유자가 즉시 참여할 수 있게 합니다.</span></li>
    <div style="background-color: #F3E5F5; border-left: 5px solid #8E44AD; padding: 15px; margin: 10px 0; border-radius: 4px;">
  <span style="color: #6A1B9A; font-weight: bold;">:pushpin: 회사 도메인을 설정하면 해당 도메인 이메일을 가진 직원들이 별도 승인 없이 자동으로 워크스페이스에 참여할 수 있습니다. SSO를 사용하지 않는 경우 특히 유용하며, 다수의 인원을 빠르게 온보딩할 수 있습니다.</span>
</div>
<details style="margin-bottom: 8px; border: 1px solid #e1e4e8; border-radius: 8px; overflow: hidden;">
  <summary style="padding: 12px; cursor: pointer; background: #f6f8fa; font-weight: 600;">
    🔒 승인 없이 다수 멤버 일괄 초대 방법
    <span style="background: #ffd33d; color: #24292e; padding: 2px 8px; border-radius: 10px; font-size: 13px; margin-left: 10px;">추천</span>
  </summary>
<div style="font-family: 'Pretendard', -apple-system, sans-serif; max-width: 900px; color: #333; line-height: 1.6; border-top: 1px solid #e1e4e8;">
  <div style="padding: 20px 0 20px 0;">
    <div style="font-size: 13px; font-weight: bold; color: #007bff; margin-bottom: 5px;margin-left: 15px;">STEP 01</div>
    <div style="font-size: 15px; font-weight: bold; margin-bottom: 5px;margin-left: 15px;">이메일 도메인 설정</div>
    <div style="padding: 15px 20px; background-color: #f9f9f9; border-radius: 8px; margin-bottom: 5px;">
      1. 관리자 화면에서 설정 > 설정 및 권한 > <b>승인된 이메일 도메인 설정</b> 
    </div>
    <img width="898" alt="이메일 도메인 설정" src="https://github.com/user-attachments/assets/f73d3b75-8076-40ce-8a5c-e5b9869cc4f2" style="display: block; max-width: 100%; border: 1px solid #eee; border-radius: 4px;margin-left: auto; margin-right: auto;" />
  </div>
  <div style="padding: 20px 0 20px 0;">
    <div style="font-size: 13px; font-weight: bold; color: #007bff; margin-bottom: 5px;margin-left: 15px;">STEP 02</div>
    <div style="font-size: 15px; font-weight: bold; margin-bottom: 5px;margin-left: 15px;">사용자 초대 메뉴 이동</div>
    <div style="padding: 15px 20px; background-color: #f9f9f9; border-radius: 8px; margin-bottom: 5px;">
      2. 워크스페이스명 > 사용자 초대 버튼 클릭해서 <b>사용자 초대 팝업 오픈</b>
    </div>
    <img width="376" alt="사용자 초대 이동" src="https://github.com/user-attachments/assets/5d6b5eb1-8aaa-4e15-8942-88b6994afc1d" style="display: block; max-width: 100%; border: 1px solid #eee; border-radius: 4px; margin-left: auto; margin-right: auto;" />
  </div>
  <div style="padding: 20px 0 20px 0;">
    <div style="font-size: 13px; font-weight: bold; color: #007bff; margin-bottom: 5px;margin-left: 15px;">STEP 03</div>
    <div style="font-size: 18px; font-weight: bold; margin-bottom: 5px;margin-left: 15px;">초대 링크 복사 및 전달</div>
    <div style="padding: 15px 20px; background-color: #f9f9f9; border-radius: 8px; margin-bottom: 5px;">
      3. 이메일 설정하거나 초대 링크를 복사해서 대상자들에게 전달<br>
      <span style="font-size: 15px;">※ 설정된 도메인 계정 사용자는 별도 승인 절차 없이 <b>즉시 입장</b>이 가능합니다.</span>
    </div>
    <img width="500" alt="초대 링크 복사" src="https://github.com/user-attachments/assets/8e1d2660-c074-4850-89ca-69c24abb469a" style="display: block; max-width: 100%; border: 1px solid #eee; border-radius: 4px;margin-left: auto; margin-right: auto;" />
  </div>
</div>
</details>
    <img width="898" alt="image" src="https://github.com/user-attachments/assets/f73d3b75-8076-40ce-8a5c-e5b9869cc4f2" />
    <li><span style="font-size: 1.15rem;"><strong>기본 채널</strong>: 신규 멤버가 자동으로 입장하게 될 채널을 지정합니다.</span></li>
    <div style="background-color: #F3E5F5; border-left: 5px solid #8E44AD; padding: 15px; margin: 10px 0; border-radius: 4px;">
  <span style="color: #6A1B9A; font-weight: bold;">:pushpin: 새로운 멤버가 들어오는 경우, 기본 채널을 설정해서 바로 전사 공용 채널에 들어올 수 있도록 할 수 있습니다.</span>
</div>
    <img width="895" alt="image" src="https://github.com/user-attachments/assets/e5e11f2f-5c59-4b15-98cf-333a3b03d57e" />
    <li><span style="font-size: 1.15rem;"><strong>새 사용자 알림</strong>: 새로운 팀원이 합류했을 때 알림 여부를 설정합니다.</span></li>
    <img width="887" alt="image" src="https://github.com/user-attachments/assets/070919b8-7734-49f3-9100-f46d7132d82d" />
    <li><span style="font-size: 1.15rem;"><strong>이름 지침 표시</strong>: 멤버가 표시 이름을 설정할 때 따라야 할 가이드를 작성합니다.</span></li>
  <div style="display: flex; align-items: center; gap: 10px;">
    <img width="906" alt="image" src="https://github.com/user-attachments/assets/d6d6c55a-b661-49f5-bdb0-441f1a83987d" style="max-width: 50%; height: auto;" />
    <img width="708" alt="image" src="https://github.com/user-attachments/assets/1138564d-d2df-4827-9f2f-1e2fa849b584" style="max-width: 50%; height: auto;" />
  </div>
    <li><span style="font-size: 1.15rem;"><strong>이메일 표시</strong>: 프로필에서 멤버의 이메일 표시 여부를 결정합니다.</span></li>
    <img width="895" alt="image" src="https://github.com/user-attachments/assets/2bb6687b-84a0-403e-9cc6-260751367e89" />
    <li><span style="font-size: 1.15rem;"><strong>Slack Connect 멤버 프로필</strong>: 외부와 연계되었을 때, 상대방에게 보이는 정보를 설정할 수 있습니다.</span></li>
    <img width="919" alt="image" src="https://github.com/user-attachments/assets/76f13512-e37c-4487-af2a-e292ce10f70b" />
  </ul>
</div>
<div id="experience-setup-section" style="padding-top: 20px; margin-bottom: 40px;">
  <h2 style="color: #1a1f23; border-left: 4px solid #0366d6; padding-left: 15px;">📍 사용자 경험 및 기능</h2>
  <ul style="line-height: 2.0; list-style-type: disc; padding-left: 20px;">
    <li><span style="font-size: 1.15rem;"><strong>GIF 첨부</strong>: GIF 사용 가능 여부를 설정합니다. 멤버들이 자유롭게 사용할 수 있도록 해보세요!!</span></li>
    <img width="889" alt="image" src="https://github.com/user-attachments/assets/2bb4d19d-de9f-4817-9c8b-3545e670878d" />
    <strong>:bulb: 사용 방법</strong>
      <div style="display: flex; align-items: center; gap: 10px;">
    <img width="906" alt="image" src="https://github.com/user-attachments/assets/5bd83311-d5e5-4b40-8baa-8c8640256c09" style="max-width: 50%; height: auto;" />
    <img width="708" alt="image" src="https://github.com/user-attachments/assets/6eee558a-c6fc-44ed-b7a5-e7bcd47e4a5c" style="max-width: 50%; height: auto;" />
  </div>
    <li><span style="font-size: 1.15rem;"><strong>방해 금지</strong>: 워크스페이스 멤버에 대한 기본 <a href="https://slack.com/intl/ko-kr/help/articles/214888418-%EA%B8%B0%EB%B3%B8-%EB%B0%A9%ED%95%B4-%EA%B8%88%EC%A7%80-%EC%8B%9C%EA%B0%84-%EC%84%A4%EC%A0%95?utm_source=slack&utm_medium=settings&utm_campaign=hc" target="_blank" rel="noopener noreferrer" style="color: #0366d6; text-decoration: underline;">방해 금지</a> 시간을 설정합니다.</span></li>
    <div style="background-color: #F3E5F5; border-left: 5px solid #8E44AD; padding: 15px; margin: 10px 0; border-radius: 4px;">
  <span style="color: #6A1B9A; font-weight: bold;">:pushpin: 설정을 했더라도 멤버가 자체적으로 변경할 수 있습니다. </span>
</div>
    <img width="894" alt="image" src="https://github.com/user-attachments/assets/d9653e60-5785-4a8b-9654-bb1f0f3ca8da" />
    <li><span style="font-size: 1.15rem;"><strong>채널 참여 및 나가기 메시지</strong>: 누군가가 참여하거나 나갈 때마다 채널에 알림 여부를 선택합니다.</span></li>
    <img width="889" alt="image" src="https://github.com/user-attachments/assets/7dcfab76-f954-40ae-a25b-3fdea575c0cb" />
    <img width="551" alt="image" src="https://github.com/user-attachments/assets/4aeeba62-5a77-4193-b166-9173bcdccc93" />
    <li><span style="font-size: 1.15rem;"><strong>모바일 사용량</strong>: 멤버들에게 Slack 모바일 앱 사용 안내 메시지를 보낼지 여부를 설정합니다.</span></li>
<div style="background-color: #F3E5F5; border-left: 5px solid #8E44AD; padding: 15px; margin: 10px 0; border-radius: 4px;">
  <span style="color: #6A1B9A; font-weight: bold;">:pushpin: 초기에 데스크탑뿐만 아니라 모바일도 적극적으로 활용할 수 있게 설정하는 것을 권장합니다.</span>
</div>
    <img width="892" alt="image" src="https://github.com/user-attachments/assets/55faa989-fab3-4580-9290-e4c6c1645e92" />
    <li><span style="font-size: 1.15rem;"><strong>캔버스</strong>: 기본 설정으로 캔버스 편집자가 버전 내역을 액세스하고 복구할 수 있습니다.</span></li>
    <img width="866" alt="image" src="https://github.com/user-attachments/assets/8caf387c-b9b5-43d6-9820-3429db5b49b8" />
    <li><span style="font-size: 1.15rem;"><strong>워크플로 내보내기</strong>: 워크플로 청사진을 JSON 파일로 내보내는 것을 허용합니다.</span></li>
    <img width="895" alt="image" src="https://github.com/user-attachments/assets/8cfed4fd-cb5d-4fd8-b0a2-19b4e6e9389b" />
  </ul>
</div>
<div id="data-setup-section" style="padding-top: 20px; margin-bottom: 40px;">
  <h2 style="color: #1a1f23; border-left: 4px solid #0366d6; padding-left: 15px;">📍 데이터 보관 정책</h2>
  <ul style="line-height: 2.0; list-style-type: disc; padding-left: 20px;">
    <li><span style="font-size: 1.15rem;"><strong>데이터 보존</strong>: 메시지의 보관 기간을 설정하여 데이터를 관리합니다.</span></li>
    <div style="background-color: #F3E5F5; border-left: 5px solid #8E44AD; padding: 15px; margin: 10px 0; border-radius: 4px;">
  <span style="color: #6A1B9A; font-weight: bold;">:pushpin: 아래의 내용으로 설정하는 것으로 추천드립니다.<br>
       - 공개 채널 / 비공개 채널 / 다이렉트 메시지 모두 : [메시지를 절대 삭제하지 않음 - 편집 내용 저장]<br>
       - 데이터 보전의 재정의를 설정할 수 있는 사람 : 재정의  허용 안 함<br>
      </span>
</div>
    <img width="924" alt="image" src="https://github.com/user-attachments/assets/0cd5f181-3582-40ef-baf5-093fdea158d3" />
    <li><span style="font-size: 1.15rem;"><strong>파일 내역</strong>: 모든 파일의 보관 기간을 설정하며, 일정 시간이 지나면 삭제되도록 관리합니다.</span></li>
    <div style="background-color: #F3E5F5; border-left: 5px solid #8E44AD; padding: 15px; margin: 10px 0; border-radius: 4px;">
  <span style="color: #6A1B9A; font-weight: bold;">:pushpin: [삭제된 파일을 포함해 모든 파일을 보관합니다.]옵션을 권장합니다.<br> 
    추후 내역 확인이 필요할 때 삭제된 기록이 남아있지 않으면 문제가 발생할 수 있기 때문입니다.
      </span>
</div>
<img width="934" alt="image" src="https://github.com/user-attachments/assets/84e770cf-8986-4c96-a310-e00f14e4381f" />
    <li><span style="font-size: 1.15rem;"><strong>캔버스 및 리스트 내역</strong>: 캔버스, 목록, 코멘트 및 버전 내역의 보존 기간을 적용합니다.</span></li>
    <img width="899" alt="image" src="https://github.com/user-attachments/assets/bfcc4763-b445-4dc6-a497-973a34b57fa3" />
  </ul>
</div>
