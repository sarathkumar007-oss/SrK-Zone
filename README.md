<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SK's Projects — Operations Command</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:wght@300;400;500;600&family=DM+Mono:wght@400;500&display=swap');

:root {
–red: #E8192C;
–gold: #D4A017;
–dark: #0D0D0D;
–surface: #141414;
–card: #1A1A1A;
–border: #2A2A2A;
–text: #F0F0F0;
–muted: #888;
–green: #00C896;
–blue: #2196F3;
–purple: #9C27B0;
–orange: #FF6B35;
}

- { margin: 0; padding: 0; box-sizing: border-box; }

body {
background: var(–dark);
color: var(–text);
font-family: ‘DM Sans’, sans-serif;
min-height: 100vh;
}

/* HEADER */
.header {
background: var(–surface);
border-bottom: 2px solid var(–red);
padding: 16px 32px;
display: flex;
align-items: center;
justify-content: space-between;
position: sticky;
top: 0;
z-index: 100;
}

.logo {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 28px;
letter-spacing: 3px;
color: var(–red);
}

.logo span { color: var(–gold); }

.header-meta {
font-family: ‘DM Mono’, monospace;
font-size: 12px;
color: var(–muted);
text-align: right;
}

/* NAV TABS */
.tabs {
display: flex;
background: var(–surface);
border-bottom: 1px solid var(–border);
padding: 0 32px;
gap: 4px;
}

.tab {
padding: 12px 20px;
font-size: 13px;
font-weight: 500;
letter-spacing: 1px;
text-transform: uppercase;
cursor: pointer;
color: var(–muted);
border-bottom: 2px solid transparent;
transition: all 0.2s;
}

.tab.active, .tab:hover {
color: var(–text);
border-bottom-color: var(–red);
}

.tab.active { color: var(–red); }

/* PANELS */
.panel { display: none; padding: 32px; }
.panel.active { display: block; }

/* STATS ROW */
.stats-row {
display: grid;
grid-template-columns: repeat(4, 1fr);
gap: 16px;
margin-bottom: 32px;
}

.stat-card {
background: var(–card);
border: 1px solid var(–border);
border-radius: 8px;
padding: 20px;
border-left: 3px solid var(–red);
}

.stat-label {
font-size: 11px;
letter-spacing: 2px;
text-transform: uppercase;
color: var(–muted);
margin-bottom: 8px;
}

.stat-value {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 36px;
color: var(–text);
line-height: 1;
}

.stat-sub { font-size: 12px; color: var(–muted); margin-top: 4px; }

/* CONTRACT MAP */
.contract-grid {
display: grid;
grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
gap: 20px;
}

.contract-card {
background: var(–card);
border: 1px solid var(–border);
border-radius: 10px;
overflow: hidden;
}

.contract-header {
padding: 14px 18px;
display: flex;
align-items: center;
justify-content: space-between;
border-bottom: 1px solid var(–border);
}

.contract-name {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 20px;
letter-spacing: 2px;
}

.contract-badge {
font-size: 11px;
font-family: ‘DM Mono’, monospace;
background: rgba(255,255,255,0.05);
padding: 3px 8px;
border-radius: 4px;
color: var(–muted);
}

.branch-list { padding: 8px 0; }

.branch-row {
display: grid;
grid-template-columns: 1fr 60px 60px 60px 60px;
align-items: center;
padding: 8px 18px;
border-bottom: 1px solid rgba(255,255,255,0.03);
transition: background 0.15s;
}

.branch-row:hover { background: rgba(255,255,255,0.03); }

.branch-row:last-child { border-bottom: none; }

.branch-name {
font-size: 13px;
font-weight: 500;
}

.shift-dot {
text-align: center;
font-family: ‘DM Mono’, monospace;
font-size: 12px;
}

.shift-header {
display: grid;
grid-template-columns: 1fr 60px 60px 60px 60px;
padding: 6px 18px;
font-size: 10px;
letter-spacing: 1px;
text-transform: uppercase;
color: var(–muted);
border-bottom: 1px solid var(–border);
}

.shift-header span { text-align: center; }

