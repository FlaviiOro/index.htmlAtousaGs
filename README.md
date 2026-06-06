<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Atousa G — House of G$ at Halcyon</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,500;1,300;1,400&family=Bebas+Neue&family=Space+Mono&display=swap" rel="stylesheet"/>
<style>
  *{box-sizing:border-box;margin:0;padding:0}
  :root{
    --black:#060606;
    --near:#0e0e0e;
    --char:#191919;
    --gun:#242428;
    --silver:#b0b0bc;
    --bright:#e0e0ea;
    --gold:#c4a24a;
    --gold2:#dfc07a;
    --white:#f0f0ee;
    --dim:#555;
  }
  html{scroll-behavior:smooth}
  body{background:var(--black);color:var(--silver);font-family:'Cormorant Garamond','Georgia',serif;-webkit-font-smoothing:antialiased;overflow-x:hidden}

  /* NOISE overlay for nightclub texture */
  body::after{content:'';position:fixed;inset:0;background:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");pointer-events:none;z-index:999;opacity:.5}

  .bebas{font-family:'Bebas Neue','Impact',sans-serif}
  .mono{font-family:'Space Mono','Courier New',monospace}

  /* TOP LINE decorative rule */
  .top-rule{height:1px;background:linear-gradient(90deg,transparent,rgba(196,162,74,.5),transparent)}

  /* MAIN HEADER */
  .header{padding:80px 32px 52px;text-align:center;position:relative}
  .header::before{content:'';position:absolute;bottom:0;left:0;right:0;height:1px;background:linear-gradient(90deg,transparent,rgba(255,255,255,.04),transparent)}
  .eyebrow{font-family:'Space Mono',monospace;font-size:9px;letter-spacing:.42em;color:var(--gold);text-transform:uppercase;margin-bottom:18px;display:block}
  .main-title{font-size:clamp(52px,12vw,108px);letter-spacing:.04em;color:var(--white);line-height:.9;text-shadow:0 0 80px rgba(196,162,74,.1)}
  .main-title span{color:var(--gold)}
  .subtitle{font-style:italic;font-size:clamp(16px,2.5vw,20px);color:#666;max-width:440px;margin:20px auto 0;line-height:1.65}

  /* DOWNLOAD LINKS */
  .section{max-width:820px;margin:0 auto;padding:52px 24px}
  .section-label{font-family:'Space Mono',monospace;font-size:8px;letter-spacing:.38em;color:var(--dim);text-transform:uppercase;margin-bottom:16px;display:block}
  .dl-list{display:flex;flex-direction:column;gap:10px;margin-bottom:0}
  .dl-link{display:flex;align-items:center;gap:16px;padding:20px 22px;background:var(--near);border:1px solid rgba(255,255,255,.06);border-left:3px solid var(--gold);text-decoration:none;transition:all .3s ease}
  .dl-link:hover{background:var(--char);transform:translateX(6px);border-color:rgba(196,162,74,.3)}
  .dl-icon{font-size:20px;flex-shrink:0}
  .dl-text strong{display:block;font-family:'Bebas Neue',sans-serif;font-size:17px;color:var(--white);letter-spacing:.06em;line-height:1}
  .dl-text em{font-size:13px;color:#555;font-style:italic;margin-top:2px;display:block}
  .dl-arrow{font-family:'Space Mono',monospace;font-size:10px;color:var(--gold);margin-left:auto;flex-shrink:0}

  /* CATEGORY FILTERS */
  .filters{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:28px}
  .filter-btn{font-family:'Space Mono',monospace;font-size:8px;letter-spacing:.28em;text-transform:uppercase;background:none;border:1px solid rgba(255,255,255,.1);color:#555;padding:7px 16px;cursor:pointer;transition:all .3s ease}
  .filter-btn:hover, .filter-btn.active{border-color:var(--gold);color:var(--gold);background:rgba(196,162,74,.07);transform:translateY(-1px)}

  /* GRID CONTAINER */
  .grid-wrap{max-width:1100px;margin:0 auto;padding:0 12px 80px}
  .grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(230px,1fr));gap:10px}

  /* CARDS WITH FADE/SCALE TRANSITIONS */
  .card{position:relative;overflow:hidden;background:var(--char);cursor:pointer;display:block;transition:opacity .4s ease, transform .4s ease, visibility .4s;opacity:1;transform:scale(1)}
  .card.hidden{opacity:0;transform:scale(0.95);position:absolute;pointer-events:none;visibility:hidden}
  .card img{width:100%;aspect-ratio:3/4;object-fit:cover;display:block;transition:transform .6s cubic-bezier(0.25, 1, 0.5, 1)}
  .card:hover img{transform:scale(1.05)}
  .card-placeholder{width:100%;aspect-ratio:3/4;background:linear-gradient(135deg,var(--char),var(--near));display:flex;flex-direction:column;justify-content:flex-end;padding:16px}
  .card-base{position:absolute;bottom:0;left:0;right:0;background:linear-gradient(to top,rgba(0,0,0,.85),transparent);padding:36px 14px 12px;transition:opacity .3s ease}
  .card-overlay{position:absolute;inset:0;background:linear-gradient(to top,rgba(0,0,0,.93) 0%,rgba(0,0,0,.2) 55%,transparent 100%);opacity:0;transition:opacity .3s ease;display:flex;flex-direction:column;justify-content:flex-end;padding:20px}
  
  .card:hover .card-overlay{opacity:1}
  .card:hover .card-base{opacity:0}
  .card-tag{font-family:'Space Mono',monospace;font-size:7px;color:var(--gold);letter-spacing:.28em;text-transform:uppercase;margin-bottom:3px;display:block}
  .card-venue{font-family:'Bebas Neue',sans-serif;font-size:14px;color:var(--white);letter-spacing:.05em;line-height:1.1}
  .card-caption{font-style:italic;font-size:13px;color:#ccc;line-height:1.5;margin-top:7px}

  /* HIGH-END DISCO BRAND STRIP (FIXED AND VISIBLE) */
  .venues-container {
    border-top: 1px solid rgba(196, 162, 74, 0.15);
    border-bottom: 1px solid rgba(196, 162, 74, 0.15);
    background: #09090b;
    padding: 60px 24px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .venues-brand-header {
    margin-bottom: 32px;
  }
  .venues-brand-header h2 {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 38px;
    letter-spacing: 0.15em;
    color: var(--white);
    line-height: 1;
    margin-bottom: 8px;
  }
  .venues-brand-sub {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.35em;
    color: var(--gold);
    text-transform: uppercase;
  }
  .venues-grid {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px 40px;
    max-width: 950px;
    margin: 0 auto;
  }
  .venue-tag {
    font-family: 'Space Mono', monospace;
    font-size: 14px;
    font-weight: 500;
    color: var(--bright);
    letter-spacing: 0.05em;
    text-transform: uppercase;
    transition: all 0.3s cubic-bezier(0.25, 1, 0.5, 1);
    cursor: default;
    position: relative;
    padding: 4px 0;
  }
  .venue-tag:hover {
    color: var(--gold2);
    text-shadow: 0 0 15px rgba(223, 192, 122, 0.7);
    transform: translateY(-2px);
  }

  /* PREMIUM FOOTER */
  .premium-footer {
    padding: 90px 24px;
    text-align: center;
    background: var(--black);
  }
  .footer-eyebrow {
    font-family: 'Space Mono', monospace;
    font-size: 9px;
    letter-spacing: 0.4em;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: 16px;
    display: block;
  }
  .footer-headline {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-size: clamp(24px, 4vw, 36px);
    color: var(--white);
    margin-bottom: 32px;
    line-height: 1.2;
  }
  .footer-btn {
    display: inline-block;
    padding: 16px 42px;
    border: 1px solid var(--gold);
    color: var(--white);
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.3em;
    text-transform: uppercase;
    text-decoration: none;
    background: transparent;
    transition: all 0.4s cubic-bezier(0.25, 1, 0.5, 1);
    position: relative;
  }
  .footer-btn:hover {
    background: var(--gold);
    color: var(--black);
    box-shadow: 0 0 25px rgba(196, 162, 74, 0.25);
    transform: translateY(-2px);
  }
  .bottom-rule{height:1px;background:linear-gradient(90deg,transparent,rgba(196,162,74,.2),transparent)}

  /* LIGHTBOX WINDOW OVERLAY */
  #lightbox{position:fixed;inset:0;background:rgba(0,0,0,.96);z-index:500;display:flex;align-items:center;justify-content:center;padding:20px;opacity:0;pointer-events:none;transition:opacity .4s ease}
  #lightbox.open{opacity:1;pointer-events:auto}
  .lb-inner{max-width:660px;width:100%;background:var(--near);border:1px solid rgba(196,162,74,.15);overflow:hidden;transform:scale(0.97);transition:transform .4s ease}
  #lightbox.open .lb-inner{transform:scale(1)}
  .lb-inner img{width:100%;max-height:62vh;object-fit:cover;display:block}
  .lb-body{padding:22px 26px}
  .lb-meta{font-family:'Space Mono',monospace;font-size:8px;color:var(--gold);letter-spacing:.28em;margin-bottom:10px;display:block}
  .lb-caption{font-style:italic;font-size:19px;color:var(--bright);line-height:1.55}
  .lb-close{display:block;width:100%;padding:13px;background:rgba(196,162,74,.02);border:none;border-top:1px solid rgba(196,162,74,.1);color:var(--dim);font-family:'Space Mono',monospace;font-size:9px;letter-spacing:.32em;cursor:pointer;text-transform:uppercase;transition:all .3s ease}
  .lb-close:hover{background:rgba(196,162,74,.08);color:var(--gold)}

  /* INITIAL ENTRANCE FADE */
  @keyframes fadeUp{from{opacity:0;transform:translateY(14px)}to{opacity:1;transform:translateY(0)}}
  .header,.section,.grid-wrap{animation:fadeUp .8s cubic-bezier(0.25, 1, 0.5, 1) both}

  @media(max-width:600px){
    .header{padding:56px 20px 40px}
    .section{padding:40px 16px}
    .grid{grid-template-columns:repeat(2,1fr);gap:6px}
    .grid-wrap{padding:0 6px 60px}
  }
</style>
</head>
<body>

<div class="top-rule"></div>

<!-- HEADER -->
<div class="header">
  <span class="eyebrow">The Space · The Pieces · The Night</span>
  <h1 class="bebas main-title">HOUSE OF G$<br><span>AT HALCYON</span></h1>
  <p class="subtitle">Upstairs, where the racks glow under club lights and every piece has somewhere to be.</p>
</div>

<!-- DOWNLOADS -->
<div class="section">
  <span class="section-label">Press Assets</span>
  <div class="dl-list">
    <a class="dl-link" href="https://drive.google.com/file/d/1TaikUTr0R8ZHuiPVkiTy0m1J013Lb4Rg/view" target="_blank">
      <span class="dl-icon">📖</span>
      <div class="dl-text"><strong>2026 Lookbook</strong><em>Full collection, editorial photography</em></div>
      <span class="dl-arrow">↗</span>
    </a>
    <a class="dl-link" href="https://drive.google.com/file/d/1pMhoxjIGRVAyXpfIUGV5Dcs4kTzFQcC3/view" target="_blank">
      <span class="dl-icon">📁</span>
      <div class="dl-text"><strong>2026 Press Kit</strong><em>Brand story, product descriptions, hi-res assets</em></div>
      <span class="dl-arrow">↗</span>
    </a>
    <a class="dl-link" href="https://pem.sdy.mybluehost.me/wp-content/uploads/2026/01/A2SAG-PRESS-DECK-2023.pdf" target="_blank">
      <span class="dl-icon">🗃</span>
      <div class="dl-text"><strong>2023 Press Deck</strong><em>The archive — the brand before the brand</em></div>
      <span class="dl-arrow">↗</span>
    </a>
  </div>
</div>

<!-- FILTERS + GRID -->
<div class="section" style="padding-bottom:0">
  <span class="section-label">Browse by</span>
  <div class="filters">
    <button class="filter-btn active" data-filter="all">All</button>
    <button class="filter-btn" data-filter="space">The Space</button>
    <button class="filter-btn" data-filter="collection">Collection</button>
    <button class="filter-btn" data-filter="editorial">Editorial</button>
    <button class="filter-btn" data-filter="event">Events</button>
  </div>
</div>

<div class="grid-wrap">
  <div class="grid" id="grid">

    <div class="card" data-type="space"
      data-tag="The Sign" data-venue="Halcyon · Level Two · SF"
      data-caption="She set up the sign herself. 'UPSTAIRS. ATOUSA G. HOUSE OF G$. POP UP SHOP.' — and that was the entire marketing campaign."
      data-src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4953.webp?resize=700%2C900&ssl=1">
      <img src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4953.webp?resize=700%2C900&ssl=1" alt="The Sign" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"/>
      <div class="card-placeholder" style="display:none"><span class="card-tag">THE SIGN</span><span class="card-venue bebas">Halcyon · Level Two · SF</span></div>
      <div class="card-base"><span class="card-tag">The Sign</span><span class="card-venue">Halcyon · Level Two · SF</span></div>
      <div class="card-overlay"><span class="card-tag">The Sign</span><span class="card-venue">Halcyon · Level Two · SF</span><p class="card-caption">She set up the sign herself. The whole marketing campaign in one letter board.</p></div>
    </div>

    <div class="card" data-type="space"
      data-tag="The Racks" data-venue="House of G$ · Opening Night"
      data-caption="Sequins against black curtain. Neons against metallics. A whole archive moved from LA and hung under club lights."
      data-src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4945.jpg?resize=700%2C900&ssl=1">
      <img src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4945.jpg?resize=700%2C900&ssl=1" alt="The Racks" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"/>
      <div class="card-placeholder" style="display:none"><span class="card-tag">THE RACKS</span><span class="card-venue bebas">House of G$ · Opening Night</span></div>
      <div class="card-base"><span class="card-tag">The Racks</span><span class="card-venue">House of G$ · Opening Night</span></div>
      <div class="card-overlay"><span class="card-tag">The Racks</span><span class="card-venue">House of G$ · Opening Night</span><p class="card-caption">Sequins against black curtain. A whole archive moved from LA and hung under club lights.</p></div>
    </div>

    <div class="card" data-type="space"
      data-tag="The Lounge" data-venue="The Whole World · Upstairs"
      data-caption="Two racks. A geometric ottoman. LED strips on the floor. Mirror panels above reflecting everything back at you. This is where you come upstairs."
      data-src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/Screenshot-2026-01-19-at-9.05.51-PM.png?fit=700%2C900&ssl=1">
      <img src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/Screenshot-2026-01-19-at-9.05.51-PM.png?fit=700%2C900&ssl=1" alt="The Lounge" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"/>
      <div class="card-placeholder" style="display:none"><span class="card-tag">THE LOUNGE</span><span class="card-venue bebas">The Whole World · Upstairs</span></div>
      <div class="card-base"><span class="card-tag">The Lounge</span><span class="card-venue">The Whole World · Upstairs</span></div>
      <div class="card-overlay"><span class="card-tag">The Lounge</span><span class="card-venue">The Whole World · Upstairs</span><p class="card-caption">Two racks. A geometric ottoman. LED strips on the floor. Mirror panels above. This is where you come upstairs.</p></div>
    </div>

    <div class="card" data-type="collection"
      data-tag="The Hats" data-venue="Accessories · House of G$"
      data-caption="Looking down through the railing to the Halcyon floor below. Two worlds, one staircase, one building."
      data-src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_5008.jpg?fit=700%2C900&ssl=1">
      <img src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_5008.jpg?fit=700%2C900&ssl=1" alt="The Hats" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"/>
      <div class="card-placeholder" style="display:none"><span class="card-tag">THE HATS</span><span class="card-venue bebas">Accessories · House of G$</span></div>
      <div class="card-base"><span class="card-tag">The Hats</span><span class="card-venue">Accessories · House of G$</span></div>
      <div class="card-overlay"><span class="card-tag">The Hats</span><span class="card-venue">Accessories · House of G$</span><p class="card-caption">Looking down through the railing to the club floor below. Two worlds, one staircase.</p></div>
    </div>

    <div class="card" data-type="editorial"
      data-tag="The Piece" data-venue="A Line Called K · Statement Hat"
      data-caption="Gold chain fringe. Wide brim. Cascades over the face and hides nothing. One of those pieces that ends conversations and starts nights."
      data-src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4950.jpg?resize=700%2C900&ssl=1">
      <img src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4950.jpg?resize=700%2C900&ssl=1" alt="The Piece" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"/>
      <div class="card-placeholder" style="display:none"><span class="card-tag">THE PIECE</span><span class="card-venue bebas">A Line Called K · Statement Hat</span></div>
      <div class="card-base"><span class="card-tag">The Piece</span><span class="card-venue">A Line Called K · Statement Hat</span></div>
      <div class="card-overlay"><span class="card-tag">The Piece</span><span class="card-venue">A Line Called K · Statement Hat</span><p class="card-caption">Gold chain fringe. Cascades over the face and hides nothing. One of those pieces that ends conversations.</p></div>
    </div>

    <div class="card" data-type="event"
      data-tag="Downstairs" data-venue="Halcyon Main Floor · SF"
      data-caption="Laser beams through smoke haze. The HALCYON sign glowing blue-white. The world you come from — before you find the lounge upstairs."
      data-src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4956.jpg?resize=700%2C900&ssl=1">
      <img src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4956.jpg?resize=700%2C900&ssl=1" alt="Halcyon Floor" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"/>
      <div class="card-placeholder" style="display:none"><span class="card-tag">DOWNSTAIRS</span><span class="card-venue bebas">Halcyon Main Floor · SF</span></div>
      <div class="card-base"><span class="card-tag">Downstairs</span><span class="card-venue">Halcyon Main Floor · SF</span></div>
      <div class="card-overlay"><span class="card-tag">Downstairs</span><span class="card-venue">Halcyon Main Floor · SF</span><p class="card-caption">Laser beams through smoke. The world you come from before you find the lounge upstairs.</p></div>
    </div>

    <div class="card" data-type="editorial"
      data-tag="A2SA × Kastle" data-venue="Collaboration · Limited Capsule"
      data-caption="Two creative forces. One limited capsule. The crossover that felt inevitable once it happened."
      data-src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4955.jpg?resize=700%2C900&ssl=1">
      <img src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_4955.jpg?resize=700%2C900&ssl=1" alt="Collaboration" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"/>
      <div class="card-placeholder" style="display:none"><span class="card-tag">A2SA × KASTLE</span><span class="card-venue bebas">Collaboration · Limited Capsule</span></div>
      <div class="card-base"><span class="card-tag">A2SA × Kastle</span><span class="card-venue">Collaboration · Limited Capsule</span></div>
      <div class="card-overlay"><span class="card-tag">A2SA × Kastle</span><span class="card-venue">Collaboration · Limited Capsule</span><p class="card-caption">Two creative forces. One limited capsule. The crossover that felt inevitable.</p></div>
    </div>

    <div class="card" data-type="collection"
      data-tag="New Drop" data-venue="LA Archive → SF"
      data-caption="Straight from the LA archive. Limited. Sequins, metallics, movement. Meant for one woman each."
      data-src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_8286-scaled.jpeg?resize=700%2C900&ssl=1">
      <img src="https://i0.wp.com/pem.sdy.mybluehost.me/wp-content/uploads/2026/01/IMG_8286-scaled.jpeg?resize=700%2C900&ssl=1" alt="New Drop" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex'"/>
      <div class="card-placeholder" style="display:none"><span class="card-tag">NEW DROP</span><span class="card-venue bebas">LA Archive → SF</span></div>
      <div class="card-base"><span class="card-tag">New Drop</span><span class="card-venue">LA Archive → SF</span></div>
      <div class="card-overlay"><span class="card-tag">New Drop</span><span class="card-venue">LA Archive → SF</span><p class="card-caption">Straight from the LA archive. Limited. Meant for one woman each.</p></div>
    </div>

  </div>
</div>

<!-- HIGH-END DISCO BRAND STRIP -->
<div class="venues-container">
  <div class="venues-brand-header">
    <h2>ATOUSA G</h2>
    <div class="venues-brand-sub">House of G$ · A Line Called K</div>
  </div>
  
  <div class="venues-grid">
    <span class="venue-tag">Halcyon · SF</span>
    <span class="venue-tag">Do Not Sit On The Furniture · Miami</span>
    <span class="venue-tag">Great Northern · SF</span>
    <span class="venue-tag">Monarch · SF</span>
    <span class="venue-tag">BPM Festival</span>
    <span class="venue-tag">Sunset Campout</span>
    <span class="venue-tag">SXM Festival</span>
    <span class="venue-tag">Symbiosis</span>
  </div>
</div>

<!-- PREMIUM FOOTER -->
<div class="premium-footer">
  <span class="footer-eyebrow">Inquiries &amp; Bookings</span>
  <p class="footer-headline">Press collaborations, styling requests &amp; archive access.</p>
  <a href="mailto:press@atousag.com" class="footer-btn">Contact Representative</a>
</div>
<div class="bottom-rule"></div>

<!-- LIGHTBOX WINDOW OVERLAY -->
<div id="lightbox">
  <div class="lb-inner">
    <img id="lb-img" src="" alt=""/>
    <div class="lb-body">
      <span class="lb-meta" id="lb-meta"></span>
      <p class="lb-caption" id="lb-caption"></p>
    </div>
    <button class="lb-close" onclick="closeLightbox()">Close ✕</button>
  </div>
</div>

<script>
  // SMOOTH GRID CATEGORY FILTERS
  document.querySelectorAll('.filter-btn').forEach(btn => {
    btn.addEventListener('click', () => {
      document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
      btn.classList.add('active');
      const f = btn.dataset.filter;
      
      document.querySelectorAll('.card').forEach(card => {
        if (f === 'all' || card.dataset.type === f) {
          card.classList.remove('hidden');
        } else {
          card.classList.add('hidden');
        }
      });
    });
  });

  // LIGHTBOX POPUP FUNCTIONALITY
  document.querySelectorAll('.card').forEach(card => {
    card.addEventListener('click', () => {
      if (card.classList.contains('hidden')) return;
      
      const lb = document.getElementById('lightbox');
      document.getElementById('lb-img').src = card.dataset.src;
      document.getElementById('lb-meta').textContent = card.dataset.tag + ' · ' + card.dataset.venue;
      document.getElementById('lb-caption').textContent = '"' + card.dataset.caption + '"';
      lb.classList.add('open');
      document.body.style.overflow = 'hidden';
    });
  });

  function closeLightbox() {
    document.getElementById('lightbox').classList.remove('open');
    document.body.style.overflow = '';
  }
  document.getElementById('lightbox').addEventListener('click', function(e) {
    if (e.target === this) closeLightbox();
  });
  document.addEventListener('keydown', e => { if (e.key === 'Escape') closeLightbox(); });
</script>
</body>
</html>
