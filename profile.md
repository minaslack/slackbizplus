
# 프로필 구성

Slack에서는 세 가지 방법 중에서 선택하여 프로필 필드를 업데이트할 수 있습니다.

1. SCIM<br>
SCIM API를 통해 프로필 필드를 자동으로 채웁니다.<br>
2. API<br>
Web API를 사용해 프로필 필드를 설정 또는 검색합니다.<br>
3. 사용자 편집 <br>
멤버는 수동으로 프로필 필드를 업데이트할 수 있습니다.<br>

<div style="background-color: #F3E5F5; border-left: 5px solid #8E44AD; padding: 15px; margin: 10px 0; border-radius: 4px;">
  <span style="color: #6A1B9A; font-weight: bold;">⚠️ 변경 후, 우측 상단의 활성화된 [변경사항 개시]버튼을 클릭해야 변경 내용이 저장됩니다.</span>
</div>

<details style="margin-bottom: 8px; border: 1px solid #e1e4e8; border-radius: 8px; overflow: hidden;">
  <summary style="padding: 16px; cursor: pointer; background: #fafbfc; font-weight: 700; color: #24292e; display: flex; align-items: center; justify-content: space-between; border-radius: 8px 8px 0 0;">
    <div>
      :dart: SCIM Provisioning 활용 방법 (프로필·유저 관리 자동화)
    </div>
  </summary>
        <div style="padding: 15px; background: #fff; border-top: 1px solid #e1e4e8;">
      📌 <Strong>SCIM이란?</Strong><br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;회사의 IDP(Identity Provider, 예: Okta, Entra ID, Google)와 Slack을 연결해서 사용자 계정을 자동으로<br> 
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;생성·수정·비활성화할 수 있게 해주는 <Strong>ID 관리를 자동화하는 국제 표준 프로토콜</Strong>입니다.<br>
      <br>
        <div style="background-color: #F3E5F5; border-left: 5px solid #8E44AD; padding: 15px; margin: 10px 0; border-radius: 4px;">
<span style="color: #6A1B9A;font-weight: bold;">⚠️ SAML : 로그인 시 싱크 담당<br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SCIM : 계정 생성·수정·비활성화 등 라이프사이클 관리를 SCIM Connector 앱을 통해 별도 수행</span>
</div>
      <br>
      🌟 <Strong>IDP별 지원 현황</Strong><br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 설정 하면서 슬랙에 해당 IDP의 SCIM Connector 설치가 진행됨. (<Strong>Org레벨</Strong>에 설치필요) <br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 만약 SCIM Connector 가 없다면 Custom SCIM Connector 제작이 필요합니다.<br>