/* COLOR per contract */
.gymnation .contract-header { background: rgba(0, 200, 150, 0.08); border-left: 3px solid var(–green); }
.gymnation .contract-name { color: var(–green); }

.gulf-agency .contract-header { background: rgba(33, 150, 243, 0.08); border-left: 3px solid var(–blue); }
.gulf-agency .contract-name { color: var(–blue); }

.wellfit .contract-header { background: rgba(156, 39, 176, 0.08); border-left: 3px solid var(–purple); }
.wellfit .contract-name { color: var(–purple); }

.mercedes .contract-header { background: rgba(212, 160, 23, 0.08); border-left: 3px solid var(–gold); }
.mercedes .contract-name { color: var(–gold); }

.jafza-group .contract-header { background: rgba(232, 25, 44, 0.08); border-left: 3px solid var(–red); }
.jafza-group .contract-name { color: var(–red); }

.other .contract-header { background: rgba(255, 107, 53, 0.08); border-left: 3px solid var(–orange); }
.other .contract-name { color: var(–orange); }

/* CALENDAR */
.calendar-section { margin-bottom: 40px; }

.section-title {
font-family: ‘Bebas Neue’, sans-serif;
font-size: 22px;
letter-spacing: 3px;
color: var(–gold);
margin-bottom: 16px;
display: flex;
align-items: center;
gap: 12px;
}

.section-title::after {
content: ‘’;
flex: 1;
height: 1px;
background: var(–border);
}

.year-calendar {
display: grid;
grid-template-columns: repeat(4, 1fr);
gap: 16px;
}

.month-block {
background: var(–card);
border: 1px solid var(–border);
border-radius: 8px;
overflow: hidden;
}

.month-title {
background: var(–red);
color: white;
font-family: ‘Bebas Neue’, sans-serif;
font-size: 16px;
letter-spacing: 2px;
padding: 8px 14px;
display: flex;
justify-content: space-between;
align-items: center;
}

.month-grid {
padding: 10px;
display: grid;
grid-template-columns: repeat(7, 1fr);
gap: 2px;
}

.day-label {
text-align: center;
font-size: 9px;
font-weight: 600;
letter-spacing: 1px;
color: var(–muted);
padding: 3px 0;
}

.day-cell {
text-align: center;
font-size: 11px;
font-family: ‘DM Mono’, monospace;
padding: 4px 2px;
border-radius: 3px;
cursor: pointer;
position: relative;
color: var(–muted);
transition: all 0.15s;
}

.day-cell:hover { background: rgba(255,255,255,0.05); }

.day-cell.has-ppm { background: rgba(0,200,150,0.15); color: var(–green); font-weight: 600; }
.day-cell.has-deep { background: rgba(33,150,243,0.15); color: var(–blue); font-weight: 600; }
.day-cell.has-carpet { background: rgba(212,160,23,0.15); color: var(–gold); font-weight: 600; }
.day-cell.has-both { background: rgba(232,25,44,0.15); color: var(–red); font-weight: 600; }
.day-cell.today { outline: 1px solid var(–red); color: var(–text); }

.events-panel {
padding: 8px 10px 10px;
border-top: 1px solid var(–border);
min-height: 40px;
}

.event-tag {
font-size: 10px;
padding: 2px 6px;
border-radius: 3px;
margin-bottom: 3px;
display: flex;
align-items: center;
gap: 4px;
}

.event-tag.ppm { background: rgba(0,200,150,0.15); color: var(–green); }
.event-tag.deep { background: rgba(33,150,243,0.15); color: var(–blue); }
.event-tag.carpet { background: rgba(212,160,23,0.15); color: var(–gold); }

/* LEGEND */
.legend {
display: flex;
gap: 20px;
margin-bottom: 20px;
flex-wrap: wrap;
}

.legend-item {
display: flex;
align-items: center;
gap: 8px;
font-size: 12px;
color: var(–muted);
}

.legend-dot {
width: 12px;
height: 12px;
border-radius: 3px;
}

/* SCHEDULE TABLE */
.schedule-table {
width: 100%;
border-collapse: collapse;
font-size: 13px;
margin-bottom: 24px;
}

