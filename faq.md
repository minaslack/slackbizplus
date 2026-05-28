<div style="font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; max-width: 800px; margin: 20px auto; color: #1d1c1d; line-height: 1.6;">
  <h2 style="margin-bottom: 25px; color: #8E44AD;">💬 Slack 자주 묻는 질문</h2>
  <div style="margin-bottom: 30px;">
    <h3 style="font-size: 16px; color: #616061; margin-bottom: 10px; border-bottom: 1px solid #e1e4e8; padding-bottom: 5px;">📁 채널 관리</h3>
    <details style="margin-bottom: 8px; border: 1px solid #e1e4e8; border-radius: 8px; overflow: hidden;">
      <summary style="padding: 12px 15px; background: #fafbfc; cursor: pointer; font-weight: 600; display: flex; justify-content: space-between; align-items: center; outline: none;">
        <span>비공개 채널을 관리하는 방법</span>
        <span style="color: #1264a3; font-size: 12px;">더보기 ▼</span>
      </summary>
      <div style="padding: 15px; background: #fff; border-top: 1px solid #e1e4e8;">
        📌 채널 리스트에 비공개 채널이 안보이시나요?<br>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 비공개 채널을 관리하기 위해서는 <Strong>데이터 내보내기 요청 후 승인</Strong>을 받아야 합니다.<br>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 데이터 내보내기 활성화 사전신청 -> 내부 심사 및 활성화 승인 -> 채널리스트에 비공개 채널 표시<br>
        <br>
          <Strong>참고💡 비공개 채널 관리 도구는 한 번 승인되면 계속 접근 가능</Strong><br>
        <br>
          <Strong>[데이터 내보내기 요청]</Strong><br>
          워크스페이스 소유자는 추가 내보내기 유형에 대한 액세스를 신청할 수 있습니다.<br>
          신청서에는 워크스페이스 주 소유자의 승인이 필요하므로, 지원 팀에서 신청서를 검토하기 전에 이메일로 연락드릴 것입니다.<br>
      </div>
    <img width="80%" alt="image" src="https://github.com/user-attachments/assets/f4ef92dc-31e6-45db-aa6b-85e51494b181" />
      </div>
    </details>
  </div>
