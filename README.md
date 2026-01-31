<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>가드너 - 이불위키</title>
  <style>
    * { box-sizing: border-box; }

    body {
      margin: 0;
      padding: 0;
      background: #000000;
      color: #e0e0e0;
      font-family: "Noto Sans KR", -apple-system, BlinkMacSystemFont, system-ui, "Segoe UI", sans-serif;
      font-size: 15px;
      line-height: 1.7;
    }

    a {
      color: #ffb54a;
      text-decoration: none;
    }
    a:hover { text-decoration: underline; }

    /* ───────────────── 헤더(메인 메뉴 / 이불위키) ───────────────── */
    #topbar {
      background: #141414;              
      border-bottom: 2px solid #ffb54a;  
      color: #f5f5f5;
      padding: 10px 0;
    }

    #topbar-inner {
      max-width: 980px;
      margin: 0 auto;
      padding: 6px 15px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      font-size: 13px;
    }

    .site-name {
      font-weight: 700;
      font-size: 18px;
      color: #ffcc33;
    }

    .top-menu a {
      margin-left: 12px;
      font-size: 13px;
      color: #dddddd;
      text-decoration: none;
    }
    .top-menu a:hover {
      color: #ffcc33;
      text-decoration: underline;
    }

    /* ───────────────── 페이지 레이아웃 (문서 박스) ───────────────── */

    #page {
      max-width: 980px;
      margin: 20px auto 40px auto;
      padding: 20px 25px 20px 25px;
      background: #141414;
      border: 1px solid #333333;
      border-radius: 4px;
    }

    .doc-title {
      font-size: 24px;
      font-weight: 700;
      margin: 8px 0 4px 0;
      color: #ffcc33;
    }

    .doc-meta {
      font-size: 12px;
      color: #aaa;
      border-bottom: 1px solid #444;
      padding-bottom: 6px;
      margin-bottom: 8px;
    }

    .top-layout {
      margin-top: 6px;
    }

    .clearfix::after {
      content: "";
      display: block;
      clear: both;
    }

    /* 목차 박스 */
    .toc-box {
      float: left;
      width: 180px;
      background: #181818;
      border: 1px solid #444;
      padding: 8px 10px;
      font-size: 13px;
      margin-right: 12px;
      margin-bottom: 12px;
      color: #ffcc66;
    }
    .toc-title {
      font-weight: 700;
      margin-bottom: 4px;
      border-bottom: 1px solid #555;
      padding-bottom: 3px;
      color: #ffcc33;
    }
    .toc-box ol {
      list-style: none;
      margin: 0;
      padding-left: 0;
    }
    .toc-box > ol > li { margin: 2px 0; }
    .toc-box ol ol {
      margin-left: 14px;
      margin-top: 2px;
    }

    /* 인포박스 */

    .char-infobox {
      float: right;
      width: 360px;
      background: #000000;
      border: 1px solid #555;
      border-collapse: collapse;
      font-size: 13px;
      margin-left: 6px;
      margin-bottom: 12px;
    }
    .char-infobox th,
    .char-infobox td {
      border: 1px solid #444;
      padding: 4px 7px;
      vertical-align: top;
    }
    .char-infobox th {
      width: 90px;
      background: #111;
      color: #ffb54a;
      font-weight: 600;
      font-size: 12px;
    }

    .char-image-cell {
      background: #000;
      text-align: center;
      padding: 10px 0;
    }
    .char-image-cell img {
      max-width: 100%;
      height: auto;
      display: block;
      margin: 0 auto;
    }

    /* 이름 구조 */

    .char-name-row {
      background: #000;
      text-align: center;
      padding-top: 10px;
      padding-bottom: 10px;
    }

    .name-eng {
      font-size: 13px;
      color: #ffb54a;
      margin-bottom: 2px;
    }

    .name-kor {
      font-size: 20px;
      font-weight: 700;
      color: #ffd54a;
      margin-bottom: 3px;
    }

    /* 본문 구역 */

    h2 {
      font-size: 18px;
      margin: 18px 0 6px 0;
      border-bottom: 1px solid #444;
      padding-bottom: 3px;
      color: #ffcc33;
    }
    h3 {
      font-size: 16px;
      margin: 12px 0 4px 0;
      border-bottom: 1px dashed #555;
      padding-bottom: 2px;
      color: #ffc96b;
    }

    p { margin: 4px 0 8px 0; }

    ul {
      margin: 4px 0 8px 18px;
      padding-left: 0;
    }
    li { margin-bottom: 4px; }

    .small {
      font-size: 13px;
      color: #bbbbbb;
    }

    /* FALL OF TITAN 링크 스타일 */

    .orange-link {
      color: #ffcc33;
      font-weight: 700;
      cursor: pointer;
    }
    .orange-link:hover {
      color: #ffe066;
      text-decoration: underline;
    }

    /* ───────── 소지품 상세 리스트 ───────── */

    .detail-list {
      list-style: disc;
      margin: 4px 0 6px 18px;
      padding-left: 0;
    }

    .detail-list li {
      margin-bottom: 10px;
    }

    .detail-title {
      font-weight: 700;
      color: #ffffff;
      margin-right: 4px;
      display: block;
      margin-bottom: 2px;
    }

    .item-note {
      color: #888888;
      text-decoration: line-through;
      font-size: 14px;
      margin-left: 4px;
    }

    /* ───────── 명언/대사 박스 ───────── */

    .quote-block {
      display: inline-block;
      background: #1f1f1f;
      border-left: 4px solid #888;
      border-top: 1px dashed #555;
      border-right: 1px dashed #555;
      border-bottom: 1px dashed #555;
      padding: 10px 14px;
      margin: 8px 0;
      border-radius: 4px;
    }

    .quote-main {
      font-size: 15px;
      font-weight: 700;
      color: #ffffff;
      line-height: 1.6;
      margin-bottom: 6px;
    }

    .quote-sep {
      border-top: 1px solid #444;
      margin: 4px 0 6px 0;
    }

    .quote-sub {
      font-size: 13px;
      color: #dcdcdc;
      line-height: 1.7;
    }