.schedule-table th {
background: var(–surface);
padding: 10px 14px;
text-align: left;
font-size: 10px;
letter-spacing: 1.5px;
text-transform: uppercase;
color: var(–muted);
border-bottom: 1px solid var(–border);
}

.schedule-table td {
padding: 10px 14px;
border-bottom: 1px solid rgba(255,255,255,0.03);
vertical-align: middle;
}

.schedule-table tr:hover td { background: rgba(255,255,255,0.02); }

.freq-badge {
display: inline-block;
padding: 2px 8px;
border-radius: 4px;
font-size: 11px;
font-family: ‘DM Mono’, monospace;
}

.freq-monthly { background: rgba(0,200,150,0.15); color: var(–green); }
.freq-quarterly { background: rgba(33,150,243,0.15); color: var(–blue); }
.freq-biannual { background: rgba(156,39,176,0.15); color: var(–purple); }
.freq-annual { background: rgba(212,160,23,0.15); color: var(–gold); }
.freq-weekly { background: rgba(232,25,44,0.15); color: var(–red); }

.dot { width: 8px; height: 8px; border-radius: 50%; display: inline-block; margin-right: 6px; }
.dot-green { background: var(–green); }
.dot-blue { background: var(–blue); }
.dot-gold { background: var(–gold); }
.dot-red { background: var(–red); }
.dot-purple { background: var(–purple); }
.dot-orange { background: var(–orange); }

/* Responsive */
@media (max-width: 900px) {
.stats-row { grid-template-columns: repeat(2, 1fr); }
.year-calendar { grid-template-columns: repeat(2, 1fr); }
}

@media (max-width: 600px) {
.panel { padding: 16px; }
.stats-row { grid-template-columns: 1fr 1fr; }
.year-calendar { grid-template-columns: 1fr; }
}

.tooltip {
position: absolute;
bottom: 100%;
left: 50%;
transform: translateX(-50%);
background: #222;
border: 1px solid var(–border);
padding: 6px 10px;
border-radius: 4px;
font-size: 11px;
white-space: nowrap;
z-index: 200;
display: none;
pointer-events: none;
}

.day-cell:hover .tooltip { display: block; }

</style>
</head>
<body>

<div class="header">
  <div class="logo">SK'S <span>PROJECTS</span></div>
  <div class="header-meta">
    Operations Command Center<br>
    2026 Full Year Dashboard
  </div>
</div>

<div class="tabs">
  <div class="tab active" onclick="showPanel('overview')">Overview</div>
  <div class="tab" onclick="showPanel('contracts')">Contracts & Branches</div>
  <div class="tab" onclick="showPanel('calendar')">Service Calendar</div>
  <div class="tab" onclick="showPanel('schedule')">PPM & Deep Clean</div>
</div>

<!-- OVERVIEW -->

