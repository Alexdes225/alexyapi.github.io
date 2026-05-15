# alexyapi.github.io
index.html
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>EduPro CI — Marketplace</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
<style>
:root {
  --green:#0A7C52;--green-light:#12A36C;--green-pale:#E8F5EE;--green-dark:#064D33;
  --gold:#C8870A;--gold-light:#F5C842;--purple:#7B3FB8;--blue:#1565C0;--red:#B53A1A;
  --dark:#0D0D0D;--dark2:#1A1A1A;--dark3:#252525;--dark4:#2E2E2E;
  --white:#FAFAF7;--gray:#E8E6DF;--gray2:#C5C2BA;--text:#1A1A1A;--muted:#6B6860;--wa:#25D366;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{font-family:'DM Sans',sans-serif;background:var(--dark);color:var(--white);min-height:100vh;overflow-x:hidden}

/* NAV */
.nav{position:sticky;top:0;z-index:200;background:rgba(13,13,13,0.95);border-bottom:1px solid rgba(255,255,255,0.06);backdrop-filter:blur(12px);display:flex;align-items:center;justify-content:space-between;padding:0 20px;height:60px}
.nav-logo{font-family:'Syne',sans-serif;font-size:18px;font-weight:800;color:var(--white);cursor:pointer;display:flex;align-items:center;gap:8px}
.nav-logo span{color:var(--green-light)}
.nav-tabs{display:flex;gap:4px}
.nav-tab{background:none;border:none;color:var(--gray2);font-family:'DM Sans',sans-serif;font-size:13px;font-weight:500;padding:6px 14px;border-radius:8px;cursor:pointer;transition:all .2s;white-space:nowrap}
.nav-tab:hover{background:var(--dark3);color:var(--white)}
.nav-tab.active{background:var(--green);color:#fff}
.nav-sell-btn{background:linear-gradient(135deg,var(--gold),var(--gold-light));color:var(--dark);border:none;font-family:'Syne',sans-serif;font-size:12px;font-weight:700;padding:7px 14px;border-radius:8px;cursor:pointer;transition:all .2s;letter-spacing:.04em;white-space:nowrap}
.nav-sell-btn:hover{transform:translateY(-1px);box-shadow:0 4px 16px rgba(200,135,10,.4)}

/* PAGES */
.page{display:none}
.page.active{display:block}

/* HERO */
.hero{position:relative;padding:70px 20px 90px;text-align:center;overflow:hidden}
.hero::before{content:'';position:absolute;inset:0;background:radial-gradient(ellipse 80% 60% at 50% 0%,rgba(10,124,82,.25) 0%,transparent 70%);pointer-events:none}
.hero-badge{display:inline-flex;align-items:center;gap:8px;background:rgba(10,124,82,.15);border:1px solid rgba(10,124,82,.4);color:#4CD99A;font-size:12px;font-weight:500;letter-spacing:.12em;text-transform:uppercase;padding:6px 16px;border-radius:100px;margin-bottom:28px}
.hero-badge::before{content:'●';font-size:8px;animation:blink 2s infinite}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.3}}
.hero h1{font-family:'Syne',sans-serif;font-size:clamp(30px,7vw,62px);font-weight:800;line-height:1.05;letter-spacing:-.02em;margin-bottom:20px}
.hero h1 span{color:var(--green-light)}
.hero-sub{font-size:clamp(14px,2.5vw,18px);color:var(--gray2);line-height:1.7;max-width:580px;margin:0 auto 40px;font-weight:300}
.hero-stats{display:flex;justify-content:center;gap:40px;flex-wrap:wrap;margin-bottom:32px}
.stat{text-align:center}
.stat-n{font-family:'Syne',sans-serif;font-size:28px;font-weight:800;color:var(--green-light)}
.stat-l{font-size:12px;color:var(--gray2);margin-top:2px}
.hero-cta-row{display:flex;gap:12px;justify-content:center;flex-wrap:wrap}
.btn-primary{background:var(--green);color:#fff;border:none;font-family:'Syne',sans-serif;font-size:15px;font-weight:700;padding:14px 28px;border-radius:12px;cursor:pointer;transition:all .2s}
.btn-primary:hover{background:var(--green-light);transform:translateY(-2px);box-shadow:0 8px 24px rgba(10,124,82,.35)}
.btn-secondary{background:transparent;color:var(--white);border:1.5px solid rgba(255,255,255,.2);font-family:'Syne',sans-serif;font-size:15px;font-weight:600;padding:14px 28px;border-radius:12px;cursor:pointer;transition:all .2s}
.btn-secondary:hover{border-color:rgba(255,255,255,.5);background:rgba(255,255,255,.05)}

/* SECTION */
.section{padding:56px 20px;max-width:1000px;margin:0 auto}
.section-label{font-size:11px;font-weight:600;letter-spacing:.16em;text-transform:uppercase;color:var(--green-light);margin-bottom:10px}
.section-title{font-family:'Syne',sans-serif;font-size:clamp(20px,4vw,30px);font-weight:700;margin-bottom:10px;line-height:1.2}
.section-sub{font-size:14px;color:var(--gray2);margin-bottom:32px}

/* FILTRES */
.filter-bar{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:28px}
.filter-btn{background:var(--dark3);border:1.5px solid rgba(255,255,255,.07);color:var(--gray2);font-family:'DM Sans',sans-serif;font-size:13px;font-weight:500;padding:7px 16px;border-radius:100px;cursor:pointer;transition:all .2s}
.filter-btn:hover{border-color:rgba(255,255,255,.2);color:var(--white)}
.filter-btn.active{background:var(--green);border-color:var(--green);color:#fff}

/* PRODUITS */
.products-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:16px}
.product-card{background:var(--dark2);border:1.5px solid var(--dark3);border-radius:16px;overflow:hidden;cursor:pointer;transition:all .25s;position:relative}
.product-card:hover{border-color:rgba(255,255,255,.12);transform:translateY(-3px);box-shadow:0 12px 32px rgba(0,0,0,.4)}
.product-thumb{height:140px;display:flex;align-items:center;justify-content:center;font-size:52px;position:relative}
.product-badge-type{position:absolute;top:10px;left:10px;font-size:10px;font-weight:700;letter-spacing:.08em;text-transform:uppercase;padding:3px 8px;border-radius:4px;background:rgba(0,0,0,.5);backdrop-filter:blur(4px)}
.product-body{padding:18px}
.product-seller{font-size:11px;color:var(--gray2);margin-bottom:6px;display:flex;align-items:center;gap:5px}
.seller-dot{width:6px;height:6px;border-radius:50%;background:var(--green-light);flex-shrink:0}
.product-title{font-family:'Syne',sans-serif;font-size:14px;font-weight:700;line-height:1.3;margin-bottom:8px}
.product-desc{font-size:12px;color:var(--gray2);line-height:1.6;margin-bottom:14px}
.product-footer{display:flex;align-items:center;justify-content:space-between}
.product-price{font-family:'Syne',sans-serif;font-size:17px;font-weight:800;color:var(--white)}
.product-price small{font-size:11px;color:var(--gray2);font-family:'DM Sans',sans-serif;font-weight:400}
.add-to-cart-btn{background:var(--green);color:#fff;border:none;font-size:12px;font-weight:600;font-family:'DM Sans',sans-serif;padding:7px 14px;border-radius:8px;cursor:pointer;transition:all .2s}
.add-to-cart-btn:hover{background:var(--green-light)}
.product-card.in-cart .add-to-cart-btn{background:var(--dark4);color:var(--green-light)}

/* VENDOR */
.vendor-hero{background:linear-gradient(135deg,rgba(10,124,82,.15) 0%,rgba(200,135,10,.08) 100%);border:1px solid rgba(10,124,82,.3);border-radius:20px;padding:36px 28px;margin-bottom:32px;text-align:center}
.vendor-hero h2{font-family:'Syne',sans-serif;font-size:clamp(22px,4vw,32px);font-weight:800;margin-bottom:10px}
.vendor-hero p{color:var(--gray2);font-size:15px;max-width:480px;margin:0 auto 24px;line-height:1.6}
.vendor-steps{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:16px;margin-bottom:28px}
.vendor-step{background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.07);border-radius:14px;padding:20px;text-align:center}
.vendor-step-num{width:36px;height:36px;border-radius:50%;background:var(--green);display:flex;align-items:center;justify-content:center;font-family:'Syne',sans-serif;font-weight:800;font-size:16px;margin:0 auto 12px}
.vendor-step h4{font-family:'Syne',sans-serif;font-size:14px;font-weight:700;margin-bottom:6px}
.vendor-step p{font-size:12px;color:var(--gray2);line-height:1.5}
.commission-badge{display:inline-flex;align-items:center;gap:8px;background:rgba(200,135,10,.15);border:1px solid rgba(200,135,10,.4);color:var(--gold-light);font-size:13px;font-weight:600;padding:8px 16px;border-radius:8px;margin-bottom:20px}
.vendor-form-card{background:var(--dark2);border:1px solid var(--dark3);border-radius:20px;padding:32px;margin-bottom:20px}
.vendor-form-title{font-family:'Syne',sans-serif;font-size:17px;font-weight:700;margin-bottom:20px;display:flex;align-items:center;gap:10px}
.step-circle{width:28px;height:28px;border-radius:50%;background:var(--green);display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:700;flex-shrink:0}
.form-grid{display:grid;grid-template-columns:1fr 1fr;gap:16px}
@media(max-width:600px){.form-grid{grid-template-columns:1fr}}
.form-group{display:flex;flex-direction:column;gap:6px}
.form-group.full{grid-column:1/-1}
label{font-size:13px;font-weight:500;color:var(--gray2)}
label span{color:#FF6B6B}
input,select,textarea{background:var(--dark3);border:1.5px solid rgba(255,255,255,.08);border-radius:10px;padding:12px 14px;font-size:14px;color:var(--white);font-family:'DM Sans',sans-serif;transition:border-color .2s;width:100%;appearance:none;-webkit-appearance:none}
input:focus,select:focus,textarea:focus{outline:none;border-color:var(--green-light)}
input::placeholder,textarea::placeholder{color:var(--muted)}
textarea{resize:vertical;min-height:90px}
select{background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath fill='%23C5C2BA' d='M6 8L0 0h12z'/%3E%3C/svg%3E");background-repeat:no-repeat;background-position:right 14px center;padding-right:36px;cursor:pointer}
select option{background:#1A1A1A;color:var(--white)}
.error-msg{font-size:12px;color:#FF6B6B;margin-top:4px;display:none}
input.err,select.err,textarea.err{border-color:#FF6B6B!important}
.category-selector{display:grid;grid-template-columns:repeat(auto-fill,minmax(140px,1fr));gap:10px}
.cat-option{background:var(--dark3);border:1.5px solid rgba(255,255,255,.07);border-radius:12px;padding:14px 12px;cursor:pointer;transition:all .2s;text-align:center;user-select:none}
.cat-option:hover{border-color:rgba(255,255,255,.2)}
.cat-option.selected{border-color:var(--green-light);background:rgba(10,124,82,.1)}
.cat-icon{font-size:26px;margin-bottom:6px}
.cat-label{font-size:12px;font-weight:600;line-height:1.3}
.payment-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:12px}
@media(max-width:480px){.payment-grid{grid-template-columns:1fr}}
.payment-option{background:var(--dark3);border:1.5px solid rgba(255,255,255,.08);border-radius:12px;padding:14px;cursor:pointer;transition:all .2s;display:flex;align-items:center;gap:12px;user-select:none}
.payment-option:hover{border-color:rgba(255,255,255,.2)}
.payment-option.selected{border-color:var(--green-light);background:rgba(10,124,82,.1)}
.pay-icon{font-size:22px;flex-shrink:0}
.pay-name{font-size:13px;font-weight:600}
.pay-desc{font-size:11px;color:var(--gray2);margin-top:2px}
.pay-radio{width:16px;height:16px;border-radius:50%;border:2px solid rgba(255,255,255,.2);margin-left:auto;flex-shrink:0;background:transparent;transition:all .2s}
.payment-option.selected .pay-radio{background:var(--green-light);border-color:var(--green-light)}
.submit-btn{width:100%;background:var(--green);color:#fff;border:none;border-radius:14px;padding:17px 24px;font-family:'Syne',sans-serif;font-size:16px;font-weight:700;cursor:pointer;transition:all .2s;display:flex;align-items:center;justify-content:center;gap:10px}
.submit-btn:hover{background:var(--green-light);transform:translateY(-2px);box-shadow:0 8px 24px rgba(10,124,82,.35)}
.garanties{display:flex;flex-wrap:wrap;gap:12px;justify-content:center;margin-top:20px}
.garantie-item{display:flex;align-items:center;gap:6px;font-size:12px;color:var(--gray2)}
.garantie-icon{color:var(--green-light)}

/* PANIER */
.cart-bar{position:fixed;bottom:0;left:0;right:0;z-index:150;background:rgba(26,26,26,.97);border-top:1px solid rgba(10,124,82,.3);backdrop-filter:blur(10px);padding:12px 20px;display:flex;align-items:center;justify-content:space-between;gap:12px;transform:translateY(100%);transition:transform .3s ease}
.cart-bar.show{transform:translateY(0)}
.cart-info{flex:1}
.cart-count{font-size:11px;color:var(--gray2);margin-bottom:2px}
.cart-total{font-family:'Syne',sans-serif;font-size:18px;font-weight:800;color:var(--green-light)}
.cart-btn{background:var(--green);color:#fff;border:none;font-family:'Syne',sans-serif;font-size:13px;font-weight:700;padding:10px 20px;border-radius:10px;cursor:pointer;transition:background .2s;white-space:nowrap}
.cart-btn:hover{background:var(--green-light)}

/* MODALS */
.modal-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.85);z-index:300;align-items:center;justify-content:center;padding:20px}
.modal-overlay.show{display:flex}
.modal{background:var(--dark2);border:1px solid rgba(10,124,82,.4);border-radius:20px;padding:32px 26px;max-width:500px;width:100%;max-height:90vh;overflow-y:auto;animation:slideUp .3s ease}
@keyframes slideUp{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)}}
.modal-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:24px}
.modal-title{font-family:'Syne',sans-serif;font-size:20px;font-weight:800}
.modal-close-btn{background:var(--dark3);border:none;color:var(--gray2);width:32px;height:32px;border-radius:50%;cursor:pointer;font-size:18px;display:flex;align-items:center;justify-content:center;transition:all .2s}
.modal-close-btn:hover{background:var(--dark4);color:var(--white)}
.cart-item{display:flex;align-items:center;gap:12px;padding:12px 0;border-bottom:1px solid rgba(255,255,255,.05)}
.cart-item-icon{font-size:28px;width:44px;height:44px;background:var(--dark3);border-radius:10px;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.cart-item-info{flex:1}
.cart-item-name{font-size:13px;font-weight:600;line-height:1.3}
.cart-item-seller{font-size:11px;color:var(--gray2);margin-top:2px}
.cart-item-price{font-family:'Syne',sans-serif;font-size:15px;font-weight:800;white-space:nowrap}
.remove-item-btn{background:none;border:none;color:var(--muted);cursor:pointer;font-size:16px;padding:4px;transition:color .2s}
.remove-item-btn:hover{color:#FF6B6B}
.cart-empty{text-align:center;padding:32px 0;color:var(--muted);font-size:14px}
.cart-total-row{display:flex;justify-content:space-between;align-items:baseline;padding:16px 0;border-top:1.5px solid rgba(255,255,255,.1);margin-top:8px}
.cart-total-label{font-size:14px;font-weight:600;color:var(--gray2)}
.cart-total-amount{font-family:'Syne',sans-serif;font-size:26px;font-weight:800;color:var(--green-light)}
.cart-checkout-btn{width:100%;background:var(--wa);color:#fff;border:none;font-family:'Syne',sans-serif;font-size:15px;font-weight:700;padding:15px 24px;border-radius:12px;cursor:pointer;transition:all .2s;display:flex;align-items:center;justify-content:center;gap:10px;margin-top:16px}
.cart-checkout-btn:hover{background:#1ebe5d}
.success-modal .modal-body{text-align:center;padding:16px 0}
.success-icon{font-size:60px;margin-bottom:16px}
.success-title{font-family:'Syne',sans-serif;font-size:22px;font-weight:800;margin-bottom:10px}
.success-text{font-size:14px;color:var(--gray2);line-height:1.7;margin-bottom:24px}
.success-steps{background:var(--dark3);border-radius:12px;padding:18px;text-align:left;margin-bottom:20px}
.success-step{display:flex;gap:10px;align-items:flex-start;margin-bottom:12px;font-size:13px;line-height:1.5;color:var(--gray)}
.success-step:last-child{margin-bottom:0}
.ss-num{width:20px;height:20px;background:var(--green);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700;flex-shrink:0;margin-top:1px}
.wa-btn{display:flex;align-items:center;justify-content:center;gap:10px;background:var(--wa);color:#fff;font-family:'Syne',sans-serif;font-size:14px;font-weight:700;padding:13px 24px;border-radius:12px;text-decoration:none;cursor:pointer;border:none;width:100%;margin-bottom:10px;transition:all .2s}
.wa-btn:hover{background:#1ebe5d}
.modal-back-btn{font-size:13px;cursor:pointer;background:none;border:none;color:var(--gray2);text-decoration:underline;font-family:'DM Sans',sans-serif}
.modal-back-btn:hover{color:var(--white)}

/* ══════════════════════════════════
   ESPACE ADMIN
══════════════════════════════════ */

/* LOGIN ADMIN */
.admin-login-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.97);z-index:500;align-items:center;justify-content:center;padding:20px}
.admin-login-overlay.show{display:flex}
.admin-login-box{background:var(--dark2);border:1.5px solid rgba(10,124,82,.5);border-radius:24px;padding:40px 32px;max-width:400px;width:100%;text-align:center;animation:slideUp .3s ease}
.admin-login-logo{font-family:'Syne',sans-serif;font-size:22px;font-weight:800;color:var(--white);margin-bottom:4px}
.admin-login-logo span{color:var(--green-light)}
.admin-login-badge{font-size:11px;font-weight:600;letter-spacing:.12em;text-transform:uppercase;color:var(--gold-light);background:rgba(200,135,10,.15);border:1px solid rgba(200,135,10,.3);padding:4px 14px;border-radius:100px;display:inline-block;margin-bottom:28px}
.admin-login-title{font-family:'Syne',sans-serif;font-size:24px;font-weight:800;margin-bottom:8px}
.admin-login-sub{font-size:13px;color:var(--gray2);margin-bottom:28px;line-height:1.5}
.admin-input-wrap{position:relative;margin-bottom:14px}
.admin-input-wrap input{background:var(--dark3);border:1.5px solid rgba(255,255,255,.1);border-radius:12px;padding:13px 16px 13px 44px;font-size:15px;color:var(--white);width:100%;font-family:'DM Sans',sans-serif}
.admin-input-wrap input:focus{outline:none;border-color:var(--green-light)}
.admin-input-wrap input::placeholder{color:var(--muted)}
.admin-input-icon{position:absolute;left:14px;top:50%;transform:translateY(-50%);font-size:18px}
.admin-login-btn{width:100%;background:var(--green);color:#fff;border:none;border-radius:12px;padding:14px;font-family:'Syne',sans-serif;font-size:16px;font-weight:700;cursor:pointer;transition:all .2s;margin-top:6px}
.admin-login-btn:hover{background:var(--green-light)}
.admin-login-error{background:rgba(181,58,26,.15);border:1px solid rgba(181,58,26,.4);color:#FF8E8E;border-radius:10px;padding:10px 14px;font-size:13px;margin-top:12px;display:none}
.admin-login-error.show{display:block}
.admin-close-login{background:none;border:none;color:var(--gray2);font-size:13px;cursor:pointer;margin-top:16px;font-family:'DM Sans',sans-serif;text-decoration:underline}
.admin-close-login:hover{color:var(--white)}

/* DASHBOARD LAYOUT */
.admin-layout{display:flex;min-height:calc(100vh - 60px)}
.admin-sidebar{width:220px;background:var(--dark2);border-right:1px solid rgba(255,255,255,.06);padding:20px 0;flex-shrink:0;position:sticky;top:60px;height:calc(100vh - 60px);overflow-y:auto}
@media(max-width:700px){.admin-sidebar{width:60px}}
.admin-sidebar-logo{font-family:'Syne',sans-serif;font-size:14px;font-weight:800;color:var(--white);padding:0 20px 20px;border-bottom:1px solid rgba(255,255,255,.06);margin-bottom:12px}
@media(max-width:700px){.admin-sidebar-logo{display:none}}
.admin-sidebar-logo span{color:var(--green-light)}
.admin-nav-item{display:flex;align-items:center;gap:12px;padding:11px 20px;cursor:pointer;transition:all .2s;color:var(--gray2);font-size:13px;font-weight:500;border-left:3px solid transparent}
.admin-nav-item:hover{background:rgba(255,255,255,.04);color:var(--white)}
.admin-nav-item.active{background:rgba(10,124,82,.12);color:var(--white);border-left-color:var(--green-light)}
.admin-nav-icon{font-size:18px;flex-shrink:0}
.admin-nav-label{white-space:nowrap}
@media(max-width:700px){.admin-nav-label{display:none}}
.admin-main{flex:1;padding:28px 24px;overflow-x:hidden}
@media(max-width:600px){.admin-main{padding:16px 14px}}

/* DASHBOARD PANELS */
.admin-panel{display:none}
.admin-panel.active{display:block}
.admin-panel-title{font-family:'Syne',sans-serif;font-size:22px;font-weight:800;margin-bottom:6px}
.admin-panel-sub{font-size:13px;color:var(--gray2);margin-bottom:24px}

/* KPI CARDS */
.kpi-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(180px,1fr));gap:14px;margin-bottom:28px}
.kpi-card{background:var(--dark2);border:1.5px solid var(--dark3);border-radius:16px;padding:20px;position:relative;overflow:hidden}
.kpi-card::before{content:'';position:absolute;top:0;left:0;right:0;height:3px}
.kpi-card.kpi-green::before{background:var(--green-light)}
.kpi-card.kpi-gold::before{background:var(--gold-light)}
.kpi-card.kpi-blue::before{background:#60A5FA}
.kpi-card.kpi-purple::before{background:#A78BFA}
.kpi-card.kpi-red::before{background:#F87171}
.kpi-label{font-size:11px;color:var(--gray2);font-weight:600;letter-spacing:.08em;text-transform:uppercase;margin-bottom:10px}
.kpi-value{font-family:'Syne',sans-serif;font-size:26px;font-weight:800;line-height:1;margin-bottom:6px}
.kpi-sub{font-size:12px;color:var(--gray2)}
.kpi-icon{position:absolute;top:18px;right:18px;font-size:28px;opacity:.25}

/* TABLE ADMIN */
.admin-table-wrap{background:var(--dark2);border:1.5px solid var(--dark3);border-radius:16px;overflow:hidden;margin-bottom:24px}
.admin-table-header{padding:16px 20px;border-bottom:1px solid rgba(255,255,255,.06);display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:10px}
.admin-table-title{font-family:'Syne',sans-serif;font-size:15px;font-weight:700}
.admin-search-input{background:var(--dark3);border:1.5px solid rgba(255,255,255,.08);border-radius:8px;padding:7px 12px;font-size:13px;color:var(--white);font-family:'DM Sans',sans-serif;width:200px}
.admin-search-input:focus{outline:none;border-color:var(--green-light)}
.admin-search-input::placeholder{color:var(--muted)}
.table-scroll{overflow-x:auto}
table{width:100%;border-collapse:collapse;font-size:13px}
th{padding:11px 16px;text-align:left;font-size:11px;font-weight:700;letter-spacing:.08em;text-transform:uppercase;color:var(--gray2);border-bottom:1px solid rgba(255,255,255,.06);white-space:nowrap}
td{padding:13px 16px;border-bottom:1px solid rgba(255,255,255,.04);vertical-align:middle}
tr:last-child td{border-bottom:none}
tr:hover td{background:rgba(255,255,255,.02)}
.td-name{font-weight:600;max-width:180px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.td-badge{display:inline-flex;align-items:center;font-size:10px;font-weight:700;letter-spacing:.06em;padding:3px 10px;border-radius:4px;text-transform:uppercase}
.badge-formation{background:rgba(10,124,82,.2);color:#4CD99A}
.badge-logiciel{background:rgba(21,101,192,.2);color:#93C5FD}
.badge-fichier{background:rgba(200,135,10,.2);color:#FCD34D}
.badge-jeu{background:rgba(123,63,184,.2);color:#C4B5FD}
.badge-pending{background:rgba(200,135,10,.2);color:#FCD34D}
.badge-paid{background:rgba(10,124,82,.2);color:#4CD99A}
.badge-active{background:rgba(10,124,82,.2);color:#4CD99A}
.badge-suspended{background:rgba(181,58,26,.2);color:#FCA5A5}
.td-price{font-family:'Syne',sans-serif;font-weight:700;color:var(--white);white-space:nowrap}
.td-comm{font-family:'Syne',sans-serif;font-weight:700;color:var(--gold-light);white-space:nowrap}
.td-actions{display:flex;gap:6px;align-items:center}
.action-btn{background:var(--dark3);border:none;color:var(--gray2);font-size:12px;padding:5px 10px;border-radius:6px;cursor:pointer;transition:all .2s;font-family:'DM Sans',sans-serif;white-space:nowrap}
.action-btn:hover{background:var(--dark4);color:var(--white)}
.action-btn.danger{color:#F87171}
.action-btn.danger:hover{background:rgba(181,58,26,.2)}
.action-btn.success{color:#4CD99A}
.action-btn.success:hover{background:rgba(10,124,82,.2)}

/* FORM ADMIN */
.admin-form-card{background:var(--dark2);border:1.5px solid var(--dark3);border-radius:16px;padding:24px;margin-bottom:20px}
.admin-form-title{font-family:'Syne',sans-serif;font-size:16px;font-weight:700;margin-bottom:18px}
.admin-btn{background:var(--green);color:#fff;border:none;font-family:'Syne',sans-serif;font-size:14px;font-weight:700;padding:11px 20px;border-radius:10px;cursor:pointer;transition:all .2s}
.admin-btn:hover{background:var(--green-light)}
.admin-btn.outline{background:transparent;border:1.5px solid rgba(255,255,255,.15);color:var(--gray2)}
.admin-btn.outline:hover{border-color:rgba(255,255,255,.3);color:var(--white)}
.admin-btn.danger{background:rgba(181,58,26,.2);color:#F87171;border:1.5px solid rgba(181,58,26,.3)}
.admin-btn.danger:hover{background:rgba(181,58,26,.35)}
.admin-btn-row{display:flex;gap:10px;flex-wrap:wrap;margin-top:16px}

/* SETTINGS */
.settings-row{display:flex;align-items:center;justify-content:space-between;padding:16px 0;border-bottom:1px solid rgba(255,255,255,.05)}
.settings-row:last-child{border-bottom:none}
.settings-label{font-size:14px;font-weight:500}
.settings-desc{font-size:12px;color:var(--gray2);margin-top:3px}
.settings-value{font-family:'Syne',sans-serif;font-size:18px;font-weight:800;color:var(--gold-light)}
.toggle-wrap{display:flex;align-items:center;gap:8px}
.toggle{width:44px;height:24px;background:var(--dark3);border-radius:100px;position:relative;cursor:pointer;transition:background .2s;flex-shrink:0;border:none}
.toggle.on{background:var(--green)}
.toggle::after{content:'';position:absolute;top:3px;left:3px;width:18px;height:18px;border-radius:50%;background:#fff;transition:transform .2s}
.toggle.on::after{transform:translateX(20px)}

/* TOAST */
.toast{position:fixed;bottom:80px;left:50%;transform:translateX(-50%) translateY(20px);background:var(--dark2);border:1px solid rgba(10,124,82,.4);color:var(--white);font-size:13px;font-weight:500;padding:12px 20px;border-radius:10px;z-index:400;opacity:0;transition:all .3s;pointer-events:none;white-space:nowrap}
.toast.show{opacity:1;transform:translateX(-50%) translateY(0)}

/* CHART BARS */
.chart-wrap{background:var(--dark2);border:1.5px solid var(--dark3);border-radius:16px;padding:20px;margin-bottom:24px}
.chart-title{font-family:'Syne',sans-serif;font-size:14px;font-weight:700;margin-bottom:16px;display:flex;justify-content:space-between;align-items:center}
.chart-bars{display:flex;align-items:flex-end;gap:8px;height:120px}
.chart-bar-wrap{flex:1;display:flex;flex-direction:column;align-items:center;gap:6px}
.chart-bar{width:100%;border-radius:6px 6px 0 0;background:var(--green);transition:height .5s ease;min-height:4px}
.chart-bar-label{font-size:10px;color:var(--gray2);text-align:center}
.chart-bar-val{font-size:10px;font-weight:700;color:var(--white);text-align:center}

/* ADMIN TRIGGER (bouton caché) */
.admin-trigger{position:fixed;bottom:20px;right:20px;width:36px;height:36px;background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.06);border-radius:50%;cursor:pointer;z-index:100;transition:all .2s;display:flex;align-items:center;justify-content:center;font-size:14px}
.admin-trigger:hover{background:rgba(255,255,255,.1)}

footer{text-align:center;padding:32px 20px 120px;font-size:12px;color:var(--muted);border-top:1px solid var(--dark3);margin-top:40px}
footer a{color:var(--green-light);text-decoration:none}
.footer-logo{font-family:'Syne',sans-serif;font-size:15px;font-weight:800;color:var(--gray2);margin-bottom:8px}
.divider{border:none;border-top:1px solid var(--dark3)}
@media(max-width:500px){.nav-tab{padding:5px 9px;font-size:12px}.nav-sell-btn{font-size:11px;padding:6px 10px}}
</style>
</head>
<body>

<!-- ══════════ NAVIGATION PUBLIQUE ══════════ -->
<nav class="nav" id="publicNav">
  <div class="nav-logo" onclick="showPage('home')">Edu<span>Pro</span> CI</div>
  <div class="nav-tabs">
    <button class="nav-tab active" onclick="showPage('home')">Accueil</button>
    <button class="nav-tab" onclick="showPage('catalogue')">Catalogue</button>
    <button class="nav-tab" onclick="showPage('vendor')">Vendre</button>
  </div>
  <button class="nav-sell-btn" onclick="showPage('vendor')">💰 Vendre ici</button>
</nav>

<!-- ══════════ PAGE ACCUEIL ══════════ -->
<div class="page active" id="page-home">
  <div class="hero">
    <div class="hero-badge">Marketplace numérique #1 CI</div>
    <h1>Achetez, vendez,<br><span>réussissez ensemble.</span></h1>
    <p class="hero-sub">Formations, logiciels, fichiers et jeux PC — tout en un seul endroit. Devenez acheteur ou vendeur en quelques minutes.</p>
    <div class="hero-stats">
      <div class="stat"><div class="stat-n" id="statProduits">14</div><div class="stat-l">Produits disponibles</div></div>
      <div class="stat"><div class="stat-n" id="statVendeurs">5</div><div class="stat-l">Vendeurs actifs</div></div>
      <div class="stat"><div class="stat-n">1 000+</div><div class="stat-l">Clients satisfaits</div></div>
      <div class="stat"><div class="stat-n">24h</div><div class="stat-l">Livraison rapide</div></div>
    </div>
    <div class="hero-cta-row">
      <button class="btn-primary" onclick="showPage('catalogue')">🛒 Explorer le catalogue</button>
      <button class="btn-secondary" onclick="showPage('vendor')">💼 Devenir vendeur</button>
    </div>
  </div>
  <hr class="divider">
  <div class="section">
    <div class="section-label">Parcourir par catégorie</div>
    <h2 class="section-title">Que cherchez-vous ?</h2>
    <div style="display:grid;grid-template-columns:repeat(auto-fill,minmax(160px,1fr));gap:14px;margin-bottom:40px">
      <div onclick="filterAndGo('formation')" style="background:var(--dark2);border:1.5px solid var(--dark3);border-radius:16px;padding:20px;cursor:pointer;text-align:center;transition:all .2s" onmouseover="this.style.borderColor='rgba(255,255,255,0.15)'" onmouseout="this.style.borderColor='var(--dark3)'">
        <div style="font-size:36px;margin-bottom:10px">📚</div>
        <div style="font-family:'Syne',sans-serif;font-size:14px;font-weight:700;margin-bottom:4px">Formations</div>
        <div style="font-size:12px;color:var(--gray2)">Marketing, IA, Canva…</div>
      </div>
      <div onclick="filterAndGo('logiciel')" style="background:var(--dark2);border:1.5px solid var(--dark3);border-radius:16px;padding:20px;cursor:pointer;text-align:center;transition:all .2s" onmouseover="this.style.borderColor='rgba(255,255,255,0.15)'" onmouseout="this.style.borderColor='var(--dark3)'">
        <div style="font-size:36px;margin-bottom:10px">💻</div>
        <div style="font-family:'Syne',sans-serif;font-size:14px;font-weight:700;margin-bottom:4px">Logiciels</div>
        <div style="font-size:12px;color:var(--gray2)">Outils, apps, licences</div>
      </div>
      <div onclick="filterAndGo('fichier')" style="background:var(--dark2);border:1.5px solid var(--dark3);border-radius:16px;padding:20px;cursor:pointer;text-align:center;transition:all .2s" onmouseover="this.style.borderColor='rgba(255,255,255,0.15)'" onmouseout="this.style.borderColor='var(--dark3)'">
        <div style="font-size:36px;margin-bottom:10px">📁</div>
        <div style="font-family:'Syne',sans-serif;font-size:14px;font-weight:700;margin-bottom:4px">Fichiers</div>
        <div style="font-size:12px;color:var(--gray2)">Templates, docs, PDF</div>
      </div>
      <div onclick="filterAndGo('jeu')" style="background:var(--dark2);border:1.5px solid var(--dark3);border-radius:16px;padding:20px;cursor:pointer;text-align:center;transition:all .2s" onmouseover="this.style.borderColor='rgba(255,255,255,0.15)'" onmouseout="this.style.borderColor='var(--dark3)'">
        <div style="font-size:36px;margin-bottom:10px">🎮</div>
        <div style="font-family:'Syne',sans-serif;font-size:14px;font-weight:700;margin-bottom:4px">Jeux PC</div>
        <div style="font-size:12px;color:var(--gray2)">Jeux, DLC, clés</div>
      </div>
    </div>
    <div class="section-label">Sélection du moment</div>
    <h2 class="section-title" style="margin-bottom:24px">Produits populaires</h2>
    <div class="products-grid" id="featuredGrid"></div>
    <div style="text-align:center;margin-top:24px">
      <button class="btn-primary" onclick="showPage('catalogue')">Voir tout le catalogue →</button>
    </div>
  </div>
  <div style="background:linear-gradient(135deg,rgba(10,124,82,.12) 0%,rgba(200,135,10,.07) 100%);border-top:1px solid rgba(10,124,82,.2);border-bottom:1px solid rgba(10,124,82,.2);padding:56px 20px;margin-top:40px">
    <div style="max-width:900px;margin:0 auto;text-align:center">
      <div class="section-label">Pour les vendeurs</div>
      <h2 class="section-title">Gagnez de l'argent en vendant vos produits</h2>
      <p style="color:var(--gray2);font-size:15px;max-width:520px;margin:0 auto 36px;line-height:1.6">Formations, logiciels, fichiers ou jeux PC — publiez votre produit en 5 minutes et commencez à vendre dès aujourd'hui.</p>
      <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:16px;margin-bottom:28px;text-align:left">
        <div style="background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.08);border-radius:14px;padding:20px">
          <div style="font-size:28px;margin-bottom:10px">⚡</div>
          <div style="font-family:'Syne',sans-serif;font-size:14px;font-weight:700;margin-bottom:6px">Publication rapide</div>
          <div style="font-size:12px;color:var(--gray2);line-height:1.5">Soumettez votre produit via WhatsApp. Mise en ligne en moins de 24h.</div>
        </div>
        <div style="background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.08);border-radius:14px;padding:20px">
          <div style="font-size:28px;margin-bottom:10px">💰</div>
          <div style="font-family:'Syne',sans-serif;font-size:14px;font-weight:700;margin-bottom:6px" id="vendeurPctLabel">80% pour vous</div>
          <div style="font-size:12px;color:var(--gray2);line-height:1.5" id="vendeurPctDesc">Vous gardez 80% de chaque vente. La plateforme perçoit 20% de commission.</div>
        </div>
        <div style="background:rgba(255,255,255,.04);border:1px solid rgba(255,255,255,.08);border-radius:14px;padding:20px">
          <div style="font-size:28px;margin-bottom:10px">📲</div>
          <div style="font-family:'Syne',sans-serif;font-size:14px;font-weight:700;margin-bottom:6px">Paiement sécurisé</div>
          <div style="font-size:12px;color:var(--gray2);line-height:1.5">Orange Money, Wave, MTN MoMo. Virement automatique chaque semaine.</div>
        </div>
      </div>
      <button class="btn-primary" onclick="showPage('vendor')">Soumettre mon produit →</button>
    </div>
  </div>
</div>

<!-- ══════════ PAGE CATALOGUE ══════════ -->
<div class="page" id="page-catalogue">
  <div class="section">
    <div class="section-label">Marketplace EduPro CI</div>
    <h2 class="section-title">Catalogue des produits numériques</h2>
    <p class="section-sub">Formations, logiciels, fichiers et jeux PC. Livraison immédiate sur WhatsApp.</p>
    <div class="filter-bar" id="filterBar">
      <button class="filter-btn active" onclick="setFilter('tous',this)">Tous</button>
      <button class="filter-btn" onclick="setFilter('formation',this)">📚 Formations</button>
      <button class="filter-btn" onclick="setFilter('logiciel',this)">💻 Logiciels</button>
      <button class="filter-btn" onclick="setFilter('fichier',this)">📁 Fichiers</button>
      <button class="filter-btn" onclick="setFilter('jeu',this)">🎮 Jeux PC</button>
    </div>
    <div class="products-grid" id="catalogueGrid"></div>
  </div>
</div>

<!-- ══════════ PAGE VENDEUR ══════════ -->
<div class="page" id="page-vendor">
  <div class="section">
    <div class="vendor-hero">
      <div class="commission-badge" id="commissionBadgeVendor">💰 Vous gardez 80% de vos ventes — commission de 20% seulement</div>
      <h2>Vendez votre produit numérique ici</h2>
      <p>Formations, logiciels, fichiers Word/Excel, jeux PC... Soumettez votre produit et touchez des milliers d'acheteurs en Côte d'Ivoire.</p>
      <div class="vendor-steps">
        <div class="vendor-step"><div class="vendor-step-num">1</div><h4>Soumettez</h4><p>Remplissez le formulaire avec les infos de votre produit</p></div>
        <div class="vendor-step"><div class="vendor-step-num">2</div><h4>Validation</h4><p>Notre équipe valide et met en ligne votre produit sous 24h</p></div>
        <div class="vendor-step"><div class="vendor-step-num">3</div><h4>Vendez</h4><p>Les clients achètent, vous recevez votre part à chaque vente</p></div>
        <div class="vendor-step"><div class="vendor-step-num">4</div><h4>Livrez</h4><p>Envoyez le produit sur WhatsApp après confirmation</p></div>
      </div>
    </div>
    <div class="vendor-form-card">
      <div class="vendor-form-title"><span class="step-circle">1</span> Vos informations de vendeur</div>
      <div class="form-grid">
        <div class="form-group"><label for="v-prenom">Prénom <span>*</span></label><input type="text" id="v-prenom" placeholder="Votre prénom"><span class="error-msg" id="err-v-prenom">Champ requis (min 2 caractères)</span></div>
        <div class="form-group"><label for="v-nom">Nom <span>*</span></label><input type="text" id="v-nom" placeholder="Votre nom"><span class="error-msg" id="err-v-nom">Champ requis (min 2 caractères)</span></div>
        <div class="form-group"><label for="v-tel">Numéro WhatsApp <span>*</span></label><input type="tel" id="v-tel" placeholder="Ex: 07 XX XX XX XX"><span class="error-msg" id="err-v-tel">Numéro invalide</span></div>
        <div class="form-group"><label for="v-ville">Ville <span>*</span></label><select id="v-ville"><option value="">Sélectionnez votre ville</option><option>Abidjan — Cocody</option><option>Abidjan — Yopougon</option><option>Abidjan — Abobo</option><option>Abidjan — Adjamé</option><option>Abidjan — Autre commune</option><option>Bouaké</option><option>San-Pédro</option><option>Yamoussoukro</option><option>Korhogo</option><option>Daloa</option><option>Autre ville CI</option><option>Hors Côte d'Ivoire</option></select><span class="error-msg" id="err-v-ville">Veuillez sélectionner</span></div>
      </div>
    </div>
    <div class="vendor-form-card">
      <div class="vendor-form-title"><span class="step-circle">2</span> Votre produit à vendre</div>
      <div class="form-group" style="margin-bottom:20px">
        <label>Catégorie <span>*</span></label>
        <div class="category-selector" id="catSelector">
          <div class="cat-option" data-cat="formation" onclick="selectCat(this)"><div class="cat-icon">📚</div><div class="cat-label">Formation / Cours en ligne</div></div>
          <div class="cat-option" data-cat="logiciel" onclick="selectCat(this)"><div class="cat-icon">💻</div><div class="cat-label">Logiciel / Application</div></div>
          <div class="cat-option" data-cat="fichier" onclick="selectCat(this)"><div class="cat-icon">📁</div><div class="cat-label">Fichier numérique</div></div>
          <div class="cat-option" data-cat="jeu" onclick="selectCat(this)"><div class="cat-icon">🎮</div><div class="cat-label">Jeu PC / Clé de jeu</div></div>
        </div>
        <span class="error-msg" id="err-cat">Veuillez choisir une catégorie</span>
      </div>
      <div class="form-grid">
        <div class="form-group full"><label for="v-produit-nom">Nom du produit <span>*</span></label><input type="text" id="v-produit-nom" placeholder="Ex: Formation WhatsApp Business Avancé"><span class="error-msg" id="err-v-produit-nom">Champ requis (min 5 caractères)</span></div>
        <div class="form-group full"><label for="v-description">Description <span>*</span></label><textarea id="v-description" placeholder="Décrivez votre produit en détail..."></textarea><span class="error-msg" id="err-v-description">Description requise (min 20 caractères)</span></div>
        <div class="form-group"><label for="v-prix">Prix de vente (FCFA) <span>*</span></label><input type="number" id="v-prix" placeholder="Ex: 15000" min="500"><span class="error-msg" id="err-v-prix">Prix invalide (min 500 FCFA)</span></div>
        <div class="form-group"><label for="v-format">Format de livraison</label><select id="v-format"><option value="">Sélectionnez le format</option><option>Lien de téléchargement</option><option>Fichier PDF</option><option>Fichier ZIP / RAR</option><option>Lien vidéo / YouTube</option><option>Google Drive</option><option>Clé de licence</option><option>Autre</option></select></div>
      </div>
    </div>
    <div class="vendor-form-card">
      <div class="vendor-form-title"><span class="step-circle">3</span> Comment souhaitez-vous recevoir vos gains ?</div>
      <div class="payment-grid">
        <div class="payment-option" onclick="selectVendorPay(this,'Orange Money')"><span class="pay-icon">🟠</span><div><div class="pay-name">Orange Money</div><div class="pay-desc">Virement hebdomadaire</div></div><div class="pay-radio"></div></div>
        <div class="payment-option" onclick="selectVendorPay(this,'Wave')"><span class="pay-icon">🔵</span><div><div class="pay-name">Wave</div><div class="pay-desc">Sans frais supplémentaires</div></div><div class="pay-radio"></div></div>
        <div class="payment-option" onclick="selectVendorPay(this,'MTN MoMo')"><span class="pay-icon">🟡</span><div><div class="pay-name">MTN MoMo</div><div class="pay-desc">Paiement sécurisé</div></div><div class="pay-radio"></div></div>
        <div class="payment-option" onclick="selectVendorPay(this,'Moov Money')"><span class="pay-icon">🟢</span><div><div class="pay-name">Moov Money</div><div class="pay-desc">Disponible partout</div></div><div class="pay-radio"></div></div>
      </div>
      <span class="error-msg" id="err-vendorpay" style="margin-top:10px;display:none">Veuillez choisir un mode de réception</span>
    </div>
    <button class="submit-btn" onclick="submitVendorForm()"><span>📲</span> Envoyer ma candidature sur WhatsApp</button>
    <div class="garanties">
      <span class="garantie-item"><span class="garantie-icon">✅</span> Validation sous 24h</span>
      <span class="garantie-item"><span class="garantie-icon">💰</span> Votre part des revenus garantie</span>
      <span class="garantie-item"><span class="garantie-icon">📲</span> Accompagnement WhatsApp</span>
      <span class="garantie-item"><span class="garantie-icon">🔒</span> Zéro frais d'inscription</span>
    </div>
  </div>
</div>

<!-- ══════════ PAGE ADMIN ══════════ -->
<div class="page" id="page-admin" style="padding:0">
  <div class="admin-layout">
    <!-- SIDEBAR -->
    <aside class="admin-sidebar">
      <div class="admin-sidebar-logo">Edu<span>Pro</span> CI<br><span style="font-size:10px;color:var(--gold-light);font-weight:600;letter-spacing:.1em">ADMIN</span></div>
      <div class="admin-nav-item active" onclick="showPanel('dashboard')"><span class="admin-nav-icon">📊</span><span class="admin-nav-label">Tableau de bord</span></div>
      <div class="admin-nav-item" onclick="showPanel('commandes')"><span class="admin-nav-icon">🛒</span><span class="admin-nav-label">Commandes</span></div>
      <div class="admin-nav-item" onclick="showPanel('produits')"><span class="admin-nav-icon">📦</span><span class="admin-nav-label">Produits</span></div>
      <div class="admin-nav-item" onclick="showPanel('vendeurs')"><span class="admin-nav-icon">👥</span><span class="admin-nav-label">Vendeurs</span></div>
      <div class="admin-nav-item" onclick="showPanel('finances')"><span class="admin-nav-icon">💰</span><span class="admin-nav-label">Finances</span></div>
      <div class="admin-nav-item" onclick="showPanel('parametres')"><span class="admin-nav-icon">⚙️</span><span class="admin-nav-label">Paramètres</span></div>
      <div style="margin-top:auto;padding:16px 20px;border-top:1px solid rgba(255,255,255,.06);margin-top:20px">
        <div class="admin-nav-item" onclick="logoutAdmin()" style="color:var(--red);padding:8px 0"><span class="admin-nav-icon">🚪</span><span class="admin-nav-label" style="font-size:12px">Déconnexion</span></div>
      </div>
    </aside>

    <!-- MAIN CONTENT -->
    <main class="admin-main">

      <!-- ── DASHBOARD ── -->
      <div class="admin-panel active" id="panel-dashboard">
        <div class="admin-panel-title">Tableau de bord</div>
        <div class="admin-panel-sub" id="dashDate"></div>

        <div class="kpi-grid">
          <div class="kpi-card kpi-green">
            <div class="kpi-icon">💰</div>
            <div class="kpi-label">Revenus totaux</div>
            <div class="kpi-value" id="kpi-revenus">0</div>
            <div class="kpi-sub">FCFA encaissés</div>
          </div>
          <div class="kpi-card kpi-gold">
            <div class="kpi-icon">🏆</div>
            <div class="kpi-label">Ma commission</div>
            <div class="kpi-value" id="kpi-commission">0</div>
            <div class="kpi-sub" id="kpi-commission-sub">FCFA (20%)</div>
          </div>
          <div class="kpi-card kpi-blue">
            <div class="kpi-icon">🛒</div>
            <div class="kpi-label">Commandes</div>
            <div class="kpi-value" id="kpi-commandes">0</div>
            <div class="kpi-sub">Total reçues</div>
          </div>
          <div class="kpi-card kpi-purple">
            <div class="kpi-icon">👥</div>
            <div class="kpi-label">Vendeurs actifs</div>
            <div class="kpi-value" id="kpi-vendeurs">0</div>
            <div class="kpi-sub">Sur la plateforme</div>
          </div>
          <div class="kpi-card kpi-red">
            <div class="kpi-icon">📦</div>
            <div class="kpi-label">Produits</div>
            <div class="kpi-value" id="kpi-produits">0</div>
            <div class="kpi-sub">En ligne</div>
          </div>
        </div>

        <!-- Graphique ventes par mois -->
        <div class="chart-wrap">
          <div class="chart-title"><span>📈 Revenus mensuels (FCFA)</span><span style="font-size:12px;color:var(--gray2)">6 derniers mois</span></div>
          <div class="chart-bars" id="chartBars"></div>
        </div>

        <!-- Dernières commandes -->
        <div class="admin-table-wrap">
          <div class="admin-table-header">
            <div class="admin-table-title">🕐 Dernières commandes</div>
            <button class="action-btn" onclick="showPanel('commandes')">Voir tout →</button>
          </div>
          <div class="table-scroll">
            <table>
              <thead><tr><th>Date</th><th>Client</th><th>Produit</th><th>Montant</th><th>Commission</th><th>Statut</th></tr></thead>
              <tbody id="recentOrdersBody"></tbody>
            </table>
          </div>
        </div>
      </div>

      <!-- ── COMMANDES ── -->
      <div class="admin-panel" id="panel-commandes">
        <div class="admin-panel-title">Gestion des commandes</div>
        <div class="admin-panel-sub">Toutes les commandes reçues via WhatsApp</div>
        <div class="admin-table-wrap">
          <div class="admin-table-header">
            <div class="admin-table-title">📋 Toutes les commandes</div>
            <input class="admin-search-input" placeholder="🔍 Rechercher..." oninput="filterOrders(this.value)">
          </div>
          <div class="table-scroll">
            <table>
              <thead><tr><th>ID</th><th>Date</th><th>Client WhatsApp</th><th>Produit(s)</th><th>Vendeur</th><th>Total</th><th>Ma commission</th><th>Vendeur reçoit</th><th>Statut</th><th>Actions</th></tr></thead>
              <tbody id="allOrdersBody"></tbody>
            </table>
          </div>
        </div>
        <div class="admin-form-card">
          <div class="admin-form-title">➕ Enregistrer une nouvelle commande</div>
          <div class="form-grid">
            <div class="form-group"><label>Client (WhatsApp)</label><input type="text" id="new-order-client" placeholder="07XXXXXXXX"></div>
            <div class="form-group"><label>Produit vendu</label>
              <select id="new-order-product">
                <option value="">Sélectionner un produit</option>
              </select>
            </div>
            <div class="form-group"><label>Montant reçu (FCFA)</label><input type="number" id="new-order-amount" placeholder="10000"></div>
            <div class="form-group"><label>Mode de paiement</label>
              <select id="new-order-pay"><option>Orange Money</option><option>Wave</option><option>MTN MoMo</option><option>Moov Money</option></select>
            </div>
          </div>
          <div class="admin-btn-row">
            <button class="admin-btn" onclick="addOrder()">💾 Enregistrer la commande</button>
          </div>
        </div>
      </div>

      <!-- ── PRODUITS ── -->
      <div class="admin-panel" id="panel-produits">
        <div class="admin-panel-title">Gestion des produits</div>
        <div class="admin-panel-sub">Ajoutez, modifiez ou supprimez des produits du catalogue</div>
        <div class="admin-table-wrap">
          <div class="admin-table-header">
            <div class="admin-table-title">📦 Catalogue complet</div>
            <input class="admin-search-input" placeholder="🔍 Rechercher..." oninput="filterProducts(this.value)">
          </div>
          <div class="table-scroll">
            <table>
              <thead><tr><th>Icône</th><th>Nom</th><th>Catégorie</th><th>Vendeur</th><th>Prix</th><th>Ma commission</th><th>Vendeur reçoit</th><th>Statut</th><th>Actions</th></tr></thead>
              <tbody id="productsBody"></tbody>
            </table>
          </div>
        </div>
        <div class="admin-form-card">
          <div class="admin-form-title">➕ Ajouter un nouveau produit</div>
          <div class="form-grid">
            <div class="form-group full"><label>Nom du produit <span>*</span></label><input type="text" id="np-nom" placeholder="Ex: Formation Instagram Pro"></div>
            <div class="form-group"><label>Catégorie</label>
              <select id="np-cat"><option value="formation">📚 Formation</option><option value="logiciel">💻 Logiciel</option><option value="fichier">📁 Fichier</option><option value="jeu">🎮 Jeu PC</option></select>
            </div>
            <div class="form-group"><label>Icône (emoji)</label><input type="text" id="np-icon" placeholder="Ex: 🎯" maxlength="4"></div>
            <div class="form-group"><label>Vendeur</label><input type="text" id="np-seller" placeholder="Nom du vendeur"></div>
            <div class="form-group"><label>Prix (FCFA)</label><input type="number" id="np-prix" placeholder="10000" min="500"></div>
            <div class="form-group full"><label>Description</label><textarea id="np-desc" placeholder="Description du produit..."></textarea></div>
          </div>
          <div class="admin-btn-row">
            <button class="admin-btn" onclick="addProduct()">💾 Ajouter au catalogue</button>
          </div>
        </div>
      </div>

      <!-- ── VENDEURS ── -->
      <div class="admin-panel" id="panel-vendeurs">
        <div class="admin-panel-title">Gestion des vendeurs</div>
        <div class="admin-panel-sub">Tous les vendeurs inscrits sur la plateforme</div>
        <div class="admin-table-wrap">
          <div class="admin-table-header">
            <div class="admin-table-title">👥 Liste des vendeurs</div>
          </div>
          <div class="table-scroll">
            <table>
              <thead><tr><th>Vendeur</th><th>WhatsApp</th><th>Ville</th><th>Produits</th><th>Ventes totales</th><th>Commission due</th><th>Reversé</th><th>Paiement</th><th>Statut</th><th>Actions</th></tr></thead>
              <tbody id="vendorsBody"></tbody>
            </table>
          </div>
        </div>
        <div class="admin-form-card">
          <div class="admin-form-title">➕ Ajouter un vendeur manuellement</div>
          <div class="form-grid">
            <div class="form-group"><label>Prénom & Nom</label><input type="text" id="nv-nom" placeholder="Kouassi Jean"></div>
            <div class="form-group"><label>WhatsApp</label><input type="tel" id="nv-tel" placeholder="07XXXXXXXX"></div>
            <div class="form-group"><label>Ville</label><input type="text" id="nv-ville" placeholder="Abidjan — Cocody"></div>
            <div class="form-group"><label>Mode de paiement</label>
              <select id="nv-pay"><option>Orange Money</option><option>Wave</option><option>MTN MoMo</option><option>Moov Money</option></select>
            </div>
          </div>
          <div class="admin-btn-row">
            <button class="admin-btn" onclick="addVendor()">💾 Ajouter le vendeur</button>
          </div>
        </div>
      </div>

      <!-- ── FINANCES ── -->
      <div class="admin-panel" id="panel-finances">
        <div class="admin-panel-title">Finances & Reversements</div>
        <div class="admin-panel-sub">Suivi de vos commissions et des reversements aux vendeurs</div>

        <div class="kpi-grid">
          <div class="kpi-card kpi-gold">
            <div class="kpi-icon">🏆</div>
            <div class="kpi-label">Total mes commissions</div>
            <div class="kpi-value" id="fin-total-comm">0</div>
            <div class="kpi-sub">FCFA gagnés</div>
          </div>
          <div class="kpi-card kpi-green">
            <div class="kpi-icon">✅</div>
            <div class="kpi-label">Reversé aux vendeurs</div>
            <div class="kpi-value" id="fin-reversed">0</div>
            <div class="kpi-sub">FCFA payés</div>
          </div>
          <div class="kpi-card kpi-red">
            <div class="kpi-icon">⏳</div>
            <div class="kpi-label">À reverser</div>
            <div class="kpi-value" id="fin-pending">0</div>
            <div class="kpi-sub">FCFA en attente</div>
          </div>
        </div>

        <div class="admin-table-wrap">
          <div class="admin-table-header">
            <div class="admin-table-title">💳 Reversements à effectuer</div>
          </div>
          <div class="table-scroll">
            <table>
              <thead><tr><th>Vendeur</th><th>WhatsApp</th><th>Mode paiement</th><th>Ventes période</th><th>Commission plateforme</th><th>Montant à reverser (80%)</th><th>Actions</th></tr></thead>
              <tbody id="reversementsBody"></tbody>
            </table>
          </div>
        </div>
      </div>

      <!-- ── PARAMÈTRES ── -->
      <div class="admin-panel" id="panel-parametres">
        <div class="admin-panel-title">Paramètres de la marketplace</div>
        <div class="admin-panel-sub">Configurez votre plateforme EduPro CI</div>

        <div class="admin-form-card">
          <div class="admin-form-title">💰 Commission de la plateforme</div>
          <div class="settings-row">
            <div>
              <div class="settings-label">Taux de commission actuel</div>
              <div class="settings-desc">Prélevé automatiquement sur chaque vente. Vendeurs informés lors de l'inscription.</div>
            </div>
            <div class="settings-value" id="commDisplay">20%</div>
          </div>
          <div class="form-group" style="margin-top:16px">
            <label>Modifier le taux de commission (%)</label>
            <input type="number" id="commInput" placeholder="20" min="5" max="50" style="max-width:200px">
          </div>
          <div class="admin-btn-row">
            <button class="admin-btn" onclick="updateCommission()">💾 Enregistrer</button>
          </div>
        </div>

        <div class="admin-form-card">
          <div class="admin-form-title">📲 Numéro WhatsApp de la plateforme</div>
          <div class="form-group">
            <label>Numéro WhatsApp (avec indicatif)</label>
            <input type="text" id="waNumberInput" placeholder="2250716752892">
          </div>
          <div class="admin-btn-row">
            <button class="admin-btn" onclick="updateWA()">💾 Mettre à jour</button>
          </div>
        </div>

        <div class="admin-form-card">
          <div class="admin-form-title">🔐 Changer le mot de passe admin</div>
          <div class="form-grid">
            <div class="form-group"><label>Nouveau mot de passe</label><input type="password" id="newPwd1" placeholder="Nouveau mot de passe"></div>
            <div class="form-group"><label>Confirmer</label><input type="password" id="newPwd2" placeholder="Répéter le mot de passe"></div>
          </div>
          <div class="admin-btn-row">
            <button class="admin-btn" onclick="changePwd()">🔐 Changer le mot de passe</button>
          </div>
        </div>

        <div class="admin-form-card">
          <div class="admin-form-title">⚠️ Zone dangereuse</div>
          <div class="admin-btn-row">
            <button class="admin-btn danger" onclick="if(confirm('Effacer toutes les commandes ?')) clearOrders()">🗑 Effacer toutes les commandes</button>
            <button class="admin-btn outline" onclick="exportData()">📥 Exporter les données (JSON)</button>
          </div>
        </div>
      </div>

    </main>
  </div>
</div>

<!-- ══════════ ÉLÉMENTS PUBLICS ══════════ -->
<!-- Barre panier -->
<div class="cart-bar" id="cartBar">
  <div class="cart-info">
    <div class="cart-count" id="cartCount">0 produit</div>
    <div class="cart-total" id="cartTotalBar">0 FCFA</div>
  </div>
  <button class="cart-btn" onclick="openCart()">🛒 Voir le panier</button>
</div>

<!-- Modal panier -->
<div class="modal-overlay" id="cartModal">
  <div class="modal">
    <div class="modal-header"><div class="modal-title">🛒 Mon panier</div><button class="modal-close-btn" onclick="closeCart()">✕</button></div>
    <div id="cartItems"></div>
    <div id="cartTotalSection" style="display:none">
      <div class="cart-total-row"><span class="cart-total-label">Total à payer</span><span class="cart-total-amount" id="cartTotalModal">0 FCFA</span></div>
      <button class="cart-checkout-btn" onclick="checkout()">📲 Commander sur WhatsApp</button>
    </div>
  </div>
</div>

<!-- Modal succès achat -->
<div class="modal-overlay" id="successModal">
  <div class="modal success-modal">
    <div class="modal-body">
      <div class="success-icon">🎉</div>
      <div class="success-title">Commande envoyée !</div>
      <div class="success-text">Cliquez sur WhatsApp pour finaliser et recevoir vos produits.</div>
      <div class="success-steps">
        <div class="success-step"><div class="ss-num">1</div><div>Cliquez sur le bouton WhatsApp ci-dessous.</div></div>
        <div class="success-step"><div class="ss-num">2</div><div>Effectuez le paiement et envoyez la capture d'écran.</div></div>
        <div class="success-step"><div class="ss-num">3</div><div>Recevez vos produits dans les 24h.</div></div>
      </div>
      <a id="waCheckoutLink" class="wa-btn" href="#" target="_blank" rel="noopener noreferrer"><span>📲</span> Finaliser sur WhatsApp</a>
      <button class="modal-back-btn" onclick="closeSuccess()">Fermer et continuer mes achats</button>
    </div>
  </div>
</div>

<!-- Modal succès vendeur -->
<div class="modal-overlay" id="vendorSuccessModal">
  <div class="modal success-modal">
    <div class="modal-body">
      <div class="success-icon">🚀</div>
      <div class="success-title">Candidature envoyée !</div>
      <div class="success-text">Finalisez via WhatsApp pour que notre équipe valide votre produit sous 24h.</div>
      <a id="waVendorLink" class="wa-btn" href="#" target="_blank" rel="noopener noreferrer"><span>📲</span> Finaliser sur WhatsApp</a>
      <button class="modal-back-btn" onclick="document.getElementById('vendorSuccessModal').classList.remove('show');document.body.style.overflow=''">Fermer</button>
    </div>
  </div>
</div>

<!-- LOGIN ADMIN -->
<div class="admin-login-overlay" id="adminLoginOverlay">
  <div class="admin-login-box">
    <div class="admin-login-logo">Edu<span>Pro</span> CI</div>
    <div class="admin-login-badge">Espace Administrateur</div>
    <div class="admin-login-title">Connexion Admin</div>
    <div class="admin-login-sub">Accès réservé. Entrez vos identifiants pour gérer la marketplace.</div>
    <div class="admin-input-wrap"><span class="admin-input-icon">👤</span><input type="text" id="adminUser" placeholder="Identifiant administrateur" autocomplete="off"></div>
    <div class="admin-input-wrap"><span class="admin-input-icon">🔐</span><input type="password" id="adminPass" placeholder="Mot de passe" onkeydown="if(event.key==='Enter')loginAdmin()"></div>
    <button class="admin-login-btn" onclick="loginAdmin()">🔓 Se connecter</button>
    <div class="admin-login-error" id="adminLoginError">Identifiants incorrects. Réessayez.</div>
    <button class="admin-close-login" onclick="closeAdminLogin()">← Retour à la marketplace</button>
  </div>
</div>

<!-- Bouton caché admin (triple clic sur logo) -->
<div class="admin-trigger" id="adminTrigger" onclick="handleAdminTrigger()" title=""></div>

<!-- Toast notification -->
<div class="toast" id="toast"></div>

<footer>
  <div class="footer-logo">EduPro CI</div>
  © 2025 EduPro CI Marketplace — Tous droits réservés<br>
  Pour toute question : WhatsApp au <a href="https://wa.me/2250716752892">07 16 75 28 92</a>
</footer>

<script>
'use strict';

// ══════════════════════════════════════
// CONFIG & ÉTAT
// ══════════════════════════════════════
let ADMIN_USER = 'admin';
let ADMIN_PASS = 'EduPro2025!';
let WA_NUMBER  = '2250716752892';
let COMMISSION = 20; // % prélevé par la plateforme

// Données de l'app
let PRODUCTS = [
  {id:'p1',cat:'formation',icon:'💬',color:'#12A36C',name:'Formation WhatsApp Business',seller:'EduPro CI',desc:'Transformez WhatsApp en boutique rentable.',price:10000,featured:true,active:true},
  {id:'p2',cat:'formation',icon:'📱',color:'#1565C0',name:'Facebook & Instagram Business',seller:'EduPro CI',desc:'Créez une boutique en ligne et attirez des clients.',price:10000,featured:true,active:true},
  {id:'p3',cat:'formation',icon:'🎯',color:'#7B3FB8',name:'Community Manager Freelance',seller:'EduPro CI',desc:'Gérez les réseaux sociaux et gagnez 250 000 FCFA/mois.',price:12000,featured:false,active:true},
  {id:'p4',cat:'formation',icon:'🎨',color:'#B53A1A',name:'Créer des visuels pro avec Canva',seller:'EduPro CI',desc:'Posts, flyers et catalogues pro sans être graphiste.',price:8000,featured:false,active:true},
  {id:'p5',cat:'formation',icon:'🤖',color:'#C8870A',name:'Gagner de l\'argent avec l\'IA',seller:'EduPro CI',desc:'Utilisez ChatGPT pour créer du contenu en masse.',price:12000,featured:true,active:true},
  {id:'p6',cat:'logiciel',icon:'🛡️',color:'#1565C0',name:'Antivirus Pro — 1 an',seller:'TechShop CI',desc:'Protection complète pour votre PC. Clé livrée sur WhatsApp.',price:7500,featured:true,active:true},
  {id:'p7',cat:'logiciel',icon:'🎵',color:'#7B3FB8',name:'Montage vidéo Pro (licence 1 an)',seller:'MediaPro',desc:'Logiciel de montage pro. Export 4K. Clé livrée sur WhatsApp.',price:15000,featured:false,active:true},
  {id:'p8',cat:'logiciel',icon:'📊',color:'#0A7C52',name:'Pack Office 2024 (Word, Excel, PPT)',seller:'TechShop CI',desc:'Microsoft Office complet. Clé d\'activation valide à vie.',price:20000,featured:true,active:true},
  {id:'p9',cat:'fichier',icon:'📋',color:'#C8870A',name:'100 Templates WhatsApp Business',seller:'DesignPro CI',desc:'100 messages prêts à copier-coller pour vendre sur WhatsApp.',price:3000,featured:false,active:true},
  {id:'p10',cat:'fichier',icon:'📈',color:'#0A7C52',name:'Pack Tableaux Excel Gestion PME',seller:'BusinessTools',desc:'15 fichiers Excel : budget, stock, facturation, comptabilité.',price:5000,featured:true,active:true},
  {id:'p11',cat:'fichier',icon:'🎨',color:'#B53A1A',name:'500 Templates Canva (posts & stories)',seller:'DesignPro CI',desc:'500 modèles pour Instagram, Facebook et WhatsApp.',price:4000,featured:false,active:true},
  {id:'p12',cat:'jeu',icon:'⚽',color:'#1565C0',name:'FIFA 24 PC (clé d\'activation)',seller:'GameZone CI',desc:'FIFA 24 complet pour PC. Clé officielle. Livraison immédiate.',price:25000,featured:true,active:true},
  {id:'p13',cat:'jeu',icon:'🔫',color:'#B53A1A',name:'GTA V PC (clé originale)',seller:'GameZone CI',desc:'Grand Theft Auto V Steam. Jouez en ligne et offline.',price:18000,featured:false,active:true},
  {id:'p14',cat:'jeu',icon:'🏆',color:'#7B3FB8',name:'Pack 5 Jeux PC — Meilleurs Hits',seller:'GameZone CI',desc:'5 jeux populaires. Clés Steam/Origin. Économisez 40%.',price:35000,featured:false,active:true},
];

let VENDORS = [
  {id:'v1',nom:'EduPro CI',tel:'07167528921',ville:'Abidjan — Cocody',pay:'Orange Money',produits:5,ventes:0,reversed:0,status:'active'},
  {id:'v2',nom:'TechShop CI',tel:'05XXXXXXXX',ville:'Abidjan — Plateau',pay:'Wave',produits:2,ventes:0,reversed:0,status:'active'},
  {id:'v3',nom:'MediaPro',tel:'01XXXXXXXX',ville:'Abidjan — Yopougon',pay:'MTN MoMo',produits:1,ventes:0,reversed:0,status:'active'},
  {id:'v4',nom:'DesignPro CI',tel:'07XXXXXXXX',ville:'Bouaké',pay:'Orange Money',produits:2,ventes:0,reversed:0,status:'active'},
  {id:'v5',nom:'GameZone CI',tel:'05XXXXXXXX',ville:'Abidjan — Cocody',pay:'Wave',produits:3,ventes:0,reversed:0,status:'active'},
  {id:'v6',nom:'BusinessTools',tel:'01XXXXXXXX',ville:'Yamoussoukro',pay:'Moov Money',produits:1,ventes:0,reversed:0,status:'active'},
];

let ORDERS = [
  {id:'CMD001',date:'2025-05-10',client:'07XX001',product:'Formation WhatsApp Business',seller:'EduPro CI',amount:10000,status:'paid'},
  {id:'CMD002',date:'2025-05-11',client:'05XX002',product:'Pack Office 2024',seller:'TechShop CI',amount:20000,status:'paid'},
  {id:'CMD003',date:'2025-05-12',client:'01XX003',product:'FIFA 24 PC',seller:'GameZone CI',amount:25000,status:'paid'},
  {id:'CMD004',date:'2025-05-13',client:'07XX004',product:'Antivirus Pro',seller:'TechShop CI',amount:7500,status:'pending'},
  {id:'CMD005',date:'2025-05-14',client:'05XX005',product:'Gagner avec l\'IA',seller:'EduPro CI',amount:12000,status:'paid'},
];

let cart = {};
let currentFilter = 'tous';
let selectedCat = '';
let selectedVendorPay = '';
let adminLoggedIn = false;
let adminClickCount = 0;
let adminClickTimer = null;

// ══════════════════════════════════════
// NAVIGATION PUBLIQUE
// ══════════════════════════════════════
function showPage(pageId) {
  if(pageId !== 'admin' && !adminLoggedIn) {
    document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
    document.querySelectorAll('.nav-tab').forEach(t => t.classList.remove('active'));
    document.getElementById('page-' + pageId).classList.add('active');
    const idx = ['home','catalogue','vendor'].indexOf(pageId);
    if(idx >= 0) document.querySelectorAll('.nav-tab')[idx].classList.add('active');
    window.scrollTo({top:0,behavior:'smooth'});
  } else if(pageId === 'admin') {
    document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
    document.querySelectorAll('.nav-tab').forEach(t => t.classList.remove('active'));
    document.getElementById('page-admin').classList.add('active');
    document.getElementById('publicNav').style.display = 'none';
    refreshAdminData();
  }
}

// ══════════════════════════════════════
// ADMIN AUTH
// ══════════════════════════════════════
function handleAdminTrigger() {
  adminClickCount++;
  clearTimeout(adminClickTimer);
  adminClickTimer = setTimeout(() => { adminClickCount = 0; }, 1500);
  if(adminClickCount >= 5) {
    adminClickCount = 0;
    openAdminLogin();
  }
}

function openAdminLogin() {
  document.getElementById('adminLoginOverlay').classList.add('show');
  setTimeout(() => document.getElementById('adminUser').focus(), 300);
}

function closeAdminLogin() {
  document.getElementById('adminLoginOverlay').classList.remove('show');
  document.getElementById('adminLoginError').classList.remove('show');
  document.getElementById('adminUser').value = '';
  document.getElementById('adminPass').value = '';
}

function loginAdmin() {
  const u = document.getElementById('adminUser').value.trim();
  const p = document.getElementById('adminPass').value.trim();
  if(u === ADMIN_USER && p === ADMIN_PASS) {
    adminLoggedIn = true;
    closeAdminLogin();
    showPage('admin');
    showToast('✅ Bienvenue Admin !');
  } else {
    document.getElementById('adminLoginError').classList.add('show');
    document.getElementById('adminPass').value = '';
  }
}

function logoutAdmin() {
  if(!confirm('Se déconnecter de l\'espace admin ?')) return;
  adminLoggedIn = false;
  document.getElementById('publicNav').style.display = 'flex';
  showPage('home');
  showToast('Déconnecté');
}

// ══════════════════════════════════════
// ADMIN PANELS
// ══════════════════════════════════════
function showPanel(panelId) {
  document.querySelectorAll('.admin-panel').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.admin-nav-item').forEach(n => n.classList.remove('active'));
  document.getElementById('panel-' + panelId).classList.add('active');
  const panels = ['dashboard','commandes','produits','vendeurs','finances','parametres'];
  const idx = panels.indexOf(panelId);
  if(idx >= 0) document.querySelectorAll('.admin-nav-item')[idx].classList.add('active');
  if(panelId === 'dashboard') renderDashboard();
  if(panelId === 'commandes') renderOrders();
  if(panelId === 'produits') renderProducts();
  if(panelId === 'vendeurs') renderVendors();
  if(panelId === 'finances') renderFinances();
  if(panelId === 'parametres') loadSettings();
}

function refreshAdminData() {
  renderDashboard();
  renderOrders();
  renderProducts();
  renderVendors();
  renderFinances();
  loadSettings();
  populateProductSelect();
}

// ── DASHBOARD ──
function renderDashboard() {
  const now = new Date();
  document.getElementById('dashDate').textContent = `Mise à jour : ${now.toLocaleDateString('fr-FR',{weekday:'long',year:'numeric',month:'long',day:'numeric'})}`;
  const paid = ORDERS.filter(o => o.status === 'paid');
  const totalRev = paid.reduce((s,o) => s+o.amount, 0);
  const totalComm = Math.round(totalRev * COMMISSION / 100);
  document.getElementById('kpi-revenus').textContent = fmt(totalRev) + ' FCFA';
  document.getElementById('kpi-commission').textContent = fmt(totalComm) + ' FCFA';
  document.getElementById('kpi-commission-sub').textContent = `FCFA (${COMMISSION}%)`;
  document.getElementById('kpi-commandes').textContent = ORDERS.length;
  document.getElementById('kpi-vendeurs').textContent = VENDORS.filter(v=>v.status==='active').length;
  document.getElementById('kpi-produits').textContent = PRODUCTS.filter(p=>p.active).length;

  // Chart mensuel (simulation)
  const months = ['Nov','Déc','Jan','Fév','Mar','Avr'];
  const vals = [185000, 220000, 310000, 280000, 410000, totalRev||350000];
  const max = Math.max(...vals);
  document.getElementById('chartBars').innerHTML = vals.map((v,i) => `
    <div class="chart-bar-wrap">
      <div class="chart-bar-val">${(v/1000).toFixed(0)}k</div>
      <div class="chart-bar" style="height:${Math.max(8,v/max*100)}px;background:${i===vals.length-1?'var(--gold-light)':'var(--green)'}"></div>
      <div class="chart-bar-label">${months[i]}</div>
    </div>`).join('');

  // Dernières commandes
  const recent = [...ORDERS].reverse().slice(0,5);
  document.getElementById('recentOrdersBody').innerHTML = recent.map(o => {
    const comm = Math.round(o.amount * COMMISSION / 100);
    return `<tr>
      <td>${o.date}</td>
      <td style="color:var(--gray2)">${o.client}</td>
      <td class="td-name">${o.product}</td>
      <td class="td-price">${fmt(o.amount)} FCFA</td>
      <td class="td-comm">${fmt(comm)} FCFA</td>
      <td><span class="td-badge ${o.status==='paid'?'badge-paid':'badge-pending'}">${o.status==='paid'?'✓ Payé':'⏳ En attente'}</span></td>
    </tr>`;
  }).join('');
}

// ── COMMANDES ──
function renderOrders(filter='') {
  const filtered = ORDERS.filter(o =>
    !filter || o.client.toLowerCase().includes(filter) || o.product.toLowerCase().includes(filter) || o.seller.toLowerCase().includes(filter)
  );
  document.getElementById('allOrdersBody').innerHTML = filtered.map(o => {
    const comm = Math.round(o.amount * COMMISSION / 100);
    const vendorGet = o.amount - comm;
    return `<tr>
      <td style="font-family:monospace;font-size:12px;color:var(--gray2)">${o.id}</td>
      <td style="white-space:nowrap">${o.date}</td>
      <td style="color:var(--gray2)">${o.client}</td>
      <td class="td-name">${o.product}</td>
      <td style="color:var(--gray2)">${o.seller}</td>
      <td class="td-price">${fmt(o.amount)} FCFA</td>
      <td class="td-comm">${fmt(comm)} FCFA</td>
      <td style="color:#4CD99A;font-family:'Syne',sans-serif;font-weight:700;white-space:nowrap">${fmt(vendorGet)} FCFA</td>
      <td><span class="td-badge ${o.status==='paid'?'badge-paid':'badge-pending'}">${o.status==='paid'?'✓ Payé':'⏳ En attente'}</span></td>
      <td class="td-actions">
        ${o.status==='pending'?`<button class="action-btn success" onclick="markPaid('${o.id}')">✓ Marquer payé</button>`:''}
        <button class="action-btn danger" onclick="deleteOrder('${o.id}')">🗑</button>
      </td>
    </tr>`;
  }).join('') || '<tr><td colspan="10" style="text-align:center;color:var(--muted);padding:24px">Aucune commande</td></tr>';
}

function filterOrders(v){ renderOrders(v.toLowerCase()); }

function markPaid(id) {
  const o = ORDERS.find(x => x.id === id);
  if(o) { o.status = 'paid'; renderOrders(); renderDashboard(); showToast('✅ Commande marquée payée'); }
}

function deleteOrder(id) {
  if(!confirm('Supprimer cette commande ?')) return;
  ORDERS = ORDERS.filter(x => x.id !== id);
  renderOrders(); renderDashboard(); renderFinances();
  showToast('🗑 Commande supprimée');
}

function addOrder() {
  const client = document.getElementById('new-order-client').value.trim();
  const productName = document.getElementById('new-order-product').value;
  const amount = parseInt(document.getElementById('new-order-amount').value);
  if(!client || !productName || !amount || amount < 500) { showToast('⚠️ Remplissez tous les champs'); return; }
  const prod = PRODUCTS.find(p => p.name === productName);
  const id = 'CMD' + String(ORDERS.length+1).padStart(3,'0');
  const today = new Date().toISOString().split('T')[0];
  ORDERS.push({id, date:today, client, product:productName, seller:prod?prod.seller:'Inconnu', amount, status:'paid'});
  document.getElementById('new-order-client').value = '';
  document.getElementById('new-order-amount').value = '';
  renderOrders(); renderDashboard(); renderFinances();
  showToast('✅ Commande enregistrée !');
}

// ── PRODUITS ──
function renderProducts(filter='') {
  const filtered = PRODUCTS.filter(p => !filter || p.name.toLowerCase().includes(filter) || p.seller.toLowerCase().includes(filter));
  document.getElementById('productsBody').innerHTML = filtered.map(p => {
    const comm = Math.round(p.price * COMMISSION / 100);
    const vendorGet = p.price - comm;
    return `<tr>
      <td style="font-size:24px;text-align:center">${p.icon}</td>
      <td class="td-name">${p.name}</td>
      <td><span class="td-badge badge-${p.cat}">${catLabel(p.cat)}</span></td>
      <td style="color:var(--gray2)">${p.seller}</td>
      <td class="td-price">${fmt(p.price)} FCFA</td>
      <td class="td-comm">${fmt(comm)} FCFA</td>
      <td style="color:#4CD99A;font-family:'Syne',sans-serif;font-weight:700">${fmt(vendorGet)} FCFA</td>
      <td><span class="td-badge ${p.active?'badge-active':'badge-suspended'}">${p.active?'En ligne':'Masqué'}</span></td>
      <td class="td-actions">
        <button class="action-btn" onclick="toggleProduct('${p.id}')">${p.active?'Masquer':'Afficher'}</button>
        <button class="action-btn danger" onclick="deleteProduct('${p.id}')">🗑</button>
      </td>
    </tr>`;
  }).join('') || '<tr><td colspan="9" style="text-align:center;color:var(--muted);padding:24px">Aucun produit</td></tr>';
}

function filterProducts(v){ renderProducts(v.toLowerCase()); }

function toggleProduct(id) {
  const p = PRODUCTS.find(x => x.id === id);
  if(p) { p.active = !p.active; renderProducts(); renderFeatured(); renderCatalogue(); showToast(p.active ? '✅ Produit mis en ligne' : '🔒 Produit masqué'); }
}

function deleteProduct(id) {
  if(!confirm('Supprimer ce produit du catalogue ?')) return;
  PRODUCTS = PRODUCTS.filter(x => x.id !== id);
  renderProducts(); renderFeatured(); renderCatalogue(); populateProductSelect();
  showToast('🗑 Produit supprimé');
}

function addProduct() {
  const nom = document.getElementById('np-nom').value.trim();
  const cat = document.getElementById('np-cat').value;
  const icon = document.getElementById('np-icon').value.trim() || '📦';
  const seller = document.getElementById('np-seller').value.trim() || 'EduPro CI';
  const prix = parseInt(document.getElementById('np-prix').value);
  const desc = document.getElementById('np-desc').value.trim();
  if(!nom || !prix || prix < 500) { showToast('⚠️ Nom et prix requis (min 500 FCFA)'); return; }
  const colors = {formation:'#12A36C',logiciel:'#1565C0',fichier:'#C8870A',jeu:'#7B3FB8'};
  const id = 'p' + Date.now();
  PRODUCTS.push({id,cat,icon,color:colors[cat],name:nom,seller,desc,price:prix,featured:false,active:true});
  document.getElementById('np-nom').value=''; document.getElementById('np-icon').value='';
  document.getElementById('np-seller').value=''; document.getElementById('np-prix').value='';
  document.getElementById('np-desc').value='';
  renderProducts(); renderFeatured(); renderCatalogue(); populateProductSelect();
  updatePublicStats();
  showToast('✅ Produit ajouté au catalogue !');
}

// ── VENDEURS ──
function renderVendors() {
  document.getElementById('vendorsBody').innerHTML = VENDORS.map(v => {
    const ventes = ORDERS.filter(o => o.seller === v.nom && o.status === 'paid').reduce((s,o) => s+o.amount, 0);
    const commDue = Math.round(ventes * COMMISSION / 100);
    const vendorDue = ventes - commDue;
    return `<tr>
      <td class="td-name" style="font-weight:700">${v.nom}</td>
      <td><a href="https://wa.me/${v.tel}" target="_blank" style="color:var(--wa);text-decoration:none">📲 ${v.tel}</a></td>
      <td style="color:var(--gray2);font-size:12px">${v.ville}</td>
      <td style="text-align:center">${PRODUCTS.filter(p=>p.seller===v.nom).length}</td>
      <td class="td-price">${fmt(ventes)} FCFA</td>
      <td class="td-comm">${fmt(commDue)} FCFA</td>
      <td style="color:#4CD99A;font-family:'Syne',sans-serif;font-weight:700">${fmt(vendorDue)} FCFA</td>
      <td><span style="font-size:12px">${v.pay}</span></td>
      <td><span class="td-badge ${v.status==='active'?'badge-active':'badge-suspended'}">${v.status==='active'?'Actif':'Suspendu'}</span></td>
      <td class="td-actions">
        <button class="action-btn" onclick="toggleVendor('${v.id}')">${v.status==='active'?'Suspendre':'Activer'}</button>
        <button class="action-btn success" onclick="reverseVendor('${v.id}','${v.nom}','${v.tel}',${vendorDue})">💸 Reverser</button>
      </td>
    </tr>`;
  }).join('');
}

function toggleVendor(id) {
  const v = VENDORS.find(x => x.id === id);
  if(v) { v.status = v.status==='active'?'suspended':'active'; renderVendors(); showToast(v.status==='active'?'✅ Vendeur réactivé':'⛔ Vendeur suspendu'); }
}

function reverseVendor(id, nom, tel, amount) {
  if(amount <= 0){ showToast('Aucun montant à reverser'); return; }
  const msg = `Bonjour ${nom} ! 👋\n\nVoici votre versement EduPro CI :\n\n💰 *Montant : ${fmt(amount)} FCFA*\n\nMerci de votre confiance sur notre plateforme ! 🙏`;
  window.open(`https://wa.me/${tel}?text=${encodeURIComponent(msg)}`, '_blank');
  showToast(`💸 Message de reversement envoyé à ${nom}`);
}

function addVendor() {
  const nom = document.getElementById('nv-nom').value.trim();
  const tel = document.getElementById('nv-tel').value.trim();
  const ville = document.getElementById('nv-ville').value.trim();
  const pay = document.getElementById('nv-pay').value;
  if(!nom || !tel) { showToast('⚠️ Nom et téléphone requis'); return; }
  VENDORS.push({id:'v'+Date.now(), nom, tel, ville, pay, produits:0, ventes:0, reversed:0, status:'active'});
  document.getElementById('nv-nom').value=''; document.getElementById('nv-tel').value=''; document.getElementById('nv-ville').value='';
  renderVendors(); updatePublicStats();
  showToast('✅ Vendeur ajouté !');
}

// ── FINANCES ──
function renderFinances() {
  const paid = ORDERS.filter(o => o.status === 'paid');
  const totalRev = paid.reduce((s,o) => s+o.amount, 0);
  const totalComm = Math.round(totalRev * COMMISSION / 100);
  document.getElementById('fin-total-comm').textContent = fmt(totalComm) + ' FCFA';
  document.getElementById('fin-reversed').textContent = '0 FCFA';
  document.getElementById('fin-pending').textContent = fmt(totalComm) + ' FCFA';

  // Tableau reversements par vendeur
  const vendorSales = {};
  paid.forEach(o => {
    if(!vendorSales[o.seller]) vendorSales[o.seller] = 0;
    vendorSales[o.seller] += o.amount;
  });
  const rows = Object.entries(vendorSales).map(([seller, total]) => {
    const comm = Math.round(total * COMMISSION / 100);
    const toReverse = total - comm;
    const vendor = VENDORS.find(v => v.nom === seller);
    const tel = vendor ? vendor.tel : '–';
    const pay = vendor ? vendor.pay : '–';
    return `<tr>
      <td style="font-weight:700">${seller}</td>
      <td><a href="https://wa.me/${tel}" target="_blank" style="color:var(--wa);text-decoration:none">📲 ${tel}</a></td>
      <td style="color:var(--gray2)">${pay}</td>
      <td class="td-price">${fmt(total)} FCFA</td>
      <td class="td-comm">${fmt(comm)} FCFA</td>
      <td style="color:#4CD99A;font-family:'Syne',sans-serif;font-size:18px;font-weight:800">${fmt(toReverse)} FCFA</td>
      <td class="td-actions">
        <button class="action-btn success" onclick="reverseVendor('',${JSON.stringify(seller)},${JSON.stringify(tel)},${toReverse})">💸 Reverser sur WhatsApp</button>
      </td>
    </tr>`;
  });
  document.getElementById('reversementsBody').innerHTML = rows.length ? rows.join('') : '<tr><td colspan="7" style="text-align:center;color:var(--muted);padding:24px">Aucune vente enregistrée</td></tr>';
}

// ── PARAMÈTRES ──
function loadSettings() {
  document.getElementById('commDisplay').textContent = COMMISSION + '%';
  document.getElementById('commInput').value = COMMISSION;
  document.getElementById('waNumberInput').value = WA_NUMBER;
}

function updateCommission() {
  const v = parseInt(document.getElementById('commInput').value);
  if(v < 5 || v > 50) { showToast('⚠️ Commission entre 5% et 50%'); return; }
  COMMISSION = v;
  document.getElementById('commDisplay').textContent = COMMISSION + '%';
  updateCommissionDisplay();
  renderDashboard(); renderOrders(); renderProducts(); renderVendors(); renderFinances();
  showToast(`✅ Commission mise à jour : ${COMMISSION}%`);
}

function updateCommissionDisplay() {
  const vendorPct = 100 - COMMISSION;
  document.getElementById('vendeurPctLabel').textContent = `${vendorPct}% pour vous`;
  document.getElementById('vendeurPctDesc').textContent = `Vous gardez ${vendorPct}% de chaque vente. La plateforme perçoit ${COMMISSION}% de commission.`;
  document.getElementById('commissionBadgeVendor').textContent = `💰 Vous gardez ${vendorPct}% de vos ventes — commission de ${COMMISSION}% seulement`;
}

function updateWA() {
  const v = document.getElementById('waNumberInput').value.trim();
  if(v.length < 8) { showToast('⚠️ Numéro invalide'); return; }
  WA_NUMBER = v;
  showToast('✅ Numéro WhatsApp mis à jour');
}

function changePwd() {
  const p1 = document.getElementById('newPwd1').value;
  const p2 = document.getElementById('newPwd2').value;
  if(p1.length < 6) { showToast('⚠️ Mot de passe trop court (min 6 caractères)'); return; }
  if(p1 !== p2) { showToast('⚠️ Les mots de passe ne correspondent pas'); return; }
  ADMIN_PASS = p1;
  document.getElementById('newPwd1').value=''; document.getElementById('newPwd2').value='';
  showToast('✅ Mot de passe changé avec succès');
}

function clearOrders() {
  ORDERS = [];
  renderOrders(); renderDashboard(); renderFinances();
  showToast('🗑 Toutes les commandes effacées');
}

function exportData() {
  const data = {products:PRODUCTS, vendors:VENDORS, orders:ORDERS, commission:COMMISSION, exported:new Date().toISOString()};
  const blob = new Blob([JSON.stringify(data, null, 2)], {type:'application/json'});
  const a = document.createElement('a');
  a.href = URL.createObjectURL(blob);
  a.download = 'edupro-data-' + new Date().toISOString().split('T')[0] + '.json';
  a.click();
  showToast('📥 Données exportées');
}

function populateProductSelect() {
  const sel = document.getElementById('new-order-product');
  if(!sel) return;
  sel.innerHTML = '<option value="">Sélectionner un produit</option>' + PRODUCTS.map(p => `<option value="${p.name}">${p.name} — ${fmt(p.price)} FCFA</option>`).join('');
}

function updatePublicStats() {
  const el1 = document.getElementById('statProduits');
  const el2 = document.getElementById('statVendeurs');
  if(el1) el1.textContent = PRODUCTS.filter(p=>p.active).length + '+';
  if(el2) el2.textContent = VENDORS.filter(v=>v.status==='active').length + '+';
}

// ══════════════════════════════════════
// CATALOGUE PUBLIC
// ══════════════════════════════════════
function renderProduct(p) {
  const inCart = !!cart[p.id];
  if(!p.active) return '';
  return `<div class="product-card ${inCart?'in-cart':''}" id="card-${p.id}">
    <div class="product-thumb" style="background:linear-gradient(135deg,${p.color}22,${p.color}11)">
      <span style="font-size:52px">${p.icon}</span>
      <span class="product-badge-type" style="color:${p.color}">${catLabel(p.cat)}</span>
    </div>
    <div class="product-body">
      <div class="product-seller"><span class="seller-dot"></span>${p.seller}</div>
      <div class="product-title">${p.name}</div>
      <div class="product-desc">${p.desc}</div>
      <div class="product-footer">
        <div class="product-price">${fmt(p.price)} <small>FCFA</small></div>
        <button class="add-to-cart-btn" onclick="toggleCart('${p.id}')">${inCart?'✓ Ajouté':'+ Panier'}</button>
      </div>
    </div>
  </div>`;
}

function catLabel(c){ return {formation:'📚 Formation',logiciel:'💻 Logiciel',fichier:'📁 Fichier',jeu:'🎮 Jeu PC'}[c]||c; }
function fmt(n){ return typeof n === 'number' ? n.toLocaleString('fr-FR') : n; }

function renderFeatured() {
  const g = document.getElementById('featuredGrid');
  if(g) g.innerHTML = PRODUCTS.filter(p=>p.featured&&p.active).map(p=>renderProduct(p)).join('');
}

function renderCatalogue() {
  const g = document.getElementById('catalogueGrid');
  if(g) {
    const f = currentFilter==='tous' ? PRODUCTS.filter(p=>p.active) : PRODUCTS.filter(p=>p.cat===currentFilter&&p.active);
    g.innerHTML = f.map(p=>renderProduct(p)).join('');
  }
}

function setFilter(cat, btn) {
  currentFilter = cat;
  document.querySelectorAll('.filter-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  renderCatalogue();
}

function filterAndGo(cat) {
  currentFilter = cat;
  showPage('catalogue');
  setTimeout(() => {
    document.querySelectorAll('.filter-btn').forEach(b => {
      b.classList.toggle('active', b.textContent.toLowerCase().includes(cat));
    });
    renderCatalogue();
  }, 100);
}

// ══════════════════════════════════════
// PANIER
// ══════════════════════════════════════
function toggleCart(id) {
  const p = PRODUCTS.find(x=>x.id===id);
  if(!p) return;
  if(cart[id]) delete cart[id]; else cart[id] = p;
  updateCartUI(); renderFeatured(); renderCatalogue();
}

function updateCartUI() {
  const items = Object.values(cart);
  const total = items.reduce((s,p)=>s+p.price,0);
  const bar = document.getElementById('cartBar');
  document.getElementById('cartCount').textContent = items.length + (items.length>1?' produits':' produit');
  document.getElementById('cartTotalBar').textContent = fmt(total) + ' FCFA';
  if(items.length>0) bar.classList.add('show'); else bar.classList.remove('show');
}

function openCart() {
  renderCartModal();
  document.getElementById('cartModal').classList.add('show');
  document.body.style.overflow='hidden';
}

function closeCart() {
  document.getElementById('cartModal').classList.remove('show');
  document.body.style.overflow='';
}

function renderCartModal() {
  const items = Object.values(cart);
  const c = document.getElementById('cartItems');
  const ts = document.getElementById('cartTotalSection');
  if(!items.length) {
    c.innerHTML='<div class="cart-empty">🛒<br><br>Votre panier est vide.</div>';
    ts.style.display='none'; return;
  }
  const total = items.reduce((s,p)=>s+p.price,0);
  c.innerHTML = items.map(p=>`<div class="cart-item">
    <div class="cart-item-icon">${p.icon}</div>
    <div class="cart-item-info"><div class="cart-item-name">${p.name}</div><div class="cart-item-seller">par ${p.seller}</div></div>
    <div class="cart-item-price">${fmt(p.price)} FCFA</div>
    <button class="remove-item-btn" onclick="removeFromCart('${p.id}')">🗑</button>
  </div>`).join('');
  document.getElementById('cartTotalModal').textContent = fmt(total) + ' FCFA';
  ts.style.display='block';
}

function removeFromCart(id) {
  delete cart[id];
  updateCartUI(); renderCartModal(); renderFeatured(); renderCatalogue();
}

function checkout() {
  const items = Object.values(cart);
  if(!items.length) return;
  const total = items.reduce((s,p)=>s+p.price,0);
  let msg = `Bonjour EduPro CI ! 👋\n\nJe souhaite commander :\n\n`;
  items.forEach((p,i) => { msg += `${i+1}. *${p.name}* — ${fmt(p.price)} FCFA\n`; });
  msg += `\n💰 *Total : ${fmt(total)} FCFA*\n\nMerci de confirmer ma commande ! 🙏`;
  document.getElementById('waCheckoutLink').href = `https://wa.me/${WA_NUMBER}?text=${encodeURIComponent(msg)}`;
  closeCart();
  document.getElementById('successModal').classList.add('show');
  document.body.style.overflow='hidden';
}

function closeSuccess() {
  document.getElementById('successModal').classList.remove('show');
  document.body.style.overflow='';
}

// ══════════════════════════════════════
// FORMULAIRE VENDEUR
// ══════════════════════════════════════
function selectCat(el) {
  document.querySelectorAll('.cat-option').forEach(c=>c.classList.remove('selected'));
  el.classList.add('selected'); selectedCat = el.dataset.cat;
  document.getElementById('err-cat').style.display='none';
}

function selectVendorPay(el, method) {
  document.querySelectorAll('.payment-option').forEach(o=>o.classList.remove('selected'));
  el.classList.add('selected'); selectedVendorPay = method;
  document.getElementById('err-vendorpay').style.display='none';
}

function submitVendorForm() {
  let ok = true;
  const v = id => document.getElementById(id).value;
  const setErr = (inp, err, cond) => {
    document.getElementById(inp).classList.toggle('err', !cond);
    document.getElementById(err).style.display = cond ? 'none' : 'block';
    if(!cond) ok = false;
  };
  setErr('v-prenom','err-v-prenom', v('v-prenom').trim().length>=2);
  setErr('v-nom','err-v-nom', v('v-nom').trim().length>=2);
  setErr('v-tel','err-v-tel', /^[\d\s\+\-\(\)]{8,}$/.test(v('v-tel').trim()));
  setErr('v-ville','err-v-ville', v('v-ville')!=='');
  setErr('v-produit-nom','err-v-produit-nom', v('v-produit-nom').trim().length>=5);
  setErr('v-description','err-v-description', v('v-description').trim().length>=20);
  setErr('v-prix','err-v-prix', parseInt(v('v-prix'))>=500);
  if(!selectedCat) { document.getElementById('err-cat').style.display='block'; ok=false; }
  if(!selectedVendorPay) { document.getElementById('err-vendorpay').style.display='block'; ok=false; }
  if(!ok) return;

  const prix = parseInt(v('v-prix'));
  const comm = Math.round(prix * COMMISSION / 100);
  const revenu = prix - comm;
  const vendeurPct = 100 - COMMISSION;
  const catLabels = {formation:'Formation',logiciel:'Logiciel',fichier:'Fichier numérique',jeu:'Jeu PC'};

  let msg = `Bonjour EduPro CI ! 👋\n\nCandidature vendeur :\n\n`;
  msg += `👤 ${v('v-prenom').trim()} ${v('v-nom').trim()}\nTél : ${v('v-tel').trim()}\nVille : ${v('v-ville')}\n\n`;
  msg += `📦 *Produit :* ${catLabels[selectedCat]}\nNom : ${v('v-produit-nom').trim()}\n`;
  msg += `Prix : ${fmt(prix)} FCFA\nMon revenu (${vendeurPct}%) : ${fmt(revenu)} FCFA\n`;
  if(v('v-format')) msg += `Format : ${v('v-format')}\n`;
  msg += `\n📝 ${v('v-description').trim()}\n\n💳 Réception : ${selectedVendorPay}\n\nMerci 🙏`;

  document.getElementById('waVendorLink').href = `https://wa.me/${WA_NUMBER}?text=${encodeURIComponent(msg)}`;
  document.getElementById('vendorSuccessModal').classList.add('show');
  document.body.style.overflow='hidden';
}

// ══════════════════════════════════════
// UTILITAIRES
// ══════════════════════════════════════
function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg; t.classList.add('show');
  setTimeout(() => t.classList.remove('show'), 3000);
}

// Fermeture modals
document.getElementById('cartModal').addEventListener('click', e=>{ if(e.target===document.getElementById('cartModal')) closeCart(); });
document.getElementById('successModal').addEventListener('click', e=>{ if(e.target===document.getElementById('successModal')) closeSuccess(); });
document.getElementById('vendorSuccessModal').addEventListener('click', e=>{ if(e.target===document.getElementById('vendorSuccessModal')){ document.getElementById('vendorSuccessModal').classList.remove('show'); document.body.style.overflow=''; }});
document.getElementById('adminLoginOverlay').addEventListener('click', e=>{ if(e.target===document.getElementById('adminLoginOverlay')) closeAdminLogin(); });
document.addEventListener('keydown', e=>{ if(e.key==='Escape'){ closeCart(); closeSuccess(); closeAdminLogin(); }});

// Date dashboard
document.getElementById('dashDate').textContent = new Date().toLocaleDateString('fr-FR',{weekday:'long',year:'numeric',month:'long',day:'numeric'});

// INIT
renderFeatured();
renderCatalogue();
updatePublicStats();
</script>
</body>
</html>