@media (max-width: 800px) {

  body {
    font-size: 14px;
    line-height: 1.6;
  }

  #page {
    margin: 10px auto 20px auto;
    padding: 15px 12px;
    border-radius: 0;
  }

  .doc-title {
    font-size: 20px;
  }

  /* 제목 아래 인포박스 → 그 밑에 목차 순서로 쌓기 */
  .top-layout {
    display: flex;
    flex-direction: column;
  }

  .toc-box,
  .char-infobox {
    float: none;
    width: 100%;
    margin: 0 0 12px 0;
  }

  .char-infobox { 
    order: 1;
    font-size: 13px;
  }

  .toc-box { 
    order: 2;
    font-size: 12px;
  }

  .char-infobox th {
    font-size: 12px;
    width: 80px;
  }

  .char-image-cell img {
    max-width: 80%;
  }

  /* 명언 박스는 화면폭 꽉 차게 */
  .quote-block {
    display: block;
    width: 100%;
  }
}

/* 아주 작은 화면 (폰 480px 이하) 튜닝 */
@media (max-width: 480px) {
  #topbar-inner {
    flex-direction: column;
    align-items: flex-start;
    gap: 4px;
  }

  .top-menu a {
    margin-left: 0;
    margin-right: 8px;
    font-size: 12px;
  }

  .char-image-cell img {
    max-width: 100%;
  }
}
  </style>

</head>
<body>

<!-- 상단 메뉴 -->
<header id="topbar">
  <div id="topbar-inner">
    <div class="site-name">이불위키</div>
    <nav class="top-menu">
      <a href="#">대문</a>
      <a href="#">최근 변경</a>
      <a href="#">랜덤 문서</a>
    </nav>
  </div>
</header>