<div class="panel active" id="panel-overview">
  <div class="stats-row">
    <div class="stat-card">
      <div class="stat-label">Total Contracts</div>
      <div class="stat-value">10</div>
      <div class="stat-sub">Active portfolios</div>
    </div>
    <div class="stat-card" style="border-left-color: var(--green)">
      <div class="stat-label">Total Branches</div>
      <div class="stat-value">39</div>
      <div class="stat-sub">Across UAE & GCC</div>
    </div>
    <div class="stat-card" style="border-left-color: var(--gold)">
      <div class="stat-label">Total Day Staff</div>
      <div class="stat-value">107</div>
      <div class="stat-sub">Headcount deployed</div>
    </div>
    <div class="stat-card" style="border-left-color: var(--blue)">
      <div class="stat-label">Night Coverage</div>
      <div class="stat-value">3</div>
      <div class="stat-sub">Branches with night shift</div>
    </div>
  </div>

  <div class="section-title">Contract Portfolio Map</div>

  <div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; margin-bottom: 32px;">
    <div style="background: var(--card); border: 1px solid var(--border); border-radius: 8px; padding: 20px; border-left: 3px solid var(--green);">
      <div style="font-family:'Bebas Neue',sans-serif;font-size:22px;color:var(--green);letter-spacing:2px;">GYMNATION</div>
      <div style="font-size:12px;color:var(--muted);margin:6px 0;">Fitness & Gym Operations</div>
      <div style="font-size:13px;">16 Branches — UAE + Abu Dhabi + Sharjah</div>
      <div style="margin-top:10px;font-size:12px;color:var(--muted);">Deep Clean: Monthly | Carpet: Quarterly</div>
    </div>
    <div style="background: var(--card); border: 1px solid var(--border); border-radius: 8px; padding: 20px; border-left: 3px solid var(--blue);">
      <div style="font-family:'Bebas Neue',sans-serif;font-size:22px;color:var(--blue);letter-spacing:2px;">GULF AGENCY</div>
      <div style="font-size:12px;color:var(--muted);margin:6px 0;">Logistics & Cargo Facilities</div>
      <div style="font-size:13px;">13 Branches — DIP, DWC, Cargo Village</div>
      <div style="margin-top:10px;font-size:12px;color:var(--muted);">PPM: Monthly | Deep Clean: Quarterly</div>
    </div>
    <div style="background: var(--card); border: 1px solid var(--border); border-radius: 8px; padding: 20px; border-left: 3px solid var(--purple);">
      <div style="font-family:'Bebas Neue',sans-serif;font-size:22px;color:var(--purple);letter-spacing:2px;">WELLFIT</div>
      <div style="font-size:12px;color:var(--muted);margin:6px 0;">Premium Fitness</div>
      <div style="font-size:13px;">2 Branches — Dubai Marina, Mirdif</div>
      <div style="margin-top:10px;font-size:12px;color:var(--muted);">Deep Clean: Monthly | Carpet: Quarterly</div>
    </div>
    <div style="background: var(--card); border: 1px solid var(--border); border-radius: 8px; padding: 20px; border-left: 3px solid var(--gold);">
      <div style="font-family:'Bebas Neue',sans-serif;font-size:22px;color:var(--gold);letter-spacing:2px;">MERCEDES BENZ</div>
      <div style="font-size:12px;color:var(--muted);margin:6px 0;">Automotive Corporate</div>
      <div style="font-size:13px;">2 Branches — JAFZA, IMPZ</div>
      <div style="margin-top:10px;font-size:12px;color:var(--muted);">PPM: Monthly | Deep Clean: Quarterly</div>
    </div>
    <div style="background: var(--card); border: 1px solid var(--border); border-radius: 8px; padding: 20px; border-left: 3px solid var(--red);">
      <div style="font-family:'Bebas Neue',sans-serif;font-size:22px;color:var(--red);letter-spacing:2px;">JAFZA CLUSTER</div>
      <div style="font-size:12px;color:var(--muted);margin:6px 0;">Casio · IDP · Hanwa · Midstar · Kotra</div>
      <div style="font-size:13px;">1 Location — Building 18/19</div>
      <div style="margin-top:10px;font-size:12px;color:var(--muted);">Shared Schedule</div>
    </div>
    <div style="background: var(--card); border: 1px solid var(--border); border-radius: 8px; padding: 20px; border-left: 3px solid var(--orange);">
      <div style="font-family:'Bebas Neue',sans-serif;font-size:22px;color:var(--orange);letter-spacing:2px;">OTHERS</div>
      <div style="font-size:12px;color:var(--muted);margin:6px 0;">Sick · Fike · Kemet · African & Eastern</div>
      <div style="font-size:13px;">4 Locations — JAFZA South, Sharjah, DIP2</div>
      <div style="margin-top:10px;font-size:12px;color:var(--muted);">Individual Schedules</div>
    </div>
  </div>

  <div class="section-title">Scheduling Rules</div>
  <div style="background: var(--card); border: 1px solid var(--border); border-radius: 8px; padding: 20px; display: grid; grid-template-columns: 1fr 1fr; gap: 12px; font-size: 13px; line-height: 1.7;">
    <div><span class="dot dot-green"></span><strong>GymNation:</strong> M-S (1–6) — 5 days/week all branches. No Sundays</div>
    <div><span class="dot dot-blue"></span><strong>Gulf Agency (CDC 1–5, DWC):</strong> Any cancelled monthly = bonus with DEDS weekends</div>
    <div><span class="dot dot-gold"></span><strong>Gulf Agency (CDC 1–5, Workshop, CFS, GIT):</strong> Fri only, 9:00AM–3:00PM</div>
    <div><span class="dot dot-red"></span><strong>JAFZA:</strong> 1–19 done, TUESDAYS YEAR END of month. Time: 3:00PM–7:00PM</div>
    <div><span class="dot dot-purple"></span><strong>Deep Cleaning:</strong> Months 24 = 2 days rolling including every 3rd month weekday</div>
    <div><span class="dot dot-orange"></span><strong>Deep Cleaning:</strong> Includes both 24-hr + 24-hr Mix equally for all locations</div>
  </div>
