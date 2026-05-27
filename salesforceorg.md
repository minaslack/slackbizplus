
# Salesforce 조직
Salesforce에 Slack을 연결하면 팀이 Slack에서 바로 Salesforce 레코드를 확인하고 편집하고 알림을 받을 수 있습니다.

<details style="margin-bottom: 8px; border: 1px solid #e1e4e8; border-radius: 8px; overflow: hidden;" class="accordion-group">
  <summary style="padding: 14px 16px; cursor: pointer; background: #FFFFFF; font-weight: 700; color: #24292e; display: flex; align-items: center; justify-content: space-between; border-radius: 8px 8px 0 0; list-style: none;">
      <div style="display: flex; align-items: center; gap: 12px;">
          <img height="32" style="border-radius: 6px;" alt="image" src="asset/image/SlackXSalesforce.png" /> 
          <span>Slack CRM 설정 가이드</span>
      </div>
      <style>
          summary::-webkit-details-marker { display: none; } /* 맥/아이폰용 기본 화살표 삭제 */
          .arrow-icon { transition: transform 0.2s ease; color: #9aa2ac; font-size: 14px; }
          details[open] .arrow-icon { transform: rotate(90deg); color: #24292e; }
      </style>
      <span class="arrow-icon">❯</span>
  </summary>
  <div style="padding: 20px; border-top: 1px solid #e1e4e8; background: #fff; border-radius: 0 0 8px 8px;">
      <div style="flex-shrink: 0;">
        <div style="margin-bottom: 8px; font-weight: 600; color: #444; font-size: 14px;">✔️ Slack CRM</div>
        Slack 안에서 대화하듯 고객을 관리하고,<br>
        Salesforce 기반의 자동 프로비저닝과 Slackbot이 메모·후속 조치·고객 조사까지 처리해 드립니다.<br>
        💡 추가 문의는 영업대표에게 연락 부탁드립니다. 
<table style="width: 100%; border-collapse: collapse; font-family: sans-serif; font-size: 14px; margin: 20px 0;">
  <thead>
    <tr style="border-top: 1px solid #d0d7de; border-bottom: 1px solid #d0d7de; background-color: #f6f8fa;">
      <th style="padding: 10px 14px; text-align: left; font-weight: 600; width: 25%; border: 1px solid #d0d7de; font-size: 13px;">항목</th>
      <th style="padding: 10px 14px; text-align: left; font-weight: 600; border: 1px solid #d0d7de;">내용</th>
    </tr>
  </thead>
  <tbody>
    <tr style="border-bottom: 1px solid #d0d7de;">
      <td style="padding: 10px 14px; font-weight: bold; border: 1px solid #d0d7de; font-size: 13px; color: #24292f;">지원 플랜</td>
      <td style="padding: 10px 14px; border: 1px solid #d0d7de; color: #24292f;"><strong>Business+ V2 전용</strong> (무료/Pro/Biz+ V1에서 업그레이드 가능)</td>
    </tr>
    <tr style="border-bottom: 1px solid #d0d7de;">
      <td style="padding: 10px 14px; font-weight: bold; border: 1px solid #d0d7de; font-size: 13px; color: #24292f;">사용자 제한</td>
      <td style="padding: 10px 14px; border: 1px solid #d0d7de; color: #24292f;">최대 100명 (Salesforce Free Suite 기반)</td>
    </tr>
    <tr style="border-bottom: 1px solid #d0d7de;">
      <td style="padding: 10px 14px; font-weight: bold; border: 1px solid #d0d7de; font-size: 13px; color: #24292f;">설정 방법</td>
      <td style="padding: 10px 14px; border: 1px solid #d0d7de; color: #24292f;">워크스페이스 이름 &gt; 환경설정 &gt; Salesforce</td>
    </tr>
  </tbody>
</table>
        <div style="margin-bottom: 8px; font-weight: 600; color: #444; font-size: 14px;">📌 설정 가이드</div>
        <video width="400" controls style="border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.06); border: 1px solid #e1e4e8; display: block;">
          <source src="https://github.com/minaslack/slackbizplus/releases/download/v1.0/SlackCRM.mp4" type="video/mp4">
        </video>
      </div>
  </div>
</details>
<details style="margin-bottom: 8px; border: 1px solid #e1e4e8; border-radius: 8px; overflow: hidden;" class="accordion-group">
  <summary style="padding: 14px 16px; cursor: pointer; background: #FFFFFF; font-weight: 700; color: #24292e; display: flex; align-items: center; justify-content: space-between; border-radius: 8px 8px 0 0; list-style: none;">
      <div style="display: flex; align-items: center; gap: 12px;">
          <img height="32" style="border-radius: 6px;" alt="image" src="asset/image/SlackXSalesforce.png" /> 
          <span>[작성중]Slack X Salesforce 연동 가이드_새 Slack 워크스페이스 만들기</span>
      </div>
      <style>
          summary::-webkit-details-marker { display: none; } /* 맥/아이폰용 기본 화살표 삭제 */
          .arrow-icon { transition: transform 0.2s ease; color: #9aa2ac; font-size: 14px; }
          details[open] .arrow-icon { transform: rotate(90deg); color: #24292e; }
      </style>
      <span class="arrow-icon">❯</span>
  </summary>
  <div style="padding: 20px; border-top: 1px solid #e1e4e8; background: #fff; border-radius: 0 0 8px 8px;">
      <div style="flex-shrink: 0;">
        <div style="margin-bottom: 8px; font-weight: 600; color: #444; font-size: 14px;">✔️ Slack X Salesforce</div>
        Salesforce 채널은 팀 대화와 고객 데이터를 하나로 연결해 더 스마트하고 빠른 협업을 가능하게 합니다.<br>
        Salesforce 채널은 레코드별 전용 채널을 제공하며, Salesforce 접근 권한 여부에 따라 데이터 열람·편집 가능 여부가 달라지지만 모든 팀원이 Slack에서 협업할 수 있습니다.<br>
        💡 추가 문의는 영업대표에게 연락 부탁드립니다.<br>
        <br>
        <div style="margin-bottom: 8px; font-weight: 600; color: #444; font-size: 14px;">📌 설정 가이드</div>
        <video width="400" controls style="border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.06); border: 1px solid #e1e4e8; display: block;">
          <source src="https://github.com/minaslack/slackbizplus/releases/download/v1.0/SlackCRM.mp4" type="video/mp4">
        </video>
      </div>
    <br>
      <div style="flex-shrink: 0;">
        <div style="margin-bottom: 8px; font-weight: 600; color: #444; font-size: 14px;">상세 가이드</div>
      </div>
  </div>
</details>
<details style="margin-bottom: 8px; border: 1px solid #e1e4e8; border-radius: 8px; overflow: hidden;" class="accordion-group">
  <summary style="padding: 14px 16px; cursor: pointer; background: #FFFFFF; font-weight: 700; color: #24292e; display: flex; align-items: center; justify-content: space-between; border-radius: 8px 8px 0 0; list-style: none;">
      <div style="display: flex; align-items: center; gap: 12px;">
          <img height="32" style="border-radius: 6px;" alt="image" src="asset/image/SlackXSalesforce.png" /> 
          <span>[작성중]Slack X Salesforce 연동 가이드_기존 워크스페이스 연결</span>
      </div>
      <style>
          summary::-webkit-details-marker { display: none; } /* 맥/아이폰용 기본 화살표 삭제 */
          .arrow-icon { transition: transform 0.2s ease; color: #9aa2ac; font-size: 14px; }
          details[open] .arrow-icon { transform: rotate(90deg); color: #24292e; }
      </style>
      <span class="arrow-icon">❯</span>
  </summary>
  <div style="padding: 20px; border-top: 1px solid #e1e4e8; background: #fff; border-radius: 0 0 8px 8px;">
      <div style="flex-shrink: 0;">
        <div style="margin-bottom: 8px; font-weight: 600; color: #444; font-size: 14px;">✔️ Slack X Salesforce</div>
        Salesforce 채널은 팀 대화와 고객 데이터를 하나로 연결해 더 스마트하고 빠른 협업을 가능하게 합니다.<br>
        Salesforce 채널은 레코드별 전용 채널을 제공하며, Salesforce 접근 권한 여부에 따라 데이터 열람·편집 가능 여부가 달라지지만 모든 팀원이 Slack에서 협업할 수 있습니다.<br>
        💡 추가 문의는 영업대표에게 연락 부탁드립니다.<br>
        <br>
        <div style="margin-bottom: 8px; font-weight: 600; color: #444; font-size: 14px;">📌 설정 가이드</div>
        <video width="400" controls style="border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.06); border: 1px solid #e1e4e8; display: block;">
          <source src="https://github.com/minaslack/slackbizplus/releases/download/v1.0/SlackCRM.mp4" type="video/mp4">
        </video>
      </div>
    <br>
      <div style="flex-shrink: 0;">
        <div style="margin-bottom: 8px; font-weight: 600; color: #444; font-size: 14px;">상세 가이드</div>
      </div>
  </div>
</details>
<head>
  <meta property="og:title" content="Salesforce Channels: Implementation Guide" />
  <meta property="og:description" content="Download our technical guide for a step-by-step walkthrough to help you configure Salesforce Channels." />
  <meta property="og:image" content="https://yourdomain.com/path-to-your-image.png" />
  <meta property="og:site_name" content="Slack" />
  <meta property="og:url" content="https://yourdomain.com/your-page-url" />
  <meta property="og:type" content="website" />
</head>
<br>
<img width="1466" alt="image" src="asset/image/SalesforceScreen.png" />




