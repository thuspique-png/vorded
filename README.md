<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>VORTEX — Cardiac Power System</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Mono:ital,wght@0,300;0,400;0,500;1,300&family=Crimson+Pro:ital,wght@0,300;0,600;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --blood: #8B0000;
    --deep-blood: #3D0000;
    --arterial: #C0392B;
    --venous: #1a0a0a;
    --pulse: #E74C3C;
    --cold: #0d1b2a;
    --bone: #d4c5b0;
    --dim: #7a6a5a;
    --forbidden: #ff2200;
    --gold: #c9a84c;
    --void: #ede4da;
    --card-bg: #f5ede6;
    --card-border: #c8b4a4;
    --text-main: #1e0e08;
    --text-dim: #7a5a4a;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--void);
    color: #1e0e08;
    font-family: 'DM Mono', monospace;
    font-size: 13px;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* NOISE OVERLAY */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 999;
    opacity: 0.4;
  }

  /* HEADER */
  header {
    position: relative;
    padding: 80px 60px 60px;
    border-bottom: 1px solid #d4c0b0;
    overflow: hidden;
  }

  header::after {
    content: '';
    position: absolute;
    top: -60px; right: -60px;
    width: 400px; height: 400px;
    border-radius: 50%;
    border: 1px solid rgba(139,0,0,0.15);
    animation: pulse-ring 4s ease-in-out infinite;
  }

  header::before {
    content: '';
    position: absolute;
    top: -20px; right: -20px;
    width: 300px; height: 300px;
    border-radius: 50%;
    border: 1px solid rgba(139,0,0,0.25);
    animation: pulse-ring 4s ease-in-out infinite 0.5s;
  }

  @keyframes pulse-ring {
    0%, 100% { transform: scale(1); opacity: 0.3; }
    50% { transform: scale(1.08); opacity: 0.6; }
  }

  .system-label {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 4px;
    color: var(--arterial);
    text-transform: uppercase;
    margin-bottom: 16px;
  }

  h1 {
    font-family: 'Bebas Neue', sans-serif;
    font-size: clamp(72px, 12vw, 140px);
    line-height: 0.9;
    color: #1e0e08;
    letter-spacing: -2px;
  }

  h1 span {
    color: var(--arterial);
  }

  .tagline {
    font-family: 'Crimson Pro', serif;
    font-style: italic;
    font-size: 18px;
    color: #8a6a5a;
    margin-top: 20px;
    max-width: 500px;
  }

  /* MAIN LAYOUT */
  main {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 40px 120px;
  }

  /* SECTION HEADER */
  .section-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 42px;
    letter-spacing: 2px;
    color: #1e0e08;
    margin: 80px 0 8px;
    position: relative;
    padding-left: 20px;
  }

  .section-title::before {
    content: '';
    position: absolute;
    left: 0; top: 8px; bottom: 8px;
    width: 3px;
    background: var(--arterial);
  }

  .section-sub {
    font-size: 11px;
    letter-spacing: 3px;
    color: #a08878;
    text-transform: uppercase;
    padding-left: 20px;
    margin-bottom: 40px;
  }

  /* TIERS */
  .tier-grid {
    display: flex;
    flex-direction: column;
    gap: 2px;
  }

  .tier-card {
    display: grid;
    grid-template-columns: 120px 1fr auto;
    align-items: start;
    gap: 30px;
    padding: 28px 32px;
    border: 1px solid #c8b4a4;
    background: rgba(255,255,255,0.5);
    transition: background 0.3s, border-color 0.3s;
    cursor: default;
    position: relative;
    overflow: hidden;
  }

  .tier-card::before {
    content: '';
    position: absolute;
    left: 0; top: 0; bottom: 0;
    width: 0;
    background: var(--arterial);
    transition: width 0.4s ease;
    opacity: 0.06;
  }

  .tier-card:hover::before { width: 100%; }
  .tier-card:hover { border-color: rgba(139,0,0,0.5); }

  .tier-card.t6 {
    border-color: #c8b4a4;
    background: rgba(255,255,255,0.5);
  }

  .tier-num {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 56px;
    line-height: 1;
    color: #d4b8aa;
    position: relative;
  }

  .tier-card:hover .tier-num { color: rgba(139,0,0,0.35); }
  .tier-card.t6 .tier-num { color: #d4b8aa; }

  .tier-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 22px;
    letter-spacing: 1px;
    color: #1e0e08;
    margin-bottom: 6px;
  }

  .tier-latin {
    font-family: 'Crimson Pro', serif;
    font-style: italic;
    color: var(--arterial);
    font-size: 13px;
    margin-bottom: 10px;
  }

  .tier-desc {
    color: #5a4038;
    font-size: 12px;
    line-height: 1.8;
  }

  .tier-stat {
    text-align: right;
    min-width: 120px;
  }

  .tier-stat-label {
    font-size: 10px;
    letter-spacing: 2px;
    color: #b89888;
    text-transform: uppercase;
    margin-bottom: 4px;
  }

  .tier-bpm {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 28px;
    color: var(--blood);
  }

  .tier-card.t6 .tier-bpm {
    color: var(--forbidden);
    animation: flicker 3s ease-in-out infinite;
  }

  @keyframes flicker {
    0%, 100% { opacity: 1; }
    92% { opacity: 1; }
    93% { opacity: 0.3; }
    94% { opacity: 1; }
    97% { opacity: 0.5; }
    98% { opacity: 1; }
  }

  /* TECHNIQUES */
  .tech-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
  }

  .tech-category {
    grid-column: 1 / -1;
    padding: 12px 0 8px;
    font-size: 10px;
    letter-spacing: 4px;
    text-transform: uppercase;
    border-top: 1px solid #1a0808;
    margin-top: 24px;
  }

  .tech-category.offense { color: var(--arterial); }
  .tech-category.defense { color: #4a7ab5; }
  .tech-category.utility { color: var(--gold); }
  .tech-category.forbidden {
    color: var(--forbidden);
    animation: flicker 4s ease-in-out infinite;
  }

  .tech-card {
    padding: 24px 28px;
    border: 1px solid #c8b4a4;
    background: rgba(255,255,255,0.5);
    transition: all 0.3s;
  }

  .tech-card:hover { background: rgba(255,255,255,0.8); border-color: #a89080; }

  .tech-card.forbidden-card {
    border-color: rgba(200,26,0,0.25);
    background: rgba(255,220,210,0.25);
  }

  .tech-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 20px;
    letter-spacing: 1px;
    margin-bottom: 4px;
  }

  .tech-card.offense .tech-name { color: var(--arterial); }
  .tech-card.defense .tech-name { color: #6a9fd8; }
  .tech-card.utility .tech-name { color: var(--gold); }
  .tech-card.forbidden-card .tech-name { color: var(--forbidden); }

  .tech-subtitle {
    font-family: 'Crimson Pro', serif;
    font-style: italic;
    font-size: 12px;
    color: #8a6a5a;
    margin-bottom: 12px;
  }

  .tech-desc {
    font-size: 12px;
    color: #5a4038;
    margin-bottom: 16px;
    line-height: 1.8;
  }

  .tech-meta {
    display: flex;
    flex-direction: column;
    gap: 6px;
  }

  .meta-row {
    display: grid;
    grid-template-columns: 60px 1fr;
    gap: 12px;
    font-size: 11px;
  }

  .meta-label {
    color: #b89888;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-size: 10px;
    padding-top: 1px;
  }

  .meta-cost { color: #a04040; }
  .meta-pro { color: #508050; }
  .meta-con { color: #a06040; }

  /* LIMITATIONS */
  .limit-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    margin-top: 8px;
  }

  .limit-card {
    padding: 28px;
    border: 1px solid #c8b4a4;
    background: rgba(255,255,255,0.5);
  }

  .limit-icon {
    font-size: 28px;
    margin-bottom: 12px;
    display: block;
  }

  .limit-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 18px;
    letter-spacing: 1px;
    color: #1e0e08;
    margin-bottom: 8px;
  }

  .limit-desc {
    font-size: 12px;
    color: #5a4038;
    line-height: 1.8;
  }

  /* FACTIONS */
  .faction-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
  }

  .faction-card {
    padding: 36px 28px;
    border: 1px solid #c8b4a4;
    background: rgba(255,255,255,0.5);
    position: relative;
    overflow: hidden;
  }

  .faction-card::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 2px;
  }

  .faction-card.guild::after { background: var(--gold); }
  .faction-card.cult::after { background: var(--arterial); }
  .faction-card.surgeon::after { background: #4a9a6a; }

  .faction-name {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 28px;
    letter-spacing: 2px;
    margin-bottom: 4px;
  }

  .faction-card.guild .faction-name { color: var(--gold); }
  .faction-card.cult .faction-name { color: var(--arterial); }
  .faction-card.surgeon .faction-name { color: #5abf8a; }

  .faction-alias {
    font-family: 'Crimson Pro', serif;
    font-style: italic;
    font-size: 13px;
    color: #8a6a5a;
    margin-bottom: 16px;
  }

  .faction-desc {
    font-size: 12px;
    color: #5a4038;
    line-height: 1.8;
    margin-bottom: 16px;
  }

  .faction-motive {
    font-size: 11px;
    letter-spacing: 1px;
    padding: 8px 12px;
    border-left: 2px solid;
    background: rgba(0,0,0,0.04);
  }

  .faction-card.guild .faction-motive { border-color: var(--gold); color: var(--gold); }
  .faction-card.cult .faction-motive { border-color: var(--arterial); color: var(--arterial); }
  .faction-card.surgeon .faction-motive { border-color: #5abf8a; color: #5abf8a; }

  /* SECRET SECTION */
  #secret-section {
    margin-top: 80px;
    padding: 40px;
    border: 1px solid rgba(200,26,0,0.2);
    background: rgba(255,220,210,0.2);
    position: relative;
    overflow: hidden;
  }

  #secret-section::before {
    content: 'CLASSIFIED';
    position: absolute;
    top: 50%; left: 50%;
    transform: translate(-50%, -50%) rotate(-12deg);
    font-family: 'Bebas Neue', sans-serif;
    font-size: 120px;
    color: rgba(200,26,0,0.06);
    letter-spacing: 10px;
    pointer-events: none;
    white-space: nowrap;
  }

  .secret-locked {
    text-align: center;
    padding: 40px 20px;
  }

  .secret-locked-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 32px;
    color: #c8a898;
    letter-spacing: 4px;
    margin-bottom: 12px;
  }

  .secret-locked-sub {
    font-size: 11px;
    color: #c0a898;
    letter-spacing: 2px;
  }

  .secret-content {
    display: none;
  }

  .secret-content.revealed {
    display: block;
    animation: fadeReveal 2s ease forwards;
  }

  @keyframes fadeReveal {
    from { opacity: 0; filter: blur(8px); }
    to { opacity: 1; filter: blur(0); }
  }

  .secret-title {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 36px;
    color: var(--gold);
    letter-spacing: 3px;
    margin-bottom: 6px;
  }

  .secret-latin {
    font-family: 'Crimson Pro', serif;
    font-style: italic;
    color: var(--arterial);
    margin-bottom: 24px;
    font-size: 15px;
  }

  .secret-body {
    font-size: 13px;
    color: #5a4038;
    line-height: 2;
    max-width: 760px;
  }

  .secret-body p { margin-bottom: 16px; }

  .secret-body strong {
    color: #a07828;
    font-weight: normal;
  }

  .secret-body em {
    font-family: 'Crimson Pro', serif;
    font-style: italic;
    color: #1e0e08;
  }

  /* DIVIDER */
  .divider {
    height: 1px;
    background: linear-gradient(to right, transparent, #c8b4a4, transparent);
    margin: 60px 0;
  }

  /* FOOTER */
  footer {
    text-align: center;
    padding: 40px;
    font-size: 11px;
    color: #c0a898;
    letter-spacing: 2px;
    border-top: 1px solid #d4c0b0;
  }

  /* RESPONSIVE */
  @media (max-width: 768px) {
    header { padding: 48px 24px 40px; }
    main { padding: 0 20px 80px; }
    .tier-card { grid-template-columns: 80px 1fr; }
    .tier-stat { display: none; }
    .tech-grid { grid-template-columns: 1fr; }
    .limit-grid { grid-template-columns: 1fr; }
    .faction-grid { grid-template-columns: 1fr; }
  }

  /* PULSE DOT */
  .pulse-dot {
    display: inline-block;
    width: 6px; height: 6px;
    background: var(--arterial);
    border-radius: 50%;
    margin-right: 8px;
    animation: beat 1.2s ease-in-out infinite;
    vertical-align: middle;
  }

  @keyframes beat {
    0%, 100% { transform: scale(1); opacity: 1; }
    14% { transform: scale(1.4); opacity: 1; }
    28% { transform: scale(1); opacity: 0.6; }
  }

  /* TIER 6 CLICK COUNTER */
  .t6-tap {
    cursor: pointer;
    user-select: none;
  }

  .t6-tap:active { opacity: 0.85; }

  .tap-hint {
    font-size: 10px;
    color: #1a0808;
    letter-spacing: 1px;
    margin-top: 8px;
    transition: color 0.5s;
  }

  .tap-hint.warming { color: #3a1010; }
  .tap-hint.hot { color: var(--arterial); }
</style>
</head>
<body>

<header>
  <div class="system-label"><span class="pulse-dot"></span>Cardiac Power System — Codex v.01</div>
  <h1>VOR<span>TEX</span></h1>
  <p class="tagline">Kekuatan bukan dari otot. Bukan dari kehendak. Ia mengalir dari yang berputar di dalam dadamu — dan dari apa yang terjadi saat ia berhenti.</p>
</header>

<main>

  <!-- ======================== TIERS ======================== -->
  <div class="section-title">Tingkatan</div>
  <div class="section-sub">Enam derajat keberadaan — dari yang bernapas hingga yang sudah tidak</div>

  <div class="tier-grid">

    <div class="tier-card">
      <div class="tier-num">01</div>
      <div>
        <div class="tier-name">Latent</div>
        <div class="tier-latin">Homo Dormiens — Manusia yang Tidur</div>
        <div class="tier-desc">Manusia biasa yang belum pernah menyentuh Vortex. Jantung berdetak normal, aliran darah linier, tidak ada kesadaran akan tekanan spiral di dalam tubuh. Mayoritas populasi ada di sini. Mereka tidak tahu apa yang mereka miliki.</div>
      </div>
      <div class="tier-stat">
        <div class="tier-stat-label">Ritme Jantung</div>
        <div class="tier-bpm">60–100</div>
        <div style="font-size:10px;color:#2a1a1a;">BPM (normal)</div>
      </div>
    </div>

    <div class="tier-card">
      <div class="tier-num">02</div>
      <div>
        <div class="tier-name">Kinetic</div>
        <div class="tier-latin">Primo Vortice — Pertama Merasakan Pusaran</div>
        <div class="tier-desc">Pengguna yang sudah "membuka" Vortex pertama kali, biasanya lewat trauma besar, olahraga ekstrem, atau kondisi hidup-mati. Bisa merasakan aliran darah sendiri secara sadar dan mulai membentuk tekanan kecil keluar tubuh. Kekuatan setara manusia terlatih yang jauh di atas rata-rata.</div>
      </div>
      <div class="tier-stat">
        <div class="tier-stat-label">Ritme Jantung</div>
        <div class="tier-bpm">100–140</div>
        <div style="font-size:10px;color:#2a1a1a;">BPM saat aktif</div>
      </div>
    </div>

    <div class="tier-card">
      <div class="tier-num">03</div>
      <div>
        <div class="tier-name">Spiral</div>
        <div class="tier-latin">Gyrus Conscii — Lingkaran yang Sadar</div>
        <div class="tier-desc">Pengguna mampu membentuk Vortex keluar tubuh secara stabil. Aliran darah bisa diarahkan secara eksternal — tekanan udara terbentuk, proyektil bisa dibelokkan, cairan di sekitar bisa dipengaruhi. Di tier ini, tubuh mulai menunjukkan tanda fisik: pembuluh darah lebih terlihat saat aktif, mata sedikit memerah.</div>
      </div>
      <div class="tier-stat">
        <div class="tier-stat-label">Ritme Jantung</div>
        <div class="tier-bpm">140–170</div>
        <div style="font-size:10px;color:#2a1a1a;">BPM saat aktif</div>
      </div>
    </div>

    <div class="tier-card">
      <div class="tier-num">04</div>
      <div>
        <div class="tier-name">Toroidal</div>
        <div class="tier-latin">Anulus Perfectus — Cincin yang Sempurna</div>
        <div class="tier-desc">Pengguna menguasai bentuk Vortex toroidal penuh — pusaran yang stabil, self-sustaining, bisa dilepas dan dikontrol dari jarak jauh. Jantung secara aktif "berkomunikasi" dengan sistem Vortex luar tubuh. Di tier ini, kemampuan mulai terasa supernatural bagi orang awam. Sangat sedikit yang mencapai ini secara alami.</div>
      </div>
      <div class="tier-stat">
        <div class="tier-stat-label">Ritme Jantung</div>
        <div class="tier-bpm">170–200</div>
        <div style="font-size:10px;color:#2a1a1a;">BPM saat aktif</div>
      </div>
    </div>

    <div class="tier-card">
      <div class="tier-num">05</div>
      <div>
        <div class="tier-name">Arrhythmic</div>
        <div class="tier-latin">Cor Sine Lege — Jantung Tanpa Hukum</div>
        <div class="tier-desc">Pengguna yang telah melampaui batas fisiologis normal. Ritme jantung tidak lagi konsisten — ia berubah secara aktif sesuai kebutuhan tempur. Vortex yang terbentuk bisa memanipulasi tekanan, gravitasi lokal, bahkan aliran cairan dalam tubuh orang lain. Biasanya disertai kerusakan jantung permanen yang dikompensasi oleh Vortex itu sendiri.</div>
      </div>
      <div class="tier-stat">
        <div class="tier-stat-label">Ritme Jantung</div>
        <div class="tier-bpm">200+</div>
        <div style="font-size:10px;color:#2a1a1a;">irregular</div>
      </div>
    </div>

    <div class="tier-card t6 t6-tap" id="tier6-card" onclick="registerT6Click()">
      <div class="tier-num">06</div>
      <div>
        <div class="tier-name">Asystole</div>
        <div class="tier-latin">Post Mortem Fluere — Mengalir Setelah Mati</div>
        <div class="tier-desc">Jantung berhenti. Secara medis, subjek sudah meninggal. Namun Vortex yang terbentuk selama hidup tidak serta-merta menghilang — ia berputar tanpa pusat, tanpa jangkar biologis. Pengguna Tier 6 beroperasi dalam kondisi klinis mati: tidak ada detak jantung, tidak ada tekanan darah, tidak ada rasa sakit. Vortex mereka bukan lagi perpanjangan tubuh — ia adalah satu-satunya hal yang membuat mereka tetap bergerak.</div>
        <div class="tap-hint" id="tap-hint">—</div>
      </div>
      <div class="tier-stat">
        <div class="tier-stat-label">Ritme Jantung</div>
        <div class="tier-bpm">0</div>
        <div style="font-size:10px;color:rgba(255,34,0,0.4);">flatline</div>
      </div>
    </div>

  </div>

  <!-- ======================== CLASSES ======================== -->
  <div class="section-title">Kelas Vortex</div>
  <div class="section-sub">Bukan daftar teknik — ini sifat. Medianya terserah penggunanya.</div>

  <div style="font-size:12px;color:var(--dim);line-height:2;padding:0 20px 32px;max-width:760px;">
    Tidak ada teknik baku dalam sistem Vortex. Yang ada hanya <em style="font-family:'Crimson Pro',serif;color:var(--bone);">kelas</em> — sifat dasar dari cara seseorang mengekspresikan Vortex mereka. Seorang pengguna Offense bisa mengekspresikannya lewat pukulan, lewat angin, lewat benda yang dilempar, lewat getaran suara, atau apapun yang jadi medianya. Kelas bukan batasan — ia adalah kecenderungan alami yang muncul saat Vortex pertama kali dibuka.<br><br>
    Setiap pengguna mengembangkan teknik sendiri. Tidak ada dua orang yang bertarung persis sama.
  </div>

  <div class="tech-grid">

    <!-- OFFENSE -->
    <div class="tech-category offense" style="grid-column:1/-1;">▶ Kelas I — Offense</div>

    <div class="tech-card offense" style="grid-column:1/-1;display:grid;grid-template-columns:1fr 1fr;gap:32px;">
      <div>
        <div class="tech-name">Sifat Dasar</div>
        <div class="tech-desc" style="margin-top:8px;">
          Vortex diarahkan keluar — memfokuskan tekanan, rotasi, dan momentum ke satu titik atau satu arah. Pengguna kelas ini secara naluriah mengekspresikan Vortex sebagai <em style="font-family:'Crimson Pro',serif;">kekuatan yang merusak</em>. Mediumnya bisa apapun: udara yang dikompres, cairan yang dilempar, benda fisik yang diputar, bahkan suara yang dijadikan gelombang kejut.<br><br>
          Yan