</div>

<!-- CONTRACTS -->

<div class="panel" id="panel-contracts">
  <div class="section-title">All Contracts & Branches</div>
  <div class="contract-grid" id="contract-grid"></div>
</div>

<!-- CALENDAR -->

<div class="panel" id="panel-calendar">
  <div class="legend">
    <div class="legend-item"><div class="legend-dot" style="background:var(--green)"></div>PPM Visit</div>
    <div class="legend-item"><div class="legend-dot" style="background:var(--blue)"></div>Deep Cleaning</div>
    <div class="legend-item"><div class="legend-dot" style="background:var(--gold)"></div>Carpet Shampooing</div>
    <div class="legend-item"><div class="legend-dot" style="background:var(--red)"></div>Multiple Events</div>
  </div>
  <div class="year-calendar" id="year-calendar"></div>
</div>

<!-- SCHEDULE -->

<div class="panel" id="panel-schedule">
  <div class="section-title">PPM & Cleaning Schedule — All Locations</div>
  <table class="schedule-table">
    <thead>
      <tr>
        <th>Contract</th>
        <th>Branch / Location</th>
        <th>PPM</th>
        <th>Deep Clean</th>
        <th>Carpet Shampoo</th>
        <th>Next Service</th>
      </tr>
    </thead>
    <tbody id="schedule-tbody"></tbody>
  </table>
</div>

