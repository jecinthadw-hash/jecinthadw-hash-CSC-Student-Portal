
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>EduFlow · COS 101</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=DM+Sans:wght@300;400;500;600&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
:root {
  --cream: #f5f0e8;
  --cream-dark: #ede5d5;
  --ink: #1a1208;
  --ink-mid: #3d3020;
  --ink-light: #6b5e48;
  --accent: #c8492a;
  --accent-warm: #e07b3a;
  --gold: #d4a017;
  --teal: #1a6b6b;
  --teal-light: #e4f0ef;
  --card-bg: #fefcf8;
  --border: rgba(26,18,8,0.1);
  --shadow: 0 4px 32px rgba(26,18,8,0.08);
}

* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  font-family: 'DM Sans', sans-serif;
  background: var(--cream);
  color: var(--ink);
  min-height: 100vh;
  overflow-x: hidden;
}

body::before {
  content: '';
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
  pointer-events: none;
  z-index: 9999;
  opacity: 0.6;
}

/* ── NAVIGATION ── */
nav {
  position: sticky;
  top: 0;
  z-index: 100;
  background: rgba(245,240,232,0.92);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--border);
  padding: 0 48px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 64px;
  animation: slideDown 0.5s ease both;
}

@keyframes slideDown { from { transform: translateY(-100%); opacity: 0; } to { transform: translateY(0); opacity: 1; } }

.nav-brand {
  display: flex;
  align-items: baseline;
  gap: 6px;
}
.nav-brand .logo {
  font-family: 'Playfair Display', serif;
  font-weight: 900;
  font-size: 1.5rem;
  color: var(--ink);
  letter-spacing: -0.5px;
}
.nav-brand .logo span { color: var(--accent); }
.nav-brand .course-tag {
  font-family: 'DM Mono', monospace;
  font-size: 0.7rem;
  background: var(--ink);
  color: var(--cream);
  padding: 3px 8px;
  border-radius: 4px;
  letter-spacing: 1px;
  margin-left: 4px;
}

.nav-items {
  display: flex;
  align-items: center;
  gap: 4px;
}
.nav-items a {
  font-size: 0.85rem;
  font-weight: 500;
  color: var(--ink-light);
  text-decoration: none;
  padding: 6px 14px;
  border-radius: 6px;
  transition: all 0.15s;
}
.nav-items a:hover { background: var(--cream-dark); color: var(--ink); }
.nav-items a.active {
  background: var(--ink);
  color: var(--cream);
}

/* ── HERO ── */
.hero {
  padding: 80px 48px 60px;
  max-width: 1280px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 380px;
  gap: 80px;
  align-items: center;
  animation: fadeUp 0.7s 0.1s ease both;
}

@keyframes fadeUp { from { opacity: 0; transform: translateY(24px); } to { opacity: 1; transform: translateY(0); } }

.hero-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-family: 'DM Mono', monospace;
  font-size: 0.72rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--accent);
  background: rgba(200,73,42,0.08);
  padding: 6px 14px;
  border-radius: 4px;
  margin-bottom: 24px;
}
.hero-eyebrow::before { content: ''; width: 6px; height: 6px; background: var(--accent); border-radius: 50%; animation: pulse 2s infinite; }
@keyframes pulse { 0%,100% { opacity: 1; transform: scale(1); } 50% { opacity: 0.5; transform: scale(0.8); } }

.hero h1 {
  font-family: 'Playfair Display', serif;
  font-size: clamp(3rem, 5vw, 4.8rem);
  font-weight: 900;
  line-height: 1.05;
  letter-spacing: -1.5px;
  color: var(--ink);
  margin-bottom: 20px;
}
.hero h1 em { font-style: italic; color: var(--accent); }

.hero-subtitle {
  font-size: 1.05rem;
  color: var(--ink-light);
  line-height: 1.7;
  max-width: 480px;
  margin-bottom: 36px;
  font-weight: 300;
}

