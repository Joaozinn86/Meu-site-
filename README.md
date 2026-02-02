


<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>DRAGON STORE</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">

<style>
/* ================= VARIABLES & RESET ================= */
:root {
    --primary: #ff0000;
    --primary-dark: #cc0000;
    --primary-glow: rgba(255, 0, 0, 0.4);
    --bg-dark: #050505;
    --card-bg: linear-gradient(135deg, #4a0000 0%, #1a0000 100%);
    --glass: rgba(20, 20, 20, 0.8);
    --glass-border: rgba(255, 255, 255, 0.08);
    --text-main: #ffffff;
    --text-muted: #aaaaaa;
    --radius: 12px;
}

* { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif; -webkit-tap-highlight-color: transparent; }

body {
    background-color: var(--bg-dark);
    background-image: radial-gradient(circle at 50% 0%, #330000 0%, #000000 70%);
    color: var(--text-main);
    min-height: 100vh;
    padding-bottom: 80px; /* Space for spacing */
}

/* ================= UTILS & ANIMATIONS ================= */
.hidden { display: none !important; }
.fade-in { animation: fadeIn 0.3s ease-out forwards; }
@keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

/* ================= HEADER ================= */
header {
    position: fixed;
    top: 0; left: 0; width: 100%;
    z-index: 100;
    background: rgba(0,0,0,0.85);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    border-bottom: 1px solid var(--glass-border);
    padding: 15px 20px;
}
header .container {
    display: flex; align-items: center; justify-content: space-between; max-width: 1200px; margin: 0 auto;
}
.logo {
    font-size: 20px; font-weight: 800; color: var(--text-main); text-transform: uppercase; letter-spacing: 1px;
    display: flex; align-items: center; gap: 5px;
}
.logo span { color: var(--primary); }

.nav-icons { display: flex; gap: 15px; align-items: center; }
.icon-btn { background: none; border: none; cursor: pointer; position: relative; display: flex; align-items: center; justify-content: center; }
.icon-svg { width: 24px; height: 24px; fill: none; stroke: white; stroke-width: 2; stroke-linecap: round; stroke-linejoin: round; transition: 0.2s; }
.icon-btn:hover .icon-svg { stroke: var(--primary); }

.badge {
    position: absolute; top: -5px; right: -5px;
    background: var(--primary); color: white;
    font-size: 10px; font-weight: bold;
    width: 16px; height: 16px; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
}

/* ================= MAIN LAYOUT ================= */
main { padding-top: 80px; width: 92%; max-width: 1200px; margin: 0 auto; }

/* ================= PRODUCT GRID (2 COLUMNS) ================= */
.products-grid {
    display: grid;
    grid-template-columns: 1fr 1fr; /* Força 2 colunas */
    gap: 12px;
}

.product-card {
    background: var(--card-bg);
    border-radius: var(--radius);
    padding: 10px;
    position: relative;
    border: 1px solid var(--glass-border);
    transition: transform 0.2s, box-shadow 0.2s;
    overflow: hidden;
    display: flex; flex-direction: column;
}

.product-card:active { transform: scale(0.98); }

/* Efeito de brilho no fundo do card */
.product-card::before {
    content: ''; position: absolute; inset: 0;
    background: radial-gradient(circle at center, rgba(255,0,0,0.2) 0%, transparent 70%);
    z-index: 0;
}

.card-img-wrapper {
    width: 100%; aspect-ratio: 1/1; /* Quadrado */
    border-radius: 8px; overflow: hidden;
    position: relative; z-index: 1;
    margin-bottom: 8px;
    background: #000;
}
.product-card img { width: 100%; height: 100%; object-fit: cover; transition: 0.3s; }
.product-card:hover img { transform: scale(1.05); }

.card-info { position: relative; z-index: 1; display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between; }
.card-title { font-size: 13px; font-weight: 700; color: #fff; margin-bottom: 4px; line-height: 1.3; text-shadow: 0 2px 4px rgba(0,0,0,0.5); }
.card-price { font-size: 14px; color: #ff4444; font-weight: 800; margin-bottom: 8px; }
.card-pix-tag { font-size: 10px; color: #aaa; margin-top: -5px; margin-bottom: 8px; display: block; }

.btn-buy {
    width: 100%;
    background: var(--primary);
    color: white;
    border: none;
    padding: 8px 0;
    border-radius: 8px;
    font-size: 12px;
    font-weight: 700;
    cursor: pointer;
    display: flex; align-items: center; justify-content: center; gap: 5px;
    box-shadow: 0 4px 10px rgba(255, 0, 0, 0.3);
    transition: 0.2s;
}
.btn-buy:hover { background: var(--primary-dark); }

/* ================= MODALS (OVERLAYS) ================= */
.modal-overlay {
    position: fixed; inset: 0;
    background: rgba(0,0,0,0.8);
    backdrop-filter: blur(5px);
    z-index: 999;
    display: flex; align-items: center; justify-content: center; /* Centralizado PC */
    align-items: flex-end; /* Mobile sheet style */
}
@media(min-width: 768px) { .modal-overlay { align-items: center; } }

.modal-box {
    background: #111;
    width: 100%; max-width: 400px;
    border-radius: 20px 20px 0 0;
    padding: 25px;
    border-top: 1px solid var(--glass-border);
    animation: slideUp 0.3s cubic-bezier(0.16, 1, 0.3, 1);
    position: relative;
}
@media(min-width: 768px) { .modal-box { border-radius: 20px; border: 1px solid var(--glass-border); animation: zoomIn 0.2s ease-out; } }

@keyframes slideUp { from { transform: translateY(100%); } to { transform: translateY(0); } }
@keyframes zoomIn { from { transform: scale(0.95); opacity: 0; } to { transform: scale(1); opacity: 1; } }

.modal-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px; }
.modal-title { font-size: 18px; font-weight: bold; color: white; }
.close-btn { background: #222; border: none; width: 30px; height: 30px; border-radius: 50%; color: #fff; font-weight: bold; cursor: pointer; }

/* ================= CART STYLES ================= */
.cart-empty { text-align: center; padding: 40px 0; color: var(--text-muted); }
.cart-empty svg { width: 50px; height: 50px; stroke: #333; margin-bottom: 10px; }
.cart-item { display: flex; justify-content: space-between; align-items: center; background: rgba(255,255,255,0.05); padding: 10px; border-radius: 8px; margin-bottom: 10px; }
.cart-total { display: flex; justify-content: space-between; font-size: 18px; font-weight: bold; margin-top: 20px; border-top: 1px solid #333; padding-top: 15px; color: var(--primary); }

/* ================= PAYMENT STYLES ================= */
.payment-method-btn {
    width: 100%;
    display: flex; align-items: center; justify-content: space-between;
    background: #1a1a1a;
    border: 1px solid #333;
    padding: 15px;
    border-radius: 12px;
    color: white;
    cursor: pointer;
    margin-bottom: 10px;
    transition: 0.2s;
}
.payment-method-btn.selected { border-color: #00bfa5; background: rgba(0, 191, 165, 0.1); }
.payment-left { display: flex; align-items: center; gap: 10px; }
.pix-icon { width: 24px; height: 24px; fill: #00bfa5; } /* PIX Green */

.qr-container { text-align: center; margin-top: 20px; }
.qr-code-box {
    background: white; padding: 10px; border-radius: 10px;
    width: 200px; height: 200px; margin: 0 auto 15px auto;
    display: flex; align-items: center; justify-content: center;
}
.copy-box {
    background: #222; border: 1px dashed #555; padding: 10px; border-radius: 8px;
    font-family: monospace; font-size: 12px; color: #aaa; word-break: break-all; margin-bottom: 10px;
}
.btn-action { width: 100%; padding: 14px; border-radius: 12px; border: none; font-weight: bold; cursor: pointer; font-size: 16px; margin-top: 10px; }
.btn-primary { background: var(--primary); color: white; }
.btn-secondary { background: #333; color: white; }
.btn-copy { background: #00bfa5; color: #000; }

/* ================= PRODUCT DETAIL PAGE ================= */
#productPage { padding-bottom: 100px; }
.detail-img { width: 100%; border-radius: 16px; margin-bottom: 20px; box-shadow: 0 10px 30px rgba(0,0,0,0.5); }
.detail-title { font-size: 24px; font-weight: 800; margin-bottom: 10px; line-height: 1.2; }
.detail-price { font-size: 28px; color: var(--primary); font-weight: 900; margin-bottom: 20px; }
.detail-desc { color: #ccc; line-height: 1.6; font-size: 14px; background: #111; padding: 15px; border-radius: 12px; margin-bottom: 20px; }
.detail-actions {
    position: fixed; bottom: 0; left: 0; width: 100%;
    background: #111; padding: 15px; border-top: 1px solid #333;
    display: flex; gap: 10px; z-index: 90;
}
.detail-actions button { flex: 1; padding: 15px; border-radius: 12px; border: none; font-weight: bold; cursor: pointer; }
.btn-add-cart { background: #333; color: white; }
.btn-buy-now { background: var(--primary); color: white; }

/* ================= SUPPORT ICON ================= */
.support-float {
    position: fixed; bottom: 20px; right: 20px;
    width: 50px; height: 50px; background: #5865F2;
    border-radius: 50%; display: flex; align-items: center; justify-content: center;
    box-shadow: 0 5px 15px rgba(0,0,0,0.5); cursor: pointer; z-index: 90;
}
.support-float svg { width: 28px; fill: white; }

</style>
</head>
<body>

<header>
    <div class="container">
        <button class="icon-btn">
            <svg class="icon-svg" viewBox="0 0 24 24"><path d="M4 6h16M4 12h16M4 18h7"></path></svg>
        </button>

        <div class="logo" onclick="showHome()">DRAGON<span>STORE</span></div>

        <div class="nav-icons">
            <button class="icon-btn" onclick="openAuth()">
                <svg class="icon-svg" viewBox="0 0 24 24"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path><circle cx="12" cy="7" r="4"></circle></svg>
            </button>
            <button class="icon-btn" onclick="openCart()">
                <svg class="icon-svg" viewBox="0 0 24 24"><path d="M9 20a1 1 0 1 0 0 2 1 1 0 0 0 0-2zm7 0a1 1 0 1 0 0 2 1 1 0 0 0 0-2zm-8-3h8a1 1 0 0 0 1-1V7H5v9a1 1 0 0 0 1 1zM4 4h16"></path></svg>
                <div class="badge" id="cartCount">0</div>
            </button>
        </div>
    </div>
</header>

<main id="mainContent">
    <section id="home" class="fade-in">
        <h3 style="margin-bottom:15px; color:#fff; font-weight:bold; border-left: 4px solid var(--primary); padding-left: 10px;">Destaques - Blox Fruits</h3>
        <div class="products-grid" id="productList">
            </div>
    </section>

    <section id="productPage" class="hidden fade-in">
        <div id="productDetailContent"></div>
    </section>
</main>

<div id="cartModal" class="modal-overlay hidden">
    <div class="modal-box">
        <div class="modal-header">
            <span class="modal-title">Seu Carrinho</span>
            <button class="close-btn" onclick="closeModal('cartModal')">✕</button>
        </div>
        <div id="cartItemsContainer">
            <div class="cart-empty">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="9" cy="21" r="1"></circle><circle cx="20" cy="21" r="1"></circle><path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"></path></svg>
                <p>Seu carrinho está vazio.</p>
            </div>
        </div>
        <div id="cartTotalSection" class="hidden">
            <div class="cart-total">
                <span>Total</span>
                <span id="cartTotalValue">R$ 0,00</span>
            </div>
            <button class="btn-action btn-primary" onclick="openPayment()">Finalizar Compra</button>
        </div>
    </div>
</div>

<div id="paymentModal" class="modal-overlay hidden">
    <div class="modal-box">
        <div class="modal-header">
            <span class="modal-title">Pagamento</span>
            <button class="close-btn" onclick="closeModal('paymentModal')">✕</button>
        </div>
        
        <div id="paymentStep1">
            <p style="color:#aaa; margin-bottom:15px; font-size:14px;">Selecione a forma de pagamento:</p>
            
            <div class="payment-method-btn selected" onclick="selectPayment('pix')">
                <div class="payment-left">
                    <svg class="pix-icon" viewBox="0 0 24 24">
                        <path d="M16.19 2H7.81C4.17 2 2 4.17 2 7.81v8.37C2 19.83 4.17 22 7.81 22h8.37c3.64 0 5.81-2.17 5.81-5.81V7.81C22 4.17 19.83 2 16.19 2zm-2.07 12.38-2.6 2.62c-.37.38-1.04.38-1.41 0l-2.6-2.62c-.22-.22-.28-.56-.16-.85s.42-.51.73-.55l1.69-.21-1.2-1.66c-.19-.27-.18-.63.02-.89.21-.26.57-.36.87-.24l1.96.8 1.96-.8c.3-.12.66-.02.87.24.2.26.21.62.02.89l-1.2 1.66 1.69.21c.31.04.59.26.71.55s.06.63-.16.85z"/>
                    </svg>
                    <span>PIX (Aprovação Imediata)</span>
                </div>
                <div style="width:16px; height:16px; border:4px solid #00bfa5; border-radius:50%;"></div>
            </div>

            <button class="btn-action btn-primary" onclick="goToQrCode()">Continuar para Pagamento</button>
        </div>

        <div id="paymentStep2" class="hidden">
            <div class="qr-container">
                <p style="font-size:14px; color:#aaa;">Escaneie o QR Code ou copie a chave:</p>
                <div class="qr-code-box">
                    <img src= "https://cdn.discordapp.com/attachments/1461806796598542377/1467278459343732908/image0.jpg?ex=697fcd0d&is=697e7b8d&hm=4052d9065828bc4865966345157bd2770e2b234f8393fa48ca35e48a1a8537d9&" style="width:100%; height:100%; opacity:0.9;">
                </div>
                <p style="color:var(--primary); font-weight:bold; margin-bottom:5px;">Tempo restante: <span id="timer">10:00</span></p>
                
                <div class="copy-box">edc9371b-2ba9-4c20-b5ce-0877d172d4fd</div>
                
                <button class="btn-action btn-copy" onclick="copyPix()">
                    <svg style="width:16px; vertical-align:middle; margin-right:5px;" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="9" y="9" width="13" height="13" rx="2" ry="2"></rect><path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"></path></svg>
                    Copiar Código PIX
                </button>
                <button class="btn-action btn-secondary" style="margin-top:10px" onclick="backToStep1()">Voltar</button>
            </div>
        </div>
    </div>
</div>

<div id="authModal" class="modal-overlay hidden">
    <div class="modal-box">
        <div class="modal-header">
            <span class="modal-title">Acessar Conta</span>
            <button class="close-btn" onclick="closeModal('authModal')">✕</button>
        </div>
        <input type="email" placeholder="Seu email" style="width:100%; padding:14px; background:#222; border:1px solid #333; color:white; border-radius:10px; margin-bottom:10px; outline:none;">
        <input type="password" placeholder="Sua senha" style="width:100%; padding:14px; background:#222; border:1px solid #333; color:white; border-radius:10px; margin-bottom:20px; outline:none;">
        
        <button class="btn-action btn-primary" onclick="alert('Login feitoa com sucesso!'); closeModal('authModal')">Entrar</button>
        
        <div style="text-align:center; margin-top:15px; font-size:12px; color:#666;">
            Ou entre com Discord
        </div>
    </div>
</div>

<div class="support-float" onclick="window.open('https://discord.gg/MtpJM7DK6a','_blank')">
    <svg viewBox="0 0 24 24"><path d="M20.317 4.37a19.791 19.791 0 0 0-4.885-1.515.074.074 0 0 0-.079.037c-.21.375-.444.864-.608 1.25a18.27 18.27 0 0 0-5.487 0 12.64 12.64 0 0 0-.617-1.25.077.077 0 0 0-.079-.037A19.736 19.736 0 0 0 3.677 4.37a.07.07 0 0 0-.032.027C.533 9.046-.32 13.58.099 18.057a.082.082 0 0 0 .031.057 19.9 19.9 0 0 0 5.993 3.03.078.078 0 0 0 .084-.028 14.09 14.09 0 0 0 1.226-1.994.076.076 0 0 0-.041-.106 13.107 13.107 0 0 1-1.872-.892.077.077 0 0 1-.008-.128 10.2 10.2 0 0 0 .372-.292.074.074 0 0 1 .077-.01c3.928 1.793 8.18 1.793 12.062 0a.074.074 0 0 1 .078.01c.12.098.246.198.373.292a.077.077 0 0 1-.006.127 12.299 12.299 0 0 1-1.873.892.077.077 0 0 0-.041.107c.36.698.772 1.362 1.225 1.993a.076.076 0 0 0 .084.028 19.839 19.839 0 0 0 6.002-3.03.077.077 0 0 0 .032-.054c.5-5.177-.838-9.674-3.549-13.66a.061.061 0 0 0-.031-.03zM8.02 15.33c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.956-2.419 2.157-2.419 1.21 0 2.176 1.086 2.157 2.419 0 1.334-.956 2.419-2.157 2.419zm7.975 0c-1.183 0-2.157-1.085-2.157-2.419 0-1.333.955-2.419 2.157-2.419 1.21 0 2.176 1.086 2.157 2.419 0 1.334-.946 2.419-2.157 2.419z"/></svg>
</div>

<script>
/* ================= DATA ================= */
// Mantive os produtos mas adicionei mais estilo
const products = [
    { id: 1, name: "FRUTA MÍTICA RANDOM 🍎", price: 8.40, oldPrice: 12.00, img: "https://ibb.co/ks84pFP8", desc: "Receba uma fruta mítica aleatória no seu inventário. Entrega automática e imediata." },
    { id: 2, name: "CONTA V4 ", price: 5.40, oldPrice: 9.90, img: "https://ibb.co/ZRSJDTtm", desc: "Conta com Godhuman garantido, frutas aleatórias e level random." },
    { id: 3, name: "DRAGON WEST 🐉", price: 179.40, oldPrice: 200.00, img: "https://pbs.twimg.com/media/F3u-jA6WcAA0q4n.jpg", desc: "Conta rara com Dragon equipada e itens exclusivos." },
    { id: 4, name: "KITSUNE FULL 🦊", price: 164.40, oldPrice: 190.00, img: "https://i.ytimg.com/vi/qYJg6lYt9bU/maxresdefault.jpg", desc: "Melhor conta para PVP com Kitsune full mastery." },
    { id: 5, name: "CONTA TIGER 🐯", price: 16.40, oldPrice: 25.00, img: "https://ibb.co/1Yg3ZpSW", desc: "Montaria exclusiva Tiger + Itens aleatórios." },
    { id: 6, name: "CONTA PARA PVP", price: 45.90, oldPrice: 60.00, img: "https://ibb.co/bjrM5WbH", desc: "Conta otima pra quem faz PVP e caça bounty " }
];

let cart = [];
let currentProduct = null;

/* ================= RENDER FUNCTIONS ================= */
function renderProducts() {
    const list = document.getElementById("productList");
    list.innerHTML = "";
    products.forEach(p => {
        list.innerHTML += `
        <div class="product-card" onclick="openProduct(${p.id})">
            <div class="card-img-wrapper">
                <img src="${p.img}" alt="${p.name}" onerror="this.src='https://via.placeholder.com/150/000000/FFFFFF/?text=No+Image'">
            </div>
            <div class="card-info">
                <div>
                    <div class="card-title">${p.name}</div>
                    <span class="card-pix-tag">À vista no Pix</span>
                    <div class="card-price">R$ ${p.price.toFixed(2).replace('.',',')}</div>
                </div>
                <button class="btn-buy">
                    <svg style="width:14px;fill:currentColor" viewBox="0 0 24 24"><path d="M7 18c-1.1 0-1.99.9-1.99 2S5.9 22 7 22s2-.9 2-2-.9-2-2-2zM1 2v2h2l3.6 7.59-1.35 2.45c-.16.28-.25.61-.25.96 0 1.1.9 2 2 2h12v-2H7.42c-.14 0-.25-.11-.25-.25l.03-.12.9-1.63h7.45c.75 0 1.41-.41 1.75-1.03l3.58-6.49c.08-.14.12-.31.12-.48 0-.55-.45-1-1-1H5.21l-.94-2H1zm16 16c-1.1 0-1.99.9-1.99 2s.89 2 1.99 2 2-.9 2-2-.9-2-2-2z"/></svg>
                    COMPRAR
                </button>
            </div>
        </div>`;
    });
}

/* ================= NAVIGATION ================= */
function showHome() {
    document.getElementById("home").classList.remove("hidden");
    document.getElementById("productPage").classList.add("hidden");
    window.scrollTo(0,0);
}

function openProduct(id) {
    currentProduct = products.find(p => p.id === id);
    document.getElementById("home").classList.add("hidden");
    const page = document.getElementById("productPage");
    page.classList.remove("hidden");
    
    document.getElementById("productDetailContent").innerHTML = `
        <img src="${currentProduct.img}" class="detail-img">
        <h1 class="detail-title">${currentProduct.name}</h1>
        <div class="detail-price">R$ ${currentProduct.price.toFixed(2).replace('.',',')}</div>
        <div class="detail-desc">
            <strong>📦 Entrega Imediata</strong><br>
            Receba o seu pacote imediatamente após o pagamento.<br><br>
            <strong>🛡️ Segurança Total</strong><br>
            Seus dados são criptografados.<br><br>
            ${currentProduct.desc}
        </div>
        
        <div class="detail-actions">
            <button class="btn-add-cart" onclick="addToCart(${currentProduct.id})">Adicionar</button>
            <button class="btn-buy-now" onclick="buyNow(${currentProduct.id})">Comprar Agora</button>
        </div>
    `;
    window.scrollTo(0,0);
}

/* ================= CART LOGIC ================= */
function addToCart(id) {
    const item = products.find(p => p.id === id);
    cart.push(item);
    updateCartIcon();
    alert("Adicionado ao carrinho!");
}

function buyNow(id) {
    const item = products.find(p => p.id === id);
    cart.push(item); // Adiciona e vai pro checkout
    updateCartIcon();
    openCart();
}

function updateCartIcon() {
    document.getElementById("cartCount").innerText = cart.length;
}

function openCart() {
    const container = document.getElementById("cartItemsContainer");
    const totalSection = document.getElementById("cartTotalSection");
    
    document.getElementById("cartModal").classList.remove("hidden");
    
    if(cart.length === 0) {
        container.innerHTML = `
            <div class="cart-empty">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="9" cy="21" r="1"></circle><circle cx="20" cy="21" r="1"></circle><path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"></path></svg>
                <p>Seu carrinho está vazio.</p>
                <button class="btn-action btn-secondary" style="margin-top:15px; width:auto; padding:10px 20px;" onclick="closeModal('cartModal')">Ver produtos</button>
            </div>`;
        totalSection.classList.add("hidden");
    } else {
        let html = "";
        let total = 0;
        cart.forEach((item, index) => {
            total += item.price;
            html += `
            <div class="cart-item">
                <div style="display:flex; align-items:center; gap:10px;">
                    <img src="${item.img}" style="width:40px; height:40px; border-radius:6px; object-fit:cover;">
                    <div>
                        <div style="font-size:14px; font-weight:bold; color:white;">${item.name.substring(0,15)}...</div>
                        <div style="font-size:12px; color:#aaa;">R$ ${item.price.toFixed(2).replace('.',',')}</div>
                    </div>
                </div>
                <button onclick="removeItem(${index})" style="background:none; border:none; color:#ff4444; font-weight:bold;">✕</button>
            </div>`;
        });
        container.innerHTML = html;
        document.getElementById("cartTotalValue").innerText = "R$ " + total.toFixed(2).replace('.',',');
        totalSection.classList.remove("hidden");
    }
}

function removeItem(index) {
    cart.splice(index, 1);
    updateCartIcon();
    openCart(); // Re-render
}

/* ================= MODAL GENERIC ================= */
function closeModal(id) {
    document.getElementById(id).classList.add("hidden");
    if(id === 'paymentModal') resetPayment();
}
function openAuth() { document.getElementById("authModal").classList.remove("hidden"); }

/* ================= PAYMENT LOGIC ================= */
let timerInterval;

function openPayment() {
    document.getElementById("cartModal").classList.add("hidden");
    document.getElementById("paymentModal").classList.remove("hidden");
}

function selectPayment(method) {
    // Only PIX for now, but logical structure for future expansion
    document.querySelectorAll('.payment-method-btn').forEach(b => b.classList.remove('selected'));
    event.currentTarget.classList.add('selected');
}

function goToQrCode() {
    document.getElementById("paymentStep1").classList.add("hidden");
    document.getElementById("paymentStep2").classList.remove("hidden");
    startTimer();
}

function backToStep1() {
    clearInterval(timerInterval);
    document.getElementById("paymentStep2").classList.add("hidden");
    document.getElementById("paymentStep1").classList.remove("hidden");
}

function resetPayment() {
    backToStep1();
}

function startTimer() {
    let time = 600; // 5 minutes
    const display = document.getElementById("timer");
    clearInterval(timerInterval);
    timerInterval = setInterval(() => {
        let m = Math.floor(time / 60);
        let s = time % 60;
        display.innerText = `${m}:${s < 5  ? '0' : ''}${s}`;
        time--;
        if (time < 0) clearInterval(timerInterval);
    }, 1000);
}

function copyPix() {
    navigator.clipboard.writeText("edc9371b-2ba9-4c20-b5ce-0877d172d4fd");
    alert("Código PIX copiado!");
}

// Inicializar
renderProducts();

// Fechar modal ao clicar fora (opcional)
document.querySelectorAll('.modal-overlay').forEach(overlay => {
    overlay.addEventListener('click', function(e) {
        if(e.target === this) closeModal(this.id);
    });
});

</script>
</body>
</html>