<script>
const contracts = [
  { name: 'GymNation', cls: 'gymnation', branches: [
    { name: 'Mirdif', d:3, m:1, e:3, n:0 },
    { name: 'Silicon Oasis', d:3, m:0, e:3, n:0 },
    { name: 'Downtown', d:3, m:0, e:4, n:0 },
    { name: 'Al Quoz', d:3, m:0, e:3, n:1 },
    { name: 'Motorcity', d:4, m:0, e:4, n:1 },
    { name: 'Burdubai', d:3, m:1, e:3, n:0 },
    { name: 'Al Ain', d:3, m:1, e:3, n:0 },
    { name: 'Mushrif Mall', d:3, m:1, e:4, n:0 },
    { name: 'Boutique Mall', d:4, m:1, e:3, n:0 },
    { name: 'Khalidiya Mall', d:3, m:1, e:4, n:0 },
    { name: 'Al Zahia Mall', d:2, m:0, e:2, n:0 },
    { name: 'Al Zahia Mall (F)', d:2, m:0, e:2, n:0 },
    { name: 'Mega Mall', d:2, m:0, e:3, n:0 },
    { name: 'Mega Mall (F)', d:2, m:0, e:3, n:0 },
    { name: 'Central Mall', d:2, m:0, e:3, n:0 },
    { name: 'Central Mall (F)', d:2, m:0, e:3, n:0 },
  ], ppm: 'Monthly', deep: 'Monthly', carpet: 'Quarterly' },

  { name: 'Gulf Agency', cls: 'gulf-agency', branches: [
    { name: 'Main Office', d:3, m:0, e:2, n:0 },
    { name: 'DC New Facility', d:2, m:0, e:1, n:0 },
    { name: 'CDC 1', d:0.5, m:0, e:1.6, n:0 },
    { name: 'CDC 2', d:0.5, m:0, e:1.6, n:0 },
    { name: 'CDC 3', d:0.5, m:0, e:1.6, n:0 },
    { name: 'CDC 4', d:1, m:0, e:1, n:0 },
    { name: 'Workshop', d:0.5, m:0, e:1.6, n:0 },
    { name: 'Group IT', d:2, m:0, e:1.6, n:0 },
    { name: 'CDC 5', d:2, m:0, e:1, n:0 },
    { name: 'CFS', d:1, m:0, e:0, n:0 },
    { name: 'DWC', d:5, m:0, e:4, n:0 },
    { name: 'African Eastern DIP 1', d:3, m:0, e:0, n:0 },
    { name: 'Cargo Village / Port Rashid', d:1, m:0, e:0, n:0 },
  ], ppm: 'Monthly', deep: 'Quarterly', carpet: 'Bi-Annual' },

  { name: 'Wellfit', cls: 'wellfit', branches: [
    { name: 'Dubai Marina', d:11, m:0, e:4, n:0 },
    { name: 'Mirdif Sports Society', d:7, m:0, e:9, n:0 },
  ], ppm: 'Monthly', deep: 'Monthly', carpet: 'Quarterly' },

  { name: 'Mercedes Benz', cls: 'mercedes', branches: [
    { name: 'Main Office JAFZA', d:11, m:0, e:0, n:0 },
    { name: 'IMPZ', d:2, m:0, e:0, n:0 },
  ], ppm: 'Monthly', deep: 'Quarterly', carpet: 'Annual' },

  { name: 'JAFZA Cluster', cls: 'jafza-group', branches: [
    { name: 'Casio', d:0.5, m:0, e:0, n:0 },
    { name: 'IDP', d:0.5, m:0, e:0, n:0 },
    { name: 'Hanwa', d:0.33, m:0, e:0, n:0 },
    { name: 'Midstar', d:0.33, m:0, e:0, n:0 },
    { name: 'Kotra Korea', d:0.33, m:0, e:0, n:0 },
  ], ppm: 'Quarterly', deep: 'Quarterly', carpet: 'Annual' },

  { name: 'Others', cls: 'other', branches: [
    { name: 'Sick — JAFZA South', d:1, m:0, e:0, n:0 },
    { name: 'Fike — JAFZA South', d:1, m:0, e:0, n:0 },
    { name: 'Kemet Precious Metal — Sharjah', d:2, m:0, e:0, n:0 },
    { name: 'African & Eastern — DIP 2', d:1, m:0, e:0, n:0 },
  ], ppm: 'Monthly', deep: 'Quarterly', carpet: 'Quarterly' },
];

// Build Contracts Panel
const grid = document.getElementById('contract-grid');
contracts.forEach(c => {
  const totalDay = c.branches.reduce((s, b) => s + b.d, 0);
  const el = document.createElement('div');
  el.className = `contract-card ${c.cls}`;
  el.innerHTML = `
    <div class="contract-header">
      <div class="contract-name">${c.name}</div>
      <div class="contract-badge">${c.branches.length} branches · ${totalDay.toFixed(1)} day staff</div>
    </div>
    <div class="shift-header">
      <span>Branch</span><span>Day</span><span>Mid</span><span>Eve</span><span>Night</span>
    </div>
    <div class="branch-list">
      ${c.branches.map(b => `
        <div class="branch-row">
          <div class="branch-name">${b.name}</div>
          <div class="shift-dot">${b.d || '—'}</div>
          <div class="shift-dot">${b.m || '—'}</div>
          <div class="shift-dot">${b.e || '—'}</div>
          <div class="shift-dot">${b.n || '—'}</div>
        </div>
      `).join('')}
    </div>
  `;
  grid.appendChild(el);
});