<table style="width: 100%; margin: 10px 0 0 10px; border-collapse: collapse; font-size: 13px; line-height: 1.5; background-color: #ffffff;">
<thead>
  <tr style="background: #f8f9fa;">
    <th style="padding: 12px 15px; border: 1px solid #e1e4e8; text-align: center; font-weight: 700; color: #1d1c1d; white-space: nowrap;">IDP</th>
    <th style="padding: 12px 15px; border: 1px solid #e1e4e8; text-align: center; font-weight: 700; color: #1d1c1d; white-space: nowrap;">SCIM 연동 앱</th>
    <th style="padding: 12px 15px; border: 1px solid #e1e4e8; text-align: center; font-weight: 700; color: #1d1c1d; white-space: nowrap;">비고</th>
    <th style="padding: 12px 15px; border: 1px solid #e1e4e8; text-align: center; font-weight: 700; color: #1d1c1d; white-space: nowrap;">공식 설정 문서</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td style="padding: 10px 15px; border: 1px solid #e1e4e8; text-align: center; font-weight: 600; white-space: nowrap;">Entra ID</td>
    <td style="padding: 10px 15px; border: 1px solid #e1e4e8; text-align: center; white-space: nowrap;">Microsoft Azure AD Provisioning</td>
    <td style="padding: 10px 15px; border: 1px solid #e1e4e8; text-align: center; white-space: nowrap;">-</td>
    <td style="padding: 10px 15px; border: 1px solid #e1e4e8; text-align: center; font-weight: 600; white-space: nowrap;">
      <a href="https://learn.microsoft.com/en-us/entra/identity/saas-apps/slack-provisioning-tutorial" target="_blank" style="color: #007bff; text-decoration: none;">링크</a>
    </td>
  </tr>
  <tr>
    <td style="padding: 10px 15px; border: 1px solid #e1e4e8; text-align: center; font-weight: 600; white-space: nowrap;">Okta</td>
    <td style="padding: 10px 15px; border: 1px solid #e1e4e8; text-align: center; white-space: nowrap;">Okta Provisioning</td>
    <td style="padding: 10px 15px; border: 1px solid #e1e4e8; text-align: center; white-space: nowrap;">-</td>
    <td style="padding: 10px 15px; border: 1px solid #e1e4e8; text-align: center; white-space: nowrap;">
      <a href="https://help.okta.com/en-us/content/topics/provisioning/slack/slck-integrate-slack.htm" target="_blank" style="color: #007bff; text-decoration: none;">링크</a>
    </td>
  </tr>
  <tr>
    <td style="padding: 10px 15px; border: 1px solid #e1e4e8; text-align: center; font-weight: 600; white-space: nowrap;">Google</td>
    <td style="padding: 10px 15px; border: 1px solid #e1e4e8; text-align: center; white-space: nowrap;">제한적</td>
    <td style="padding: 10px 15px; border: 1px solid #e1e4e8; text-align: center; white-space: nowrap;">이름·이메일 등 일부 필드만, 그룹 푸시❌</td>
    <td style="padding: 10px 15px; border: 1px solid #e1e4e8; text-align: center; white-space: nowrap;">
      <a href="https://knowledge.workspace.google.com/admin/users/advanced/configure-slack-user-provisioning?sjid=17221264273189227714-AP&visit_id=639104557331627052-2063466825&rd=1&hl=ko" target="_blank" style="color: #007bff; text-decoration: none;">링크</a>
    </td>
  </tr>
</tbody>
</table>
    </div>
</details>
<details style="margin-bottom: 8px; border: 1px solid #e1e4e8; border-radius: 8px; overflow: hidden;">
  <summary style="padding: 16px; cursor: pointer; background: #fafbfc; font-weight: 700; color: #24292e; display: flex; align-items: center; justify-content: space-between; border-radius: 8px 8px 0 0;">
    <div>
      :dart: SCIM API를 활용한 Atlas 설정 방법
    </div>
  </summary>
        <div style="padding: 15px; background: #fff; border-top: 1px solid #e1e4e8;">
          📌 SCIM API를 활용한 Atlas[Add-On기능] 설정가이드입니다.<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<Strong>초기설정1,2 완료 후 사용자 업데이트</Strong> 진행해주세요.<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;해당 방식으로 사용자 프로필정보(SCIM API타입 항목)도 업데이트 가능합니다.<br>
          <a href="https://slack.com/intl/ko-kr/help/articles/22467765879315-Slack-%EC%95%84%ED%8B%80%EB%9D%BC%EC%8A%A4%EB%A1%9C-%ED%94%84%EB%A1%9C%ED%95%84-%EC%82%AC%EC%9A%A9%EC%9E%90-%EC%A7%80%EC%A0%95#%EC%97%94%ED%84%B0%ED%94%84%EB%9D%BC%EC%9D%B4%EC%A6%88-%ED%94%8C%EB%9E%9C-2" target="_blank" 
     rel="noopener noreferrer" style="color: #1264a3; text-decoration: none;">📌 Slack 아틀라스로 프로필 사용자 지정</a></li>
          <br>
          <img src="asset/image/Org_Chart.png"
     alt="Slack Admin Guide"
     width="400"
     loading="eager"
      </div>