<div id="page">
  <div class="doc-title">가드너</div>
  <div class="doc-meta">최근 수정 시각: 2025-03-01 00:00:00</div>

  <div class="top-layout clearfix">

    <!-- 목차 -->
    <nav class="toc-box">
      <div class="toc-title">목차</div>
      <ol>
        <li><a href="#개요">1. 개요</a></li>
        <li>
          <a href="#특징">2. 특징</a>
          <ol>
            <li><a href="#외모">2.1. 외모</a></li>
            <li><a href="#소지품">2.2. 소지품</a></li>
            <li><a href="#성격">2.3. 성격</a></li>
          </ol>
        </li>
        <li><a href="#기타특징">3. 기타 특징</a></li>
        <li><a href="#커플링">4. 커플링</a></li>
        <li><a href="#여담">5. 여담</a></li>
      </ol>
    </nav>

    <!-- 인포박스 -->
    <table class="char-infobox">
      <tr>
        <td class="char-name-row" colspan="2">
          <div class="name-eng">Gardener</div>
          <div class="name-kor">가드너</div>
        </td>
      </tr>

      <tr>
        <td class="char-image-cell" colspan="2">
          <img src="일러스트8.png" alt="가드너" />
        </td>
      </tr>

      <tr>
        <th>소속 게임</th>
        <td>
          <a href="https://sawa1023.github.io/FALL-OF-TITAN/"
             class="orange-link" target="_blank">
             FALL OF TITAN
          </a>
        </td>
      </tr>

      <tr><th>거주 지역</th><td>잊혀진 신전, 멸지</td></tr>
      <tr><th>성별</th><td>여성</td></tr>
      <tr><th>나이</th><td>22세</td></tr>
      <tr><th>신체</th><td>160cm / 45kg</td></tr>
      <tr><th>취미</th><td>풀에 물주기</td></tr>
      <tr><th>좋아하는 것</th><td>명상, 개미 관찰, 숫자 세기</td></tr>
      <tr><th>종족</th><td>인간</td></tr>

    </table>
  </div>

  <!-- 본문 -->

  <h2 id="개요">1. 개요</h2>

  <div class="quote-block">
    <div class="quote-main">
      잊힌 신전의 가드너.
    </div>
    <div class="quote-sep"></div>
    <div class="quote-sub">
      가드너의 캐치프레이즈
    </div>
  </div>

  <br>

  <div class="quote-block">
    <div class="quote-main">
      “거인은 모두 묻힐거다.”
    </div>
    <div class="quote-sep"></div>
    <div class="quote-sub">
      무너진 신전의 석상을 본 가드너
    </div>
  </div>

  <p>
    <a href="https://sawa1023.github.io/FALL-OF-TITAN/"
       class="orange-link" target="_blank">
       FALL OF TITAN
    </a>
    의 주인공. 거인의 봉인을 지키기 위해
    시간이 멈춘 멸지에서 홀로 신전을 관리하는 소녀다.
    거인들이 악에 물들자 거인을 신전과 함께 완전히 봉인하기 위해
    단검 한자루(...)를 들고 멸지 곳곳을 여행한다.
  </p>

  <h2 id="특징">2. 특징</h2>

  <h3 id="외모">2.1. 외모</h3>
  <p>털이 달린 후드를 눌러쓰고 있어 맨 얼굴은 알 수 없으며 평소에는 항상 주머니에 손을 넣고있으나 무기를 들거나 급박한 상황에선 손을 빼기도 한다. 겨울에나 어울리는 상의와 달리 하의는 짧은 반바지로 허벅지가 드러날 정도이다. 양 허벅지에 밴드가 붙어있다. 시간이 흐르지 않는 멸지라는 지역의 특성 탓에 긁힌 상처도 자연치유 되지 않아 항상 밴드를 붙이고 다니는 듯 하다. 같은 이유로 일백년이 넘는 세월을 신전에서 살아왔음에도 20대의 외모 그대로 늙지 않았다.</p>

  <h3 id="소지품">2.2. 소지품</h3>

  <ul class="detail-list">
    <li>
      <span class="detail-title">단검</span>
      오직 거인만을 상대하기 위해 만들어진 무기. 인축의 살갖에는 생채기조차 내지 못하며, 주인공 '가드너'의 유일한 무기다. 거인을 쓰러뜨리고 난 뒤 사냥에 사용한 단검은 심장부에 꽂아 거인을 그 자리에 일시적으로 봉인한다. 이후 다른 거인을 상대할 땐 단검 주머니에서 새 단검을 뽑아 사용한다.
      <span class="item-note"> 집채만한 거인을 상대하는 무기를 단검으로 만들자는 생각은 누구 머리에서 나왔는지…</span><br><br>
      여담으로 거인과 전투 도중 움직이지 않고 가만히 있을 경우 단검을 핥으려다가 고개를 젓는 모션이 존재한다.
    </li>

    <li>
      <span class="detail-title">물뿌리개</span>
      신전 곳곳의 화분과 풀이 마르지 않도록 돌보는 데 사용한다. 인게임에서 식물과 상호작용하면 품에서 꺼내 물을 주는데 주머니도 없으면서 어디에 넣어다니는지 불명이다.
    </li>

    <li>
      <span class="detail-title">부적</span>
      신전 깊은 곳에 붙어있는 오래된 부적. 거인이 신전을 건너 멸지 외부로 나가는 것을 막기 위해 제작되었으나 주인공 '가드너'가 게임 시작과 동시에 떼어내고 직접 들고다닌다. 거인이 분노하지 않았을 때 거인의 시야에 부적을 노출시키면 일시적으로 거인을 경직시키는 효과가 있다.
    </li>
  </ul>

  <h3 id="성격">2.3. 성격</h3>
  <p>스토리 상에서는 그저 묵묵히 거인을 죽이고 신전과 함께 거인과 자신까지 봉인하는 행보를 통해 냉정하고 결단적인 모습을 보여줬으나, 전투 도중 잠수를 할 시 칼을 핥으려 한다거나 생물이 살기 힘든 멸지에 자라난 식물들을 묵묵히 가꾸는 등, 나름 장난스럽고 인간적인 면모도 보여준다.</p>
  <p>또한 개미 등을 관찰하거나 가끔 말까지 거는 것으로 보아, 일백 하고도 이십구년을 혼자 살다보니 그저 대화할 사람이 없어서 저절로 과묵해졌다고 추측해볼 수 있다.</p>

  <h2 id="기타특징">3. 기타 특징</h2>

  <h3 id="좋아하는것">3.1. 좋아하는 것</h3>
  <ul>
    <li>명상</li>
    <li>개미 관찰</li>
    <li>숫자 세기</li>
  </ul>

  <h3 id="싫어하는것">3.2. 싫어하는 것</h3>
  <ul>
    <li>좋아하는 것과 달리, 싫어하는 것은 딱히 공개되어있지 않다. 허나 높은 곳에서 떨어지거나 거인의 몸에서 떨어져 바닥을 구르면 특유의 "나읏...!" 하는 신음과 함께 바닥을 때리며 일어난다거나, 돌이나 나뭇가지 등에 걸리면 낮은 확률로 넘어지며 마찬가지로 특유의 신음과 함께 원인을 차버리는 모션이 존재한다. 흙먼지가 묻는다거나 물에 젖을 때도 별다른 모션이 없으나 바닥과 접촉할 때만 이러한 상호작용이 있는 것으로 보아 땅과 접촉하는 것을 싫어하는 듯.<br></li>
    <li>유독 몸이 묶이는 것을 싫어한다. 거인의 손에 붙잡히거나 돌에 깔려 움직이지 못하는 장면에서 노골적으로 불쾌함을 드러냈다.<br></li>
    <li>제작자가 밝히길 포도를 안좋아한다고 한다. 이유는 너무 셔서...</li>
  </ul>

  <h2 id="커플링">4. 커플링</h2>
  <p>작중 등장하는 인물이 가드너 한 명 밖에 없으며, 제작자도 가드너가 누군가와 연애하는 것은 상정한 적 없다 밝혔다.</p>

  <h2 id="여담">5. 여담</h2>
  <ul>
    <li>어드벤쳐 퍼즐 게임, Nyaruut! 제작자의 야심찬 후속작이다. 전작에 비해 모든 면이 말도안되게 발전했다며 같은 제작자가 맞냐는 반응을 얻어낼 만큼 좋은 평가를 받았다.</li>
    <li>출시 전 공개된 상징 이모지는 '🗿'.</li>
  </ul>

  <p class="small">
    이 문서는 팬메이드 자캐 문서이며, 실제로 존재하는 게임 및 웹사이트가 아닙니다.
  </p>

</div>
</body>
</html>