<div style="margin-bottom: 30px;">
  <h3 style="font-size: 16px; color: #616061; margin-bottom: 10px; border-bottom: 1px solid #e1e4e8; padding-bottom: 5px;">🔐 보안 및 인증</h3>
  <details style="margin-bottom: 8px; border: 1px solid #e1e4e8; border-radius: 8px; overflow: hidden;">
    <summary style="padding: 12px 15px; background: #fafbfc; cursor: pointer; font-weight: 600; display: flex; justify-content: space-between; align-items: center; outline: none;">
      <span>Google OAuth vs SAML 차이 및 권장 설정</span>
      <span style="color: #1264a3; font-size: 12px;">더보기 ▼</span>
    </summary>
    <div style="padding: 15px 0; background: #fff; border-top: 1px solid #e1e4e8;">
      <div style="padding: 0 15px;">
        <p style="margin-top: 0; margin-bottom: 15px; font-size: 14px; color: #1d1c1d;">
          <strong>[Google OAuth vs SAML 차이]</strong><br>
          아래와 같이 제어가 가능하기 때문에 <Strong>SAML설정을 권장</Strong>합니다.<br>
        </p>
      </div>
      <table style="width: 70%; margin: 0 auto; border-collapse: collapse; font-size: 13px; line-height: 1.5; background-color: #ffffff;">
        <thead>
          <tr style="background: #f8f9fa;">
            <th style="padding: 12px 10px; border: 1px solid #e1e4e8; text-align: center; font-weight: 700; color: #1d1c1d;">항목</th>
            <th style="padding: 12px 10px; border: 1px solid #e1e4e8; text-align: center; font-weight: 700; color: #1d1c1d;">Google OAuth</th>
            <th style="padding: 12px 10px; border: 1px solid #e1e4e8; text-align: center; font-weight: 700; color: #1d1c1d;">Google SAML</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; font-weight: 600; background-color: transparent;">설정 난이도</td>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; background-color: transparent;">쉬움 (빠른 설정)</td>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; background-color: transparent;">중간 (IDP 설정 필요)</td>
          </tr>
          <tr>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; font-weight: 600; background-color: transparent;">지원 플랜</td>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; background-color: transparent;">Pro, Business+</td>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; background-color: transparent;">Business+, Enterprise Grid</td>
          </tr>
          <tr>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; font-weight: 600; background-color: transparent;">JIT 프로비저닝 제어</td>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; background-color: transparent;"><span style="color: #e01e5a;">❌</span> 항상 ON (끌 수 없음)</td>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; background-color: transparent;"><span style="color: #2eb67d;">✅</span> ON/OFF 선택 가능</td>
          </tr>
          <tr>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; font-weight: 600; background-color: transparent;">사용자 단위 접근 제어</td>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; background-color: transparent;"><span style="color: #e01e5a;">❌</span> 도메인 단위만 가능</td>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; background-color: transparent;"><span style="color: #2eb67d;">✅</span> 사용자/그룹 단위 제어</td>
          </tr>
          <tr>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; font-weight: 600; background-color: transparent;">SCIM 연동</td>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; background-color: transparent;"><span style="color: #e01e5a;">❌</span> 불가</td>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; background-color: transparent;"><span style="color: #2eb67d;">✅</span> 가능</td>
          </tr>
          <tr>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; font-weight: 600; background-color: transparent;">2FA 적용</td>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; background-color: transparent;">IDP 레벨 설정 필요</td>
            <td style="padding: 10px; border: 1px solid #e1e4e8; text-align: center; background-color: transparent;">IDP 레벨 설정 필요</td>
          </tr>
        </tbody>
      </table>
        <div style="padding: 0 15px;">
          <p style="margin-top: 0; margin-bottom: 15px; font-size: 14px; color: #1d1c1d;">
            <br>
            📌 참조<br>
                  1. <strong>JIT(Just-In-Time) 프로비저닝</strong>은 <strong>사용자가 처음 로그인할 때 자동으로 계정이 만들어지는 기능</strong>입니다.<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;이 기능을 끄면 관리자가 사전에 승인한 사용자만 접근할 수 있어서 보안을 강화할 수 있습니다.<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;참고) 필요한 경우, Feedback 팀으로 요청하여 JIT를 Off할 수 있습니다.<br>
              2. <strong>SCIM</strong>은 사용자 계정을 IDP(Okta, Google Workspace 등)와 Slack 사이에서 자동으로 동기화해주는 기능입니다.
          </p>
      </div>
      <div style="height: 15px;"></div>
    </div>
  </details>
  <details style="margin-bottom: 8px; border: 1px solid #e1e4e8; border-radius: 8px; overflow: hidden;">
    <summary style="padding: 12px 15px; background: #fafbfc; cursor: pointer; font-weight: 600; display: flex; justify-content: space-between; align-items: center; outline: none;">
      <span>SCIM Provisioning 활용 방법 (프로필·유저 관리 자동화)</span>
      <span style="color: #1264a3; font-size: 12px;">더보기 ▼</span>
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
</div>
  <div style="margin-bottom: 30px;">
    <h3 style="font-size: 16px; color: #616061; margin-bottom: 10px; border-bottom: 1px solid #e1e4e8; padding-bottom: 5px;">📤 데이터 내보내기 및 메시지 관리</h3>
        <details style="margin-bottom: 8px; border: 1px solid #e1e4e8; border-radius: 8px; overflow: hidden;">
      <summary style="padding: 12px 15px; background: #fafbfc; cursor: pointer; font-weight: 600; display: flex; justify-content: space-between; align-items: center; outline: none;">
        <span>비공개 채널/DM까지 포함하여 데이터 내보내기 방법</span>
        <span style="color: #1264a3; font-size: 12px;">더보기 ▼</span>
      </summary>
      <div style="padding: 15px; background: #fff; border-top: 1px solid #e1e4e8;">
        📌 <Strong>비공개 채널/DM까지 포함하여 데이터 내보내기</Strong>를 하기위해서는 아래의 절차가 필요합니다.<br>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;- 데이터 내보내기 활성화 사전신청 -> 내부 심사 및 활성화 승인 -> 데이터 내보내기 가능<br>
        <br>
          <Strong>[데이터 내보내기 요청]</Strong><br>
          워크스페이스 소유자는 추가 내보내기 유형에 대한 액세스를 신청할 수 있습니다.<br>
          신청서에는 워크스페이스 주 소유자의 승인이 필요하므로, 지원 팀에서 신청서를 검토하기 전에 이메일로 연락드릴 것입니다.<br>
      </div>
    <img width="80%" alt="image" src="https://github.com/user-attachments/assets/f4ef92dc-31e6-45db-aa6b-85e51494b181" />
    </details>
    <details style="margin-bottom: 8px; border: 1px solid #e1e4e8; border-radius: 8px; overflow: hidden;">
      <summary style="padding: 12px 15px; background: #fafbfc; cursor: pointer; font-weight: 600; display: flex; justify-content: space-between; align-items: center; outline: none;">
        <span>데이터 내보내기 및 가독성 있게 확인하는 방법</span>
        <span style="color: #1264a3; font-size: 12px;">더보기 ▼</span>
      </summary>
            <div style="padding: 15px; background: #fff; border-top: 1px solid #e1e4e8;">
        📌 <Strong>비공개 채널/DM까지 포함하여 데이터 내보내기</Strong>를 하기위해서 [<a href="https://slackforadmin.github.io/slackbizplus/#/dataexport?id=%eb%8d%b0%ec%9d%b4%ed%84%b0-%eb%82%b4%eb%b3%b4%eb%82%b4%ea%b8%b0-%ec%9a%94%ec%b2%ad" target="_blank" rel="noopener" style="color: #1264a3; text-decoration: underline; font-size: 15px; font-weight: 600;"> 데이터 내보내기 요청 </a>]🔼이 필요합니다.
      </div>