<details style="border-radius: 6px; overflow: hidden;">
      <summary style="padding: 10px 15px; cursor: pointer; font-weight: 600; outline: none;">
        1️⃣ [초기설정1]SCIM API를 호출 하기 위한 앱 생성
      </summary>
    <div style="padding: 20px; border-top: 1px solid #e1e4e8; background: #fff; border-radius: 0 0 8px 8px;">
    <div style="display: flex; align-items: center; justify-content: flex-start; gap: 30px; flex-wrap: nowrap;">
      <div style="flex-shrink: 0;">
        <div style="margin-bottom: 8px; font-weight: 600; color: #444; font-size: 14px;">✔️ 영상 가이드</div>
        <video width="400" controls style="border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.06); border: 1px solid #e1e4e8; display: block;">
          <source src="https://github.com/minaslack/slackbizplus/releases/download/v1.0/Setup01_SCIMAPI.mp4" type="video/mp4">
        </video>
      </div>
    </div>
  </div>
      <div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
        1) <a href="http://api.slack.com/apps" target="_blank" rel="noopener" style="color: #1264a3; text-decoration: underline; font-size: 15px; font-weight: 600;"> api.slack.com/apps </a>으로 접속 > [Create New App] 버튼 클릭
        </div>
      <img width="1301" alt="image" src="https://github.com/user-attachments/assets/6d9b0386-b79d-4ef6-959b-308e3a483875" />
      <div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
        2) From scratch 선택
      </div>
      <img width="508" alt="image" src="https://github.com/user-attachments/assets/8493ad6c-42fd-40ce-b9e9-d37cf47cb7b2" />
<div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
        3) APP 이름을 지정하고, 워크스페이스를 선택 후 [Create App]버튼 클릭
      </div>
      <img width="512" alt="image" src="https://github.com/user-attachments/assets/1395a0f7-579d-4f4d-8403-da8da4bcf92d" />
      <div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
        4) 사이드바의 [OAuth & Permissions]선택 > [Redirect URLs]섹션에 [Add New Redirect URL]버튼 클릭 후, [https://localhost]기입 >[Add]버튼 클릭 > [Save URLs]버튼 클릭
      </div>
      <img width="1225" alt="image" src="https://github.com/user-attachments/assets/de3e8501-c353-4a50-8c81-880ce33b5bd4" />
 <div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
        5) 동일 페이지 아래 [사용자 토큰 범위]섹션에 [OAuth범위 추가]버튼 클릭 후, [admin] 선택
      </div>
      <div style="display: flex; align-items: center; gap: 10px;">
    <img width="906" alt="image" src="https://github.com/user-attachments/assets/de16a797-41b6-4df5-9db3-a6782ffa7c7d" style="max-width: 50%; height: auto;" />
    <img width="708" alt="image" src="https://github.com/user-attachments/assets/4026586b-34a9-41fe-8f44-9e013c291163" style="max-width: 50%; height: auto;" />
  </div>
 <div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
        6) 사이드바의 [Manage Distribution]선택 > [Remove Hard Coded Information]의 [I've reviewed and removed any hard-coded information] 체크 후, 활성화된 [Activate public distribution]버튼 클릭<br>
   <br>
       📌 만약 [Enable Features & Functionality], [Add OAuth Redirect URLs]가 체크되어 있지 않으면 해당 페이지 새로고침 해주세요!!<br>
      </div>
      <img width="1186" alt="image" src="https://github.com/user-attachments/assets/94db60f8-8fe3-4c6c-bfbb-d05c8cff2583" />
 <div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
        7) 사이드바의 [Basic Information]선택 > Client ID & Client Secret 복사
      </div>
