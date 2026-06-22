<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PokéBundle TCG · Bundles &amp; Pre-órdenes</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Rajdhani:wght@500;600;700&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --bg: #1a0e0c;
    --panel: #2a1411;
    --panel-2: #3a1a15;
    --line: #5a2a22;
    --text: #f7ece6;
    --text-dim: #c89a8c;
    --red: #e3350d;
    --red-dim: #7a1e0a;
    --gold: #f4b942;
    --green: #3fb97d;
    --blue-meg: #4f8ff7;
    --font-display: 'Rajdhani', sans-serif;
    --font-body: 'Inter', sans-serif;
  }
  *{box-sizing:border-box;}
  body{margin:0;background:var(--bg);color:var(--text);font-family:var(--font-body);}

  /* ---------- top bar ---------- */
  header.top{
    position:sticky; top:0; z-index:50;
    background:rgba(26,14,12,0.92); backdrop-filter:blur(8px);
    border-bottom:1px solid var(--line);
    display:flex; align-items:center; justify-content:space-between;
    padding:14px 28px;
  }
  .brand{display:flex; align-items:center; gap:10px;}
  .brand-mark{
    width:34px;height:34px;border-radius:8px;
    background:conic-gradient(from 220deg, var(--red), var(--gold), var(--red));
    display:flex;align-items:center;justify-content:center;
    font-family:var(--font-display);font-weight:700;color:#1a0e0c;font-size:15px;
  }
  .brand-name{font-family:var(--font-display); font-weight:700; font-size:20px; letter-spacing:0.5px;}
  .brand-name span{color:var(--gold);}
  nav.filters{display:flex; gap:8px; flex-wrap:wrap;}
  .chip{
    border:1px solid var(--line); background:var(--panel); color:var(--text-dim);
    padding:7px 14px; border-radius:999px; font-size:13px; font-weight:600;
    cursor:pointer; transition:all .15s ease; font-family:var(--font-body);
  }
  .chip:hover{border-color:var(--gold); color:var(--text);}
  .chip.active{background:var(--red); border-color:var(--red); color:#fff;}
  .cart-btn{
    position:relative; background:var(--panel-2); border:1px solid var(--line);
    color:var(--text); padding:9px 16px; border-radius:8px; font-family:var(--font-display);
    font-weight:600; font-size:14px; cursor:pointer; display:flex; align-items:center; gap:8px;
  }
  .cart-btn:hover{border-color:var(--gold);}
  .cart-count{
    background:var(--red); color:#fff; font-size:11px; font-weight:700;
    border-radius:999px; padding:1px 7px; min-width:18px; text-align:center;
  }

  /* ---------- hero ---------- */
  .hero{
    padding:64px 28px 40px; text-align:left; max-width:1200px; margin:0 auto;
    border-bottom:1px solid var(--line);
  }
  .hero-eyebrow{
    font-family:var(--font-display); color:var(--gold); letter-spacing:3px;
    font-size:13px; font-weight:700; text-transform:uppercase; margin-bottom:10px;
  }
  .hero h1{
    font-family:var(--font-display); font-size:clamp(34px, 5vw, 58px); line-height:1.02;
    margin:0 0 14px; font-weight:700; letter-spacing:-0.5px;
  }
  .hero h1 em{font-style:normal; color:var(--red);}
  .hero p{max-width:560px; color:var(--text-dim); font-size:15.5px; line-height:1.6; margin:0;}
  .hero-stamps{display:flex; gap:10px; margin-top:24px; flex-wrap:wrap;}
  .stamp{
    border:1px solid var(--line); border-radius:6px; padding:6px 12px;
    font-family:var(--font-display); font-size:12.5px; font-weight:600; color:var(--text-dim);
  }
  .stamp b{color:var(--text);}

  /* ---------- catalog ---------- */
  main{max-width:1200px; margin:0 auto; padding:36px 28px 80px;}
  .section-title{
    font-family:var(--font-display); font-size:13px; font-weight:700; letter-spacing:2.5px;
    text-transform:uppercase; color:var(--text-dim); margin:36px 0 16px;
    display:flex; align-items:center; gap:10px;
  }
  .section-title::after{content:''; flex:1; height:1px; background:var(--line);}

  .grid{display:grid; grid-template-columns:repeat(auto-fill, minmax(250px, 1fr)); gap:18px;}

  .card{
    background:var(--panel); border:1px solid var(--line); border-radius:14px;
    overflow:hidden; position:relative; display:flex; flex-direction:column;
    transition:transform .2s ease, border-color .2s ease, box-shadow .2s ease;
  }
  .card:hover{
    transform:translateY(-4px);
    border-color:var(--gold);
    box-shadow:0 14px 30px -10px rgba(244,185,66,0.18);
  }
  .card-art{
    height:130px; position:relative; display:flex; align-items:center; justify-content:center;
    background: radial-gradient(circle at 30% 20%, rgba(244,185,66,0.18), transparent 60%),
                linear-gradient(135deg, var(--panel-2), #1a0e0c);
    border-bottom:1px solid var(--line);
  }
  .card-art .icon{font-size:42px; filter:drop-shadow(0 4px 10px rgba(0,0,0,.4));}
  .preorder-flag{
    position:absolute; top:10px; left:-32px; background:var(--gold); color:#1a0e0c;
    font-family:var(--font-display); font-weight:700; font-size:11px; letter-spacing:1px;
    padding:3px 38px; transform:rotate(-38deg); box-shadow:0 2px 6px rgba(0,0,0,.3);
  }
  .set-badge{
    position:absolute; top:10px; right:10px; font-family:var(--font-display); font-weight:700;
    font-size:11px; padding:3px 9px; border-radius:5px; letter-spacing:0.5px;
  }
  .set-sv{background:rgba(79,143,247,0.18); color:var(--blue-meg); border:1px solid rgba(79,143,247,0.4);}
  .set-meg{background:rgba(227,53,13,0.18); color:#ff7b54; border:1px solid rgba(227,53,13,0.4);}

  .card-body{padding:14px 16px 16px; display:flex; flex-direction:column; gap:8px; flex:1;}
  .card-exp{font-size:11.5px; color:var(--text-dim); font-weight:600; letter-spacing:0.5px;}
  .card-title{font-family:var(--font-display); font-size:17px; font-weight:700; line-height:1.2;}
  .card-desc{font-size:12.5px; color:var(--text-dim); line-height:1.5; flex:1;}

  .card-foot{display:flex; align-items:center; justify-content:space-between; margin-top:6px;}
  .price{font-family:var(--font-display); font-size:19px; font-weight:700; color:var(--text);}
  .price small{font-size:11px; color:var(--text-dim); font-weight:500;}
  .stock{font-size:11px; font-weight:600;}
  .stock.ok{color:var(--green);}
  .stock.low{color:var(--gold);}
  .stock.pre{color:var(--blue-meg);}

  .add-btn{
    margin-top:10px; width:100%; padding:10px; border-radius:8px; border:none;
    background:var(--red); color:#fff; font-family:var(--font-display); font-weight:700;
    font-size:13.5px; letter-spacing:0.5px; cursor:pointer; transition:background .15s;
  }
  .add-btn:hover{background:#c92c0b;}
  .add-btn.pre{background:var(--blue-meg);}
  .add-btn.pre:hover{background:#3a78e0;}
  .add-btn.added{background:var(--green); pointer-events:none;}


  /* ---------- cart drawer ---------- */
  .overlay{
    position:fixed; inset:0; background:rgba(0,0,0,0.55); z-index:90; opacity:0; pointer-events:none;
    transition:opacity .2s ease;
  }
  .overlay.open{opacity:1; pointer-events:auto;}
  .drawer{
    position:fixed; top:0; right:0; height:100%; width:380px; max-width:92vw;
    background:var(--panel); border-left:1px solid var(--line); z-index:100;
    transform:translateX(100%); transition:transform .25s ease;
    display:flex; flex-direction:column;
  }
  .drawer.open{transform:translateX(0);}
  .drawer-head{
    padding:18px 20px; border-bottom:1px solid var(--line);
    display:flex; align-items:center; justify-content:space-between;
  }
  .drawer-head h3{font-family:var(--font-display); margin:0; font-size:18px;}
  .drawer-head button{background:none; border:none; color:var(--text-dim); font-size:20px; cursor:pointer;}
  .drawer-items{flex:1; overflow-y:auto; padding:14px 20px; display:flex; flex-direction:column; gap:12px;}
  .empty-cart{color:var(--text-dim); font-size:13.5px; text-align:center; margin-top:40px; line-height:1.6;}
  .drawer-item{display:flex; gap:10px; align-items:flex-start; border-bottom:1px solid var(--line); padding-bottom:12px;}
  .di-icon{font-size:24px; width:38px; text-align:center;}
  .di-info{flex:1;}
  .di-name{font-size:13.5px; font-weight:600;}
  .di-meta{font-size:11.5px; color:var(--text-dim); margin-top:2px;}
  .di-qty{display:flex; align-items:center; gap:8px; margin-top:6px;}
  .di-qty button{
    width:22px; height:22px; border-radius:5px; border:1px solid var(--line); background:var(--panel-2);
    color:var(--text); cursor:pointer; font-size:13px; line-height:1;
  }
  .di-price{font-family:var(--font-display); font-weight:700; font-size:13.5px; white-space:nowrap;}
  .di-remove{background:none; border:none; color:var(--text-dim); font-size:11px; cursor:pointer; text-decoration:underline; margin-top:6px;}
  .drawer-foot{padding:18px 20px; border-top:1px solid var(--line);}
  .drawer-total{display:flex; justify-content:space-between; font-family:var(--font-display); font-weight:700; font-size:17px; margin-bottom:14px;}
  .checkout-btn{
    width:100%; padding:13px; border-radius:8px; border:none; background:var(--gold); color:#1a0e0c;
    font-family:var(--font-display); font-weight:700; font-size:14.5px; cursor:pointer; letter-spacing:0.5px;
  }
  .checkout-btn:hover{background:#ffcb5c;}
  .preorder-note{font-size:11px; color:var(--text-dim); margin-top:10px; line-height:1.5;}

  footer{border-top:1px solid var(--line); padding:24px 28px; text-align:center; color:var(--text-dim); font-size:12px;}

  @media (max-width:720px){
    header.top{flex-direction:column; align-items:flex-start; gap:12px;}
    nav.filters{width:100%;}
  }
  @media (prefers-reduced-motion: reduce){
    *{transition:none !important;}
  }
</style>
</head>
<body>

<header class="top">
  <div class="brand">
    <div class="brand-mark">PB</div>
    <div class="brand-name">Poké<span>Bundle</span> TCG</div>
  </div>
  <nav class="filters" id="filters">
    <button class="chip active" data-filter="all">Todo</button>
    <button class="chip" data-filter="SV">Scarlet &amp; Violet</button>
    <button class="chip" data-filter="MEG">Megaevoluciones</button>
    <button class="chip" data-filter="preorder">Pre-órdenes</button>
  </nav>
  <button class="cart-btn" id="cartBtn">🛒 Carrito <span class="cart-count" id="cartCount">0</span></button>
</header>

<section class="hero">
  <div class="hero-eyebrow">Catálogo de bundles · Edición coleccionista</div>
  <h1>Cada bundle es<br><em>una vitrina</em> en miniatura.</h1>
  <p>Bundles sellados de Pokémon TCG con las expansiones vigentes de Scarlet &amp; Violet y la nueva era Megaevoluciones. Reservá también las próximas expansiones aún sin fecha confirmada.</p>
  <div class="hero-stamps">
    <div class="stamp"><b>14</b> bundles activos</div>
    <div class="stamp"><b>4</b> expansiones SV</div>
    <div class="stamp"><b>2</b> sets Megaevoluciones</div>
    <div class="stamp"><b>3</b> pre-órdenes abiertas</div>
  </div>
</section>

<main>
  <div class="section-title">Catálogo</div>
  <div class="grid" id="catalog"></div>
</main>

<footer>PokéBundle TCG — proyecto educativo, Unidad 2: Registros y Claves. No afiliado a The Pokémon Company.</footer>

<div class="overlay" id="overlay"></div>
<aside class="drawer" id="drawer">
  <div class="drawer-head">
    <h3>Tu carrito</h3>
    <button id="closeDrawer">✕</button>
  </div>
  <div class="drawer-items" id="drawerItems"></div>
  <div class="drawer-foot">
    <div class="drawer-total"><span>Total</span><span id="totalPrice">$0</span></div>
    <button class="checkout-btn" id="checkoutBtn">Finalizar compra</button>
    <div class="preorder-note">Los productos marcados como pre-orden se cobran ahora y se envían en la fecha de lanzamiento estimada.</div>
  </div>
</aside>

<script>
// ---------- Registro Producto (instancias) ----------
const PRODUCTOS = [
  {sku_bundle:"BND-SV09-001", nombre_bundle:"Bundle Iniciador Destellos de Ruina", codigo_expansion:"SV09", cantidad_sobres:4, precio_unitario:18999, stock_disponible:23, es_preorden:false, fecha_lanzamiento:null, icon:"🔥"},
  {sku_bundle:"BND-SV09-002", nombre_bundle:"Bundle Elite Destellos de Ruina", codigo_expansion:"SV09", cantidad_sobres:8, precio_unitario:34999, stock_disponible:9, es_preorden:false, fecha_lanzamiento:null, icon:"⚡"},
  {sku_bundle:"BND-SV08-001", nombre_bundle:"Bundle Coronas Astrales", codigo_expansion:"SV08", cantidad_sobres:6, precio_unitario:27999, stock_disponible:4, es_preorden:false, fecha_lanzamiento:null, icon:"👑"},
  {sku_bundle:"BND-SV08-002", nombre_bundle:"Bundle Mega Coronas Astrales", codigo_expansion:"SV08", cantidad_sobres:10, precio_unitario:42999, stock_disponible:0, es_preorden:false, fecha_lanzamiento:null, icon:"✨"},
  {sku_bundle:"BND-SV07-001", nombre_bundle:"Bundle Fuerzas Espectrales", codigo_expansion:"SV07", cantidad_sobres:6, precio_unitario:26999, stock_disponible:15, es_preorden:false, fecha_lanzamiento:null, icon:"👻"},
  {sku_bundle:"BND-SV06-001", nombre_bundle:"Bundle Fuerzas Temporales", codigo_expansion:"SV06", cantidad_sobres:4, precio_unitario:18499, stock_disponible:31, es_preorden:false, fecha_lanzamiento:null, icon:"⏳"},
  {sku_bundle:"BND-MEG01-001", nombre_bundle:"Bundle Iniciador Megaevoluciones", codigo_expansion:"MEG01", cantidad_sobres:6, precio_unitario:32999, stock_disponible:18, es_preorden:false, fecha_lanzamiento:null, icon:"🌀"},
  {sku_bundle:"BND-MEG01-009", nombre_bundle:"Bundle Triple Megaevoluciones", codigo_expansion:"MEG01", cantidad_sobres:9, precio_unitario:54999, stock_disponible:12, es_preorden:false, fecha_lanzamiento:null, icon:"💠"},
  {sku_bundle:"BND-MEG01-ETB", nombre_bundle:"Elite Trainer Box Megaevoluciones", codigo_expansion:"MEG01", cantidad_sobres:11, precio_unitario:64999, stock_disponible:3, es_preorden:false, fecha_lanzamiento:null, icon:"📦"},
  {sku_bundle:"BND-MEG02-001", nombre_bundle:"Bundle Megaevoluciones: Resonancia (Pre-orden)", codigo_expansion:"MEG02", cantidad_sobres:6, precio_unitario:33999, stock_disponible:999, es_preorden:true, fecha_lanzamiento:"2026-09-12", icon:"🔮"},
  {sku_bundle:"BND-MEG02-009", nombre_bundle:"Bundle Triple Megaevoluciones: Resonancia (Pre-orden)", codigo_expansion:"MEG02", cantidad_sobres:9, precio_unitario:57999, stock_disponible:999, es_preorden:true, fecha_lanzamiento:"2026-09-12", icon:"🌌"},
  {sku_bundle:"BND-SV10-001", nombre_bundle:"Bundle Vórtice Carmesí (Pre-orden)", codigo_expansion:"SV10", cantidad_sobres:6, precio_unitario:29999, stock_disponible:999, es_preorden:true, fecha_lanzamiento:"2026-08-01", icon:"🌪️"},
  {sku_bundle:"BND-SV10-002", nombre_bundle:"Elite Trainer Box Vórtice Carmesí (Pre-orden)", codigo_expansion:"SV10", cantidad_sobres:11, precio_unitario:61999, stock_disponible:999, es_preorden:true, fecha_lanzamiento:"2026-08-01", icon:"🧨"},
  {sku_bundle:"BND-SV05-001", nombre_bundle:"Bundle Evolución Paldea", codigo_expansion:"SV05", cantidad_sobres:4, precio_unitario:16999, stock_disponible:27, es_preorden:false, fecha_lanzamiento:null, icon:"🌿"},
  {sku_bundle:"BND-SV04-001", nombre_bundle:"Bundle Fuerza Salvaje", codigo_expansion:"SV04", cantidad_sobres:6, precio_unitario:23999, stock_disponible:6, es_preorden:false, fecha_lanzamiento:null, icon:"🐉"},
];

const EXPANSIONES = {
  SV04:{nombre:"Fuerza Salvaje", familia:"SV"}, SV05:{nombre:"Evolución Paldea", familia:"SV"},
  SV06:{nombre:"Fuerzas Temporales", familia:"SV"}, SV07:{nombre:"Fuerzas Espectrales", familia:"SV"},
  SV08:{nombre:"Coronas Astrales", familia:"SV"}, SV09:{nombre:"Destellos de Ruina", familia:"SV"},
  SV10:{nombre:"Vórtice Carmesí", familia:"SV"},
  MEG01:{nombre:"Megaevoluciones", familia:"MEG"}, MEG02:{nombre:"Megaevoluciones: Resonancia", familia:"MEG"},
};

let cart = {}; // sku_bundle -> qty
let activeFilter = "all";

function fmt(n){ return "$" + n.toLocaleString("es-AR"); }

function stockLabel(p){
  if(p.es_preorden) return {cls:"pre", text:"Pre-orden · " + (p.fecha_lanzamiento || "fecha a confirmar")};
  if(p.stock_disponible === 0) return {cls:"low", text:"Sin stock"};
  if(p.stock_disponible <= 5) return {cls:"low", text:"Últimas " + p.stock_disponible + " u."};
  return {cls:"ok", text:p.stock_disponible + " disponibles"};
}

function renderCatalog(){
  const catalog = document.getElementById("catalog");
  catalog.innerHTML = "";
  const filtered = PRODUCTOS.filter(p=>{
    if(activeFilter === "all") return true;
    if(activeFilter === "preorder") return p.es_preorden;
    return EXPANSIONES[p.codigo_expansion].familia === activeFilter;
  });

  filtered.forEach(p=>{
    const exp = EXPANSIONES[p.codigo_expansion];
    const st = stockLabel(p);
    const disabled = (!p.es_preorden && p.stock_disponible === 0);
    const card = document.createElement("div");
    card.className = "card";
    card.innerHTML = `
      <div class="card-art">
        ${p.es_preorden ? '<div class="preorder-flag">PRE-ORDEN</div>' : ''}
        <span class="set-badge ${exp.familia === 'SV' ? 'set-sv' : 'set-meg'}">${p.codigo_expansion}</span>
        <span class="icon">${p.icon}</span>
      </div>
      <div class="card-body">
        <div class="card-exp">${exp.nombre}</div>
        <div class="card-title">${p.nombre_bundle}</div>
        <div class="card-desc">${p.cantidad_sobres} sobres incluidos · SKU ${p.sku_bundle}</div>
        <div class="card-foot">
          <div class="price">${fmt(p.precio_unitario)}</div>
          <div class="stock ${st.cls}">${st.text}</div>
        </div>
        <button class="add-btn ${p.es_preorden ? 'pre' : ''}" data-sku="${p.sku_bundle}" ${disabled ? 'disabled style="opacity:.4;cursor:not-allowed;"' : ''}>
          ${disabled ? 'Sin stock' : (p.es_preorden ? 'Reservar ahora' : 'Agregar al carrito')}
        </button>
      </div>
    `;
    catalog.appendChild(card);
  });

  document.querySelectorAll(".add-btn:not([disabled])").forEach(btn=>{
    btn.addEventListener("click", ()=>{
      addToCart(btn.dataset.sku);
      btn.textContent = "Agregado ✓";
      btn.classList.add("added");
      setTimeout(()=>{
        btn.textContent = btn.classList.contains("pre") ? "Reservar ahora" : "Agregar al carrito";
        btn.classList.remove("added");
      }, 900);
    });
  });
}

function addToCart(sku){
  cart[sku] = (cart[sku] || 0) + 1;
  renderCart();
}
function changeQty(sku, delta){
  cart[sku] = (cart[sku] || 0) + delta;
  if(cart[sku] <= 0) delete cart[sku];
  renderCart();
}
function removeFromCart(sku){
  delete cart[sku];
  renderCart();
}

function renderCart(){
  const items = Object.keys(cart);
  const countEl = document.getElementById("cartCount");
  const totalQty = items.reduce((s,k)=>s+cart[k],0);
  countEl.textContent = totalQty;

  const container = document.getElementById("drawerItems");
  container.innerHTML = "";

  if(items.length === 0){
    container.innerHTML = '<div class="empty-cart">Tu carrito está vacío.<br>Agregá algún bundle del catálogo.</div>';
  } else {
    items.forEach(sku=>{
      const p = PRODUCTOS.find(x=>x.sku_bundle === sku);
      const qty = cart[sku];
      const row = document.createElement("div");
      row.className = "drawer-item";
      row.innerHTML = `
        <div class="di-icon">${p.icon}</div>
        <div class="di-info">
          <div class="di-name">${p.nombre_bundle}</div>
          <div class="di-meta">${EXPANSIONES[p.codigo_expansion].nombre} ${p.es_preorden ? '· Pre-orden' : ''}</div>
          <div class="di-qty">
            <button data-sku="${sku}" data-d="-1">−</button>
            <span>${qty}</span>
            <button data-sku="${sku}" data-d="1">+</button>
          </div>
          <button class="di-remove" data-sku="${sku}">Quitar</button>
        </div>
        <div class="di-price">${fmt(p.precio_unitario * qty)}</div>
      `;
      container.appendChild(row);
    });
  }

  container.querySelectorAll("[data-d]").forEach(btn=>{
    btn.addEventListener("click", ()=>changeQty(btn.dataset.sku, parseInt(btn.dataset.d)));
  });
  container.querySelectorAll(".di-remove").forEach(btn=>{
    btn.addEventListener("click", ()=>removeFromCart(btn.dataset.sku));
  });

  const total = items.reduce((s,sku)=>{
    const p = PRODUCTOS.find(x=>x.sku_bundle === sku);
    return s + p.precio_unitario * cart[sku];
  }, 0);
  document.getElementById("totalPrice").textContent = fmt(total);
}

// filtros
document.querySelectorAll(".chip").forEach(chip=>{
  chip.addEventListener("click", ()=>{
    document.querySelectorAll(".chip").forEach(c=>c.classList.remove("active"));
    chip.classList.add("active");
    activeFilter = chip.dataset.filter;
    renderCatalog();
  });
});

// drawer
const drawer = document.getElementById("drawer");
const overlay = document.getElementById("overlay");
document.getElementById("cartBtn").addEventListener("click", ()=>{
  drawer.classList.add("open"); overlay.classList.add("open");
});
document.getElementById("closeDrawer").addEventListener("click", closeDrawer);
overlay.addEventListener("click", closeDrawer);
function closeDrawer(){ drawer.classList.remove("open"); overlay.classList.remove("open"); }

document.getElementById("checkoutBtn").addEventListener("click", ()=>{
  if(Object.keys(cart).length === 0){ alert("Tu carrito está vacío."); return; }
  alert("¡Gracias por tu compra! (Demo educativa — no se procesa pago real)");
  cart = {};
  renderCart();
  closeDrawer();
});

renderCatalog();
renderCart();
</script>
</body>
</html>