<div style="font-family: 'Pretendard', -apple-system, sans-serif; max-width: 900px; color: #333; line-height: 1.6;">
  
  <div style="padding: 20px 0 20px 0;">
    <div style="font-size: 13px; font-weight: bold; color: #007bff; margin-bottom: 5px; margin-left: 15px;">STEP 01</div>
    <div style="font-size: 15px; font-weight: bold; margin-bottom: 5px; margin-left: 15px;">데이터 내보내기 설정</div>
    <div style="padding: 15px 20px; background-color: #f9f9f9; border-radius: 8px; margin-bottom: 5px;">
      1. 보안 > 데이터 가져오기 및 내보내기 > 내보내기 날짜 범위 선택 후 <b>[내보내기 시작]</b> 클릭
    </div>
    <img width="401" alt="image" src="https://github.com/user-attachments/assets/7a2a06a8-cc2d-4a89-ad76-7e74c96f4423" style="display: block; border: 1px solid #eee; border-radius: 4px; margin-left: auto; margin-right: auto;" />
  </div>
  <div style="padding: 20px 0 20px 0;">
    <div style="font-size: 13px; font-weight: bold; color: #007bff; margin-bottom: 5px;margin-left: 15px">STEP 02</div>
    <div style="font-size: 15px; font-weight: bold; margin-bottom: 5px;margin-left: 15px;">파일 다운로드</div>
    <div style="padding: 15px 20px; background-color: #f9f9f9; border-radius: 8px; margin-bottom: 5px;">
      2. 목록에서 <b>[다운로드 준비]</b> 버튼을 클릭하여 파일을 저장
    </div>
    <img width="926" alt="image" src="https://github.com/user-attachments/assets/27de6c60-b338-42dd-9b1a-fdd95157a69c" style="display: block; max-width: 100%; border: 1px solid #eee; border-radius: 4px;" />
  </div>
  <div style="padding: 20px 0 20px 0;">
    <div style="font-size: 13px; font-weight: bold; color: #007bff; margin-bottom: 5px;margin-left: 15px;">STEP 03</div>
    <div style="font-size: 15px; font-weight: bold; margin-bottom: 5px;margin-left: 15px;">JSON 데이터 변환</div>
    <div style="padding: 15px 20px; background-color: #f9f9f9; border-radius: 8px; margin-bottom: 10px;">
      3. <b>[JSON을 표로 변환하기]</b> 버튼 클릭 후 변환 도구 웹사이트 오픈<br>
      &nbsp;&nbsp;&nbsp;JSON 파일 업로드 또는 붙여넣기 후 결과 확인
    </div>
  <a href="https://jsontotable.org/" target="_blank" rel="noopener" style="display: inline-block; padding: 8px 16px; background-color: #8E44AD; color: #ffffff; text-decoration: none; border-radius: 4px; font-size: 13px; font-weight: 600;margin-bottom: 10px;">
    JSON을 표로 변환하기 (JSON to Table)
  </a>
    <br>
    <img width="1454" alt="image" src="https://github.com/user-attachments/assets/b48dc82e-3f96-46cf-ad56-9ed7798e4d08" style="display: block; max-width: 100%; border: 1px solid #eee; border-radius: 4px;" />