<img width="1103" alt="image" src="https://github.com/user-attachments/assets/ee5592a4-d2f9-4dee-a27a-e92206b86951" />
      </details>
        <details style="border-radius: 6px; overflow: hidden;">
      <summary style="padding: 10px 15px; cursor: pointer; font-weight: 600; outline: none;">
        2️⃣ [초기설정2]POST MAN 연동
      </summary>
            <div style="padding: 20px; border-top: 1px solid #e1e4e8; background: #fff; border-radius: 0 0 8px 8px;">
    <div style="display: flex; align-items: center; justify-content: flex-start; gap: 30px; flex-wrap: nowrap;">
      <div style="flex-shrink: 0;">
        <div style="margin-bottom: 8px; font-weight: 600; color: #444; font-size: 14px;">✔️ 영상 가이드</div>
        <video width="400" controls style="border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.06); border: 1px solid #e1e4e8; display: block;">
          <source src="https://github.com/minaslack/slackbizplus/releases/download/v1.0/Setup02_Postman.mp4" type="video/mp4">
        </video>
      </div>
      <div style="flex: 1; display: flex; flex-direction: column; align-items: center; justify-content: center;">
        <a href="asset/pdf/SCIM_postman_collection.json" 
           download="SCIM_postman_collection.json" 
           target="_blank" 
           title="SCIM_postman_collection.json 다운로드" 
           style="display: inline-flex; align-items: center; justify-content: center; width: 72px; height: 72px; background-color: #f0f3f6; border: 2.5px solid #0366d6; border-radius: 50%; transition: all 0.2s ease-in-out; text-decoration: none; box-shadow: 0 4px 12px rgba(3,102,214,0.15); flex-shrink: 0;"
           onmouseover="this.style.backgroundColor='#0366d6'; this.style.transform='scale(1.1)';" 
           onmouseout="this.style.backgroundColor='#f0f3f6'; this.style.transform='scale(1)';"
           onmousedown="this.style.transform='scale(0.9)';" 
           onmouseup="this.style.transform='scale(1.1)';">
          <img src="https://github.com/user-attachments/assets/efddf926-e9b0-49cf-89af-95be928c75b1" alt="PDF 다운로드" style="width: 36px; height: auto; display: block;">
        </a>
        <div style="margin-top: 10px; font-size: 13px; color: #0366d6; font-weight: 700; letter-spacing: -0.5px;">SCIM_postman_collection.json</div>
      </div>
    </div>
  </div>
         <div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
        📌 잠깐!! 우선 PostMan계정부터 생성해주세요!!<br>
           <br>
        1) <a href="https://www.postman.com/" target="_blank" rel="noopener" style="color: #1264a3; text-decoration: underline; font-size: 15px; font-weight: 600;"> Post Man </a> 오픈 > [Import]선택 > SCIM_postman_collection.json파일 import > [SCIM]폴더 신규 추가 확인
      </div>
        <div style="display: flex; align-items: center; gap: 10px;">
    <img width="906" alt="image" src="https://github.com/user-attachments/assets/94e7bdee-f008-492b-a1da-e7b8edafb30f" style="max-width: 50%; height: auto;" />
    <img width="708" alt="image" src="https://github.com/user-attachments/assets/826f06a8-dc5f-4a56-9196-0eec7b6cc7f4" style="max-width: 50%; height: auto;" />
  </div>
        <div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
        2) SCIM (Shared) > Authentication > Get access token에서 slack api page에서 발급받은 Client Id/Client Secret값 붙여넣고 [Save]버튼 클릭&nbsp;&nbsp;(**Client Secret는 [Show]버튼 클릭 후, 복사)
      </div>
        <div style="display: flex; align-items: center; gap: 10px;">
    <img width="906" alt="image" src="https://github.com/user-attachments/assets/e6013cf9-0dab-4dea-a07f-cd2963caeeb0" style="max-width: 50%; height: auto;" />
    <img width="708" alt="image" src="https://github.com/user-attachments/assets/191953e7-2e0b-43da-be36-31f32a9d37d3" style="max-width: 50%; height: auto;" />
  </div>
        <div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
        3) Slack api page에서 [Settings] > [Manage Distribution]  > Shareable URL을 복사
      </div>
<img width="1118" alt="image" src="https://github.com/user-attachments/assets/1ba5daa1-a1d1-4bc7-8e36-3e452022ec8e" />
        <div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
        4) 복사한 URL을 크롬의 새창에서 붙여넣기
      </div>
        <img width="1306" alt="image" src="https://github.com/user-attachments/assets/4bd7a004-0efe-480c-98c1-c881a6871d56" />
<div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
        5) 적용 워크스페이스 선택 후, [허용] 버튼 클릭
      </div>
        <img width="1253" alt="image" src="https://github.com/user-attachments/assets/dcc375cc-67e8-4694-8358-1d500cffd642" />
        <div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
        6) [code=]와 사이 [&state=]사이 값을 복사
      </div>
        <img width="779" alt="image" src="https://github.com/user-attachments/assets/6644df59-563e-4d9d-8556-9fb038cfdc09" />
<div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
        7) SCIM (Shared) > Authentication > Get Access Token에서 code값 붙여넣고 [Save]버튼 클릭
      </div>
        <img width="1061" alt="image" src="https://github.com/user-attachments/assets/03f041de-9a15-41a4-bcc5-484f73f47669" />