// Schedule events 2026
const events2026 = {
  // Format: "YYYY-MM-DD": [{type, label}]
  // PPM events - monthly (first Tuesday of each month approx)
  "2026-01-06": [{type:'ppm', label:'GymNation PPM'}, {type:'deep', label:'GymNation Deep Clean'}],
  "2026-01-13": [{type:'ppm', label:'Gulf Agency PPM'}],
  "2026-01-20": [{type:'ppm', label:'Mercedes PPM'}],
  "2026-02-03": [{type:'ppm', label:'GymNation PPM'}, {type:'deep', label:'GymNation Deep Clean'}],
  "2026-02-10": [{type:'ppm', label:'Gulf Agency PPM'}],
  "2026-02-17": [{type:'ppm', label:'Mercedes PPM'}],
  "2026-02-24": [{type:'carpet', label:'Wellfit Carpet Shampoo'}],
  "2026-02-27": [{type:'deep', label:'GymNation DC — Al Ain, Mirdif'}],
  "2026-03-03": [{type:'ppm', label:'GymNation PPM'}, {type:'deep', label:'GymNation Deep Clean'}],
  "2026-03-10": [{type:'ppm', label:'Gulf Agency PPM'}],
  "2026-03-17": [{type:'ppm', label:'Mercedes PPM'}],
  "2026-03-20": [{type:'carpet', label:'GymNation Carpet Shampoo Q1'}],
  "2026-04-07": [{type:'ppm', label:'GymNation PPM'}, {type:'deep', label:'GymNation Deep Clean'}],
  "2026-04-14": [{type:'ppm', label:'Gulf Agency PPM'}],
  "2026-05-05": [{type:'ppm', label:'GymNation PPM'}],
  "2026-05-12": [{type:'ppm', label:'Gulf Agency PPM'}],
  "2026-05-19": [{type:'deep', label:'Gulf Agency Deep Clean Q2'}],
  "2026-06-02": [{type:'ppm', label:'GymNation PPM'}, {type:'deep', label:'GymNation Deep Clean'}],
  "2026-06-16": [{type:'ppm', label:'Gulf Agency PPM'}],
  "2026-06-20": [{type:'carpet', label:'GymNation Carpet Shampoo Q2'}, {type:'carpet', label:'Wellfit Carpet Q2'}],
  "2026-07-07": [{type:'ppm', label:'GymNation PPM'}],
  "2026-07-21": [{type:'ppm', label:'Gulf Agency PPM'}, {type:'deep', label:'Gulf Agency Deep Clean'}],
  "2026-08-04": [{type:'ppm', label:'GymNation PPM'}, {type:'deep', label:'GymNation Deep Clean'}],
  "2026-08-18": [{type:'ppm', label:'Mercedes PPM'}],
  "2026-09-01": [{type:'ppm', label:'GymNation PPM'}],
  "2026-09-15": [{type:'ppm', label:'Gulf Agency PPM'}, {type:'deep', label:'Gulf Agency Deep Clean Q3'}],
  "2026-09-19": [{type:'carpet', label:'GymNation Carpet Shampoo Q3'}, {type:'carpet', label:'Wellfit Carpet Q3'}],
  "2026-10-06": [{type:'ppm', label:'GymNation PPM'}, {type:'deep', label:'GymNation Deep Clean'}],
  "2026-10-20": [{type:'ppm', label:'Gulf Agency PPM'}],
  "2026-11-03": [{type:'ppm', label:'GymNation PPM'}],
  "2026-11-17": [{type:'ppm', label:'Gulf Agency PPM'}, {type:'deep', label:'Gulf Agency Deep Clean Q4'}],
  "2026-12-01": [{type:'ppm', label:'GymNation PPM'}, {type:'deep', label:'GymNation Deep Clean'}],
  "2026-12-15": [{type:'ppm', label:'Gulf Agency PPM'}],
  "2026-12-19": [{type:'carpet', label:'GymNation Carpet Shampoo Q4'}, {type:'carpet', label:'Wellfit Carpet Q4'}],
};

const months = ['January','February','March','April','May','June','July','August','September','October','November','December'];
const monthDays = [31,28,31,30,31,30,31,31,30,31,30,31];

function getDayClass(year, month, day) {
  const key = `${year}-${String(month+1).padStart(2,'0')}-${String(day).padStart(2,'0')}`;
  const evs = events2026[key];
  if (!evs) return '';
  const types = evs.map(e=>e.type);
  if (types.includes('ppm') && (types.includes('deep') || types.includes('carpet'))) return 'has-both';
  if (types.includes('ppm')) return 'has-ppm';
  if (types.includes('deep')) return 'has-deep';
  if (types.includes('carpet')) return 'has-carpet';
  return '';
}

