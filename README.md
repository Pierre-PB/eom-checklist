<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>YESSS UK — End of Month Checklist</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #dce2ef;
    --bg2: #f0f3fa;
    --bg3: #cdd4e6;
    --border: rgba(0,0,0,0.08);
    --text: #1a1d2e;
    --muted: #8892a4;
    --done-bg: rgba(0,0,0,0.02);

    --bank:    #38bdf8;
    --start:   #34d399;
    --salary:  #a78bfa;
    --sales:   #fb923c;
    --purchase:#fbbf24;
    --cars:    #4ade80;
    --various: #f472b6;
    --distrib: #f87171;
    --end:     #22d3ee;
    --yearend: #e879f9;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 14px;
    min-height: 100vh;
    padding-bottom: 60px;
  }

  /* ── HEADER ── */
  .header {
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(240,242,247,0.92);
    backdrop-filter: blur(16px);
    border-bottom: 1px solid var(--border);
    padding: 14px 24px;
    display: flex;
    align-items: center;
    gap: 20px;
    flex-wrap: wrap;
  }
  .header-title {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 18px;
    letter-spacing: -0.3px;
    white-space: nowrap;
  }
  .header-title span { color: #38bdf8; }

  .global-bar-wrap {
    flex: 1;
    min-width: 180px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .global-bar-bg {
    flex: 1;
    height: 6px;
    background: rgba(0,0,0,0.1);
    border-radius: 99px;
    overflow: hidden;
  }
  .global-bar-fill {
    height: 100%;
    background: linear-gradient(90deg, #38bdf8, #34d399);
    border-radius: 99px;
    transition: width 0.5s cubic-bezier(.4,0,.2,1);
  }
  .global-pct {
    font-family: 'Syne', sans-serif;
    font-size: 13px;
    font-weight: 700;
    color: #38bdf8;
    min-width: 36px;
    text-align: right;
  }

  .header-actions {
    display: flex;
    gap: 8px;
    align-items: center;
    flex-wrap: wrap;
  }

  /* ── CONTROLS ── */
  .controls {
    padding: 16px 24px 4px;
    display: flex;
    gap: 10px;
    align-items: center;
    flex-wrap: wrap;
  }
  .controls label {
    font-size: 11px;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: var(--muted);
    margin-right: 2px;
  }

  .chip {
    display: inline-flex;
    align-items: center;
    gap: 4px;
    padding: 4px 11px;
    border-radius: 99px;
    font-size: 12px;
    font-weight: 500;
    cursor: pointer;
    border: 1px solid var(--border);
    background: var(--bg2);
    color: var(--muted);
    transition: all 0.15s;
    user-select: none;
  }
  .chip:hover { border-color: rgba(255,255,255,0.2); color: var(--text); }
  .chip.active {
    background: rgba(56,189,248,0.15);
    border-color: rgba(56,189,248,0.4);
    color: #38bdf8;
  }
  .chip-dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: currentColor;
  }

  .btn {
    padding: 5px 12px;
    border-radius: 8px;
    border: 1px solid var(--border);
    background: var(--bg2);
    color: var(--muted);
    font-family: 'DM Sans', sans-serif;
    font-size: 12px;
    cursor: pointer;
    transition: all 0.15s;
  }
  .btn:hover { color: var(--text); border-color: rgba(255,255,255,0.2); }
  .btn.danger:hover { color: #f87171; border-color: rgba(248,113,113,0.4); }
  .btn.primary {
    background: rgba(56,189,248,0.12);
    border-color: rgba(56,189,248,0.3);
    color: #38bdf8;
  }
  .btn.primary:hover { background: rgba(56,189,248,0.2); }

  /* ── SYNC ── */
  .sync-bar {
    padding: 8px 24px;
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 12px;
    color: var(--muted);
    background: var(--bg);
    border-bottom: 1px solid var(--border);
  }
  .sync-dot {
    width: 7px; height: 7px;
    border-radius: 50%;
    background: var(--muted);
    transition: background 0.3s;
  }
  .sync-dot.ok { background: #34d399; }
  .sync-dot.err { background: #f87171; }
  .sync-input {
    flex: 1;
    max-width: 380px;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 4px 10px;
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 11px;
  }
  .sync-input:focus { outline: 1px solid rgba(56,189,248,0.4); }
  .sync-toggle { cursor: pointer; text-decoration: underline; }

  /* ── MAIN CONTENT ── */
  .content {
    padding: 20px 24px;
    max-width: 1200px;
  }

  /* ── SECTION ── */
  .section {
    margin-bottom: 24px;
    border-radius: 14px;
    border: 1px solid var(--border);
    background: var(--bg2);
    overflow: hidden;
    transition: opacity 0.2s;
  }
  .section.hidden { display: none; }

  .section-header {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 14px 18px;
    border-bottom: 1px solid var(--border);
    cursor: pointer;
    user-select: none;
  }
  .section-dot {
    width: 10px; height: 10px;
    border-radius: 50%;
    flex-shrink: 0;
  }
  .section-title {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 13px;
    letter-spacing: 0.5px;
    text-transform: uppercase;
  }
  .section-bar-wrap {
    flex: 1;
    height: 4px;
    background: rgba(0,0,0,0.08);
    border-radius: 99px;
    overflow: hidden;
  }
  .section-bar-fill {
    height: 100%;
    border-radius: 99px;
    transition: width 0.4s cubic-bezier(.4,0,.2,1);
  }
  .section-pct {
    font-family: 'Syne', sans-serif;
    font-size: 12px;
    font-weight: 700;
    min-width: 34px;
    text-align: right;
    opacity: 0.7;
  }
  .section-count {
    font-size: 11px;
    color: var(--muted);
    white-space: nowrap;
  }
  .section-chevron {
    font-size: 12px;
    color: var(--muted);
    transition: transform 0.2s;
  }
  .section.collapsed .section-chevron { transform: rotate(-90deg); }
  .section.collapsed .section-body { display: none; }

  /* ── TASK ITEM ── */
  .task-item {
    display: flex;
    align-items: flex-start;
    gap: 12px;
    padding: 10px 18px;
    border-bottom: 1px solid rgba(0,0,0,0.05);
    transition: background 0.15s;
    cursor: pointer;
  }
  .task-item:last-child { border-bottom: none; }
  .task-item:hover { background: rgba(0,0,0,0.025); }
  .task-item.done { background: var(--done-bg); }
  .task-item.filtered-out { display: none; }

  .checkbox {
    width: 18px; height: 18px;
    border-radius: 5px;
    border: 1.5px solid rgba(0,0,0,0.2);
    flex-shrink: 0;
    margin-top: 1px;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.2s;
    position: relative;
    overflow: hidden;
  }
  .checkbox::after {
    content: '✓';
    font-size: 11px;
    font-weight: 700;
    color: #ffffff;
    opacity: 0;
    transform: scale(0.5);
    transition: all 0.2s;
  }
  .task-item.done .checkbox {
    border-color: transparent;
    background: #34d399;
  }
  .task-item.done .checkbox::after {
    opacity: 1;
    transform: scale(1);
  }

  .task-text {
    flex: 1;
    line-height: 1.45;
    color: var(--text);
    transition: all 0.2s;
    font-size: 13px;
  }
  .task-item.done .task-text {
    color: #b0b8c8;
    text-decoration: line-through;
    text-decoration-color: rgba(0,0,0,0.15);
  }

  .task-people {
    display: flex;
    gap: 4px;
    flex-wrap: wrap;
    flex-shrink: 0;
  }
  .person-tag {
    font-size: 10px;
    font-weight: 500;
    padding: 2px 7px;
    border-radius: 99px;
    background: rgba(0,0,0,0.06);
    color: var(--muted);
    white-space: nowrap;
    transition: all 0.15s;
  }
  .person-tag.highlight {
    background: rgba(56,189,248,0.15);
    color: #38bdf8;
  }

  /* ── CONFETTI ── */
  .confetti-wrap {
    position: fixed;
    top: 0; left: 0;
    width: 100%; height: 100%;
    pointer-events: none;
    z-index: 999;
  }
  .confetti-piece {
    position: absolute;
    width: 8px; height: 8px;
    border-radius: 2px;
    animation: fall 2s ease-in forwards;
  }
  @keyframes fall {
    0% { transform: translateY(-20px) rotate(0deg); opacity: 1; }
    100% { transform: translateY(100vh) rotate(720deg); opacity: 0; }
  }

  /* ── SEARCH ── */
  .search-wrap {
    position: relative;
    flex: 1;
    min-width: 180px;
    max-width: 280px;
  }
  .search-input {
    width: 100%;
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 6px 10px 6px 30px;
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 13px;
  }
  .search-input:focus { outline: 1px solid rgba(56,189,248,0.4); }
  .search-input::placeholder { color: var(--muted); }
  .search-icon {
    position: absolute;
    left: 9px; top: 50%;
    transform: translateY(-50%);
    font-size: 13px;
    color: var(--muted);
    pointer-events: none;
  }

  /* ── EMPTY ── */
  .empty-state {
    padding: 40px;
    text-align: center;
    color: var(--muted);
    font-size: 13px;
  }

  /* ── TOOLTIP / SECTION ALL DONE ── */
  .section-done-badge {
    font-size: 10px;
    padding: 2px 8px;
    border-radius: 99px;
    background: rgba(52,211,153,0.15);
    color: #34d399;
    font-weight: 600;
    letter-spacing: 0.5px;
  }

  /* ── MONTH SELECTOR ── */
  .month-badge {
    font-family: 'Syne', sans-serif;
    font-size: 12px;
    color: var(--muted);
    padding: 4px 10px;
    border: 1px solid var(--border);
    border-radius: 8px;
    background: var(--bg2);
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 600px) {
    .controls { padding: 12px 14px 4px; }
    .content { padding: 14px; }
    .header { padding: 12px 14px; gap: 12px; }
    .task-text { font-size: 12px; }
  }
</style>
</head>
<body>

<!-- CONFETTI CONTAINER -->
<div class="confetti-wrap" id="confettiWrap"></div>

<!-- HEADER -->
<div class="header">
  <div class="header-title">YESSS <span>UK</span> — End of Month</div>
  <div class="global-bar-wrap">
    <div class="global-bar-bg">
      <div class="global-bar-fill" id="globalBarFill" style="width:0%"></div>
    </div>
    <div class="global-pct" id="globalPct">0%</div>
  </div>
  <div class="header-actions">
    <select id="monthSelect" class="month-badge" onchange="changeMonth()" style="cursor:pointer"></select>
    <button class="btn primary" onclick="syncNow()">⟳ Sync</button>
    <button class="btn danger" onclick="resetMonth()">↺ Reset</button>
  </div>
</div>

<!-- SYNC BAR -->
<div class="sync-bar">
  <div class="sync-dot" id="syncDot"></div>
  <span id="syncStatus">Local (npoint.io non configuré)</span>
  &nbsp;·&nbsp;
  <span class="sync-toggle" onclick="toggleSyncConfig()">Configurer le partage ▾</span>
  <div id="syncConfigBox" style="display:none;display:flex;gap:8px;align-items:center;flex:1">
    &nbsp;
    <input class="sync-input" id="npointUrl" placeholder="https://api.npoint.io/VOTRE_ID  (collez l'URL npoint.io ici)" />
    <button class="btn primary" onclick="saveNpointUrl()">Sauver</button>
  </div>
</div>

<!-- CONTROLS -->
<div class="controls">
  <label>Personne :</label>
  <div class="chip active" data-person="ALL" onclick="filterPerson(this)">Tous</div>
  <div class="chip" data-person="PIERRE" onclick="filterPerson(this)"><span class="chip-dot" style="color:#38bdf8"></span>Pierre</div>
  <div class="chip" data-person="CEDRIC" onclick="filterPerson(this)"><span class="chip-dot" style="color:#a78bfa"></span>Cédric</div>
  <div class="chip" data-person="LIAM" onclick="filterPerson(this)"><span class="chip-dot" style="color:#fb923c"></span>Liam</div>
  <div class="chip" data-person="LOURDES" onclick="filterPerson(this)"><span class="chip-dot" style="color:#f472b6"></span>Lourdes</div>
  <div class="chip" data-person="MAHER" onclick="filterPerson(this)"><span class="chip-dot" style="color:#fbbf24"></span>Maher</div>
  <div class="chip" data-person="ABDUL" onclick="filterPerson(this)"><span class="chip-dot" style="color:#34d399"></span>Abdul</div>
  <div class="chip" data-person="EQUIPE" onclick="filterPerson(this)"><span class="chip-dot" style="color:#22d3ee"></span>Équipes</div>

  &nbsp;
  <div class="search-wrap">
    <span class="search-icon">🔍</span>
    <input class="search-input" id="searchInput" placeholder="Rechercher une tâche..." oninput="applySearch()" />
  </div>

  <div class="chip" id="showDoneChip" onclick="toggleShowDone()" style="margin-left:auto">
    ☑ Masquer faites
  </div>
</div>

<!-- MAIN CONTENT -->
<div class="content" id="mainContent"></div>

<script>
// ══════════════════════════════════════
// DATA
// ══════════════════════════════════════
const SECTIONS = [
  {
    id: 'bank', label: 'Bank', color: '#38bdf8',
    tasks: [
      { id: 'b1', text: 'Provisional sales (3rd working day) — envoyer Octopus & Vivo Sales à Johnathan dès la fin de saisie des ventes', people: ['PIERRE','CEDRIC'] },
      { id: 'b2', text: 'Edition / validation Rapprochements Bancaires (year end : écritures datées de Mai à transférer sur le HO)', people: ['EQUIPE SOUMAYA'] },
      { id: 'b3', text: 'Vérifier solde du 41300001 + saisie des discounts charges', people: ['LIAM','CEDRIC'] },
      { id: 'b4', text: 'Saisie des intérêts HSBC liés au prêt HSBC Guernsey + intérêts RBS loan rollover sur HSBC 919 (Saisie de la tréso du mois)', people: ['LOURDES','CEDRIC'] },
    ]
  },
  {
    id: 'start', label: 'Start', color: '#34d399',
    tasks: [
      { id: 's1', text: "Vérifier l'initialisation des STATISTIQUES (+ INIMONTH) + initialisation des tables BAS", people: ['PIERRE','CEDRIC'] },
      { id: 's2', text: 'Annuler automatiquement les provisions M-1 BAS Jal 36 et lettrage des comptes de tiers des provisions', people: ['PIERRE','CEDRIC'] },
      { id: 's3', text: 'Ecritures du Journal 39', people: ['PIERRE','CEDRIC'] },
      { id: 's4', text: 'Faire les écritures jals 31/39 des factures reçues sur le mois pour les renewal leases 62260000/62262000/63512000', people: ['CEDRIC'] },
    ]
  },
  {
    id: 'salary', label: 'Salaires', color: '#a78bfa',
    tasks: [
      { id: 'sal1', text: 'Provision AXA', people: ['PIERRE','CEDRIC'] },
      { id: 'sal2', text: 'NIC on benefit in kind (Car & insurance)', people: ['PIERRE','CEDRIC'] },
      { id: 'sal3', text: 'Amnack recharge for payroll services Nov19 onwards — info in manual postings energy file 333.33', people: ['LIAM'] },
      { id: 'sal4', text: 'TIMESHEET envoyé par Lewis Holden pour répartition salaire (Busitrade, Zahn, YESSS France)', people: ['CEDRIC'] },
      { id: 'sal5', text: 'Vérif des effectifs', people: ['PIERRE','CEDRIC'] },
    ]
  },
  {
    id: 'sales', label: 'Sales', color: '#fb923c',
    tasks: [
      { id: 'sa1', text: 'Sales & balance re-allocation OCTOPUS (800/4100888) & VIVO USVF + réaffectation des balances des mois précédents', people: ['PIERRE','CEDRIC'] },
      { id: 'sa2', text: "Net GP Variation from YS — OCTOPUS GP : utiliser l'import table avec le tableau de Dan Haines", people: ['PIERRE'] },
      { id: 'sa3', text: 'Refacturation des ventes du National Account — à partir du 5ème WORKING DAYS (+ entité 810 à checker)', people: ['EQUIPE KATR ENNADA'] },
      { id: 'sa4', text: "Transfert de la balance du National Account sur les agences — à partir du 5ème WORKING DAYS (year end : écriture sur HO pour 4180000 & 41801000) + entité 810", people: ['PIERRE','CEDRIC'] },
      { id: 'sa5', text: "NAT ACCOUNTS Cash Sales adjustment (AE's files)", people: ['PIERRE','CEDRIC'] },
      { id: 'sa6', text: 'Vérifier la ventilation des rebates du Nat. Account 800/70970000 = 800/70970800', people: ['EQUIPE MARIEM BEN ARFI'] },
      { id: 'sa7', text: 'Refacturation Discount on payment National Account : ventiler au prorata des ventes Nat.Acc par agence (après finalisation des ventes)', people: ['PIERRE','CEDRIC'] },
      { id: 'sa8', text: 'Customer Rebate reserves / VIP CARDS (dupliquer provision des mois précédents si facture pas reçue — supprimer les NIC car calculé au cumul)', people: ['PIERRE','LIAM'] },
      { id: 'sa9', text: 'Sortir les ventes du Nat. Acc. Across company : faire OD sur NA si 70970800 pas à 0 et vérifier la table 970970800 des agences', people: ['PIERRE','CEDRIC'] },
      { id: 'sa10', text: 'Vérifier que la distribution des ventes du National Accounts soit bien à 0 (70710000+70712000=70710800)', people: ['CEDRIC'] },
      { id: 'sa11', text: 'Validation fin de saisie des ventes — pour le calcul définitif des debtor days', people: ['PIERRE','CEDRIC'] },
      { id: 'sa12', text: 'Splitter les sales & balance de Christchurch / Lymington + ajustement double booking/booking credit', people: ['CEDRIC'] },
      { id: 'sa13', text: 'Calcul des rotations clients', people: ['PIERRE','CEDRIC'] },
      { id: 'sa14', text: 'Atradius : insured turnover declaration before the 20th of next month', people: ['CEDRIC'] },
    ]
  },
  {
    id: 'purchase', label: 'Purchases', color: '#fbbf24',
    tasks: [
      { id: 'p1', text: 'NDC Rebate Reserve — 80% of YE + EB Reserve BEFORE CO CHARGEBACK', people: ['LIAM'] },
      { id: 'p2', text: 'YDC Pink Page', people: ['LIAM'] },
      { id: 'p3', text: 'Supplier Rebate Reserve', people: ['PIERRE','LIAM'] },
      { id: 'p4', text: "Concur Credit Cards Reserve + table INFOS LINE (penser au dossier SPECIFICITIES) — télécharger le fichier V5 à partir du 5ème working day et prévenir Soumaya", people: ['LIAM','CEDRIC'] },
      { id: 'p5', text: "Tableau + écritures des DOUBLE BOOKING (attention aux transactions entre l'agence 6 et l'agence 93 — 5% GST entre SDS & Jersey branches)", people: ['EQUIPE MARWA MADANI'] },
      { id: 'p6', text: 'Tableau + écritures des INTERBRANCH TRANSACTION', people: ['EQUIPE MARWA MADANI'] },
      { id: 'p7', text: 'Purchase Reserve', people: ['PIERRE'] },
      { id: 'p8', text: '% support with report from BAS', people: ['PIERRE'] },
      { id: 'p9', text: 'Réintégrer Note de débit de 3 mois et plus', people: ['PIERRE'] },
      { id: 'p10', text: 'Debit Note League (EDNOT de BAS)', people: ['PIERRE'] },
      { id: 'p11', text: 'Calcul des rotations de stock', people: ['PIERRE','CEDRIC'] },
      { id: 'p12', text: 'Interbranch adjustment for consolidated invoices (e.g. CHARGED EV @ Sheffield East) — vérifier comptes client 31/4100741 - 82/4100301', people: ['PIERRE','CEDRIC'] },
    ]
  },
  {
    id: 'cars', label: 'Cars', color: '#4ade80',
    tasks: [
      { id: 'c1', text: 'Recharge for 3x mackies email in fleet folder 909 / 61530000', people: ['LIAM'] },
      { id: 'c2', text: 'Provision assurance véhicules', people: ['LIAM'] },
      { id: 'c3', text: 'Provision Excess Mileage (Various reserve folder)', people: ['LIAM'] },
      { id: 'c4', text: 'Mettre à jour les fuels cards (closed) avec les employés partis — contrôler les employés avec 2 cartes (sauf GMs & RMs)', people: ['CEDRIC'] },
      { id: 'c5', text: 'Vérif des véhicules (PAH file with BAS) + queries to check + refaire tourner le workforce calculation', people: ['CEDRIC'] },
      { id: 'c6', text: 'Regarder les nouveaux véhicules arrivés sur le mois et voir si une provision doit être faite si pas de facture reçue (+ nouveaux VANS)', people: ['CEDRIC'] },
      { id: 'c7', text: 'Vérifier les nouveaux véhicules dans le fichier de Paul avec les emails de commande (validation) des véhicules', people: ['CEDRIC'] },
      { id: 'c8', text: 'Réconciliation du compte 46861899', people: ['MAHER'] },
    ]
  },
  {
    id: 'various', label: 'Various', color: '#f472b6',
    tasks: [
      { id: 'v1', text: 'Recharge LMH Cyprus for smart software solutions (envoyer la liste à Mark & Eddie pour validation avant refacturation)', people: ['LIAM','CEDRIC'] },
      { id: 'v2', text: 'AIRTEL — print the invoice and send to Paul + Dean for approval', people: ['EQUIPE JIHEN ROMDHANI'] },
      { id: 'v3', text: 'JT JERSEY — print the invoice and send to Paul + Dean for approval', people: ['EQUIPE JIHEN ROMDHANI'] },
      { id: 'v4', text: 'Calcul des intérêts sur emprunt + écriture correspondante (Man4-Man5 pour IOM/JSY/SDS + IH2 YESSSA) — dupliquer saisie du 16888000/16888400/16888500', people: ['PIERRE','CEDRIC'] },
      { id: 'v5', text: 'DAISY Invoice', people: ['PIERRE'] },
      { id: 'v6', text: "Vérifier avec les comptes si toutes les immos ont bien été créées", people: ['PIERRE','CEDRIC'] },
      { id: 'v7', text: 'Depreciation postings', people: ['PIERRE','CEDRIC'] },
      { id: 'v8', text: 'Fixed assets Tab', people: ['PIERRE','CEDRIC'] },
      { id: 'v9', text: 'Interests on CAPEX NBV all companies', people: ['PIERRE','CEDRIC'] },
      { id: 'v10', text: 'Ecritures des CUT-OFF', people: ['PIERRE','LIAM','CEDRIC'] },
      { id: 'v11', text: 'European fees AB+CC+VP+HO Interests on bonus unpaid, 5%', people: ['PIERRE'] },
      { id: 'v12', text: 'Facture NT VOICE indépendant — Sur le site Web : Create Report: Department analysis', people: ['EQUIPE WADII'] },
      { id: 'v13', text: 'ICUK Invoices — https://control.icuk.net', people: ['EQUIPE WADII'] },
      { id: 'v14', text: 'H&S Maintenance cover Invoice (61550200)', people: ['PIERRE'] },
      { id: 'v15', text: 'LMH — file in reserve folder, update and send to alexandre ribeiro, 65110000 rsv managed by cutoff (after ndc sales finished)', people: ['LIAM'] },
      { id: 'v16', text: 'NDC back rent (909) £1170 (Arn>Build>Avg Rent) 31/56746 (until 2027) — rent review reserve no longer done', people: ['LIAM'] },
      { id: 'v17', text: 'Provision Clients douteux (Rentrer table pour le national account) — Year End passer en journal 31 — TO BE DONE FOR THE 10TH OF THE MONTH', people: ['ABDUL'] },
      { id: 'v18', text: 'Provision White book (1% sales)', people: ['LIAM'] },
      { id: 'v19', text: 'Specificities to check', people: ['PIERRE','LIAM','CEDRIC'] },
      { id: 'v20', text: 'Various reserves — initial', people: ['LIAM'] },
      { id: 'v21', text: "Vérifier la P&L avec les tables de l'agence 51 Airdrie et si besoin transférer les frais sur la 96", people: ['CEDRIC'] },
      { id: 'v22', text: 'YESSS Book 893 INCREASING £8k per month 62360000 from Apr 21 (£16.5k 31 reserved from 19/20)', people: ['LIAM'] },
    ]
  },
  {
    id: 'distrib', label: 'Distribution SH.DEPT + Regions + GMs', color: '#f87171',
    tasks: [
      { id: 'd1', text: 'Bloquer la période de saisie', people: ['PIERRE','LIAM','CEDRIC'] },
      { id: 'd2', text: 'Link Accounts to match', people: ['CEDRIC'] },
      { id: 'd3', text: 'To check that no charges on Divisions', people: ['PIERRE','CEDRIC'] },
      { id: 'd4', text: 'To check suspense account 47100000', people: ['PIERRE','CEDRIC'] },
      { id: 'd5', text: 'Ensure to post all tables before starting the distribution', people: ['PIERRE'] },
      { id: 'd6', text: "PA's costs to GMs+YDC", people: ['LIAM'] },
      { id: 'd7', text: 'IT chargeback to CEF(W) + Distribution on to HO', people: ['LIAM'] },
      { id: 'd8', text: 'Jordan Ashworth Northern Renewables 816 (without recharge → table 900999046)', people: ['CEDRIC'] },
      { id: 'd9', text: 'TO OFFSET 13/70880000 AGAINST 46865000 FOR GOLF DAY EVENT', people: ['PIERRE','CEDRIC'] },
      { id: 'd10', text: 'TO OFFSET 881/70880000 AGAINST 46864000 FOR TRADE DAY EVENT — YESSS EXPO MERCEDES BENZ WORLD 4TH JUNE 2026', people: ['PIERRE','CEDRIC'] },
      { id: 'd11', text: 'National accounts 800 — GP allocation file for distribution table (10th of the month)', people: ['CEDRIC'] },
      { id: 'd12', text: 'National Accounts new project 810 — GP allocation + TABLE pour les ventes & GP% de la stat 810', people: ['CEDRIC'] },
      { id: 'd13', text: 'Renseigner la tot du National Acc new project + HO specialists classeur 7104 (mode forçage pour Month & YTD)', people: ['CEDRIC'] },
      { id: 'd14', text: "National Accounts \"Month 13 on Specific Sales\" — vérifier les ventes & achats pour cohérence de la marge", people: ['CEDRIC'] },
      { id: 'd15', text: 'Shared Departments & Regions Distribution', people: ['PIERRE','CEDRIC'] },
      { id: 'd16', text: 'Dummies distribution (Year End credit on HO) — DUMMY N-1 à faire réalimenter par le service info', people: ['PIERRE','CEDRIC'] },
      { id: 'd17', text: 'Services communs partagés 50/50 entre 13/623 à contrôler', people: ['PIERRE','CEDRIC'] },
      { id: 'd18', text: "Voir Graham Wignall pour solde de la 678 NWR en fin d'année", people: ['PIERRE','LIAM','CEDRIC'] },
      { id: 'd19', text: 'Refacturation entre YESSS (A), YESSS (B), YESSS (GUERNSEY) & YESSS (IOM)', people: ['LOURDES'] },
      { id: 'd20', text: 'Recalculate regions and shared departments after all adjustments done — après le dernier calcul du 100', people: ['PIERRE','LIAM'] },
      { id: 'd21', text: 'Tables à ajuster sur HO — Region YESSS A HO (values from IOM & Guernsey) + Dummies offshores HO', people: ['PIERRE','CEDRIC'] },
      { id: 'd22', text: 'Refacturer les shd dpt pour les offshores (Alimenter la table des regions sur la 919 avant de lancer le programme)', people: ['PIERRE','CEDRIC'] },
      { id: 'd23', text: "Sortir les balances des Regions & Shared dpt pour vérifier qu'elles soient bien à 0", people: ['PIERRE','CEDRIC'] },
    ]
  },
  {
    id: 'end', label: 'End', color: '#22d3ee',
    tasks: [
      { id: 'e1', text: 'BONUS calculated — attention aux agences avec implant ainsi que Jersey (modifier le bonus si nécessaire Table BONUS ADJ) — MODIFIER LA VALEUR N-1 si nécessaire', people: ['PIERRE','LIAM','CEDRIC'] },
      { id: 'e2', text: 'Table Postings 999', people: ['PIERRE','LIAM','CEDRIC'] },
      { id: 'e3', text: "Lancer le calcul des éléments variables si les employés n'apparaissent pas sur les pages conso Agences", people: ['PIERRE','LIAM','CEDRIC'] },
      { id: 'e4', text: 'Workforce folder calculation — calculates sum of workforce/LTA/AN on consolidated sheets', people: ['PIERRE','LIAM','CEDRIC'] },
      { id: 'e5', text: 'Vérifier les comptes de refacturation (au bilan passer une écriture pour régulariser les centimes dans les comptes de vidage)', people: ['PIERRE','LIAM','CEDRIC'] },
      { id: 'e6', text: 'Vérifier bank interests sur feuille de stats (classeur 7105 + YDC avec HO)', people: ['PIERRE','LIAM','CEDRIC'] },
      { id: 'e7', text: 'Vérifier sur la stat YESSS UK HO que la ligne YESSS UK company payments & sht dpt distribution offshore soit à 0', people: ['PIERRE','LIAM','CEDRIC'] },
      { id: 'e8', text: "Vérifier qu'il n'y ait plus rien dans les brouillards de saisies", people: ['PIERRE','LIAM','CEDRIC'] },
      { id: 'e9', text: 'To check working days / TF calendar', people: ['PIERRE','LIAM','CEDRIC'] },
      { id: 'e10', text: 'Contrôle des balances avec les STATISTIQUES — RAPSTA', people: ['PIERRE','LIAM','CEDRIC'] },
      { id: 'e11', text: "Changer la période du menu Chargeback invoice une fois la fin de mois terminée", people: ['PIERRE','LIAM','CEDRIC'] },
      { id: 'e12', text: "Forfait YESSS S/LTAPP/BUNKER forfait en début d'année", people: ['LIAM'] },
      { id: 'e13', text: 'Facture LIFE COVER (1 fois par an)', people: ['LIAM','CEDRIC'] },
      { id: 'e14', text: 'Penser à facturer les comptes 40810200 & 41810200 (au long de l\'année — 5% déjà inclus)', people: ['PIERRE','LIAM','CEDRIC'] },
      { id: 'e15', text: 'Vérifier les comptes clients / fournisseurs interco', people: ['CEDRIC'] },
      { id: 'e16', text: 'Envoyer à Steve Kay la stat Luxworks 805 (attention à la nouvelle ligne total) + breakdown excel de la ligne sponsorship and other income', people: ['PIERRE','CEDRIC'] },
      { id: 'e17', text: 'En AVRIL : voir Claude pour RAZ tables (+ vérifier les tables des debt/stock interests — Claude doit faire une modif du programme RAZ pour Avril 2026)', people: ['PIERRE'] },
    ]
  },
  {
    id: 'yearend', label: 'Year End (spécifique)', color: '#e879f9',
    tasks: [
      { id: 'ye1', text: 'YDC sales chargeback across companies 70617001', people: ['PIERRE'] },
      { id: 'ye2', text: 'Customer receipts first 3 working days adjustment — to be done before bank reconciliation', people: ['LIAM','CEDRIC'] },
      { id: 'ye3', text: 'Year End : annuler les customer payments postés en Avril mais liés à Mai 4199… Year End Balance', people: ['LIAM','CEDRIC'] },
      { id: 'ye4', text: "Year End : TO CANCEL NATIONAL ACCOUNTS BALANCE TRANSFER VIA HO TO PUT BALANCE TO £0 BETWEEN 41800000 & 41801000", people: ['CEDRIC'] },
      { id: 'ye5', text: 'Ecritures des intérêts stock et clients à passer sur BRANCHES & HO', people: ['PIERRE','CEDRIC'] },
      { id: 'ye6', text: "Vérifier que les balances de la 705 et 710 soient bien à 0 sur YESSS A (quand plus de distribution sur Skipton bloquer l'entité 710)", people: ['PIERRE'] },
      { id: 'ye7', text: 'OCTOPUS adjustment £727.81 monthly adj table, to cancel at YE', people: ['PIERRE'] },
      { id: 'ye8', text: 'Chichester ELECISERVE stock interest adjustment', people: ['PIERRE'] },
      { id: 'ye9', text: '678 NW Renewables to recharge final result against 712', people: ['PIERRE'] },
      { id: 'ye10', text: 'Year End 2024-2027 : 909 / 2611 0000 charge to be split over 4 years', people: ['LIAM'] },
    ]
  }
];

// ══════════════════════════════════════
// STATE
// ══════════════════════════════════════
let state = {
  done: {},         // taskId -> true
  npointUrl: '',
  currentPerson: 'ALL',
  showDone: true,
  collapsed: {}
};

const STORAGE_KEY = 'yesss_eom_checklist_v2';

function loadState() {
  try {
    const saved = localStorage.getItem(STORAGE_KEY);
    if (saved) {
      const parsed = JSON.parse(saved);
      state = { ...state, ...parsed };
    }
  } catch(e) {}
  // Set npoint URL from storage
  const urlEl = document.getElementById('npointUrl');
  if (urlEl && state.npointUrl) urlEl.value = state.npointUrl;
}

function saveState() {
  try {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
  } catch(e) {}
}

// ══════════════════════════════════════
// MONTH SELECTOR
// ══════════════════════════════════════
const MONTHS_FR = ['Janvier','Février','Mars','Avril','Mai','Juin','Juillet','Août','Septembre','Octobre','Novembre','Décembre'];

function initMonthSelect() {
  const sel = document.getElementById('monthSelect');
  const now = new Date();
  // Generate last 3 months + next month
  for (let offset = -3; offset <= 1; offset++) {
    const d = new Date(now.getFullYear(), now.getMonth() + offset, 1);
    const opt = document.createElement('option');
    opt.value = d.getFullYear() + '-' + d.getMonth();
    opt.textContent = MONTHS_FR[d.getMonth()] + ' ' + d.getFullYear();
    // Default: previous month (the one being closed)
    if (offset === -1) opt.selected = true;
    sel.appendChild(opt);
  }
  // Restore saved selection
  if (state.selectedMonth) sel.value = state.selectedMonth;
}

function changeMonth() {
  const sel = document.getElementById('monthSelect');
  state.selectedMonth = sel.value;
  saveState();
}

function getMonthLabel() {
  const sel = document.getElementById('monthSelect');
  return sel ? sel.options[sel.selectedIndex]?.text || '' : '';
}

// ══════════════════════════════════════
// RENDER
// ══════════════════════════════════════
function render() {
  const container = document.getElementById('mainContent');
  container.innerHTML = '';

  SECTIONS.forEach(section => {
    const el = buildSection(section);
    container.appendChild(el);
  });

  updateGlobal();
  applyPersonFilter();
  applySearch();
}

function buildSection(section) {
  const total = section.tasks.length;
  const doneCount = section.tasks.filter(t => state.done[t.id]).length;
  const pct = total > 0 ? Math.round(doneCount / total * 100) : 0;

  const div = document.createElement('div');
  div.className = 'section' + (state.collapsed[section.id] ? ' collapsed' : '');
  div.id = 'section-' + section.id;

  // Header
  const header = document.createElement('div');
  header.className = 'section-header';
  header.innerHTML = `
    <div class="section-dot" style="background:${section.color}"></div>
    <div class="section-title" style="color:${section.color}">${section.label}</div>
    ${pct === 100 ? '<div class="section-done-badge">✓ DONE</div>' : ''}
    <div class="section-bar-wrap">
      <div class="section-bar-fill" style="width:${pct}%;background:${section.color}"></div>
    </div>
    <div class="section-pct" style="color:${section.color}">${pct}%</div>
    <div class="section-count">${doneCount}/${total}</div>
    <div class="section-chevron">▾</div>
  `;
  header.addEventListener('click', () => toggleSection(section.id));
  div.appendChild(header);

  // Body
  const body = document.createElement('div');
  body.className = 'section-body';
  body.id = 'body-' + section.id;

  section.tasks.forEach(task => {
    const item = buildTask(task, section.color);
    body.appendChild(item);
  });

  div.appendChild(body);
  return div;
}

function buildTask(task, color) {
  const isDone = !!state.done[task.id];
  const div = document.createElement('div');
  div.className = 'task-item' + (isDone ? ' done' : '');
  div.id = 'task-' + task.id;
  div.setAttribute('data-people', task.people.join(',').toUpperCase());

  const peopleHTML = task.people.map(p =>
    `<span class="person-tag" data-person="${p.toUpperCase()}">${p}</span>`
  ).join('');

  div.innerHTML = `
    <div class="checkbox"></div>
    <div class="task-text">${task.text}</div>
    <div class="task-people">${peopleHTML}</div>
  `;

  div.addEventListener('click', () => toggleTask(task.id));
  return div;
}

function toggleTask(taskId) {
  if (state.done[taskId]) {
    delete state.done[taskId];
  } else {
    state.done[taskId] = true;
    // Check if section complete
    checkSectionComplete(taskId);
  }

  // Update task element
  const el = document.getElementById('task-' + taskId);
  if (el) {
    el.classList.toggle('done', !!state.done[taskId]);
  }

  // Rebuild section header
  const section = SECTIONS.find(s => s.tasks.some(t => t.id === taskId));
  if (section) refreshSectionHeader(section);

  updateGlobal();
  saveState();
  pushToNpoint();
}

function refreshSectionHeader(section) {
  const sectionEl = document.getElementById('section-' + section.id);
  if (!sectionEl) return;
  const total = section.tasks.length;
  const doneCount = section.tasks.filter(t => state.done[t.id]).length;
  const pct = total > 0 ? Math.round(doneCount / total * 100) : 0;

  const header = sectionEl.querySelector('.section-header');
  const fill = header.querySelector('.section-bar-fill');
  const pctEl = header.querySelector('.section-pct');
  const countEl = header.querySelector('.section-count');
  const badgeEl = header.querySelector('.section-done-badge');

  if (fill) fill.style.width = pct + '%';
  if (pctEl) pctEl.textContent = pct + '%';
  if (countEl) countEl.textContent = doneCount + '/' + total;
  if (pct === 100 && !badgeEl) {
    const badge = document.createElement('div');
    badge.className = 'section-done-badge';
    badge.textContent = '✓ DONE';
    header.querySelector('.section-title').after(badge);
  } else if (pct < 100 && badgeEl) {
    badgeEl.remove();
  }
}

function checkSectionComplete(taskId) {
  const section = SECTIONS.find(s => s.tasks.some(t => t.id === taskId));
  if (!section) return;
  const total = section.tasks.length;
  const doneCount = section.tasks.filter(t => state.done[t.id]).length;
  if (doneCount === total) {
    // Section complete — small confetti
    launchConfetti(30, section.color);
  }
}

function updateGlobal() {
  const totalTasks = SECTIONS.reduce((a, s) => a + s.tasks.length, 0);
  const doneTasks = SECTIONS.reduce((a, s) => a + s.tasks.filter(t => state.done[t.id]).length, 0);
  const pct = totalTasks > 0 ? Math.round(doneTasks / totalTasks * 100) : 0;

  document.getElementById('globalBarFill').style.width = pct + '%';
  document.getElementById('globalPct').textContent = pct + '%';
  // month label handled by select

  if (pct === 100) {
    setTimeout(() => launchConfetti(100, null), 100);
  }
}

function toggleSection(sectionId) {
  if (state.collapsed[sectionId]) {
    delete state.collapsed[sectionId];
  } else {
    state.collapsed[sectionId] = true;
  }
  const el = document.getElementById('section-' + sectionId);
  if (el) el.classList.toggle('collapsed', !!state.collapsed[sectionId]);
  saveState();
}

// ══════════════════════════════════════
// FILTERS
// ══════════════════════════════════════
let currentPerson = 'ALL';
let showDone = true;
let searchQuery = '';

function filterPerson(chipEl) {
  document.querySelectorAll('.chip[data-person]').forEach(c => c.classList.remove('active'));
  chipEl.classList.add('active');
  currentPerson = chipEl.getAttribute('data-person');
  applyPersonFilter();
}

function applyPersonFilter() {
  document.querySelectorAll('.task-item').forEach(el => {
    const people = (el.getAttribute('data-people') || '').toUpperCase();
    let visible = true;
    if (currentPerson !== 'ALL') {
      if (currentPerson === 'EQUIPE') {
        visible = people.includes('EQUIPE');
      } else {
        visible = people.split(',').includes(currentPerson);
      }
    }
    if (!showDone && el.classList.contains('done')) visible = false;
    el.classList.toggle('filtered-out', !visible || (searchQuery && !el.querySelector('.task-text').textContent.toLowerCase().includes(searchQuery)));

    // Highlight person tags
    el.querySelectorAll('.person-tag').forEach(tag => {
      const tp = (tag.getAttribute('data-person') || '').toUpperCase();
      tag.classList.toggle('highlight',
        currentPerson !== 'ALL' && (
          currentPerson === 'EQUIPE' ? tp.includes('EQUIPE') : tp === currentPerson
        )
      );
    });
  });

  // Hide sections with no visible tasks
  SECTIONS.forEach(s => {
    const sEl = document.getElementById('section-' + s.id);
    if (!sEl) return;
    const body = document.getElementById('body-' + s.id);
    if (!body) return;
    const visibleTasks = [...body.querySelectorAll('.task-item')].filter(t => !t.classList.contains('filtered-out'));
    sEl.classList.toggle('hidden', visibleTasks.length === 0);
  });
}

function applySearch() {
  searchQuery = document.getElementById('searchInput').value.toLowerCase().trim();
  applyPersonFilter();
}

function toggleShowDone() {
  showDone = !showDone;
  const chip = document.getElementById('showDoneChip');
  chip.classList.toggle('active', !showDone);
  chip.textContent = showDone ? '☑ Masquer faites' : '☑ Afficher faites';
  applyPersonFilter();
}

// ══════════════════════════════════════
// RESET
// ══════════════════════════════════════
function resetMonth() {
  if (!confirm('Réinitialiser toutes les tâches pour le nouveau mois ?')) return;
  state.done = {};
  state.collapsed = {};
  saveState();
  render();
  pushToNpoint();
}

// ══════════════════════════════════════
// CONFETTI
// ══════════════════════════════════════
function launchConfetti(count, baseColor) {
  const container = document.getElementById('confettiWrap');
  const colors = baseColor
    ? [baseColor, '#fff', baseColor + 'aa']
    : ['#38bdf8','#34d399','#a78bfa','#fb923c','#fbbf24','#f472b6','#f87171','#22d3ee'];

  for (let i = 0; i < count; i++) {
    const piece = document.createElement('div');
    piece.className = 'confetti-piece';
    piece.style.left = Math.random() * 100 + 'vw';
    piece.style.top = '-10px';
    piece.style.background = colors[Math.floor(Math.random() * colors.length)];
    piece.style.animationDuration = (1.2 + Math.random() * 1.2) + 's';
    piece.style.animationDelay = Math.random() * 0.5 + 's';
    piece.style.transform = `rotate(${Math.random()*360}deg)`;
    piece.style.width = piece.style.height = (5 + Math.random() * 8) + 'px';
    if (Math.random() > 0.5) piece.style.borderRadius = '50%';
    container.appendChild(piece);
    setTimeout(() => piece.remove(), 3000);
  }
}

// ══════════════════════════════════════
// NPOINT.IO SYNC
// ══════════════════════════════════════
let syncInterval = null;

function toggleSyncConfig() {
  const box = document.getElementById('syncConfigBox');
  box.style.display = box.style.display === 'none' ? 'flex' : 'none';
}

function saveNpointUrl() {
  const url = document.getElementById('npointUrl').value.trim();
  state.npointUrl = url;
  saveState();
  if (url) {
    startSync();
    syncNow();
  }
  document.getElementById('syncConfigBox').style.display = 'none';
}

function startSync() {
  if (syncInterval) clearInterval(syncInterval);
  if (!state.npointUrl) return;
  syncInterval = setInterval(pullFromNpoint, 30000);
  pullFromNpoint();
}

async function syncNow() {
  await pushToNpoint();
  await pullFromNpoint();
}

async function pushToNpoint() {
  if (!state.npointUrl) return;
  try {
    const res = await fetch(state.npointUrl, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ done: state.done, ts: Date.now() })
    });
    if (res.ok) setSyncStatus('ok', 'Sync OK — ' + new Date().toLocaleTimeString('fr-FR'));
    else setSyncStatus('err', 'Erreur sync');
  } catch(e) {
    setSyncStatus('err', 'Hors ligne');
  }
}

async function pullFromNpoint() {
  if (!state.npointUrl) return;
  try {
    const res = await fetch(state.npointUrl + '?t=' + Date.now());
    if (!res.ok) throw new Error();
    const data = await res.json();
    if (data && data.done) {
      const remoteDone = data.done;
      // Merge: union of local + remote
      let changed = false;
      for (const id of Object.keys(remoteDone)) {
        if (!state.done[id]) { state.done[id] = true; changed = true; }
      }
      if (changed) {
        saveState();
        // Soft update (refresh checkboxes + bars)
        softRefresh();
      }
    }
    setSyncStatus('ok', 'Sync OK — ' + new Date().toLocaleTimeString('fr-FR'));
  } catch(e) {
    setSyncStatus('err', 'Erreur connexion');
  }
}

function setSyncStatus(status, msg) {
  const dot = document.getElementById('syncDot');
  const txt = document.getElementById('syncStatus');
  dot.className = 'sync-dot ' + status;
  txt.textContent = msg;
}

function softRefresh() {
  SECTIONS.forEach(section => {
    section.tasks.forEach(task => {
      const el = document.getElementById('task-' + task.id);
      if (el) el.classList.toggle('done', !!state.done[task.id]);
    });
    refreshSectionHeader(section);
  });
  updateGlobal();
  applyPersonFilter();
}

// ══════════════════════════════════════
// INIT
// ══════════════════════════════════════
loadState();
initMonthSelect();
render();
if (state.npointUrl) startSync();
setSyncStatus('', state.npointUrl ? 'npoint.io configuré' : 'Local — configurez npoint.io pour le partage multi-utilisateurs');
</script>
</body>
</html>