.hero-stats {
  display: flex;
  gap: 32px;
  padding-top: 32px;
  border-top: 1px solid var(--border);
}
.hstat { display: flex; flex-direction: column; gap: 2px; }
.hstat-num {
  font-family: 'Playfair Display', serif;
  font-size: 2.4rem;
  font-weight: 900;
  color: var(--ink);
  line-height: 1;
}
.hstat-lbl { font-size: 0.78rem; color: var(--ink-light); text-transform: uppercase; letter-spacing: 1px; }

.hero-visual {
  background: var(--ink);
  border-radius: 24px;
  padding: 40px;
  color: var(--cream);
  position: relative;
  overflow: hidden;
}
.hero-visual::before {
  content: '';
  position: absolute;
  top: -60px; right: -60px;
  width: 200px; height: 200px;
  background: var(--accent);
  border-radius: 50%;
  opacity: 0.15;
}
.hero-visual::after {
  content: '';
  position: absolute;
  bottom: -40px; left: -40px;
  width: 140px; height: 140px;
  background: var(--gold);
  border-radius: 50%;
  opacity: 0.1;
}
.visual-label {
  font-family: 'DM Mono', monospace;
  font-size: 0.65rem;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: rgba(245,240,232,0.4);
  margin-bottom: 12px;
}
.visual-time {
  font-family: 'Playfair Display', serif;
  font-size: 3.5rem;
  font-weight: 900;
  color: var(--cream);
  line-height: 1;
  margin-bottom: 6px;
}
.visual-day { font-size: 1rem; color: rgba(245,240,232,0.6); margin-bottom: 32px; }

.visual-next {
  background: rgba(245,240,232,0.06);
  border: 1px solid rgba(245,240,232,0.1);
  border-radius: 12px;
  padding: 16px 20px;
  margin-bottom: 12px;
  position: relative;
  z-index: 1;
}
.visual-next-label { font-size: 0.72rem; color: rgba(245,240,232,0.4); margin-bottom: 4px; text-transform: uppercase; letter-spacing: 1px; }
.visual-next-title { font-weight: 600; font-size: 0.95rem; }
.visual-next-time { font-size: 0.8rem; color: var(--accent-warm); margin-top: 3px; }

.semester-pill {
  display: inline-block;
  background: var(--accent);
  color: white;
  font-size: 0.75rem;
  font-weight: 600;
  padding: 5px 12px;
  border-radius: 20px;
  position: relative;
  z-index: 1;
  margin-top: 8px;
}

/* ── MAIN LAYOUT ── */
.wrapper {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 48px 80px;
  display: grid;
  grid-template-columns: 1fr 360px;
  gap: 32px;
}