const calContainer = document.getElementById('year-calendar');
const today = new Date();

months.forEach((month, mi) => {
  const firstDay = new Date(2026, mi, 1).getDay();
  const days = monthDays[mi];
  
  // Count events this month
  let monthEvents = 0;
  for(let d=1; d<=days; d++) {
    const key = `2026-${String(mi+1).padStart(2,'0')}-${String(d).padStart(2,'0')}`;
    if(events2026[key]) monthEvents += events2026[key].length;
  }

  const block = document.createElement('div');
  block.className = 'month-block';
  
  let gridHTML = '<div class="month-grid">';
  ['S','M','T','W','T','F','S'].forEach(d => {
    gridHTML += `<div class="day-label">${d}</div>`;
  });
  
  for(let i=0; i<firstDay; i++) gridHTML += '<div></div>';
  
  for(let d=1; d<=days; d++) {
    const key = `2026-${String(mi+1).padStart(2,'0')}-${String(d).padStart(2,'0')}`;
    const evs = events2026[key] || [];
    const cls = getDayClass(2026, mi, d);
    const isToday = today.getFullYear()===2026 && today.getMonth()===mi && today.getDate()===d;
    const tooltip = evs.map(e=>e.label).join(', ');
    gridHTML += `<div class="day-cell ${cls} ${isToday?'today':''}" title="${tooltip}">${d}${tooltip?`<div class="tooltip">${tooltip}</div>`:''}</div>`;
  }
  gridHTML += '</div>';

  // next event this month
  let eventsHtml = '<div class="events-panel">';
  let shown = 0;
  for(let d=1; d<=days && shown<3; d++) {
    const key = `2026-${String(mi+1).padStart(2,'0')}-${String(d).padStart(2,'0')}`;
    if(events2026[key]) {
      events2026[key].forEach(e => {
        if(shown < 3) {
          eventsHtml += `<div class="event-tag ${e.type}"><span style="font-size:9px">▸</span>${d} ${e.label}</div>`;
          shown++;
        }
      });
    }
  }
  if(shown === 0) eventsHtml += '<div style="font-size:11px;color:var(--muted);padding:2px 0">No scheduled events</div>';
  eventsHtml += '</div>';

  block.innerHTML = `
    <div class="month-title">
      <span>${month} 2026</span>
      <span style="font-size:12px;font-family:'DM Mono';font-weight:400">${monthEvents} tasks</span>
    </div>
    ${gridHTML}
    ${eventsHtml}
  `;
  calContainer.appendChild(block);
});

// Schedule Table
const tbody = document.getElementById('schedule-tbody');
const freqClass = { 'Monthly':'freq-monthly','Quarterly':'freq-quarterly','Bi-Annual':'freq-biannual','Annual':'freq-annual','Weekly':'freq-weekly' };

const nextDates = {
  'Monthly': 'Mar 3, 2026',
  'Quarterly': 'Jun 20, 2026',
  'Bi-Annual': 'Jun 15, 2026',
  'Annual': 'Dec 1, 2026',
};

contracts.forEach(c => {
  c.branches.forEach((b, i) => {
    const tr = document.createElement('tr');
    tr.innerHTML = `
      <td>${i===0 ? `<span class="dot dot-${c.cls==='gymnation'?'green':c.cls==='gulf-agency'?'blue':c.cls==='wellfit'?'purple':c.cls==='mercedes'?'gold':c.cls==='jafza-group'?'red':'orange'}"></span>${c.name}` : ''}</td>
      <td>${b.name}</td>
      <td><span class="freq-badge ${freqClass[c.ppm]}">${c.ppm}</span></td>
      <td><span class="freq-badge ${freqClass[c.deep]}">${c.deep}</span></td>
      <td><span class="freq-badge ${freqClass[c.carpet]}">${c.carpet}</span></td>
      <td style="font-family:'DM Mono';font-size:11px;color:var(--muted)">${nextDates[c.ppm]||'TBD'}</td>
    `;
    tbody.appendChild(tr);
  });
});

function showPanel(id) {
  document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  document.getElementById('panel-'+id).classList.add('active');
  event.target.classList.add('active');
}
</script>

</body>
</html>