<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Caisse APE - Fêtes & Événements</title>
  <style>
    /* Reset & Base Local Styles */
    *, ::before, ::after { box-sizing: border-box; margin: 0; padding: 0; }
    html, body { height: 100%; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif; background-color: #f1f5f9; color: #1e293b; user-select: none; }
    button, input, select { font: inherit; color: inherit; }
    button { cursor: pointer; border: none; background: none; }
    table { border-collapse: collapse; width: 100%; }

    /* Layout & Helpers */
    .flex { display: flex; }
    .flex-col { flex-direction: column; }
    .flex-1 { flex: 1 1 0%; }
    .items-center { align-items: center; }
    .items-baseline { align-items: baseline; }
    .justify-between { justify-content: space-between; }
    .justify-end { justify-content: flex-end; }
    .grid { display: grid; }
    .grid-cols-2 { grid-template-columns: repeat(2, minmax(0, 1fr)); }
    .grid-cols-3 { grid-template-columns: repeat(3, minmax(0, 1fr)); }
    .gap-1-5 { gap: 0.375rem; }
    .gap-2 { gap: 0.5rem; }
    .gap-3 { gap: 0.75rem; }
    .gap-4 { gap: 1rem; }
    .hidden { display: none !important; }
    .relative { position: relative; }
    .fixed { position: fixed; }
    .overflow-hidden { overflow: hidden; }
    .overflow-x-auto { overflow-x: auto; }
    .overflow-y-auto { overflow-y: auto; }
    .w-full { width: 100%; }
    .h-full { height: 100%; }
    .max-w-7xl { max-width: 80rem; margin-left: auto; margin-right: auto; }
    .p-2 { padding: 0.5rem; }
    .p-3 { padding: 0.75rem; }
    .p-4 { padding: 1rem; }
    .p-5 { padding: 1.25rem; }
    .p-6 { padding: 1.5rem; }
    .px-2 { padding-left: 0.5rem; padding-right: 0.5rem; }
    .px-3 { padding-left: 0.75rem; padding-right: 0.75rem; }
    .px-4 { padding-left: 1rem; padding-right: 1rem; }
    .py-1 { padding-top: 0.25rem; padding-bottom: 0.25rem; }
    .py-1-5 { padding-top: 0.375rem; padding-bottom: 0.375rem; }
    .py-2 { padding-top: 0.5rem; padding-bottom: 0.5rem; }
    .py-2-5 { padding-top: 0.625rem; padding-bottom: 0.625rem; }
    .py-3 { padding-top: 0.75rem; padding-bottom: 0.75rem; }

    /* UI Components */
    header { background-color: #4338ca; color: #ffffff; box-shadow: 0 4px 6px -1px rgba(0,0,0,0.1); }
    .nav-bg { background-color: rgba(49, 46, 129, 0.6); padding: 0.25rem; border-radius: 0.75rem; }
    .nav-btn { padding: 0.375rem 0.75rem; border-radius: 0.5rem; font-size: 0.75rem; font-weight: 600; color: #e0e7ff; }
    .nav-btn.active { background-color: #ffffff; color: #312e81; box-shadow: 0 1px 3px rgba(0,0,0,0.1); }
    
    .cat-btn { padding: 0.375rem 0.75rem; border-radius: 0.75rem; font-size: 0.75rem; font-weight: 700; background-color: #ffffff; color: #475569; border: 1px solid #cbd5e1; white-space: nowrap; }
    .cat-btn.active { background-color: #4f46e5; color: #ffffff; border-color: #4f46e5; }

    .card { background-color: #ffffff; border-radius: 1rem; border: 1px solid #e2e8f0; box-shadow: 0 1px 2px rgba(0,0,0,0.05); }
    .product-card { border-width: 2px; border-style: solid; border-radius: 1rem; padding: 0.75rem; height: 6rem; display: flex; flex-direction: column; justify-content: space-between; cursor: pointer; transition: all 0.15s; }
    .product-card:active { transform: scale(0.98); }
    .product-card.dragging { opacity: 0.4; transform: scale(0.95); }

    /* Color Themes for Products */
    .bg-amber-50 { background-color: #fffbeb; border-color: #fcd34d; color: #78350f; }
    .bg-sky-50 { background-color: #f0f9ff; border-color: #7dd3fc; color: #0c4a6e; }
    .bg-emerald-50 { background-color: #ecfdf5; border-color: #6ee7b7; color: #064e3b; }
    .bg-purple-50 { background-color: #faf5ff; border-color: #d8b4fe; color: #581c87; }
    .bg-rose-50 { background-color: #fff1f2; border-color: #fca5a5; color: #881337; }

    /* Buttons & Controls */
    .btn-emerald { background-color: #059669; color: #ffffff; font-weight: 800; border-radius: 0.75rem; text-align: center; }
    .btn-emerald:hover { background-color: #047857; }
    .btn-indigo { background-color: #4f46e5; color: #ffffff; font-weight: 700; border-radius: 0.75rem; }
    .btn-amber { background-color: #f59e0b; color: #0f172a; font-weight: 700; border-radius: 0.75rem; }
    .pay-btn { padding: 0.5rem; border-radius: 0.75rem; font-size: 0.75rem; font-weight: 700; border: 2px solid #e2e8f0; background-color: #ffffff; color: #475569; width: 100%; text-align: center; }
    .pay-btn.active { border-color: #4f46e5; background-color: #eef2ff; color: #4338ca; }

    /* PANIER TOUJOURS OUVERT ET VISIBLE */
    #cart-drawer { position: relative !important; width: 100% !important; border-radius: 1rem !important; display: flex !important; flex-direction: column !important; box-shadow: 0 1px 2px rgba(0,0,0,0.05) !important; }
    #cart-content { display: flex !important; flex: 1 !important; max-height: none !important; border-bottom-left-radius: 1rem; border-bottom-right-radius: 1rem; justify-content: space-between; }
    #cart-list { flex: 1 !important; max-height: 8rem !important; }

    /* Mode Paysage / Tablette : Panier à droite */
    @media (min-width: 600px), (orientation: landscape) {
      #tab-pos { flex-direction: row !important; }
      #pos-products-area { padding-bottom: 0.5rem !important; }
      #cart-drawer { width: 24rem !important; flex-shrink: 0; height: 100% !important; }
      #cart-content { max-height: none !important; }
      #cart-list { max-height: none !important; }
      #pos-grid { grid-template-columns: repeat(3, minmax(0, 1fr)) !important; }
    }
    @media (min-width: 1024px) {
      #pos-grid { grid-template-columns: repeat(4, minmax(0, 1fr)) !important; }
    }

    .no-print { display: block; }
  </style>
</head>
<body class="flex flex-col">

  <!-- Header Nav -->
  <header class="no-print">
    <div class="max-w-7xl p-3 flex justify-between items-center">
      <div class="flex items-center gap-2">
        <span style="font-size:1.5rem;">🏪</span>
        <div>
          <h1 style="font-size:1.125rem; font-weight:800; line-height:1.2;">Caisse APE</h1>
          <span style="font-size:0.65rem; color:#c7d2fe;">Association Parents</span>
        </div>
      </div>

      <nav class="flex nav-bg gap-1">
        <button id="nav-pos" onclick="switchTab('pos')" class="nav-btn active">🧮 Caisse</button>
        <button id="nav-catalog" onclick="switchTab('catalog')" class="nav-btn">📦 Catalogue</button>
        <button id="nav-stats" onclick="switchTab('stats')" class="nav-btn">📊 Session</button>
        <button id="nav-archives" onclick="switchTab('archives')" class="nav-btn">📁 Archives</button>
      </nav>
    </div>
  </header>

  <!-- Contenu Principal -->
  <main class="flex-1 max-w-7xl w-full p-2 overflow-hidden no-print">

    <!-- Onglet Caisse -->
    <section id="tab-pos" class="h-full flex flex-col relative overflow-hidden" style="gap:0.5rem;">
      
      <!-- Zone Articles -->
      <div class="card flex flex-col flex-1 overflow-hidden h-full">
        <div class="p-2 flex gap-1-5 overflow-x-auto items-center justify-between" style="background-color:#f8fafc; border-bottom:1px solid #f1f5f9;">
          <div class="flex gap-1-5">
            <button onclick="filterCategory('all')" class="cat-btn active">Tous</button>
            <button onclick="filterCategory('Restauration')" class="cat-btn">🍕 Restauration</button>
            <button onclick="filterCategory('Buvette')" class="cat-btn">🥤 Buvette</button>
            <button onclick="filterCategory('Tickets')" class="cat-btn">🎟 Tickets</button>
            <button onclick="filterCategory('Divers')" class="cat-btn">🎈 Divers</button>
          </div>
        </div>
        <div id="pos-products-area" class="flex-1 p-2 overflow-y-auto" style="padding-bottom: 2rem;">
          <div id="pos-grid" class="grid grid-cols-2 gap-2"></div>
        </div>
      </div>

      <!-- Panier -->
      <div id="cart-drawer" class="card">
        <div class="p-3 flex justify-between items-center" style="background-color:#1e293b; color:#ffffff; border-top-left-radius:1rem; border-top-right-radius:1rem;">
          <div class="flex items-center gap-2">
            <span>🛒</span>
            <h2 style="font-size:0.875rem; font-weight:700;">Commande</h2>
            <span id="mobile-badge" style="background-color:#4f46e5; color:#ffffff; font-size:0.65rem; font-weight:800; padding:0.1rem 0.4rem; border-radius:9999px;">0</span>
          </div>
          <div class="flex items-center gap-2">
            <button onclick="clearCart()" style="font-size:0.75rem; color:#fca5a5; background:rgba(153,27,27,0.4); padding:0.25rem 0.5rem; border-radius:0.25rem; font-weight:600;">Vider</button>
          </div>
        </div>

        <div id="cart-content" class="flex flex-col p-3" style="background-color:#f8fafc; gap:0.5rem;">
          <div id="cart-list" class="flex flex-col gap-1 overflow-y-auto" style="border-bottom:1px solid #e2e8f0; padding-bottom:0.5rem;"></div>
          
          <div class="flex justify-between items-baseline">
            <span style="font-weight:800; font-size:0.875rem;">TOTAL :</span>
            <span id="cart-total" style="font-size:1.5rem; font-weight:900; color:#4f46e5;">0.00 €</span>
          </div>

          <div class="grid grid-cols-3 gap-1-5">
            <button type="button" onclick="setPaymentMethod('Espèces')" id="pay-Espèces" class="pay-btn active">💵 Espèces</button>
            <button type="button" onclick="setPaymentMethod('CB')" id="pay-CB" class="pay-btn">💳 CB</button>
            <button type="button" onclick="setPaymentMethod('Chèque')" id="pay-Chèque" class="pay-btn">📝 Chèque</button>
          </div>

          <div id="cash-box" class="p-2" style="background-color:#fffbeb; border:1px solid #fde68a; border-radius:0.75rem; font-size:0.75rem;">
            <div class="flex justify-between items-center">
              <label style="font-weight:700; color:#78350f;">Reçu :</label>
              <input type="number" id="cash-given" step="0.5" placeholder="0.00" oninput="calculateChange()" style="width:5rem; text-align:right; font-weight:700; background:#fff; border:1px solid #fcd34d; border-radius:0.25rem; padding:0.1rem 0.25rem;">
            </div>
            <div class="flex justify-between items-center" style="font-weight:700; margin-top:0.25rem; padding-top:0.25rem; border-top:1px solid #fde68a;">
              <span>Monnaie :</span><span id="cash-change" style="font-size:0.875rem; color:#78350f;">0.00 €</span>
            </div>
          </div>

          <div class="flex justify-between items-center" style="font-size:0.75rem; color:#475569;">
            <span>Impression :</span>
            <select id="print-mode" style="background:#fff; border:1px solid #cbd5e1; border-radius:0.25rem; padding:0.25rem; font-size:0.75rem; font-weight:600;">
              <option value="global">1 Ticket Récap</option>
              <option value="coupons">Coupons indiv.</option>
              <option value="both">Récap + Coupons</option>
              <option value="none">Ne pas imprimer</option>
            </select>
          </div>

          <button onclick="processCheckout()" class="btn-emerald py-2-5 w-full">✓ Valider la Vente</button>
        </div>
      </div>
    </section>

    <!-- Onglet Session -->
    <section id="tab-stats" class="hidden flex flex-col gap-3 overflow-y-auto">
      <div class="card p-3 flex flex-col gap-2" style="background-color:#312e81; color:#fff;">
        <div>
          <span style="font-size:0.65rem; font-weight:700; color:#a5b4fc; text-transform:uppercase;">Nom de la session</span>
          <input type="text" id="session-title-input" value="Ventes de la journée" onchange="updateSessionTitle(this.value)" style="background:rgba(67,56,202,0.8); color:#fff; font-weight:900; font-size:1.125rem; border-radius:0.5rem; padding:0.25rem 0.5rem; border:1px solid #6366f1; width:100%; margin-top:0.25rem;">
        </div>
        <div class="flex gap-1-5" style="flex-wrap:wrap;">
          <button onclick="exportCurrentCSV()" class="btn-emerald px-3 py-1-5" style="font-size:0.75rem;">📊 CSV Complet</button>
          <button onclick="printSessionTicket()" class="btn-indigo px-3 py-1-5" style="font-size:0.75rem;">🖨 Ticket Bilan</button>
          <button onclick="openArchiveModal()" class="btn-amber px-3 py-1-5" style="font-size:0.75rem;">🔒 Clôturer</button>
        </div>
      </div>

      <div class="grid grid-cols-2 gap-2">
        <div class="card p-3"><span style="font-size:0.65rem; font-weight:700; color:#94a3b8; text-transform:uppercase;">Recette Totale</span><span id="session-total-euros" style="display:block; font-size:1.25rem; font-weight:900; color:#059669; margin-top:0.25rem;">0.00 €</span></div>
        <div class="card p-3"><span style="font-size:0.65rem; font-weight:700; color:#94a3b8; text-transform:uppercase;">Articles Vendus</span><span id="session-total-qty" style="display:block; font-size:1.25rem; font-weight:900; color:#1e293b; margin-top:0.25rem;">0</span></div>
        <div class="card p-3"><span style="font-size:0.65rem; font-weight:700; color:#94a3b8; text-transform:uppercase;">Transactions</span><span id="session-total-tx" style="display:block; font-size:1.25rem; font-weight:900; color:#1e293b; margin-top:0.25rem;">0</span></div>
        <div class="card p-3"><span style="font-size:0.65rem; font-weight:700; color:#94a3b8; text-transform:uppercase;">Panier Moyen</span><span id="session-avg-cart" style="display:block; font-size:1.25rem; font-weight:900; color:#4f46e5; margin-top:0.25rem;">0.00 €</span></div>
      </div>

      <div class="card p-3 flex flex-col gap-2">
        <h3 style="font-weight:800; font-size:0.875rem; border-bottom:1px solid #f1f5f9; padding-bottom:0.25rem;">Règlements</h3>
        <div class="flex justify-between" style="font-size:0.75rem; font-weight:600;"><span>💵 Espèces</span><span id="session-pay-cash" style="font-weight:700;">0.00 €</span></div>
        <div class="flex justify-between" style="font-size:0.75rem; font-weight:600;"><span>💳 Carte Bancaire</span><span id="session-pay-cb" style="font-weight:700;">0.00 €</span></div>
        <div class="flex justify-between" style="font-size:0.75rem; font-weight:600;"><span>📝 Chèques</span><span id="session-pay-check" style="font-weight:700;">0.00 €</span></div>
      </div>

      <div class="card p-3 flex flex-col gap-2">
        <h3 style="font-weight:800; font-size:0.875rem; border-bottom:1px solid #f1f5f9; padding-bottom:0.25rem;">Détail des ventes par article</h3>
        <table style="font-size:0.75rem; text-align:left;">
          <thead>
            <tr style="color:#64748b; border-bottom:1px solid #e2e8f0;">
              <th style="padding:0.25rem;">Article</th>
              <th style="padding:0.25rem;">Prix U.</th>
              <th style="padding:0.25rem;">Qté</th>
              <th style="padding:0.25rem; text-align:right;">Sous-Total</th>
            </tr>
          </thead>
          <tbody id="session-product-rows"></tbody>
        </table>
      </div>
    </section>

    <!-- Onglet Catalogue -->
    <section id="tab-catalog" class="hidden flex flex-col gap-3 overflow-y-auto">
      <div class="card p-4 flex flex-col gap-3">
        <h2 style="font-size:1.125rem; font-weight:800;">Gestion du Catalogue</h2>
        <form onsubmit="handleProductSubmit(event)" class="flex flex-col gap-2" style="background:#f8fafc; padding:0.75rem; border-radius:0.75rem; border:1px solid #e2e8f0;">
          <input type="hidden" id="prod-id">
          <input type="text" id="prod-name" required placeholder="Nom article" style="padding:0.5rem; border:1px solid #cbd5e1; border-radius:0.375rem; font-size:0.875rem;">
          <input type="number" id="prod-price" step="0.1" required placeholder="Prix €" style="padding:0.5rem; border:1px solid #cbd5e1; border-radius:0.375rem; font-size:0.875rem;">
          <select id="prod-category" style="padding:0.5rem; border:1px solid #cbd5e1; border-radius:0.375rem; font-size:0.875rem;">
            <option value="Restauration">🍕 Restauration</option>
            <option value="Buvette">🥤 Buvette</option>
            <option value="Tickets">🎟 Tickets</option>
            <option value="Divers">🎈 Divers</option>
          </select>
          <select id="prod-color" style="padding:0.5rem; border:1px solid #cbd5e1; border-radius:0.375rem; font-size:0.875rem; font-weight:600;">
            <option value="amber">🟧 Amber / Doré</option>
            <option value="sky">🟦 Ciel / Bleu</option>
            <option value="emerald">🟩 Émeraude / Vert</option>
            <option value="purple">🟪 Violet</option>
            <option value="rose">🟥 Rose / Rouge</option>
          </select>
          <button type="submit" class="btn-indigo py-2">Enregistrer</button>
        </form>
      </div>
    </section>

    <!-- Onglet Archives -->
    <section id="tab-archives" class="hidden flex flex-col gap-3 overflow-y-auto">
      <div class="card p-4 flex flex-col gap-3">
        <h2 style="font-size:1.125rem; font-weight:800; border-bottom:1px solid #f1f5f9; padding-bottom:0.5rem;">Événements Clôturés</h2>
        <div id="archives-list" class="flex flex-col gap-3"></div>
      </div>
    </section>

  </main>

  <!-- MODAL CLÔTURE -->
  <div id="archive-modal" class="fixed hidden" style="top:0; bottom:0; left:0; right:0; background:rgba(15,23,42,0.6); z-index:50; display:flex; align-items:center; justify-content:center; padding:1rem;">
    <div class="card p-5 w-full flex flex-col gap-4" style="max-width:24rem; background:#fff;">
      <h3 style="font-size:1.125rem; font-weight:800; color:#d97706;">📁 Clôturer la journée</h3>
      <p style="font-size:0.75rem; color:#64748b;">Cette action sauvegardera définitivement le bilan dans vos archives et réinitialisera la caisse.</p>
      
      <div class="flex flex-col gap-2">
        <label style="font-size:0.75rem; font-weight:700;">Nom de l'événement *</label>
        <input type="text" id="archive-eventName" style="padding:0.5rem; border:1px solid #cbd5e1; border-radius:0.5rem; font-size:0.875rem; font-weight:600;">
        
        <label style="font-size:0.75rem; font-weight:700;">Date *</label>
        <input type="date" id="archive-eventDate" style="padding:0.5rem; border:1px solid #cbd5e1; border-radius:0.5rem; font-size:0.875rem; font-weight:600;">
      </div>

      <div class="flex justify-end gap-2" style="border-top:1px solid #f1f5f9; padding-top:0.75rem;">
        <button onclick="closeArchiveModal()" style="padding:0.5rem 1rem; font-size:0.75rem; font-weight:700; color:#64748b;">Annuler</button>
        <button onclick="confirmArchiveSession()" class="btn-amber px-4 py-2" style="font-size:0.75rem;">Valider & Archiver</button>
      </div>
    </div>
  </div>

  <script>
    const defaultProducts = [
      { id: 1, name: "Crêpe Sucrée", price: 2.00, category: "Restauration", color: "amber" },
      { id: 2, name: "Gaufre Nutella", price: 2.50, category: "Restauration", color: "amber" },
      { id: 3, name: "Soda 33cl", price: 1.50, category: "Buvette", color: "sky" },
      { id: 4, name: "Café", price: 1.00, category: "Buvette", color: "sky" },
      { id: 5, name: "Ticket Tombola", price: 2.00, category: "Tickets", color: "emerald" }
    ];

    const colorClasses = {
      amber: "bg-amber-50",
      sky: "bg-sky-50",
      emerald: "bg-emerald-50",
      purple: "bg-purple-50",
      rose: "bg-rose-50"
    };

    let products = JSON.parse(localStorage.getItem('ape_products')) || defaultProducts;
    let sales = JSON.parse(localStorage.getItem('ape_sales')) || [];
    let archives = JSON.parse(localStorage.getItem('ape_archives')) || [];
    let sessionTitle = localStorage.getItem('ape_session_title') || "Ventes de la journée";

    let cart = {}, selectedPayment = 'Espèces', currentCategory = 'all';
    let draggedItemIndex = null;

    window.onload = function() { 
      renderPOS(); 
      renderCart(); 
      renderSessionSummary();
      renderArchives();
      document.getElementById('session-title-input').value = sessionTitle;
      document.getElementById('archive-eventDate').value = new Date().toISOString().slice(0, 10);
    };

    function updateSessionTitle(val) {
      sessionTitle = val.trim() || "Ventes de la journée";
      localStorage.setItem('ape_session_title', sessionTitle);
    }

    function switchTab(t) {
      ['pos', 'catalog', 'stats', 'archives'].forEach(x => {
        document.getElementById(`tab-${x}`).classList.add('hidden');
        document.getElementById(`nav-${x}`).classList.remove('active');
      });
      document.getElementById(`tab-${t}`).classList.remove('hidden');
      document.getElementById(`nav-${t}`).classList.add('active');
      if (t === 'stats') renderSessionSummary();
      if (t === 'archives') renderArchives();
    }

    function filterCategory(cat) {
      currentCategory = cat;
      document.querySelectorAll('.cat-btn').forEach(btn => {
        btn.classList.remove('active');
        if ((cat === 'all' && btn.innerText.includes('Tous')) || btn.innerText.includes(cat)) {
          btn.classList.add('active');
        }
      });
      renderPOS();
    }

    function setPaymentMethod(method) {
      selectedPayment = method;
      ['Espèces', 'CB', 'Chèque'].forEach(m => {
        const btn = document.getElementById(`pay-${m}`);
        if (btn) {
          if (m === method) btn.classList.add('active');
          else btn.classList.remove('active');
        }
      });
    }

    function renderPOS() {
      const grid = document.getElementById('pos-grid'); 
      grid.innerHTML = '';
      
      products.forEach((p, index) => {
        if (currentCategory !== 'all' && p.category !== currentCategory) return;

        const colorStyle = colorClasses[p.color] || colorClasses.amber;
        const card = document.createElement('div');
        card.className = `product-card ${colorStyle}`;
        card.draggable = true;
        card.dataset.index = index;
        card.onclick = () => addToCart(p.id);

        card.innerHTML = `
          <span style="font-weight:700; font-size:0.875rem; line-height:1.2;">${p.name}</span>
          <div class="flex justify-between items-baseline">
            <span style="font-size:0.6rem; opacity:0.8; font-weight:700; text-transform:uppercase;">${p.category}</span>
            <span style="font-weight:900; font-size:1.125rem;">${p.price.toFixed(2)} €</span>
          </div>
        `;

        card.addEventListener('dragstart', () => { draggedItemIndex = index; card.classList.add('dragging'); });
        card.addEventListener('dragend', () => { card.classList.remove('dragging'); });
        card.addEventListener('dragover', (e) => e.preventDefault());
        card.addEventListener('drop', (e) => {
          e.preventDefault();
          if (draggedItemIndex !== null && draggedItemIndex !== index) {
            const movedItem = products.splice(draggedItemIndex, 1)[0];
            products.splice(index, 0, movedItem);
            localStorage.setItem('ape_products', JSON.stringify(products));
            renderPOS();
          }
        });

        grid.appendChild(card);
      });
    }

    function handleProductSubmit(e) {
      e.preventDefault();
      const id = document.getElementById('prod-id').value;
      const name = document.getElementById('prod-name').value.trim();
      const price = parseFloat(document.getElementById('prod-price').value);
      const category = document.getElementById('prod-category').value;
      const color = document.getElementById('prod-color').value;

      if (id) {
        const index = products.findIndex(p => p.id == id);
        if (index !== -1) products[index] = { id: Number(id), name, price, category, color };
      } else {
        products.push({ id: Date.now(), name, price, category, color });
      }

      localStorage.setItem('ape_products', JSON.stringify(products));
      e.target.reset();
      document.getElementById('prod-id').value = '';
      renderPOS();
      alert('Article enregistré !');
    }

    function addToCart(id) {
      const p = products.find(x => x.id === id);
      cart[id] = cart[id] ? { ...cart[id], qty: cart[id].qty + 1 } : { ...p, qty: 1 };
      renderCart();
    }

    function renderCart() {
      const list = document.getElementById('cart-list'); list.innerHTML = '';
      let total = 0, totalItemsCount = 0;

      Object.values(cart).forEach(i => {
        total += i.price * i.qty;
        totalItemsCount += i.qty;
        list.innerHTML += `<div class="flex justify-between items-center" style="font-size:0.75rem; padding:0.2rem 0;">
          <span>${i.name} x${i.qty}</span>
          <span style="font-weight:700;">${(i.price * i.qty).toFixed(2)} €</span>
        </div>`;
      });
      document.getElementById('cart-total').innerText = `${total.toFixed(2)} €`;
      
      const badge = document.getElementById('mobile-badge');
      if (badge) badge.innerText = totalItemsCount;

      calculateChange();
    }

    function calculateChange() {
      const total = Object.values(cart).reduce((sum, i) => sum + (i.price * i.qty), 0);
      const cashGivenInput = document.getElementById('cash-given');
      const changeEl = document.getElementById('cash-change');
      
      if (!cashGivenInput || !changeEl) return;

      const cashGiven = parseFloat(cashGivenInput.value) || 0;
      const change = cashGiven - total;

      if (cashGiven <= 0) {
        changeEl.innerText = '0.00 €';
        changeEl.style.color = '#78350f';
      } else if (change < 0) {
        changeEl.innerText = `Incomplet (${change.toFixed(2)} €)`;
        changeEl.style.color = '#dc2626';
      } else {
        changeEl.innerText = `${change.toFixed(2)} €`;
        changeEl.style.color = '#047857';
      }
    }

    function clearCart() { 
      cart = {}; 
      const cashGivenInput = document.getElementById('cash-given');
      if (cashGivenInput) cashGivenInput.value = '';
      renderCart(); 
    }

    function processCheckout() {
      const items = Object.values(cart);
      if(!items.length) return alert('Panier vide !');
      
      const printMode = document.getElementById('print-mode').value;
      const total = items.reduce((s, i) => s + i.price * i.qty, 0);
      
      const sale = { id: Date.now(), timestamp: new Date().toISOString(), items, total, paymentMethod: selectedPayment };
      
      sales.push(sale);
      localStorage.setItem('ape_sales', JSON.stringify(sales));

      if (printMode !== 'none') {
        printSaleReceipt(sale, printMode);
      } else {
        finishCheckout();
      }
    }

    // --- ENVOI DIRECT RAWBT AVEC COMMANDE DE COUPE EPSON ---
    const ESC_INIT = "\x1B\x40";
    const ESC_CUT = "\n\n\x1D\x56\x42\x00";

    function sendToRawBT(rawCommands) {
      const fullPayload = ESC_INIT + rawCommands + ESC_CUT;
      const bytes = new TextEncoder().encode(fullPayload);
      let binary = "";
      for (let i = 0; i < bytes.byteLength; i++) {
        binary += String.fromCharCode(bytes[i]);
      }
      const base64Data = window.btoa(binary);

      const link = document.createElement('a');
      link.href = "rawbt:base64," + base64Data;
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
    }

    function printSaleReceipt(sale, mode) {
      const now = new Date(sale.timestamp);
      const dateStr = now.toLocaleDateString('fr-FR');
      const timeStr = now.toLocaleTimeString('fr-FR');

      let textRaw = "";

      if (mode === 'global' || mode === 'both') {
        textRaw += "================================\n";
        textRaw += `     ${sessionTitle.toUpperCase()}     \n`;
        textRaw += "        TICKET DE CAISSE        \n";
        textRaw += `    ${dateStr} a ${timeStr}    \n`;
        textRaw += "================================\n";

        sale.items.forEach(i => {
          let name = i.name.normalize("NFD").replace(/[\u0300-\u036f]/g, "").padEnd(18, ' ').substring(0, 18);
          let qty = `x${i.qty}`.padStart(4, ' ');
          let price = `${(i.price * i.qty).toFixed(2)}E`.padStart(8, ' ');
          textRaw += `${name}${qty}${price}\n`;
        });

        textRaw += "--------------------------------\n";
        textRaw += `TOTAL : ${sale.total.toFixed(2)} EUR\n`;
        textRaw += `Paiement : ${sale.paymentMethod.normalize("NFD").replace(/[\u0300-\u036f]/g, "")}\n`;
        textRaw += "================================\n";
        textRaw += "      Merci de votre visite!    \n";
      }

      if (mode === 'coupons' || mode === 'both') {
        if (mode === 'both') textRaw += ESC_CUT;

        sale.items.forEach(i => {
          let cleanName = i.name.normalize("NFD").replace(/[\u0300-\u036f]/g, "");
          for (let c = 0; c < i.qty; c++) {
            textRaw += "--------------------------------\n";
            textRaw += `     ${sessionTitle.toUpperCase()}     \n`;
            textRaw += "        COUPON DETACHABLE       \n";
            textRaw += `       >> ${cleanName} <<       \n`;
            textRaw += `    ${dateStr} - ${timeStr}     \n`;
            textRaw += "--------------------------------\n";
            textRaw += ESC_CUT;
          }
        });
      } else {
        textRaw += ESC_CUT;
      }

      finishCheckout();
      setTimeout(() => {
        sendToRawBT(textRaw);
      }, 150);
    }

    function finishCheckout() {
      clearCart();
      renderSessionSummary();
    }

    function renderSessionSummary() {
      let totalEuros = 0, totalQty = 0;
      let payCash = 0, payCB = 0, payCheck = 0;
      const itemStats = {};

      sales.forEach(s => {
        totalEuros += s.total;
        if (s.paymentMethod === 'Espèces') payCash += s.total;
        else if (s.paymentMethod === 'CB') payCB += s.total;
        else if (s.paymentMethod === 'Chèque') payCheck += s.total;

        s.items.forEach(i => {
          totalQty += i.qty;
          if (!itemStats[i.name]) itemStats[i.name] = { price: i.price, qty: 0, subtotal: 0 };
          itemStats[i.name].qty += i.qty;
          itemStats[i.name].subtotal += (i.price * i.qty);
        });
      });

      const avgCart = sales.length ? (totalEuros / sales.length) : 0;

      document.getElementById('session-total-euros').innerText = `${totalEuros.toFixed(2)} €`;
      document.getElementById('session-total-qty').innerText = totalQty;
      document.getElementById('session-total-tx').innerText = sales.length;
      document.getElementById('session-avg-cart').innerText = `${avgCart.toFixed(2)} €`;

      document.getElementById('session-pay-cash').innerText = `${payCash.toFixed(2)} €`;
      document.getElementById('session-pay-cb').innerText = `${payCB.toFixed(2)} €`;
      document.getElementById('session-pay-check').innerText = `${payCheck.toFixed(2)} €`;

      const tbody = document.getElementById('session-product-rows');
      tbody.innerHTML = '';
      if (!Object.keys(itemStats).length) {
        tbody.innerHTML = `<tr><td colspan="4" style="padding:0.5rem; text-align:center; color:#94a3b8;">Aucune vente enregistrée.</td></tr>`;
      } else {
        Object.entries(itemStats).forEach(([name, data]) => {
          tbody.innerHTML += `<tr>
            <td style="padding:0.25rem; font-weight:700;">${name}</td>
            <td style="padding:0.25rem;">${data.price.toFixed(2)} €</td>
            <td style="padding:0.25rem; font-weight:700;">${data.qty}</td>
            <td style="padding:0.25rem; text-align:right; font-weight:900; color:#059669;">${data.subtotal.toFixed(2)} €</td>
          </tr>`;
        });
      }
    }

    function exportCurrentCSV() {
      exportCSVData(sales, sessionTitle.replace(/[^a-zA-Z0-9]/g, "_"));
    }

    function exportArchiveCSV(id) {
      const arc = archives.find(a => a.id === id);
      if (arc) exportCSVData(arc.salesData, arc.title.replace(/[^a-zA-Z0-9]/g, "_"));
    }

    function exportCSVData(data, filename) {
      let csv = "ID;Date;Heure;Total;Paiement;Articles\n";
      data.forEach(s => {
        const d = new Date(s.timestamp);
        const dateStr = d.toLocaleDateString('fr-FR');
        const timeStr = d.toLocaleTimeString('fr-FR');
        const itemsStr = s.items.map(i => `${i.name} (x${i.qty})`).join(' | ');
        csv += `${s.id};${dateStr};${timeStr};${s.total.toFixed(2).replace('.', ',')};${s.paymentMethod};"${itemsStr}"\n`;
      });
      const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
      const link = document.createElement("a");
      link.href = URL.createObjectURL(blob);
      link.setAttribute("download", `${filename}_${new Date().toISOString().slice(0,10)}.csv`);
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
    }

    function printSessionTicket() {
      let totalEuros = 0, totalQty = 0;
      const itemStats = {};
      sales.forEach(s => {
        totalEuros += s.total;
        s.items.forEach(i => {
          totalQty += i.qty;
          if (!itemStats[i.name]) itemStats[i.name] = { price: i.price, qty: 0, subtotal: 0 };
          itemStats[i.name].qty += i.qty;
          itemStats[i.name].subtotal += (i.price * i.qty);
        });
      });

      let textRaw = "================================\n";
      textRaw += `     ${sessionTitle.toUpperCase()}     \n`;
      textRaw += "        BILAN DE SESSION        \n";
      textRaw += `      ${new Date().toLocaleDateString('fr-FR')}      \n`;
      textRaw += "================================\n";

      Object.entries(itemStats).forEach(([name, data]) => {
        let n = name.normalize("NFD").replace(/[\u0300-\u036f]/g, "").padEnd(18, ' ').substring(0, 18);
        let q = `x${data.qty}`.padStart(4, ' ');
        let p = `${data.subtotal.toFixed(2)}E`.padStart(8, ' ');
        textRaw += `${n}${q}${p}\n`;
      });

      textRaw += "--------------------------------\n";
      textRaw += `TOTAL VENTES : ${totalEuros.toFixed(2)} EUR\n`;
      textRaw += `Total articles : ${totalQty}\n`;
      textRaw += `Transactions : ${sales.length}\n`;
      textRaw += "================================\n";

      sendToRawBT(textRaw);
    }

    function openArchiveModal() {
      document.getElementById('archive-eventName').value = sessionTitle;
      document.getElementById('archive-modal').classList.remove('hidden');
    }

    function closeArchiveModal() {
      document.getElementById('archive-modal').classList.add('hidden');
    }

    function confirmArchiveSession() {
      const eventName = document.getElementById('archive-eventName').value.trim() || sessionTitle;
      const eventDate = document.getElementById('archive-eventDate').value || new Date().toISOString().slice(0, 10);
      
      if (!sales.length) {
        alert('Aucune vente à archiver dans cette session !');
        closeArchiveModal();
        return;
      }

      const archiveItem = {
        id: Date.now(),
        title: eventName,
        date: eventDate,
        salesData: [...sales],
        totalEuros: sales.reduce((s, x) => s + x.total, 0),
        totalTx: sales.length
      };

      archives.push(archiveItem);
      localStorage.setItem('ape_archives', JSON.stringify(archives));

      sales = [];
      localStorage.removeItem('ape_sales');
      sessionTitle = "Ventes de la journée";
      localStorage.setItem('ape_session_title', sessionTitle);
      document.getElementById('session-title-input').value = sessionTitle;

      closeArchiveModal();
      renderSessionSummary();
      renderArchives();
      alert('Session archivée et caisse réinitialisée avec succès !');
    }

    function renderArchives() {
      const list = document.getElementById('archives-list');
      if (!list) return;
      list.innerHTML = '';
      if (!archives.length) {
        list.innerHTML = `<p style="font-size:0.75rem; color:#94a3b8; text-align:center;">Aucune archive enregistrée.</p>`;
        return;
      }
      archives.slice().reverse().forEach(arc => {
        list.innerHTML += `
          <div style="background:#f8fafc; border:1px solid #e2e8f0; border-radius:0.75rem; padding:0.75rem; display:flex; flex-direction:column; gap:0.5rem;">
            <div class="flex justify-between items-center">
              <div>
                <strong style="font-size:0.875rem; color:#1e293b;">${arc.title}</strong><br>
                <span style="font-size:0.65rem; color:#64748b;">Date : ${arc.date} | Transactions : ${arc.totalTx}</span>
              </div>
              <span style="font-weight:900; font-size:1rem; color:#059669;">${arc.totalEuros.toFixed(2)} €</span>
            </div>
            <div class="flex gap-2">
              <button onclick="exportArchiveCSV(${arc.id})" class="btn-emerald px-2 py-1" style="font-size:0.65rem;">📊 Exporter CSV</button>
            </div>
          </div>
        `;
      });
    }
  </script>
</body>
</html>