/* left column stacks cards vertically */
.left-col {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

/* right column stacks cards vertically */
.right-col {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

/* ── CARDS ── */
.card {
  background: var(--card-bg);
  border: 1px solid var(--border);
  border-radius: 20px;
  overflow: hidden;
  box-shadow: var(--shadow);
}

.card-header {
  padding: 28px 32px 20px;
  border-bottom: 1px solid var(--border);
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.card-title {
  display: flex;
  align-items: center;
  gap: 12px;
}
.card-icon {
  width: 36px; height: 36px;
  background: var(--ink);
  border-radius: 10px;
  display: grid;
  place-items: center;
  font-size: 1.1rem;
  flex-shrink: 0;
}
.card-title h2 {
  font-family: 'Playfair Display', serif;
  font-size: 1.4rem;
  font-weight: 700;
  color: var(--ink);
}
.card-badge {
  font-family: 'DM Mono', monospace;
  font-size: 0.72rem;
  background: var(--accent);
  color: white;
  padding: 4px 12px;
  border-radius: 20px;
  letter-spacing: 0.5px;
}
.card-badge.teal { background: var(--teal); }
.card-badge.gold { background: var(--gold); color: var(--ink); }

/* ── ANNOUNCEMENTS ── */
.announcements-body { padding: 24px 32px; display: flex; flex-direction: column; gap: 16px; }

.ann-item {
  display: flex;
  gap: 18px;
  padding: 20px;
  border-radius: 14px;
  background: var(--cream);
  border: 1px solid var(--border);
  transition: all 0.2s;
  animation: fadeUp 0.5s ease both;
}
.ann-item:nth-child(1) { animation-delay: 0.15s; }
.ann-item:nth-child(2) { animation-delay: 0.2s; }
.ann-item:nth-child(3) { animation-delay: 0.25s; }
.ann-item.pinned {
  background: rgba(200,73,42,0.04);
  border-color: rgba(200,73,42,0.2);
}
.ann-item:hover { transform: translateX(4px); box-shadow: 4px 8px 24px rgba(26,18,8,0.07); }

.ann-avatar {
  width: 48px; height: 48px;
  background: var(--ink);
  border-radius: 12px;
  display: grid; place-items: center;
  font-weight: 700; color: var(--cream);
  font-size: 1rem;
  flex-shrink: 0;
  font-family: 'Playfair Display', serif;
}
.ann-avatar.red { background: var(--accent); }
.ann-avatar.teal { background: var(--teal); }
.ann-avatar.gold { background: var(--gold); color: var(--ink); }

.ann-body { flex: 1; }
.ann-top { display: flex; align-items: flex-start; justify-content: space-between; margin-bottom: 6px; gap: 12px; }
.ann-title-row { display: flex; align-items: center; gap: 8px; flex-wrap: wrap; }
.ann-title { font-weight: 600; font-size: 1rem; color: var(--ink); }
.ann-pin {
  font-family: 'DM Mono', monospace;
  font-size: 0.62rem; letter-spacing: 1px; text-transform: uppercase;
  background: var(--accent); color: white;
  padding: 2px 8px; border-radius: 20px;
}
.ann-date { font-family: 'DM Mono', monospace; font-size: 0.72rem; color: var(--ink-light); flex-shrink: 0; }
.ann-text { font-size: 0.9rem; color: var(--ink-mid); line-height: 1.65; margin-bottom: 10px; }
.ann-meta { display: flex; gap: 12px; flex-wrap: wrap; }
.ann-tag {
  font-size: 0.78rem; color: var(--ink-light);
  background: var(--cream-dark);
  padding: 3px 10px; border-radius: 20px;
}

/* ── COURSE SCHEDULE ── */
.courses-body { padding: 24px 32px; display: flex; flex-direction: column; gap: 12px; }

.course-card {
  display: grid;
  grid-template-columns: auto 1fr auto;
  align-items: center;
  gap: 20px;
  padding: 18px 22px;
  border-radius: 14px;
  border: 1px solid var(--border);
  background: var(--cream);
  transition: all 0.2s;
  animation: fadeUp 0.5s ease both;
  text-decoration: none;
  color: inherit;
}
.course-card:hover { background: var(--card-bg); transform: translateY(-2px); box-shadow: 0 8px 32px rgba(26,18,8,0.1); }

.course-stripe {
  width: 5px;
  height: 52px;
  border-radius: 3px;
  flex-shrink: 0;
}

.course-code {
  font-family: 'Playfair Display', serif;
  font-weight: 700;
  font-size: 1.2rem;
  color: var(--ink);
  margin-bottom: 2px;
}
.course-name { font-size: 0.82rem; color: var(--ink-light); }

.course-right { text-align: right; }
.course-days-wrap { display: flex; gap: 4px; margin-bottom: 4px; justify-content: flex-end; }
.course-day {
  font-family: 'DM Mono', monospace;
  font-size: 0.65rem;
  font-weight: 500;
  background: var(--ink);
  color: var(--cream);
  padding: 2px 8px;
  border-radius: 4px;
  letter-spacing: 0.5px;
}
.course-time {
  font-family: 'DM Mono', monospace;
  font-size: 0.78rem;
  color: var(--ink-light);
  margin-bottom: 3px;
}
.course-venue { font-size: 0.75rem; color: var(--ink-light); }

/* ── CLASS REPS ── */
.reps-body { padding: 24px 28px; display: flex; flex-direction: column; gap: 14px; }

.rep-card {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 16px 18px;
  background: var(--cream);
  border: 1px solid var(--border);
  border-radius: 14px;
  transition: all 0.2s;
}
.rep-card:hover { background: var(--card-bg); box-shadow: 0 6px 24px rgba(26,18,8,0.08); transform: translateX(3px); }

.rep-avatar {
  width: 58px; height: 58px;
  border-radius: 14px;
  background: var(--ink);
  display: grid; place-items: center;
  font-family: 'Playfair Display', serif;
  font-weight: 700; font-size: 1.4rem;
  color: var(--cream);
  flex-shrink: 0;
  overflow: hidden;
}
.rep-avatar.female { background: var(--teal); }
.rep-name { font-weight: 600; font-size: 0.95rem; color: var(--ink); margin-bottom: 4px; }
.rep-role {
  font-family: 'DM Mono', monospace;
  font-size: 0.68rem;
  letter-spacing: 0.5px;
  color: var(--accent);
  text-transform: uppercase;
  margin-bottom: 3px;
}
.rep-reg {
  font-family: 'DM Mono', monospace;
  font-size: 0.72rem;
  color: var(--ink-light);
  background: var(--cream-dark);
  display: inline-block;
  padding: 2px 8px;
  border-radius: 4px;
}

/* ── UPCOMING EVENTS ── */
.events-body { padding: 20px 28px; }

.event-row {
  display: flex;
  gap: 16px;
  align-items: flex-start;
  padding: 16px 0;
  border-bottom: 1px solid var(--border);
}
.event-row:last-child { border-bottom: none; }

.event-cal {
  background: var(--ink);
  color: var(--cream);
  min-width: 56px;
  height: 56px;
  border-radius: 12px;
  display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  flex-shrink: 0;
}
.event-cal .eday { font-family: 'Playfair Display', serif; font-size: 1.6rem; font-weight: 900; line-height: 1; }
.event-cal .emon { font-size: 0.65rem; text-transform: uppercase; letter-spacing: 1px; opacity: 0.6; }

.event-title { font-weight: 600; font-size: 0.92rem; color: var(--ink); margin-bottom: 4px; }
.event-desc { font-size: 0.8rem; color: var(--ink-light); line-height: 1.5; }
.event-chip {
  display: inline-block; margin-top: 5px;
  font-size: 0.7rem; font-weight: 500;
  padding: 2px 8px; border-radius: 20px;
}
.event-chip.exam { background: rgba(200,73,42,0.1); color: var(--accent); }
.event-chip.test { background: rgba(212,160,23,0.15); color: #a07010; }
.event-chip.assign { background: var(--teal-light); color: var(--teal); }

/* ── QUICK STATS ── */
.stats-body { padding: 20px 28px; }
.stats-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
.stat-tile {
  background: var(--cream);
  border: 1px solid var(--border);
  border-radius: 14px;
  padding: 18px 16px;
  text-align: center;
  transition: 0.2s;
}
.stat-tile:hover { background: var(--ink); }
.stat-tile:hover .stnum, .stat-tile:hover .stlbl { color: var(--cream); }
.stnum {
  font-family: 'Playfair Display', serif;
  font-size: 2.2rem; font-weight: 900;
  color: var(--ink); line-height: 1;
  margin-bottom: 4px;
}
.stlbl { font-size: 0.75rem; color: var(--ink-light); text-transform: uppercase; letter-spacing: 0.5px; }

/* ── FOOTER ── */
footer {
  background: var(--ink);
  color: rgba(245,240,232,0.7);
  padding: 64px 48px 40px;
  position: relative;
  overflow: hidden;
}
footer::before {
  content: 'NASCO';
  position: absolute;
  bottom: -20px; right: 40px;
  font-family: 'Playfair Display', serif;
  font-size: 9rem;
  font-weight: 900;
  color: rgba(255,255,255,0.03);
  pointer-events: none;
  letter-spacing: -4px;
}

.footer-inner {
  max-width: 1280px; margin: 0 auto;
  display: grid; grid-template-columns: 2fr 1fr 1fr 1fr;
  gap: 48px; margin-bottom: 48px;
}

.footer-brand .logo {
  font-family: 'Playfair Display', serif;
  font-size: 1.8rem; font-weight: 900;
  color: var(--cream); margin-bottom: 12px;
}
.footer-brand .logo span { color: var(--accent); }
.footer-brand p { font-size: 0.88rem; line-height: 1.7; max-width: 260px; }

.footer-col h4 {
  font-size: 0.72rem; text-transform: uppercase; letter-spacing: 2px;
  color: rgba(245,240,232,0.4); margin-bottom: 16px; font-weight: 500;
}
.footer-col ul { list-style: none; display: flex; flex-direction: column; gap: 10px; }
.footer-col ul li a { color: rgba(245,240,232,0.6); text-decoration: none; font-size: 0.88rem; transition: 0.15s; }
.footer-col ul li a:hover { color: var(--cream); }

.footer-bottom {
  max-width: 1280px; margin: 0 auto;
  padding-top: 28px; border-top: 1px solid rgba(245,240,232,0.08);
  display: flex; align-items: center; justify-content: space-between; flex-wrap: wrap; gap: 12px;
}
.footer-bottom p { font-size: 0.8rem; color: rgba(245,240,232,0.3); }
.footer-pills { display: flex; gap: 8px; }
.footer-pill {
  font-family: 'DM Mono', monospace;
  font-size: 0.65rem; letter-spacing: 1px;
  background: rgba(245,240,232,0.06);
  color: rgba(245,240,232,0.4);
  padding: 4px 12px; border-radius: 20px; text-transform: uppercase;
}

/* ── RESPONSIVE ── */
@media (max-width: 1080px) {
  .hero { padding: 60px 32px 48px; gap: 48px; }
  .wrapper { padding: 0 32px 80px; gap: 24px; }
}

@media (max-width: 960px) {
  nav { padding: 0 24px; }
  .hero { grid-template-columns: 1fr; gap: 40px; padding: 48px 24px 40px; }
  .hero-visual { display: none; }
  .wrapper { grid-template-columns: 1fr; padding: 0 24px 60px; }
  .footer-inner { grid-template-columns: 1fr 1fr; }
  footer { padding: 48px 24px 32px; }
}

@media (max-width: 600px) {
  .nav-items { display: none; }
  .hero h1 { font-size: 2.6rem; }
  .footer-inner { grid-template-columns: 1fr; gap: 32px; }
}
</style>
</head>
<body>

<!-- TOAST CONTAINER -->
<div id="toast-container"></div>

<!-- NAV -->
<nav>
  <div class="nav-brand">
    <div class="logo">NASCO<span>.</span></div>
    <span class="course-tag">CSC 1/4</span>
  </div>
  <div class="nav-items">
    <a href="#home" class="active" data-section="home">Home</a>
NTENT — correct 2-column grid -->
<div class="wrapper">

  <!-- ── LEFT COLUMN ── -->
  <div class="left-col">

    <!-- COURSE SCHEDULE -->
    <div class="card" id="schedule" style="animation: fadeUp 0.6s 0.3s ease both;">
      <div class="card-header">
        <div class="card-title">
          <div class="card-icon">📚</div>
          <h2>Course Schedule</h2>
        </div>
        <span class="card-badge teal">7 courses</span>
      </div>

      <!-- DAY FILTER BAR -->
      <div class="filter-bar">
        <button class="filter-btn active" data-day="all">All</button>
        <button class="filter-btn" data-day="MON">Mon</button>
        <button class="filter-btn" data-day="TUE">Tue</button>
        <button class="filter-btn" data-day="WED">Wed</button>
        <button class="filter-btn" data-day="THU">Thu</button>
        <button class="filter-btn" data-day="FRI">Fri</button>
      </div>
      <div class="courses-body">

        <div class="course-card" data-days="MON THU">
          <div class="course-stripe" style="background:#3498db"></div>
          <div class="course-info">
            <div class="course-code">MTH 101</div>
            <div class="course-name">Mathematics I — Algebra & Calculus</div>
          </div>
          <div class="course-right">
            <div class="course-days-wrap"><span class="course-day">MON</span><span class="course-day">THU</span></div>
            <div class="course-time">10:00 – 12:00 PM</div>
            <div class="course-venue">📍 Room 204, Block B</div>
          </div>
        </div>

        <div class="course-card" data-days="TUE FRI">
          <div class="course-stripe" style="background:#e67e22"></div>
          <div c