<div style="margin-top: 15px; padding: 12px 20px; padding-left: 15px; padding-right: 15px; background-color: #fff5f5; border: 1px solid #fcbbbb; border-radius: 6px;">
  <p style="margin: 0 0 8px 0; font-size: 15px; color: #c0392b; font-weight: bold;">
    ⚠️ 보안 주의사항
  </p>
  <p style="margin: 0; font-size: 15px; color: #444; line-height: 1.6;">
    기업의 민감 데이터가 포함된 경우 외부 사이트 대신 <strong>엑셀(데이터 가져오기 > JSON)</strong>이나 
    브라우저의 <strong>JSON Viewer 확장 프로그램</strong>을 사용해 로컬에서 확인하는 것을 권장합니다.
  </p>
</div>
  </div>
</div>
    </details>
  </div>
    <div style="margin-bottom: 30px;">
    <h3 style="font-size: 16px; color: #616061; margin-bottom: 10px; border-bottom: 1px solid #e1e4e8; padding-bottom: 5px;">👤 계정 및 사용자 관리</h3>
    <details style="margin-bottom: 8px; border: 1px solid #e1e4e8; border-radius: 8px; overflow: hidden;">
      <summary style="padding: 12px 15px; background: #fafbfc; cursor: pointer; font-weight: 600; display: flex; justify-content: space-between; align-items: center; outline: none;">
        <span>승인 없이 다수 멤버 일괄 초대 방법</span>
        <span style="color: #1264a3; font-size: 12px;">더보기 ▼</span>
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
    <img width="376" alt="사용자 초대 이동" src="https://github.com/user-attachments/assets/5d6b5eb1-8aaa-4e15-8942-88b6994afc1d" style="display: block; max-width: 100%; border: 1px solid #eee; border-radius: 4px;margin-left: auto; margin-right: auto;" />
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
    <details style="margin-bottom: 8px; border: 1px solid #e1e4e8; border-radius: 8px; overflow: hidden;">
      <summary style="padding: 12px 15px; background: #fafbfc; cursor: pointer; font-weight: 600; display: flex; justify-content: space-between; align-items: center; outline: none;">
        <span>SSO연동 시에 사용자 이메일 변경 방법</span>
        <span style="color: #1264a3; font-size: 12px;">더보기 ▼</span>
      </summary>