<div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
        8) [Send]버튼 클릭 후, 아래 Body 영역에 access_token값을 복사 
      </div>
        <img width="1063" alt="image" src="https://github.com/user-attachments/assets/9453e4b5-e282-46da-bb65-14b46b9c382c" />
          <div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
          9) SCIM (Shared) > SCIM > Users > Edit User (PATCH) 우측에 [...] > Duplicate 클릭해서 복제
      </div>
          <div style="display: flex; align-items: center; gap: 10px;">
    <img width="906" alt="image" src="https://github.com/user-attachments/assets/fc9310ad-5d26-4185-91a8-b8f2ff902ea3" style="max-width: 70%; height: auto;" />
    <img width="708" alt="image" src="https://github.com/user-attachments/assets/29339acd-7248-4617-aa3d-877c69739607" style="max-width: 30%; height: auto;" />
  </div>
          <div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
          10) SCIM (Shared) > SCIM > Users > Edit User (PATCH) Copy의 Headers > Authorization에 복사한 access_token값 붙여넣고 [Save]버튼 클릭
      </div>
<img width="1351" alt="image" src="https://github.com/user-attachments/assets/f5fbd075-1af8-4ba9-a55e-7ab1c0a4704e" />
          <div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
          11) SCIM (Shared) > SCIM > Users > Edit User (PATCH) Copy<br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1. URL의 Users/뒤 주소 삭제<br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2. Body > 아래 User Update 내용 복사&붙여넣기<br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3. Type을 JSON으로 설정<br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4. [Save]버튼 클릭<br>
      </div>
<img width="1351" alt="image" src="https://github.com/user-attachments/assets/de0b4320-5611-42fd-924b-200e28b6a1c3" />
          <div style="margin-top: 15px; padding: 12px 20px; padding-left: 15px; padding-right: 15px; background-color: #fff5f5; border: 1px solid #fcbbbb; border-radius: 6px;">
  <p style="margin: 0 0 8px 0; font-size: 15px; color: #c0392b; font-weight: bold;">
    📍 User Update
  </p>
  <p style="margin: 0; font-size: 15px; color: #444; line-height: 1.6;">
{<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"schemas": [<br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"urn:scim:schemas:core:1.0",<br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"urn:scim:schemas:extension:enterprise:1.0"<br>
    &nbsp;&nbsp;&nbsp;&nbsp;],<br>
    &nbsp;&nbsp;&nbsp;&nbsp;"id": "{{id}}",<br>
    &nbsp;&nbsp;&nbsp;&nbsp;"urn:scim:schemas:extension:enterprise:1.0": {<br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"manager": {<br>
            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"managerId": "{{managerid}}"<br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}<br>
    &nbsp;&nbsp;&nbsp;&nbsp;}<br>
}<br>
  </p>
</div>
          </details>
        <details style="border-radius: 6px; overflow: hidden;">
      <summary style="padding: 10px 15px; cursor: pointer; font-weight: 600; outline: none;">
        3️⃣ 사용자 정보 일괄 Update
      </summary>
              <div style="padding: 20px; border-top: 1px solid #e1e4e8; background: #fff; border-radius: 0 0 8px 8px;">
    <div style="display: flex; align-items: center; justify-content: flex-start; gap: 30px; flex-wrap: nowrap;">
      <div style="flex-shrink: 0;">
        <div style="margin-bottom: 8px; font-weight: 600; color: #444; font-size: 14px;">✔️ 영상 가이드</div>
        <video width="400" controls style="border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.06); border: 1px solid #e1e4e8; display: block;">
          <source src="https://github.com/minaslack/slackbizplus/releases/download/v1.0/Setup03_UserUpdate.mp4" type="video/mp4">
        </video>
      </div>
    </div>
  </div>
<div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
          1) 우측 하단의 [Tools] > [Runner]선택
      </div>
<img width="1202" alt="image" src="https://github.com/user-attachments/assets/4460bc62-ea1b-4e4c-ba8a-cc8c8bab4c88" />
<div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
          2) 좌측 사이드바에서 [User]폴더를 드래그 앤 드롭
      </div>
