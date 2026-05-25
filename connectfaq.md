# 🛠️ Slack Connector Issue Tracker

이슈 카드를 클릭하면 해당 카드만 독립적으로 강조되면서, 숨겨져 있던 구체적인 해결책 리스트가 스르륵 나타납니다.

<style>
  .card-grid {
    display: grid;
    /* 한 줄에 정확히 2개씩 배치 */
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
    margin-top: 20px;
    /* [수정] stretch를 제거하여 같은 줄의 카드가 강제로 늘어나는 현상 방지 */
    align-items: start; 
  }
  
  /* 그리드 아이템 wrap */
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
    /* [수정] 기본 상태에서 카드가 가질 최소 높이 지정 (줄바꿈 시 깔끔한 정렬을 위함) */
    min-height: 140px; 
    transition: background-color 0.3s, border-color 0.3s, box-shadow 0.3s, min-height 0.3s;
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
    overflow: visible;
    /* [수정] 펼쳐졌을 때는 최소 높이 제약을 풀어줌 */
    min-height: auto; 
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
    .focus-card {
      min-height: auto; /* 모바일에서는 굳이 최소 높이를 고정할 필요가 없음 */
    }
  }
</style>