<div style="padding: 15px; background: #fff; border-top: 1px solid #e1e4e8;">
    📌 이메일이나 표시이름을 변경할 수 없으신가요?<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SSO를 활성화한 경우, 이메일 주소를 포함한 <b>개인 정보 편집 기능이 제한</b>될 수 있으나,<br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<b>워크스페이스 소유자</b>가 사용자들이 이메일 주소를 변경할 수 있도록 허용할 수 있습니다.
        <br>
  <br>
        🔗 참조 링크<br>
        <a href="https://slack.com/intl/ko-kr/help/articles/207262907-%EC%9D%B4%EB%A9%94%EC%9D%BC-%EC%A3%BC%EC%86%8C-%EB%B3%80%EA%B2%BD?gad_source=1&gad_campaignid=23274986143&gbraid=0AAAAACylTvomOl6mvXW5Kww-Pj98WDTOo&gclid=Cj0KCQjwve7NBhC-ARIsALZy9HWion0c2Ez6xoOYmDZYm113CjSolE9b0bVu26oxttDRe9rdAcAD_1saAkk-EALw_wcB#%EB%8D%B0%EC%8A%A4%ED%81%AC%ED%86%B1-1" target="_blank" rel="noopener" style="color: #1264a3; text-decoration: underline; font-size: 15px; font-weight: 600;"> 이메일 주소 변경 </a><br>
        <a href="https://slack.com/intl/ko-kr/help/articles/225531168-%EA%B5%AC%EC%84%B1%EC%9B%90%EC%9D%98-%EC%9D%B4%EB%A9%94%EC%9D%BC-%EC%A3%BC%EC%86%8C-%EB%B3%80%EA%B2%BD" target="_blank" rel="noopener" style="color: #1264a3; text-decoration: underline; font-size: 15px; font-weight: 600;"> 구성원의 이메일 주소 변경 </a><br>
        <br>
        💡 <b>이메일 주소를 변경할 수 있도록 허용하는 방법</b>
      </div>
      <img width="591" alt="image" src="https://github.com/user-attachments/assets/1b52ca77-dadf-4cf5-89f7-321452d0a7e3" />
      <div style="padding: 15px; background: #fff;">
              📌 단, 아래 3개 항목 중 하나라도 기본값과 다르게 설정되어 있는 경우,<br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;로그인 시, 해당 사용자의 프로필 값이 업데이트 되지 않는 다는 것 기억해주세요!!<br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;즉, 이메일 주소를 변경할 수 있도록 설정을 변경하면 사용자 프로필 정보가 싱크되지 않습니다.<br>
        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(전제 : 자동 프로비저닝을 사용하고 있지 않음)<br>
              <br>
      </div>
      <img width="1154" alt="image" src="https://github.com/user-attachments/assets/7f316619-32f0-4bcb-84c1-dd66c909df5d" />
    </details>
      <details style="margin-bottom: 8px; border: 1px solid #e1e4e8; border-radius: 8px; overflow: hidden;">
      <summary style="padding: 12px 15px; background: #fafbfc; cursor: pointer; font-weight: 600; display: flex; justify-content: space-between; align-items: center; outline: none;">
        <span>SCIM API를 활용한 Atlas 설정 방법</span>
        <span style="color: #1264a3; font-size: 12px;">더보기 ▼</span>
      </summary>
        <div style="padding: 15px; background: #fff; border-top: 1px solid #e1e4e8;">
          📌 SCIM API를 활용한 Atlas[Add-On기능] 설정가이드입니다.<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<Strong>초기설정1,2 완료 후 사용자 업데이트</Strong> 진행해주세요.<br>
              &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;해당 방식으로 사용자 프로필정보(SCIM API타입 항목)도 업데이트 가능합니다.<br>
          <a href="https://slack.com/intl/ko-kr/help/articles/22467765879315-Slack-%EC%95%84%ED%8B%80%EB%9D%BC%EC%8A%A4%EB%A1%9C-%ED%94%84%EB%A1%9C%ED%95%84-%EC%82%AC%EC%9A%A9%EC%9E%90-%EC%A7%80%EC%A0%95" target="_blank" 
     rel="noopener noreferrer" style="color: #1264a3; text-decoration: none;">📌 [참조 링크] Slack 아틀라스로 프로필 사용자 지정</a></li>
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
    <div style="margin-bottom: 30px;">
    <h3 style="font-size: 16px; color: #616061; margin-bottom: 10px; border-bottom: 1px solid #e1e4e8; padding-bottom: 5px;">🌐 외부 협업 및 권한 설정</h3>
    <details style="margin-bottom: 8px; border: 1px solid #e1e4e8; border-radius: 8px; overflow: hidden;">
      <summary style="padding: 12px 15px; background: #fafbfc; cursor: pointer; font-weight: 600; display: flex; justify-content: space-between; align-items: center; outline: none;">
        <span>Slack Connect 및 게스트 초대를 관리자 승인 하에 운영하는 방법</span>
        <span style="color: #1264a3; font-size: 12px;">더보기 ▼</span>
      </summary>
      <div style="padding: 15px; background: #fff; border-top: 1px solid #e1e4e8;">
        곧 업로드 예정(5월 내)
      </div>
    </details>
      <details style="margin-bottom: 8px; border: 1px solid #e1e4e8; border-radius: 8px; overflow: hidden;">
      <summary style="padding: 12px 15px; background: #fafbfc; cursor: pointer; font-weight: 600; display: flex; justify-content: space-between; align-items: center; outline: none;">
        <span>Slack Connect 외부 사용자의 채널 권한</span>
        <span style="color: #1264a3; font-size: 12px;">더보기 ▼</span>
      </summary>
      <div style="padding: 15px; background: #fff; border-top: 1px solid #e1e4e8;">
        Slack Connect는 <strong>초대를 보내는 쪽에서 채널 소유권</strong>을 가지게 됩니다.(변경할 수 없음)<br>
        <br>
        Slack Connect 외부 사용자의 채널권한은 아래와 같습니다.<br>
        참고해서 Connect 초대 해주세요.<br>
        <br>
  <table style="width: 100%; border-collapse: collapse; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; font-size: 14px; line-height: 1.5; color: #333; text-align: left;">
    <thead>
      <tr style="background-color: #f6f8fa; border-top: 1px solid #e1e4e8; border-bottom: 1px solid #e1e4e8;">
        <th style="padding: 12px; font-weight: bold; width: 25%; border-right: 1px solid #e1e4e8;">Action</th>
        <th style="padding: 12px; font-weight: bold; width: 37.5%; border-right: 1px solid #e1e4e8;">초대 및 포스트 가능</th>
        <th style="padding: 12px; font-weight: bold; width: 37.5%;">포스트만 가능</th>
      </tr>
    </thead>
    <tbody>
      <tr style="border-bottom: 1px solid #e1e4e8;">
        <td style="padding: 12px; font-weight: 500; border-right: 1px solid #e1e4e8; background-color: #fafbfc;">비용</td>
        <td colspan="2" style="padding: 12px;">
          유료플랜간 추가비용없이 사용가능<br>
          Ent+ 플랜은 무료플랜과도 Slack Connect 연결 가능 (Sponsored)
        </td>
      </tr>
      <tr style="border-bottom: 1px solid #e1e4e8;">
        <td style="padding: 12px; font-weight: 500; border-right: 1px solid #e1e4e8; background-color: #fafbfc;">누가 대화에 사람을 추가할 수 있나요?</td>
        <td style="padding: 12px; border-right: 1px solid #e1e4e8;">
          채널소유자 조직 <br>- 모든 조직 멤버 초대 가능<br>
          외부 조직 <br>- 각 외부 조직의 멤버만 초대 가능
        </td>
        <td style="padding: 12px;">채널소유자 조직만 추가 가능</td>
      </tr>
      <tr style="border-bottom: 1px solid #e1e4e8;">
        <td style="padding: 12px; font-weight: 500; border-right: 1px solid #e1e4e8; background-color: #fafbfc;">만료/연결 해제 시 대화 기록 및 파일에 액세스할 수 있는 사람은 누구인가요?</td>
        <td style="padding: 12px; border-right: 1px solid #e1e4e8;">상대방 조직에 채널 보관 상태로 사본 유지</td>
        <td style="padding: 12px;">연결 해제시 상대방 조직에 사본 남지 않음</td>
      </tr>
      <tr style="border-bottom: 1px solid #e1e4e8;">
        <td style="padding: 12px; font-weight: 500; border-right: 1px solid #e1e4e8; background-color: #fafbfc;">신원은 누가 관리하나요?</td>
        <td colspan="2" style="padding: 12px;">각 조직에서 관리</td>
      </tr>
      <tr style="border-bottom: 1px solid #e1e4e8;">
        <td style="padding: 12px; font-weight: 500; border-right: 1px solid #e1e4e8; background-color: #fafbfc;">초대 / 제거</td>
        <td style="padding: 12px; border-right: 1px solid #e1e4e8;">
          각 조직에서 각자 멤버 초대 및 제거 가능(비공개채널인 경우)<br>
          채널 소유자 조직의 관리자는 상대방 멤버 제거 가능
        </td>
        <td style="padding: 12px;">채널 소유자 조직에서 상대방 조직의 멤버 초대/제거 가능</td>
      </tr>
      <tr style="border-bottom: 1px solid #e1e4e8;">
        <td style="padding: 12px; font-weight: 500; border-right: 1px solid #e1e4e8; background-color: #fafbfc;">관리자 관리</td>
        <td colspan="2" style="padding: 12px;">
          채널 생성시 각 조직의 관리자가 승인 (승인 필요 설정시)<br>
          외부 조직과의 모든 연결을 승인하고 감사할 수 있습니다.
        </td>
      </tr>
      <tr style="border-bottom: 1px solid #e1e4e8;">
        <td style="padding: 12px; font-weight: 500; border-right: 1px solid #e1e4e8; background-color: #fafbfc;">앱</td>
        <td style="padding: 12px; border-right: 1px solid #e1e4e8;">각 조직은 채널에서 자체 앱 및 통합 기능에 액세스할 수 있습니다. <br>(상대방 조직의 앱 사용 불가)</td>
        <td style="padding: 12px;">채널에서 봇을 추가 또는 제거하거나 워크플로우를 추가하거나 워크플로우를 제거할 수 없습니다. <br>(상대방 조직의 앱 사용 불가)</td>
      </tr>
      <tr style="border-bottom: 1px solid #e1e4e8;">
        <td style="padding: 12px; font-weight: 500; border-right: 1px solid #e1e4e8; background-color: #fafbfc;">워크플로우</td>
        <td colspan="2" style="padding: 12px;">허용 되어있는 경우 사용가능</td>
      </tr>
      <tr style="border-bottom: 1px solid #e1e4e8;">
        <td style="padding: 12px; font-weight: 500; border-right: 1px solid #e1e4e8; background-color: #fafbfc;">3rd-party 가 포함된 워크플로우</td>
        <td colspan="2" style="padding: 12px;">허용 되어있는 경우 사용가능</td>
      </tr>
      <tr style="border-bottom: 1px solid #e1e4e8;">
        <td style="padding: 12px; font-weight: 500; border-right: 1px solid #e1e4e8; background-color: #fafbfc;">이모지</td>
        <td colspan="2" style="padding: 12px;">각 조직은 자체의 이모티콘 팩에 액세스할 수 있습니다.</td>
      </tr>
      <tr style="border-bottom: 1px solid #e1e4e8;">
        <td style="padding: 12px; font-weight: 500; border-right: 1px solid #e1e4e8; background-color: #fafbfc;">캔버스 / 리스트</td>
        <td colspan="2" style="padding: 12px;">상대방 조직에 공유 가능<br>(상대방 조직이 무료 플랜인 경우 리스트 공유 불가 / 캔버스 공유 가능-읽기전용)</td>
      </tr>
    </tbody>
</table>
</div>
    </details>
  </div>
</div>
