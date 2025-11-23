<!doctype html>
<html lang="zh-Hant">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>個人履歷表 — 亞洲大學 經營管理系</title>
  <style>
    :root{--accent:#0b77d1;--muted:#666}
    body{font-family: system-ui,-apple-system,Segoe UI,Roboto,'Noto Sans TC',"Helvetica Neue",Arial; background:#f6f8fb; color:#222; margin:0; padding:32px}
    .card{max-width:900px; margin:24px auto; background:#fff; border-radius:12px; box-shadow:0 8px 30px rgba(12,20,40,0.08); overflow:hidden}
    .header{display:flex; gap:24px; padding:28px 32px; align-items:center}
    .avatar{width:96px;height:96px;border-radius:12px;background:linear-gradient(135deg,var(--accent),#5bc0eb);display:flex;align-items:center;justify-content:center;color:#fff;font-weight:700;font-size:28px}
    .title{flex:1}
    h1{margin:0;font-size:22px}
    .meta{color:var(--muted);margin-top:6px}
    .actions{padding:16px 32px;border-top:1px solid #f0f2f6;display:flex;gap:12px;align-items:center}
    button{background:var(--accent);border:none;color:#fff;padding:10px 14px;border-radius:8px;font-weight:600;cursor:pointer}
    .btn-ghost{background:transparent;color:var(--accent);border:1px solid rgba(11,119,209,0.12)}
    .content{display:grid;grid-template-columns:1fr 360px;gap:24px;padding:24px 32px}
    section{background:transparent}
    .section-title{font-weight:700;margin-bottom:8px}
    .info-row{display:flex;gap:8px;align-items:center;margin-bottom:8px}
    .label{min-width:86px;color:var(--muted);font-size:14px}
    .value{font-size:15px}
    .sidebar{background:#fbfdff;border-left:1px solid #f0f2f6;padding:16px;border-radius:8px}
    ul{padding-left:18px;margin-top:6px}
    .note{font-size:13px;color:var(--muted)}
    @media (max-width:800px){.content{grid-template-columns:1fr;}.header{flex-direction:row;gap:12px}.avatar{width:72px;height:72px;font-size:20px}}
  </style>
</head>
<body>
  <div class="card" id="resume">
    <div class="header">
      <div class="avatar" aria-hidden="true">A</div>
      <div class="title">
        <h1 id="name">王小明（範例）</h1>
        <div class="meta">亞洲大學｜經營管理系</div>
      </div>
      <div style="text-align:right">
        <div class="meta">更新：2025-11-22</div>
      </div>
    </div>

    <div class="content">
      <main>
        <section>
          <div class="section-title">聯絡資訊</div>
          <div class="info-row"><div class="label">電子郵件</div><div class="value">example@asu.edu.tw</div></div>
          <div class="info-row"><div class="label">電話</div><div class="value" id="phoneMasked">--</div></div>
          <div class="note">為保護隱私，電話已遮碼（中間數字以星號替代）。</div>
        </section>

        <section style="margin-top:18px">
          <div class="section-title">學歷</div>
          <div><strong>亞洲大學</strong>，經營管理系（預計 2026 畢業）</div>
        </section>

        <section style="margin-top:18px">
          <div class="section-title">學校經歷 / 社團</div>
          <ul>
            <li>系學會幹部 — 活動企劃與預算管理</li>
            <li>商管案例競賽隊員 — 跨校專案提案</li>
          </ul>
        </section>

        <section style="margin-top:18px">
          <div class="section-title">實習與工作經驗</div>
          <div><strong>實習生 — 某企業行銷部</strong>（2024/07 — 2024/08）</div>
          <ul>
            <li>協助活動企劃與社群內容撰寫</li>
            <li>整理消費者回饋與簡報彙整</li>
          </ul>
        </section>

        <section style="margin-top:18px">
          <div class="section-title">技能</div>
          <ul>
            <li>簡報與報告撰寫</li>
            <li>Excel 基本分析（樞紐、函數）</li>
            <li>中文／英文溝通能力</li>
          </ul>
        </section>
      </main>

      <aside class="sidebar">
        <div style="font-weight:700;margin-bottom:8px">個人簡介</div>
        <div class="note">我是亞洲大學經營管理系的學生，對行銷與商業分析有興趣，擅長團隊合作與專案管理。</div>

        <div style="margin-top:14px;font-weight:700">技能標籤</div>
        <ul>
          <li>企劃</li>
          <li>簡報</li>
          <li>數據整理</li>
        </ul>

        <div style="margin-top:14px;font-weight:700">其他</div>
        <div class="note">可依需要修改此範本內容與排版，並將檔案另存為 HTML 後以瀏覽器列印為 PDF。</div>
      </aside>
    </div>

    <div class="actions">
      <button id="exportPdf">輸出成 PDF</button>
      <button class="btn-ghost" id="downloadHtml">下載 HTML 檔</button>
      <div style="margin-left:auto;color:var(--muted);font-size:13px">電話已遮碼範例：091****678</div>
    </div>
  </div>

  <script>
    // 使用者資料（範例）
    const user = {
      name: '吳旻臻',
      school: '亞洲大學',
      dept: '經營管理系',
      email: '114031089@live.asia.edu.tw',
      phone: '0912345678' // <-- 若要換成你的電話，請直接修改這裡（但注意隱私）
    };

    // 將資料寫入頁面
    document.getElementById('name').textContent = user.name + ' （範例）';
    // 遮碼電話：保留前三與後三位，中間以星號替代（若長度較短會自適應）
    function maskPhone(p){
      if(!p) return '--';
      const digits = p.replace(/\D/g,'');
      if(digits.length <= 4) return digits.replace(/.(?=.)/g,'*');
      const keepStart = 3;
      const keepEnd = 3;
      const middleCount = Math.max(0,digits.length - keepStart - keepEnd);
      return digits.slice(0,keepStart) + '*'.repeat(middleCount) + digits.slice(-keepEnd);
    }
    document.getElementById('phoneMasked').textContent = maskPhone(user.phone);

    // 輸出成 PDF（使用瀏覽器的列印功能）
    document.getElementById('exportPdf').addEventListener('click', ()=>{
      // 簡單優化列印樣式：開啟新視窗列印可以避免頁面 UI 影響，但這裡用 print()
      window.print();
    });

    // 下載 HTML 檔（將目前頁面內容包成檔案）
    document.getElementById('downloadHtml').addEventListener('click', ()=>{
      const doctype = '<!doctype html>\n';
      const html = document.documentElement.outerHTML;
      const blob = new Blob([doctype + html], {type: 'text/html'});
      const a = document.createElement('a');
      a.href = URL.createObjectURL(blob);
      a.download = (user.name || 'resume') + '.html';
      document.body.appendChild(a);
      a.click();
      a.remove();
    });
  </script>
</body>
</html>