<img width="1539" alt="image" src="https://github.com/user-attachments/assets/34ce249f-807f-4973-bb8d-c43343a97e4c" />
<div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
          3) [Deselect All]을 선택 후, Edit user(patch) Copy를 선택
      </div>
      <img width="1539" alt="image" src="https://github.com/user-attachments/assets/9b4f174d-25d5-4c57-a04c-8fdbd7893a85" />
<div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
          4) 우측 화면에서 [Select File]버튼 클릭 후, 편집한 CSV파일 선택
      </div>
                    <div style="margin-top: 15px; padding: 12px 20px; padding-left: 15px; padding-right: 15px; background-color: #fff5f5; border: 1px solid #fcbbbb; border-radius: 6px;">
                          <div style="display: flex; align-items: center; justify-content: flex-start; gap: 30px; flex-wrap: nowrap;">
  <p style="margin: 0 0 8px 0; font-size: 15px; color: #c0392b; font-weight: bold;">
    📍 CSV 편집
  </p>
  <p style="margin: 0; font-size: 15px; color: #444; line-height: 1.6;">
&nbsp;&nbsp;&nbsp;&nbsp;아래 내용으로 맵핑해서 CSV파일 편집해주세요.<br>
&nbsp;&nbsp;&nbsp;&nbsp;* Id : 사용자 UserId<br>
&nbsp;&nbsp;&nbsp;&nbsp;* ManagerId : 해당 사용자의 관리자의 UserId<br>
  </p>
      <div style="flex: 1; display: flex; flex-direction: column; align-items: center; justify-content: center;">
        <a href="asset/pdf/SCIM_Update_ManagerID.csv" 
           download="SCIM_Update_ManagerID.csv" 
           target="_blank" 
           title="SCIM_Update_ManagerID.csv 다운로드" 
           style="display: inline-flex; align-items: center; justify-content: center; width: 50px; height: 50px; background-color: #f0f3f6; border: 2.5px solid #0366d6; border-radius: 50%; transition: all 0.2s ease-in-out; text-decoration: none; box-shadow: 0 4px 12px rgba(3,102,214,0.15); flex-shrink: 0;"
           onmouseover="this.style.backgroundColor='#0366d6'; this.style.transform='scale(1.1)';" 
           onmouseout="this.style.backgroundColor='#f0f3f6'; this.style.transform='scale(1)';"
           onmousedown="this.style.transform='scale(0.9)';" 
           onmouseup="this.style.transform='scale(1.1)';">
          <img src="https://github.com/user-attachments/assets/786795b8-66c7-4bb9-b2c5-c172546fe21f" alt="PDF 다운로드" style="width: 36px; height: auto; display: block;">
        </a>
        <div style="margin-top: 10px; font-size: 13px; color: #0366d6; font-weight: 700; letter-spacing: -0.5px;">SCIM_Update_ManagerID.csv</div>
      </div>            
    </div>
<br>
&nbsp;&nbsp;&nbsp;&nbsp;* UserId 확인방법 : 관리자 화면의 [사람] > [멤버]에서 각 사용자별 [멤버ID]확인
</div>
                    <img width="708" alt="image" src="https://github.com/user-attachments/assets/43b2ceee-5154-4bf5-af3f-91de11afcdb2" />
<div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
          5) Preview를 통해서 정상적으로 불러오기가 되었는지 확인 후 [Upload to Workspace]버튼 클릭
      </div>
          <img width="833" alt="image" src="https://github.com/user-attachments/assets/eef17552-7112-4468-9d09-e3e875006373" />
<div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
          6) [Start run]버튼 클릭
      </div>
<img width="707" alt="image" src="https://github.com/user-attachments/assets/6f83a72c-8699-4e2d-b10a-16ac2b079e24" />
<div style="padding: 15px; background: #f9f9f9; border-top: 1px solid #e1e4e8;">
          7) 결과 확인 (200 OK면 User Update성공!!)
      </div>
          <img width="1163" alt="image" src="https://github.com/user-attachments/assets/03f37855-8858-4a36-a093-6c9a948628c4" />
        </details>
        </details>

<img width="2940" alt="image" src="https://github.com/user-attachments/assets/af072ee6-61a4-49e0-8b70-aad0a882e9df" />
