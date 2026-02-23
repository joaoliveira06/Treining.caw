<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CAW Projetos — Plataforma de Treinamento Industrial</title>
<link href="https://fonts.googleapis.com/css2?family=Barlow:wght@300;400;500;600;700;800;900&family=Barlow+Condensed:wght@700;800;900&display=swap" rel="stylesheet">
<style>
/* ═══════════════════════ TOKENS ═══════════════════════ */
:root{
  --or:#FF6A00;--or-dk:#D95700;--or-lt:#FFF0E6;--or-mid:rgba(255,106,0,.12);
  --bg:#F4F5F7;--surf:#FFFFFF;--surf2:#F9FAFB;
  --bdr:#E5E7EB;--bdr-lt:#F0F1F3;
  --t1:#111827;--t2:#4B5563;--t3:#9CA3AF;
  --ok:#16a34a;--err:#dc2626;--warn:#d97706;
  --s1:0 1px 3px rgba(0,0,0,.06),0 1px 2px rgba(0,0,0,.04);
  --s2:0 4px 16px rgba(0,0,0,.08);--s3:0 12px 40px rgba(0,0,0,.14);
}
*{margin:0;padding:0;box-sizing:border-box}
body{font-family:'Barlow',sans-serif;background:var(--bg);color:var(--t1);overflow-x:hidden;
  /* content protection */
  user-select:none;-webkit-user-select:none;
}
img{pointer-events:none;-webkit-user-drag:none}
#landing{display:block}#app{display:none}

/* ═══════════════════════ LANDING NAV ═══════════════════════ */
.lnav{position:fixed;top:0;left:0;right:0;z-index:100;display:flex;align-items:center;justify-content:space-between;padding:0 60px;height:64px;background:rgba(255,255,255,.97);backdrop-filter:blur(12px);border-bottom:1px solid var(--bdr);box-shadow:var(--s1)}
.logo{display:flex;align-items:center;gap:10px}
.lm{width:34px;height:34px;background:var(--or);clip-path:polygon(0 0,68% 0,100% 32%,100% 100%,32% 100%,0 68%);display:flex;align-items:center;justify-content:center;font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:12px;color:#fff;flex-shrink:0}
.lb{font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:18px;letter-spacing:2px;color:var(--t1);line-height:1}
.ls{font-size:9px;font-weight:600;letter-spacing:2.5px;color:var(--or);text-transform:uppercase}
.lnav-links{display:flex;gap:24px;align-items:center}
.lnav-links a{text-decoration:none;color:var(--t2);font-size:13px;font-weight:600;transition:color .2s}
.lnav-links a:hover{color:var(--or)}

/* ═══════════════════════ BUTTONS ═══════════════════════ */
.btn{display:inline-flex;align-items:center;gap:6px;border:none;cursor:pointer;font-family:'Barlow',sans-serif;font-weight:700;text-transform:uppercase;letter-spacing:.5px;transition:all .2s;white-space:nowrap;text-decoration:none}
.b-or{background:var(--or);color:#fff;padding:11px 28px;border-radius:6px;font-size:13px;box-shadow:0 4px 14px rgba(255,106,0,.25)}
.b-or:hover{background:var(--or-dk);transform:translateY(-1px);box-shadow:0 8px 22px rgba(255,106,0,.35)}
.b-gh{background:var(--surf);color:var(--t1);border:1.5px solid var(--bdr);padding:11px 22px;border-radius:6px;font-size:13px}
.b-gh:hover{border-color:var(--or);color:var(--or);background:var(--or-lt)}
.b-sm{padding:6px 12px;font-size:11px;border-radius:5px;border:1.5px solid var(--bdr);background:var(--surf);color:var(--t2);cursor:pointer;font-family:'Barlow',sans-serif;font-weight:700;letter-spacing:.3px;transition:all .15s;display:inline-flex;align-items:center;gap:4px}
.b-sm:hover{border-color:var(--or);color:var(--or);background:var(--or-lt)}
.b-danger{background:rgba(220,38,38,.07);color:var(--err);border:1.5px solid rgba(220,38,38,.2);padding:6px 12px;font-size:11px;border-radius:5px;cursor:pointer;font-family:'Barlow',sans-serif;font-weight:700;transition:all .15s;display:inline-flex;align-items:center;gap:4px}
.b-danger:hover{background:rgba(220,38,38,.14)}
.b-ok{background:rgba(22,163,74,.08);color:#16a34a;border:1.5px solid rgba(22,163,74,.2);padding:6px 12px;font-size:11px;border-radius:5px;cursor:pointer;font-family:'Barlow',sans-serif;font-weight:700;transition:all .15s;display:inline-flex;align-items:center;gap:4px}

/* ═══════════════════════ HERO ═══════════════════════ */
.hero{min-height:100vh;background:linear-gradient(158deg,#fff 0%,#FFF7F2 55%,#FFF0E6 100%);display:flex;flex-direction:column;align-items:center;justify-content:center;padding:110px 60px 80px;position:relative;overflow:hidden}
.orb{position:absolute;border-radius:50%;pointer-events:none}
.orb1{top:-80px;right:-60px;width:460px;height:460px;background:radial-gradient(circle,rgba(255,106,0,.07) 0%,transparent 70%)}
.orb2{bottom:-100px;left:-80px;width:360px;height:360px;background:radial-gradient(circle,rgba(255,106,0,.05) 0%,transparent 70%)}
.pill{display:inline-flex;align-items:center;gap:7px;background:var(--or-lt);border:1px solid rgba(255,106,0,.25);padding:5px 16px;border-radius:100px;margin-bottom:24px;font-size:12px;font-weight:700;color:var(--or);position:relative;z-index:1}
.pill::before{content:'';width:6px;height:6px;background:var(--or);border-radius:50%;animation:blink 2s infinite}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.3}}
.hero h1{font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:clamp(44px,7vw,84px);line-height:.92;text-align:center;text-transform:uppercase;position:relative;z-index:1;margin-bottom:20px}
.h-l1{display:block;color:var(--t1)}.h-l2{display:block;color:var(--or)}
.h-l3{display:block;color:var(--t3);font-size:.5em;letter-spacing:4px;font-weight:700;margin-top:10px}
.hdesc{max-width:490px;text-align:center;margin-bottom:34px;color:var(--t2);font-size:15px;line-height:1.75;position:relative;z-index:1}
.hctas{display:flex;gap:10px;align-items:center;position:relative;z-index:1}
.sstrip{display:grid;grid-template-columns:repeat(4,1fr);max-width:820px;width:100%;margin:44px auto 0;background:var(--surf);border:1px solid var(--bdr);border-radius:12px;overflow:hidden;box-shadow:var(--s2);position:relative;z-index:1}
.si{padding:20px 22px;text-align:center;border-right:1px solid var(--bdr)}.si:last-child{border-right:none}
.sn{font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:32px;color:var(--or);line-height:1}
.sl{font-size:10px;font-weight:600;letter-spacing:1.5px;text-transform:uppercase;color:var(--t3);margin-top:3px}

/* ═══════════════════════ FEATURES ═══════════════════════ */
.fsec{background:var(--surf);border-top:1px solid var(--bdr);border-bottom:1px solid var(--bdr)}
.sec{max-width:1120px;margin:0 auto;padding:80px 60px}
.seye{font-size:11px;font-weight:700;letter-spacing:3px;text-transform:uppercase;color:var(--or);margin-bottom:10px}
.sttl{font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:clamp(28px,5vw,48px);text-transform:uppercase;color:var(--t1);line-height:.95;margin-bottom:44px}
.fgrid{display:grid;grid-template-columns:repeat(3,1fr);gap:16px}
.fc{background:var(--surf2);border:1px solid var(--bdr);border-radius:10px;padding:26px;transition:all .2s}
.fc:hover{border-color:var(--or);box-shadow:var(--s2);transform:translateY(-2px)}
.fci{width:42px;height:42px;border-radius:8px;background:var(--or-lt);display:flex;align-items:center;justify-content:center;font-size:19px;margin-bottom:14px}
.fc h3{font-weight:700;font-size:15px;color:var(--t1);margin-bottom:8px}
.fc p{font-size:13px;color:var(--t2);line-height:1.7}

/* ═══════════════════════ FOOTER ═══════════════════════ */
.lfoot{background:var(--surf);border-top:1px solid var(--bdr);padding:26px 60px;display:flex;align-items:center;justify-content:space-between}
.lfoot-c{font-size:13px;color:var(--t3)}

/* ═══════════════════════ MODAL LOGIN ═══════════════════════ */
.ov{display:none;position:fixed;inset:0;z-index:200;background:rgba(0,0,0,.4);backdrop-filter:blur(6px);align-items:center;justify-content:center}
.ov.open{display:flex}
.modal{background:var(--surf);border:1px solid var(--bdr);border-radius:14px;width:460px;padding:40px;box-shadow:var(--s3);position:relative;animation:sup .25s ease}
@keyframes sup{from{transform:translateY(14px);opacity:0}to{transform:translateY(0);opacity:1}}
.mx{position:absolute;top:14px;right:14px;background:var(--surf2);border:1px solid var(--bdr);width:28px;height:28px;border-radius:50%;cursor:pointer;font-size:16px;color:var(--t3);display:flex;align-items:center;justify-content:center;transition:all .15s}
.mx:hover{background:var(--bdr);color:var(--t1)}
.flbl{font-size:11px;font-weight:700;letter-spacing:1.5px;text-transform:uppercase;color:var(--t2);display:block;margin-bottom:6px}
.finp{width:100%;background:var(--surf2);border:1.5px solid var(--bdr);border-radius:8px;padding:12px 14px;color:var(--t1);font-family:'Barlow',sans-serif;font-size:15px;outline:none;transition:border-color .2s;margin-bottom:14px}
.finp:focus{border-color:var(--or);background:#fff;box-shadow:0 0 0 3px rgba(255,106,0,.08)}
.finp::placeholder{color:var(--t3)}
.dbox{background:var(--or-lt);border:1px solid rgba(255,106,0,.2);border-radius:8px;padding:12px 14px;margin-bottom:18px;font-size:13px;color:var(--t2);line-height:1.7}
.dbox strong{color:var(--or)}

/* ═══════════════════════ BADGES ═══════════════════════ */
.abadge{display:inline-flex;align-items:center;gap:5px;padding:3px 10px;border-radius:20px;font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.5px}
.ab-master{background:#FEF3C7;color:#92400E;border:1px solid #FDE68A}
.ab-gestor{background:#EDE9FE;color:#5B21B6;border:1px solid #C4B5FD}
.ab-colab{background:var(--or-lt);color:var(--or);border:1px solid rgba(255,106,0,.2)}
.bdg{display:inline-block;padding:2px 8px;border-radius:20px;font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:.5px}
.bdg-ok{background:rgba(22,163,74,.1);color:#16a34a}
.bdg-off{background:var(--bdr-lt);color:var(--t3)}
.bdg-tag{background:var(--or-lt);color:var(--or)}

/* ═══════════════════════ APP SHELL ═══════════════════════ */
.shell{display:flex;height:100vh;overflow:hidden}
.sidebar{width:250px;flex-shrink:0;background:var(--surf);border-right:1px solid var(--bdr);display:flex;flex-direction:column;overflow-y:auto}
.sbh{padding:16px 14px;border-bottom:1px solid var(--bdr)}
.sbnav{padding:8px 0;flex:1}
.sbsec{padding:14px 14px 4px;font-size:10px;font-weight:700;letter-spacing:2px;text-transform:uppercase;color:var(--t3)}
.ni{display:flex;align-items:center;gap:9px;margin:2px 8px;padding:9px 11px;border-radius:8px;cursor:pointer;transition:all .15s;font-size:13px;font-weight:500;color:var(--t2)}
.ni:hover{background:var(--surf2);color:var(--t1)}
.ni.active{background:var(--or-lt);color:var(--or);font-weight:700}
.ni-ico{font-size:16px;width:20px;text-align:center;flex-shrink:0}
.ni-out{color:var(--err)!important}.ni-out:hover{background:rgba(220,38,38,.06)!important}
.sbu{padding:12px 14px;border-top:1px solid var(--bdr);display:flex;align-items:center;gap:9px}
.uav{width:34px;height:34px;border-radius:8px;display:flex;align-items:center;justify-content:center;font-weight:800;font-size:12px;color:#fff;flex-shrink:0}
.unm{font-size:13px;font-weight:700;color:var(--t1)}.url{font-size:11px;color:var(--t3)}
.main{flex:1;overflow-y:auto;background:var(--bg)}
.pgh{background:var(--surf);border-bottom:1px solid var(--bdr);padding:15px 28px;position:sticky;top:0;z-index:10;display:flex;align-items:center;justify-content:space-between}
.pgh h1{font-family:'Barlow Condensed',sans-serif;font-weight:800;font-size:22px;text-transform:uppercase;color:var(--t1);line-height:1}
.pgcr{font-size:12px;color:var(--t3);margin-top:2px}.pgb{padding:24px 28px}

/* ═══════════════════════ KPIs ═══════════════════════ */
.krow{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;margin-bottom:22px}
.kpi{background:var(--surf);border:1px solid var(--bdr);border-radius:10px;padding:18px;box-shadow:var(--s1);position:relative;overflow:hidden;transition:box-shadow .2s}
.kpi:hover{box-shadow:var(--s2)}.kpi::after{content:'';position:absolute;top:0;left:0;right:0;height:3px;background:var(--or)}
.kico{font-size:22px;margin-bottom:8px}
.kval{font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:30px;color:var(--t1);line-height:1}
.klbl{font-size:11px;font-weight:600;color:var(--t3);text-transform:uppercase;letter-spacing:1px;margin-top:2px}
.sh{display:flex;align-items:center;justify-content:space-between;margin-bottom:14px}
.sh h2{font-family:'Barlow Condensed',sans-serif;font-weight:800;font-size:18px;text-transform:uppercase;color:var(--t1)}
.sha{font-size:12px;font-weight:700;color:var(--or);cursor:pointer}.sha:hover{text-decoration:underline}

/* ═══════════════════════ COURSE CARDS ═══════════════════════ */
.cgrid{display:grid;grid-template-columns:repeat(3,1fr);gap:15px}
.cc{background:var(--surf);border:1px solid var(--bdr);border-radius:10px;overflow:hidden;cursor:pointer;transition:all .2s;box-shadow:var(--s1)}
.cc:hover{transform:translateY(-3px);box-shadow:var(--s3);border-color:var(--or)}
.cth{height:110px;background:linear-gradient(135deg,#1e293b,#334155);display:flex;align-items:center;justify-content:center;position:relative}
.cth-ico{font-size:36px;opacity:.55}.ctag{position:absolute;top:8px;right:8px;background:var(--or);color:#fff;font-size:10px;font-weight:700;text-transform:uppercase;padding:3px 8px;border-radius:4px}
.cbody{padding:14px}
.ctitle{font-weight:700;font-size:14px;color:var(--t1);margin-bottom:3px;line-height:1.35}
.cinst{font-size:12px;color:var(--t3);margin-bottom:10px}
.pb{height:4px;background:var(--bdr);border-radius:3px;overflow:hidden;margin-bottom:5px}
.pbf{height:100%;background:var(--or);border-radius:3px;transition:width .4s}
.pi{display:flex;justify-content:space-between;font-size:11px;font-weight:600}
.pi-p{color:var(--or)}.pi-m{color:var(--t3)}
.cpill{display:inline-block;padding:2px 8px;border-radius:20px;font-size:10px;font-weight:700;text-transform:uppercase;margin-top:7px}
.p-ns{background:var(--bdr-lt);color:var(--t3)}.p-ip{background:var(--or-lt);color:var(--or)}.p-cp{background:rgba(22,163,74,.1);color:#16a34a}

/* ═══════════════════════ VIEWER ═══════════════════════ */
.vwr{display:grid;grid-template-columns:270px 1fr;height:calc(100vh - 62px);overflow:hidden}
.vws{background:var(--surf);border-right:1px solid var(--bdr);overflow-y:auto}
.vwsh{padding:14px 13px;border-bottom:1px solid var(--bdr)}
.vwsh h3{font-family:'Barlow Condensed',sans-serif;font-weight:800;font-size:14px;text-transform:uppercase;color:var(--t1)}
.mg{border-bottom:1px solid var(--bdr-lt)}
.mgl{padding:9px 13px;font-weight:700;font-size:11px;color:var(--surf);background:#1e293b;display:flex;align-items:center;justify-content:space-between;text-transform:uppercase;letter-spacing:.5px;border-bottom:1px solid rgba(255,255,255,.1)}
.lr{padding:8px 13px 8px 22px;display:flex;align-items:center;gap:7px;font-size:13px;color:var(--t2);cursor:pointer;border-left:3px solid transparent;transition:all .15s;line-height:1.3}
.lr:hover{background:var(--surf2);color:var(--t1)}
.lr.active{background:var(--or-lt);color:var(--or);border-left-color:var(--or);font-weight:700}
.lr.done{color:var(--ok)}.li{font-size:12px;flex-shrink:0}
.lt{font-size:9px;color:var(--t3);margin-left:auto;text-transform:uppercase;font-weight:700;background:var(--surf2);padding:2px 6px;border-radius:4px;border:1px solid var(--bdr);white-space:nowrap}
.lr-locked{opacity:.45;cursor:not-allowed!important}
.lr-locked:hover{background:transparent!important;color:var(--t2)!important}
.lr-quiz{background:rgba(22,163,74,.04)}
.lr-quiz.locked{opacity:.45;cursor:not-allowed!important}
.vwc{overflow-y:auto;background:var(--bg)}
.vci{padding:24px 32px;max-width:820px}
.vbox{width:100%;aspect-ratio:16/9;background:linear-gradient(135deg,#0f172a,#1e293b);border-radius:10px;display:flex;flex-direction:column;align-items:center;justify-content:center;margin-bottom:20px;overflow:hidden;box-shadow:var(--s2)}
.vplay{width:60px;height:60px;background:var(--or);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:22px;cursor:pointer;transition:transform .2s;box-shadow:0 0 0 10px rgba(255,106,0,.15)}
.vplay:hover{transform:scale(1.1)}
.vcap{margin-top:12px;color:rgba(255,255,255,.4);font-size:13px}
.vttl{font-family:'Barlow Condensed',sans-serif;font-weight:800;font-size:22px;text-transform:uppercase;color:var(--t1);margin-bottom:6px}
.vmeta{font-size:13px;color:var(--t3);margin-bottom:16px;display:flex;gap:10px;flex-wrap:wrap;align-items:center}
.vtxt{font-size:15px;color:var(--t2);line-height:1.8;margin-bottom:20px}

/* Protected PDF viewer */
.pdf-protected{width:100%;height:520px;border:1px solid var(--bdr);border-radius:8px;overflow:hidden;background:#2d2d2d;position:relative;margin-bottom:16px}
.pdf-protected embed,.pdf-protected iframe{width:100%;height:100%;border:none;pointer-events:auto}
.pdf-toolbar-block{position:absolute;bottom:0;left:0;right:0;height:40px;background:rgba(45,45,45,.95);z-index:5}
.pdfrow{background:var(--surf);border:1px solid var(--bdr);border-radius:8px;padding:13px 16px;margin-bottom:10px;display:flex;align-items:center;gap:12px;box-shadow:var(--s1)}
.pdfrow-ico{font-size:26px}.pdfrow-info h4{font-weight:700;font-size:14px;color:var(--t1)}.pdfrow-info p{font-size:12px;color:var(--t3);margin-top:2px}

/* ═══════════════════════ QUIZ ═══════════════════════ */
.qcard{background:var(--surf);border:1px solid var(--bdr);border-radius:12px;padding:26px;max-width:680px;box-shadow:var(--s1)}
.qhead{margin-bottom:22px;padding-bottom:16px;border-bottom:1px solid var(--bdr-lt)}
.qhead h2{font-family:'Barlow Condensed',sans-serif;font-weight:800;font-size:22px;text-transform:uppercase;color:var(--t1)}
.qhead p{font-size:13px;color:var(--t3);margin-top:4px}
.qb{margin-bottom:22px;padding-bottom:22px;border-bottom:1px solid var(--bdr-lt)}.qb:last-of-type{border-bottom:none}
.qn{font-size:11px;font-weight:700;color:var(--or);text-transform:uppercase;letter-spacing:1px;margin-bottom:6px}
.qt{font-size:15px;font-weight:600;color:var(--t1);margin-bottom:12px;line-height:1.55}
.opt{display:flex;align-items:center;gap:10px;padding:11px 14px;border:1.5px solid var(--bdr);border-radius:8px;margin-bottom:7px;cursor:pointer;transition:all .15s;font-size:14px;color:var(--t2)}
.opt:hover{border-color:var(--or);background:var(--or-lt);color:var(--t1)}
.opt.sel{border-color:var(--or);background:var(--or-lt);color:var(--t1);font-weight:600}
.opt.ok{border-color:#16a34a;background:rgba(22,163,74,.08);color:#15803d}
.opt.err{border-color:#dc2626;background:rgba(220,38,38,.06);color:#dc2626}
.ol{width:26px;height:26px;border:2px solid var(--bdr);border-radius:6px;display:flex;align-items:center;justify-content:center;font-weight:700;font-size:12px;flex-shrink:0}
.opt.sel .ol{border-color:var(--or);background:var(--or);color:#fff}
.opt.ok .ol{border-color:#16a34a;background:#16a34a;color:#fff}
.opt.err .ol{border-color:#dc2626;background:#dc2626;color:#fff}
.qfoot{display:flex;justify-content:space-between;align-items:center;gap:10px;margin-top:22px;padding-top:18px;border-top:1px solid var(--bdr-lt)}
.qprog{font-size:12px;color:var(--t3);font-weight:600}
.resbox{text-align:center;padding:36px 28px}
.resc{font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:72px;line-height:1;margin-bottom:6px}
.resc.pass{color:#16a34a}.resc.fail{color:#dc2626}
.ressub{font-size:13px;font-weight:600;color:var(--t3);text-transform:uppercase;letter-spacing:2px}
.resmsg{font-size:15px;color:var(--t2);margin:14px 0 22px;line-height:1.6}

/* Attempts history */
.attempt-row{display:flex;align-items:center;gap:12px;padding:10px 14px;background:var(--surf);border:1px solid var(--bdr);border-radius:8px;margin-bottom:8px}
.att-score{font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:20px}
.att-score.pass{color:#16a34a}.att-score.fail{color:#dc2626}

/* ═══════════════════════ CERTIFICATE ═══════════════════════ */
.cert{background:#fff;border:6px solid var(--t1);padding:46px;max-width:780px;margin:0 auto;position:relative;text-align:center;box-shadow:var(--s3)}
.cert::before{content:'';position:absolute;inset:8px;border:2px solid var(--or);pointer-events:none}
.cert-co{font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:22px;letter-spacing:3px;color:var(--t1)}
.cert-cos{font-size:9px;letter-spacing:4px;text-transform:uppercase;color:var(--t3);margin-bottom:30px}
.cert-h1{font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:42px;text-transform:uppercase;letter-spacing:3px;color:var(--t1);margin-bottom:4px}
.cert-h1 em{font-style:normal;color:var(--t1)}
.cert-h2{font-size:11px;letter-spacing:4px;text-transform:uppercase;color:var(--t3);margin-bottom:32px}
.cert-nm{font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:46px;color:var(--or);line-height:1;margin-bottom:7px}
.cert-bd{font-size:14px;color:var(--t2);margin-bottom:24px}
.cert-cs{font-family:'Barlow Condensed',sans-serif;font-weight:800;font-size:23px;text-transform:uppercase;color:var(--t1);border-top:2px solid var(--or);border-bottom:2px solid var(--or);padding:9px 0;display:inline-block;margin-bottom:32px}
.cert-ft{display:flex;justify-content:space-between;align-items:flex-end;padding-top:28px;border-top:1px solid var(--bdr)}
.csig{text-align:center}.csln{width:130px;height:1px;background:var(--t1);margin:0 auto 5px}
.cssn{font-weight:700;font-size:12px;color:var(--t1)}.cssr{font-size:11px;color:var(--t3)}

/* ═══════════════════════ TABLE ═══════════════════════ */
.tbl{width:100%;border-collapse:collapse;background:var(--surf);border-radius:10px;overflow:hidden;border:1px solid var(--bdr);box-shadow:var(--s1)}
.tbl th{background:var(--surf2);padding:11px 14px;text-align:left;font-size:11px;font-weight:700;letter-spacing:1.5px;text-transform:uppercase;color:var(--t3);border-bottom:1px solid var(--bdr)}
.tbl td{padding:12px 14px;font-size:14px;color:var(--t2);border-bottom:1px solid var(--bdr-lt);vertical-align:middle}
.tbl tr:last-child td{border-bottom:none}.tbl tr:hover td{background:var(--surf2)}

/* ═══════════════════════ CHART ═══════════════════════ */
.cht{background:var(--surf);border:1px solid var(--bdr);border-radius:10px;padding:18px;box-shadow:var(--s1)}
.chtt{font-family:'Barlow Condensed',sans-serif;font-weight:800;font-size:15px;text-transform:uppercase;color:var(--t1);margin-bottom:16px}
.bch{display:flex;align-items:flex-end;gap:8px;height:120px}
.bg{flex:1;display:flex;flex-direction:column;align-items:center;gap:4px}
.bar{width:100%;background:var(--or);border-radius:3px 3px 0 0;opacity:.8;transition:opacity .2s;min-width:22px}
.bar:hover{opacity:1}.brl{font-size:10px;color:var(--t3);font-weight:600;text-align:center}

/* ═══════════════════════ RANKING ═══════════════════════ */
.rkr{display:flex;align-items:center;gap:12px;padding:12px 14px;background:var(--surf);border:1px solid var(--bdr);border-radius:10px;margin-bottom:7px;box-shadow:var(--s1);transition:box-shadow .15s}
.rkr:hover{box-shadow:var(--s2)}.rkp{font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:22px;color:var(--bdr);width:34px;text-align:center}.rkp.top{color:var(--or)}
.rkav{width:34px;height:34px;border-radius:7px;display:flex;align-items:center;justify-content:center;font-weight:800;font-size:13px;color:#fff;flex-shrink:0}
.rknm{font-weight:700;font-size:14px;color:var(--t1)}.rkdt{font-size:12px;color:var(--t3)}.rksc{font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:20px;color:var(--or)}

/* ═══════════════════════ SECURITY ═══════════════════════ */
.sec-info{background:var(--surf);border:1px solid var(--bdr);border-radius:10px;padding:20px;box-shadow:var(--s1);margin-bottom:16px}
.sec-info h3{font-family:'Barlow Condensed',sans-serif;font-weight:800;font-size:17px;text-transform:uppercase;color:var(--t1);margin-bottom:14px;padding-bottom:11px;border-bottom:1px solid var(--bdr-lt)}
.sec-item{display:flex;align-items:center;justify-content:space-between;padding:10px 0;border-bottom:1px solid var(--bdr-lt)}.sec-item:last-child{border-bottom:none}
.sec-item-info{display:flex;align-items:center;gap:10px}.sec-item-ico{font-size:18px;width:22px;text-align:center}
.sec-item-label{font-size:14px;font-weight:600;color:var(--t1)}.sec-item-desc{font-size:12px;color:var(--t3)}
.sec-ok{color:var(--ok);font-size:11px;font-weight:700;background:rgba(22,163,74,.1);padding:3px 9px;border-radius:20px}
.sec-warn{color:var(--warn);font-size:11px;font-weight:700;background:#FEF3C7;padding:3px 9px;border-radius:20px}

/* ═══════════════════════ FORM SYSTEM ═══════════════════════ */
.fcard{background:var(--surf);border:1px solid var(--bdr);border-radius:12px;padding:24px;box-shadow:var(--s1)}
.form-section-label{display:flex;align-items:center;gap:10px;font-family:'Barlow Condensed',sans-serif;font-weight:800;font-size:16px;text-transform:uppercase;letter-spacing:1px;color:var(--t1);margin-bottom:22px;padding-bottom:14px;border-bottom:2px solid var(--bdr-lt)}
.form-section-num{width:26px;height:26px;border-radius:50%;background:var(--or);color:#fff;display:flex;align-items:center;justify-content:center;font-size:13px;font-weight:900;flex-shrink:0}
.form-label{display:block;font-size:12px;font-weight:700;letter-spacing:1px;text-transform:uppercase;color:var(--t2);margin-bottom:8px}
.form-req{color:var(--err);margin-left:2px}
.form-hint{display:block;font-size:12px;color:var(--t3);margin-top:5px;font-weight:400;text-transform:none;letter-spacing:0;line-height:1.5}
.form-input{width:100%;background:var(--surf);border:1.5px solid var(--bdr);border-radius:8px;padding:13px 15px;color:var(--t1);font-family:'Barlow',sans-serif;font-size:15px;outline:none;transition:border-color .2s,box-shadow .2s}
.form-input:focus{border-color:var(--or);box-shadow:0 0 0 3px rgba(255,106,0,.1);background:#fff}
.form-input::placeholder{color:var(--t3)}
.form-input option{background:#fff;color:var(--t1)}
.form-input-with-unit{position:relative;display:flex;align-items:center}
.form-input-with-unit .form-input{padding-right:54px}
.form-unit{position:absolute;right:14px;font-size:12px;font-weight:700;color:var(--t3);text-transform:uppercase;letter-spacing:.5px;pointer-events:none}
.form-cols-2{display:grid;grid-template-columns:1fr 1fr;gap:20px}
.form-cols-3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:20px}
.form-preview-bar{display:flex;align-items:stretch;background:var(--surf2);border:1px solid var(--bdr);border-radius:10px;overflow:hidden}
.fpb-item{flex:1;display:flex;flex-direction:column;align-items:center;padding:14px 10px;border-right:1px solid var(--bdr)}.fpb-item:last-child{border-right:none}
.fpb-ico{font-size:20px;margin-bottom:5px}
.fpb-val{font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:22px;color:var(--or);line-height:1}
.fpb-lbl{font-size:10px;font-weight:600;text-transform:uppercase;letter-spacing:1px;color:var(--t3);margin-top:3px;text-align:center}
.form-info-box{display:flex;align-items:flex-start;gap:12px;background:var(--or-lt);border:1px solid rgba(255,106,0,.2);border-radius:8px;padding:14px 16px}
.form-info-box strong{display:block;font-size:13px;color:var(--t1);margin-bottom:3px}
.form-info-box p{font-size:13px;color:var(--t2);line-height:1.6;margin:0}
.form-actions{display:flex;justify-content:flex-end;gap:10px;padding:20px 0 6px;border-top:2px solid var(--bdr-lt);margin-top:6px}

/* ═══════════════════════ ACCESS CARDS ═══════════════════════ */
.access-card{border:2px solid var(--bdr);border-radius:10px;padding:16px;text-align:center;cursor:pointer;transition:all .2s;background:var(--surf)}
.access-card:hover{border-color:var(--or);background:var(--or-lt)}
.access-card-active{border-color:var(--or)!important;background:var(--or-lt)!important;box-shadow:0 0 0 3px rgba(255,106,0,.15)}

/* ═══════════════════════ MODULE BUILDER ═══════════════════════ */
.module-block{background:var(--surf);border:2px solid var(--bdr);border-radius:12px;margin-bottom:16px;overflow:hidden;transition:border-color .2s}
.module-block:hover{border-color:rgba(255,106,0,.3)}
.module-header{display:flex;align-items:center;gap:12px;padding:14px 16px;background:var(--surf2);border-bottom:1px solid var(--bdr)}
.mod-num{width:28px;height:28px;border-radius:50%;background:var(--or);color:#fff;display:flex;align-items:center;justify-content:center;font-weight:900;font-size:13px;flex-shrink:0}
.mod-title-inp{flex:1;background:#fff;border:1.5px solid var(--bdr);border-radius:7px;padding:9px 13px;font-family:'Barlow',sans-serif;font-size:15px;font-weight:600;color:var(--t1);outline:none;transition:border-color .2s}
.mod-title-inp:focus{border-color:var(--or)}
.module-body{padding:16px;display:flex;flex-direction:column;gap:14px}
.mod-section{background:var(--surf2);border:1px solid var(--bdr);border-radius:8px;padding:14px}
.mod-section-hd{display:flex;align-items:center;justify-content:space-between;margin-bottom:12px;flex-wrap:wrap;gap:8px}
.lessons-list,.questions-list{display:flex;flex-direction:column;gap:10px}
.list-empty{font-size:13px;color:var(--t3);text-align:center;padding:16px;background:var(--surf);border-radius:6px;border:1px dashed var(--bdr)}
.lesson-item{display:flex;align-items:flex-start;gap:10px;background:var(--surf);border:1px solid var(--bdr);border-radius:8px;padding:12px;transition:border-color .15s}
.lesson-item:hover{border-color:rgba(255,106,0,.3)}
.lesson-item-left{display:flex;align-items:flex-start;gap:10px;flex:1;min-width:0}
.lesson-type-ico{font-size:22px;margin-top:2px;flex-shrink:0}
.lesson-type-tag{background:var(--or-lt);color:var(--or);font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:.5px;padding:2px 8px;border-radius:10px;border:1px solid rgba(255,106,0,.2);white-space:nowrap}
.lesson-upload-row{display:flex;align-items:center;margin-top:7px;flex-wrap:wrap;gap:6px}
.lesson-upload-btn{display:inline-flex;align-items:center;gap:5px;background:var(--surf2);border:1.5px solid var(--bdr);border-radius:6px;padding:6px 12px;font-size:12px;font-weight:700;color:var(--t2);cursor:pointer;transition:all .15s}
.lesson-upload-btn:hover{border-color:var(--or);color:var(--or);background:var(--or-lt)}
.question-item{background:var(--surf);border:1px solid var(--bdr);border-radius:8px;padding:14px;transition:border-color .15s}
.question-item:hover{border-color:rgba(255,106,0,.3)}
.q-num{min-width:26px;height:26px;border-radius:50%;background:var(--surf2);border:1.5px solid var(--bdr);display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700;color:var(--t2);flex-shrink:0}
.course-tag{background:var(--or-lt);color:var(--or);font-size:10px;font-weight:700;padding:2px 8px;border-radius:10px;border:1px solid rgba(255,106,0,.2);display:inline-block}

/* ═══════════════════════ TOAST ═══════════════════════ */
.toast{position:fixed;bottom:18px;right:18px;z-index:9999;background:var(--t1);color:#fff;padding:11px 18px;border-radius:8px;border-left:4px solid var(--or);font-size:13px;font-weight:600;display:none;box-shadow:var(--s3);max-width:360px;animation:tin .3s ease}
@keyframes tin{from{transform:translateY(8px);opacity:0}to{transform:translateY(0);opacity:1}}
.toast.show{display:block}

/* ═══════════════════════ PRINT (certificate only) ═══════════════════════ */
@media print{
  body *{visibility:hidden}
  #printArea,#printArea *{visibility:visible}
  #printArea{position:fixed;inset:0;display:flex;align-items:center;justify-content:center;background:#fff}
}

/* ═══════════════════════ RESPONSIVE ═══════════════════════ */
@media(max-width:900px){
  .lnav,.lfoot{padding-left:18px;padding-right:18px}
  .hero{padding:100px 18px 60px}
  .sstrip{grid-template-columns:repeat(2,1fr);margin:34px 18px 0}
  .sec{padding:56px 18px}
  .fgrid{grid-template-columns:1fr}
  .lfoot{flex-direction:column;gap:8px;text-align:center}
  .sidebar{display:none}
  .krow{grid-template-columns:repeat(2,1fr)}
  .cgrid{grid-template-columns:1fr}
  .form-cols-2,.form-cols-3{grid-template-columns:1fr}
  .vwr{grid-template-columns:1fr}
}
</style>
</head>
<body>
<!-- ════════════════════════════════════════════════════════ LANDING ════ -->
<div id="landing">
<nav class="lnav">
  <div class="logo"><img src="data:image/png;base64,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" style="height: 38px; width: auto; object-fit: contain; image-rendering: -webkit-optimize-contrast;" alt="CAW Logo"></div>
  <div class="lnav-links">
    <a href="#features">Plataforma</a><a href="#features">Sobre</a><a href="#features">Contato</a>
    <button class="btn b-or" style="padding:9px 20px;font-size:12px" onclick="openLogin()">Acessar →</button>
  </div>
</nav>
<section class="hero">
  <div class="orb orb1"></div><div class="orb orb2"></div>
  <div class="pill">🏭 Plataforma Oficial de Treinamento Industrial</div>
  <h1><span class="h-l1">Capacitação</span><span class="h-l2">Industrial</span><span class="h-l3">Treinamento Técnico Corporativo</span></h1>
  <p class="hdesc">A plataforma oficial da CAW Projetos e Consultoria Industrial. Capacite sua equipe com cursos técnicos, avaliações certificadas e relatórios em tempo real.</p>
  <div class="hctas">
    <button class="btn b-or" onclick="openLogin()">Acessar Plataforma →</button>
    <button class="btn b-gh" onclick="demoLogin('hans','Hans7411')">Demo Master</button>
  </div>
  <div class="sstrip">
    <div class="si"><div class="sn">20+</div><div class="sl">Cursos Ativos</div></div>
    <div class="si"><div class="sn">1000+</div><div class="sl">Colaboradores</div></div>
    <div class="si"><div class="sn">94%</div><div class="sl">Aprovação</div></div>
    <div class="si"><div class="sn">-</div><div class="sl">Certificados</div></div>
  </div>
</section>
<section class="fsec" id="features">
  <div class="sec">
    <div class="seye">Funcionalidades</div>
    <h2 class="sttl">Tudo que sua<br>equipe precisa</h2>
    <div class="fgrid">
      <div class="fc"><div class="fci">📦</div><h3>Cursos com Módulos</h3><p>Estrutura hierárquica: curso → módulos → aulas → provas. Progressão sequencial garantida.</p></div>
      <div class="fc"><div class="fci">📝</div><h3>Provas por Módulo</h3><p>Cada módulo possui sua própria avaliação. O aluno só acessa a prova após concluir todas as aulas.</p></div>
      <div class="fc"><div class="fci">🎓</div><h3>Certificação Digital</h3><p>Certificado emitido automaticamente após aprovação em todos os módulos do curso.</p></div>
      <div class="fc"><div class="fci">🔐</div><h3>Conteúdo Protegido</h3><p>PDFs e materiais visualizados apenas na plataforma, sem opção de download ou cópia.</p></div>
      <div class="fc"><div class="fci">👥</div><h3>3 Níveis de Acesso</h3><p>Master (controle total), Gestor (visualização) e Colaborador (estudo), definidos pelo curso.</p></div>
      <div class="fc"><div class="fci">📊</div><h3>Histórico de Desempenho</h3><p>Registro de todas as tentativas de prova, notas obtidas e progresso por módulo.</p></div>
    </div>
  </div>
</section>
<footer class="lfoot">
  <div class="logo"><img src="data:image/png;base64,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" style="height: 28px; width: auto; object-fit: contain; image-rendering: -webkit-optimize-contrast;" alt="CAW Logo"></div>
  <div class="lfoot-c">© 2025 CAW Projetos e Consultoria Industrial. Todos os direitos reservados.</div>
</footer>
</div>

<!-- ════════════════════════════════════════════════════════ LOGIN MODAL ════ -->
<div class="ov" id="loginModal" onclick="if(event.target===this)closeLogin()">
<div class="modal">
  <button class="mx" onclick="closeLogin()">×</button>
  <div style="display:flex;align-items:center;gap:10px;margin-bottom:22px">
    <img src="data:image/png;base64,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" style="height: 34px; width: auto; object-fit: contain; image-rendering: -webkit-optimize-contrast;" alt="CAW Logo">
    <div><div style="font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:17px;letter-spacing:1.5px;color:var(--t1)">CAW Projetos</div>
    <div style="font-size:10px;letter-spacing:2px;color:var(--or);text-transform:uppercase;font-weight:600">Plataforma de Treinamento</div></div>
  </div>
  <h2 style="font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:22px;text-transform:uppercase;color:var(--t1);margin-bottom:5px">Acesso à Plataforma</h2>
  <p style="font-size:14px;color:var(--t2);margin-bottom:18px">Entre com suas credenciais corporativas.</p>
  <div class="dbox">
    <strong>Master:</strong> hans / Hans7411 &nbsp;|&nbsp;
    <strong>Gestor:</strong> geraldo / Ger@2025 &nbsp;|&nbsp;
    <strong>Colab.:</strong> joao / Joao@2025
  </div>
  <label class="flbl">Usuário</label>
  <input class="finp" type="text" id="loginUser" placeholder="seu.usuario" autocomplete="username">
  <label class="flbl">Senha</label>
  <input class="finp" type="password" id="loginPass" placeholder="••••••••" autocomplete="current-password" style="margin-bottom:20px">
  <button class="btn b-or" style="width:100%;justify-content:center;padding:13px" onclick="doLogin()">Entrar na Plataforma →</button>
  <div id="loginErr" style="display:none;margin-top:12px;padding:10px 13px;background:rgba(220,38,38,.07);border:1px solid rgba(220,38,38,.2);border-radius:7px;font-size:13px;color:var(--err)">❌ Credenciais inválidas.</div>
</div>
</div>

<!-- ════════════════════════════════════════════════════════ APP ════ -->
<div id="app">
<div class="shell">
  <aside class="sidebar" id="sidebar">
    <div class="sbh"><div class="logo"><img src="data:image/png;base64,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" style="height: 28px; width: auto; object-fit: contain; image-rendering: -webkit-optimize-contrast;" alt="CAW Logo"></div></div>
    <div class="sbnav" id="sidebarNav"></div>
    <div class="sbu"><div class="uav" id="uAv">?</div><div><div class="unm" id="uNm">–</div><div class="url" id="uRl">–</div></div></div>
  </aside>
  <main class="main" id="main"></main>
</div>
</div>
<div id="printArea" style="display:none"></div>
<div class="toast" id="toast"></div>

<script>
'use strict';
/* ════════════════════════════════════════════════════════════════
   DATA LAYER
════════════════════════════════════════════════════════════════ */
let CU = null; // current user

// ── COURSES ──────────────────────────────────────────────────────
const DEFAULT_COURSES = [
  { id:1, title:'NR-12: Segurança em Máquinas', instructor:'Eng. Carlos Mendes', category:'Segurança', ico:'⚙️', hours:16, minScore:7.0, maxAttempts:3, sequential:true,
    modules:[
      { id:1, order:1, title:'Fundamentos da NR-12',
        lessons:[
          {id:1,title:'Introdução à NR-12',type:'pdf',url:'',text:'A NR-12 estabelece os requisitos mínimos para prevenção de acidentes em máquinas e equipamentos industriais. É obrigatória para todos os setores que utilizem máquinas.'},
          {id:2,title:'Zonas de Perigo e Risco',type:'video',url:'',text:'Identificação e classificação de zonas de perigo conforme a norma. Compreenda como mapear os riscos na sua área.'},
        ],
        quiz:{ title:'Avaliação — Módulo 1', minScore:7.0, maxAttempts:3, questions:[
          {id:1,txt:'O que é considerado zona de perigo conforme a NR-12?',opts:['Área de manutenção','Local de descanso','Espaço com risco de acidente por parte móvel','Corredor de saída'],ok:2},
          {id:2,txt:'A NR-12 se aplica a:',opts:['Apenas máquinas pesadas','Todos os equipamentos e máquinas industriais','Somente equipamentos elétricos','Apenas tornos CNC'],ok:1},
        ]}
      },
      { id:2, order:2, title:'EPIs e Procedimentos de Bloqueio',
        lessons:[
          {id:3,title:'EPIs Obrigatórios',type:'pdf',url:'',text:'Equipamentos de proteção individual exigidos pela NR-12. Luvas, óculos, calçado de segurança e protetor auditivo são essenciais.'},
          {id:4,title:'Lockout/Tagout',type:'pdf',url:'',text:'Procedimento de bloqueio e etiquetagem de energia para manutenção segura de máquinas.'},
        ],
        quiz:{ title:'Avaliação — Módulo 2', minScore:7.0, maxAttempts:3, questions:[
          {id:1,txt:'Qual EPI é obrigatório para operadores de máquinas?',opts:['Apenas luvas','Luvas, óculos e calçado de segurança','Somente capacete','Nenhum EPI'],ok:1},
          {id:2,txt:'Lockout/Tagout é um procedimento de:',opts:['Limpeza de máquinas','Bloqueio de energia para manutenção segura','Calibração de equipamentos','Registro de produção'],ok:1},
        ]}
      },
    ]
  },
  { id:2, title:'Operação de Torno CNC', instructor:'Téc. Roberto Alves', category:'Técnico', ico:'🔩', hours:20, minScore:7.0, maxAttempts:3, sequential:true,
    modules:[
      { id:1, order:1, title:'Fundamentos do CNC',
        lessons:[
          {id:1,title:'Introdução ao CNC',type:'video',url:'',text:'Componentes, funcionamento e tipos de torno CNC utilizados na indústria.'},
          {id:2,title:'Linguagem G-Code',type:'pdf',url:'',text:'Fundamentos de programação CNC: funções G e M, coordenadas e ciclos fixos.'},
        ],
        quiz:{ title:'Avaliação — Módulo 1', minScore:7.0, maxAttempts:3, questions:[
          {id:1,txt:'O que é G-Code?',opts:['Sistema operacional','Linguagem de programação CNC','Software CAD','Protocolo de comunicação'],ok:1},
        ]}
      },
      { id:2, order:2, title:'Operação Prática',
        lessons:[
          {id:3,title:'Configuração de Parâmetros',type:'pdf',url:'',text:'Definição de velocidade de corte, avanço e profundidade para diferentes materiais.'},
          {id:4,title:'Usinagem Demonstrativa',type:'video',url:'',text:'Demonstração prática de usinagem de uma peça cilíndrica do zero ao produto acabado.'},
        ],
        quiz:{ title:'Avaliação — Módulo 2', minScore:7.0, maxAttempts:3, questions:[
          {id:1,txt:'A velocidade do fuso no CNC é controlada pelo código:',opts:['G-code (G)','Velocidade (F)','Spindle speed (S)','Depth (D)'],ok:2},
        ]}
      },
    ]
  },
  { id:3, title:'Gestão da Qualidade ISO 9001', instructor:'Esp. Carla Souza', category:'Qualidade', ico:'🏅', hours:12, minScore:7.0, maxAttempts:3, sequential:false,
    modules:[
      { id:1, order:1, title:'Princípios da ISO 9001',
        lessons:[
          {id:1,title:'Os 7 Princípios da Qualidade',type:'pdf',url:'',text:'Os sete princípios de gestão da qualidade conforme ISO 9001:2015: foco no cliente, liderança, engajamento, abordagem por processo, melhoria, decisão baseada em evidência e gestão de relacionamento.'},
          {id:2,title:'Auditorias Internas',type:'video',url:'',text:'Como planejar e conduzir auditorias internas de qualidade com eficácia.'},
        ],
        quiz:{ title:'Avaliação Final', minScore:7.0, maxAttempts:3, questions:[
          {id:1,txt:'Quantos princípios de gestão a ISO 9001:2015 define?',opts:['5','6','7','8'],ok:2},
          {id:2,txt:'Qual princípio coloca o cliente como prioridade?',opts:['Liderança','Foco no cliente','Melhoria','Engajamento'],ok:1},
        ]}
      },
    ]
  },
];

let COURSES = JSON.parse(localStorage.getItem('caw_courses')||'null') || DEFAULT_COURSES;
function saveCourses(){ localStorage.setItem('caw_courses', JSON.stringify(COURSES)); }

// ── USERS ─────────────────────────────────────────────────────────
const DEFAULT_USERS = [
  { id:1, name:'Hans', login:'hans', pass:'Hans7411', role:'Diretor', sector:'Diretoria', type:'master', ini:'H', color:'#92400E', courseId:null, active:true },
  { id:2, name:'Geraldo Andrade', login:'geraldo', pass:'Ger@2025', role:'Gestor de T&D', sector:'Gestão', type:'gestor', ini:'GA', color:'#5B21B6', courseId:null, active:true },
  { id:3, name:'João Silva', login:'joao', pass:'Joao@2025', role:'Operador CNC', sector:'Produção', type:'colaborador', ini:'JS', color:'#FF6A00', courseId:1, active:true },
  { id:4, name:'Maria Fernanda', login:'maria', pass:'Maria@2025', role:'Técnica de Qualidade', sector:'Qualidade', type:'colaborador', ini:'MF', color:'#3b82f6', courseId:3, active:true },
  { id:5, name:'Ana Paula Ramos', login:'ana', pass:'Ana@2025', role:'Coord. Segurança', sector:'SST', type:'colaborador', ini:'AP', color:'#f59e0b', courseId:1, active:true },
];
let USERS = JSON.parse(localStorage.getItem('caw_users')||'null') || DEFAULT_USERS;
function saveUsers(){ localStorage.setItem('caw_users', JSON.stringify(USERS)); }

// ── PROGRESS ──────────────────────────────────────────────────────
// Structure: { [userId]: { [courseId]: { completedLessons:[], quizAttempts:{ [modId]:[{score,date,pass}] } } } }
let PROGRESS = JSON.parse(localStorage.getItem('caw_progress')||'{}');
function saveProgress(){ localStorage.setItem('caw_progress', JSON.stringify(PROGRESS)); }

function getProgress(uid, cid){
  if(!PROGRESS[uid]) PROGRESS[uid]={};
  if(!PROGRESS[uid][cid]) PROGRESS[uid][cid]={ completedLessons:[], quizAttempts:{} };
  return PROGRESS[uid][cid];
}

function isLessonDone(uid, cid, mid, lid){
  return getProgress(uid,cid).completedLessons.includes(`${mid}-${lid}`);
}
function isModuleLessonsDone(uid, cid, m){
  return m.lessons.every(l=>isLessonDone(uid,cid,m.id,l.id));
}
function isModulePassed(uid, cid, mid){
  const atts = getProgress(uid,cid).quizAttempts[mid]||[];
  return atts.some(a=>a.pass);
}
function isCourseComplete(uid, cid){
  const c=COURSES.find(x=>x.id===cid); if(!c) return false;
  return c.modules.every(m=>isModuleLessonsDone(uid,cid,m)&&isModulePassed(uid,cid,m.id));
}
function courseProgress(uid, cid){
  const c=COURSES.find(x=>x.id===cid); if(!c) return 0;
  const totalLessons=c.modules.reduce((s,m)=>s+m.lessons.length,0);
  const doneLessons=getProgress(uid,cid).completedLessons.length;
  return totalLessons?Math.round(doneLessons/totalLessons*100):0;
}

/* ════════════════════════════════════════════════════════════════
   AUTH
════════════════════════════════════════════════════════════════ */
function openLogin(){ document.getElementById('loginModal').classList.add('open'); document.getElementById('loginErr').style.display='none'; }
function closeLogin(){ document.getElementById('loginModal').classList.remove('open'); }
function demoLogin(u,p){ document.getElementById('loginUser').value=u; document.getElementById('loginPass').value=p; openLogin(); }

function doLogin(){
  const u = document.getElementById('loginUser').value.trim().toLowerCase();
  const p = document.getElementById('loginPass').value;
  const user = USERS.find(x=>(x.login===u||x.name.toLowerCase()===u) && x.pass===p && x.active);
  if(user){ CU={...user}; closeLogin(); launchApp(); }
  else { document.getElementById('loginErr').style.display='block'; }
}
document.addEventListener('keydown',e=>{ if(e.key==='Enter'&&document.getElementById('loginModal').classList.contains('open')) doLogin(); });

function launchApp(){
  document.getElementById('landing').style.display='none';
  document.getElementById('app').style.display='block';
  document.getElementById('uNm').textContent=CU.name;
  const tl={master:'Master',gestor:'Gestor',colaborador:'Colaborador'}[CU.type]||CU.type;
  document.getElementById('uRl').textContent=tl+' · '+(CU.sector||'—');
  document.getElementById('uAv').textContent=CU.ini||CU.name[0];
  document.getElementById('uAv').style.background=CU.color||'#666';
  buildSidebar();
  if(CU.type==='master') go('mDash');
  else if(CU.type==='gestor') go('gDash');
  else go('dashboard');
}
function logout(){ CU=null; document.getElementById('landing').style.display='block'; document.getElementById('app').style.display='none'; }

/* ════════════════════════════════════════════════════════════════
   SIDEBAR
════════════════════════════════════════════════════════════════ */
function buildSidebar(){
  let h='';
  if(CU.type==='master'){
    h=`<div class="sbsec">🔑 Master</div>
    <div class="ni" id="n-mDash" onclick="go('mDash')"><span class="ni-ico">📊</span>Dashboard</div>
    <div class="ni" id="n-mUsers" onclick="go('mUsers')"><span class="ni-ico">👥</span>Usuários</div>
    <div class="ni" id="n-mNewUser" onclick="go('mNewUser')"><span class="ni-ico">➕</span>Novo Usuário</div>
    <div class="ni" id="n-mCourses" onclick="go('mCourses')"><span class="ni-ico">📚</span>Cursos</div>
    <div class="ni" id="n-mNewCourse" onclick="go('mNewCourse')"><span class="ni-ico">➕</span>Novo Curso</div>
    <div class="ni" id="n-mReports" onclick="go('mReports')"><span class="ni-ico">📈</span>Relatórios</div>
    <div class="ni" id="n-mSecurity" onclick="go('mSecurity')"><span class="ni-ico">🔐</span>Segurança</div>
    <div class="sbsec">Conta</div>
    <div class="ni ni-out" onclick="logout()"><span class="ni-ico">🚪</span>Sair</div>`;
  } else if(CU.type==='gestor'){
    h=`<div class="sbsec">👁 Visualização</div>
    <div class="ni" id="n-gDash" onclick="go('gDash')"><span class="ni-ico">📊</span>Dashboard</div>
    <div class="ni" id="n-gUsers" onclick="go('gUsers')"><span class="ni-ico">👥</span>Colaboradores</div>
    <div class="ni" id="n-gCourses" onclick="go('gCourses')"><span class="ni-ico">📚</span>Cursos</div>
    <div class="ni" id="n-gReports" onclick="go('gReports')"><span class="ni-ico">📈</span>Relatórios</div>
    <div class="sbsec">Conta</div>
    <div class="ni ni-out" onclick="logout()"><span class="ni-ico">🚪</span>Sair</div>`;
  } else {
    h=`<div class="sbsec">Aprendizado</div>
    <div class="ni" id="n-dashboard" onclick="go('dashboard')"><span class="ni-ico">🏠</span>Dashboard</div>
    <div class="ni" id="n-myCourses" onclick="go('myCourses')"><span class="ni-ico">📚</span>Meus Cursos</div>
    <div class="ni" id="n-ranking" onclick="go('ranking')"><span class="ni-ico">🏆</span>Ranking</div>
    <div class="sbsec">Conta</div>
    <div class="ni ni-out" onclick="logout()"><span class="ni-ico">🚪</span>Sair</div>`;
  }
  document.getElementById('sidebarNav').innerHTML=h;
}

/* ════════════════════════════════════════════════════════════════
   ROUTER
════════════════════════════════════════════════════════════════ */
let activeCourseId=null, activeModId=null;

function go(pg, ...args){
  document.querySelectorAll('.ni').forEach(e=>e.classList.remove('active'));
  const el=document.getElementById('n-'+pg); if(el) el.classList.add('active');
  const R={
    dashboard,myCourses,courseViewer,ranking,certificate,
    gDash,gUsers,gCourses,gReports,
    mDash,mUsers,mNewUser,mCourses,mNewCourse,mReports,mSecurity,
  };
  R[pg]?.(...args);
}

function page(title,crumb,body,actions=''){
  document.getElementById('main').innerHTML=`
  <div class="pgh">
    <div><h1>${title}</h1><div class="pgcr">${crumb}</div></div>
    <div style="display:flex;gap:8px;align-items:center">${actions}</div>
  </div>
  <div class="pgb">${body}</div>`;
}

/* ════════════════════════════════════════════════════════════════
   HELPERS
════════════════════════════════════════════════════════════════ */
function toast(msg, dur=3200){
  const t=document.getElementById('toast'); t.textContent=msg; t.classList.add('show');
  clearTimeout(t._tid); t._tid=setTimeout(()=>t.classList.remove('show'),dur);
}

function cc(c, uid){
  const pct=courseProgress(uid||CU.id, c.id);
  const done=isCourseComplete(uid||CU.id,c.id);
  const status=done?'completed':pct>0?'in-progress':'not-started';
  const lbl={completed:'Concluído','in-progress':'Em andamento','not-started':'Não iniciado'};
  const cls={completed:'p-cp','in-progress':'p-ip','not-started':'p-ns'};
  const mods=c.modules?.length||0;
  return `<div class="cc" onclick="activeCourseId=${c.id};go('courseViewer')">
    <div class="cth"><div class="cth-ico">${c.ico||'📚'}</div><div class="ctag">${c.category||'Geral'}</div></div>
    <div class="cbody">
      <div class="ctitle">${c.title}</div>
      <div class="cinst">👤 ${c.instructor}</div>
      <div class="pb"><div class="pbf" style="width:${pct}%"></div></div>
      <div class="pi"><span class="pi-p">${pct}%</span><span class="pi-m">${c.hours}h · ${mods} módulo(s)</span></div>
      <span class="cpill ${cls[status]}">${lbl[status]}</span>
    </div>
  </div>`;
}

/* ════════════════════════════════════════════════════════════════
   COLABORADOR PAGES
════════════════════════════════════════════════════════════════ */
function dashboard(){
  // Colaborador only sees their assigned course
  const userCourses = CU.courseId
    ? COURSES.filter(c=>c.id===CU.courseId)
    : COURSES;
  const done=userCourses.filter(c=>isCourseComplete(CU.id,c.id)).length;
  page('Dashboard','Meu painel de aprendizado','',
    `<button class="btn b-or" style="font-size:12px;padding:9px 18px" onclick="go('myCourses')">Meus Cursos</button>`);
  document.getElementById('main').innerHTML=`
  <div class="pgh"><div><h1>Dashboard</h1><div class="pgcr">Meu painel de aprendizado</div></div></div>
  <div class="pgb">
    <div class="krow" style="grid-template-columns:repeat(3,1fr)">
      <div class="kpi"><div class="kico">📚</div><div class="kval">${userCourses.length}</div><div class="klbl">Cursos</div></div>
      <div class="kpi"><div class="kico">✅</div><div class="kval">${done}</div><div class="klbl">Concluídos</div></div>
      <div class="kpi"><div class="kico">⭐</div><div class="kval">${done===userCourses.length&&userCourses.length>0?'100%':courseProgress(CU.id,CU.courseId||0)+'%'}</div><div class="klbl">Progresso</div></div>
    </div>
    <div class="sh"><h2>Meus Cursos</h2></div>
    <div class="cgrid">${userCourses.map(c=>cc(c)).join('')}</div>
  </div>`;
}

function myCourses(){
  const userCourses = CU.courseId ? COURSES.filter(c=>c.id===CU.courseId) : COURSES;
  document.getElementById('main').innerHTML=`
  <div class="pgh"><div><h1>Meus Cursos</h1><div class="pgcr">Cursos disponíveis para você</div></div></div>
  <div class="pgb"><div class="cgrid">${userCourses.map(c=>cc(c)).join('')}</div></div>`;
}

function courseViewer(){
  const cid = activeCourseId || CU.courseId || COURSES[0]?.id;
  activeCourseId = cid;
  const c = COURSES.find(x=>x.id===cid);
  if(!c){ toast('Curso não encontrado'); return; }
  const uid = CU.id;
  const prog = getProgress(uid,cid);
  const pct = courseProgress(uid,cid);
  const modules = c.modules||[];

  // Build sidebar
  let sbHtml='';
  modules.forEach((m,mi)=>{
    const prevOk = mi===0 || (isModuleLessonsDone(uid,cid,modules[mi-1]) && isModulePassed(uid,cid,modules[mi-1].id));
    const modLocked = c.sequential && !prevOk && mi>0;
    const allLessDone = isModuleLessonsDone(uid,cid,m);
    const quizPassed = isModulePassed(uid,cid,m.id);
    sbHtml+=`<div class="mg">
      <div class="mgl" style="${modLocked?'opacity:.55':''}">
        <span>${modLocked?'🔒 ':allLessDone&&quizPassed?'✅ ':'📦 '}<strong>${m.order||mi+1}.</strong> ${m.title}</span>
      </div>`;
    m.lessons.forEach((l,li)=>{
      const done=isLessonDone(uid,cid,m.id,l.id);
      const lLocked = modLocked || (c.sequential&&li>0&&!isLessonDone(uid,cid,m.id,m.lessons[li-1].id));
      const ico=l.type==='pdf'?'📄':l.type==='video'?'🎬':'📎';
      const lid=`vl-${m.id}-${l.id}`;
      sbHtml+=`<div class="lr ${done?'done':''} ${lLocked?'lr-locked':''}" id="${lid}"
        onclick="${lLocked?`toast('🔒 Conclua a aula anterior primeiro.')`:`showLesson(${cid},${m.id},${l.id})`}">
        <span class="li">${done?'✅':'⭕'}</span>${l.title}
        <span class="lt">${ico} ${l.type.toUpperCase()}</span>
      </div>`;
    });
    // Quiz row
    const qLocked = modLocked || !allLessDone;
    const atts = prog.quizAttempts[m.id]||[];
    const bestAtt = atts.reduce((b,a)=>(!b||a.score>b.score)?a:b, null);
    sbHtml+=`<div class="lr lr-quiz ${qLocked?'lr-locked':''}" id="vq-${m.id}"
      onclick="${qLocked?`toast('📝 Conclua todas as aulas deste módulo para liberar a prova.')`:`showQuiz(${cid},${m.id})`}">
      <span class="li">${quizPassed?'✅':'📝'}</span>
      ${m.quiz?.title||'Avaliação do Módulo'}
      <span class="lt" style="${quizPassed?'color:var(--ok)':qLocked?'color:var(--err)':''}">${quizPassed?'APROVADO':qLocked?'BLOQUEADO':atts.length?'TENTAR NOVO':'DISPONÍVEL'}</span>
    </div>`;
    sbHtml+=`</div>`;
  });

  document.getElementById('main').innerHTML=`
  <div class="pgh">
    <div><h1>${c.title}</h1><div class="pgcr">Meus Cursos → ${c.title}</div></div>
    <button class="btn b-gh" style="font-size:11px;padding:7px 14px" onclick="go('myCourses')">← Voltar</button>
  </div>
  <div class="vwr">
    <div class="vws">
      <div class="vwsh">
        <h3>Conteúdo do Curso</h3>
        <div style="margin-top:8px"><div class="pb"><div class="pbf" style="width:${pct}%"></div></div>
        <div style="font-size:11px;color:var(--t3);margin-top:3px">${pct}% · ${modules.length} módulo(s)</div></div>
      </div>
      ${sbHtml}
    </div>
    <div class="vwc"><div class="vci" id="lessonArea">
      <div style="text-align:center;padding:48px 20px;color:var(--t3)">
        <div style="font-size:48px;margin-bottom:14px">📖</div>
        <div style="font-size:16px;font-weight:700;color:var(--t1);margin-bottom:6px">Bem-vindo, ${CU.name.split(' ')[0]}!</div>
        <p style="font-size:14px">Selecione uma aula no menu lateral para começar.</p>
      </div>
    </div></div>
  </div>`;

  // Auto-select first incomplete lesson
  for(const m of modules){
    for(const l of m.lessons){
      if(!isLessonDone(uid,cid,m.id,l.id)){
        showLesson(cid,m.id,l.id); return;
      }
    }
  }
}

function showLesson(cid,mid,lid){
  const c=COURSES.find(x=>x.id===cid);
  const m=c?.modules?.find(x=>x.id===mid);
  const l=m?.lessons?.find(x=>x.id===lid);
  if(!l) return;
  document.querySelectorAll('.lr').forEach(e=>e.classList.remove('active'));
  document.getElementById(`vl-${mid}-${lid}`)?.classList.add('active');

  const ico=l.type==='pdf'?'📄':l.type==='video'?'🎬':'📎';
  let mediaHtml='';

  if(l.type==='video'){
    if(l.url){
      let src=l.url;
      const yt=l.url.match(/(?:youtube\.com\/watch\?v=|youtu\.be\/)([a-zA-Z0-9_-]{11})/);
      if(yt) src=`https://www.youtube.com/embed/${yt[1]}`;
      mediaHtml=`<div class="vbox"><iframe src="${src}" style="width:100%;height:100%;border:none" allowfullscreen></iframe></div>`;
    } else {
      mediaHtml=`<div class="vbox"><div class="vplay" onclick="toast('▶ Reproduzindo: ${l.title}')">▶</div><div class="vcap">${l.title}</div></div>`;
    }
  } else if(l.type==='pdf'){
    if(l.url){
      // Protected PDF: block download bar, disable right-click
      mediaHtml=`
      <div class="pdf-protected" oncontextmenu="return false">
        <embed src="${l.url}#toolbar=0&navpanes=0&scrollbar=1&statusbar=0&view=FitH" type="application/pdf" style="width:100%;height:100%;border:none">
        <div class="pdf-toolbar-block"></div>
      </div>
      <div class="pdfrow">
        <div class="pdfrow-ico">🔒</div>
        <div class="pdfrow-info"><h4>${l.title}</h4><p>Visualização protegida — download não disponível</p></div>
      </div>`;
    } else {
      mediaHtml=`<div class="pdfrow"><div class="pdfrow-ico">📄</div><div class="pdfrow-info"><h4>${l.title}</h4><p style="color:var(--t3)">Material aguardando upload pelo administrador</p></div></div>`;
    }
  } else {
    mediaHtml=`<div class="pdfrow"><div class="pdfrow-ico">${ico}</div><div class="pdfrow-info"><h4>${l.title}</h4><p>Material complementar</p></div></div>`;
  }

  const done=isLessonDone(CU.id,cid,mid,lid);
  document.getElementById('lessonArea').innerHTML=`
  <div class="vttl">${l.title}</div>
  <div class="vmeta">
    <span style="background:var(--or-lt);color:var(--or);font-size:11px;font-weight:700;padding:2px 9px;border-radius:20px;border:1px solid rgba(255,106,0,.2)">📦 ${m.title}</span>
    <span>👤 ${c.instructor}</span>
  </div>
  ${mediaHtml}
  ${l.text?`<p class="vtxt">${l.text}</p>`:''}
  <div style="display:flex;gap:10px;margin-top:18px;padding-top:16px;border-top:1px solid var(--bdr-lt)">
    ${done
      ? `<button class="btn b-ok" style="cursor:default">✅ Aula Concluída</button>`
      : `<button class="btn b-or" onclick="markLessonDone(${cid},${mid},${lid})">✓ Marcar como Concluída</button>`
    }
  </div>`;
}

function markLessonDone(cid,mid,lid){
  const prog=getProgress(CU.id,cid);
  const key=`${mid}-${lid}`;
  if(!prog.completedLessons.includes(key)) prog.completedLessons.push(key);
  saveProgress();
  toast('✅ Aula concluída!');
  courseViewer(); // refresh to unlock next items
}

/* ════════════════════════════════════════════════════════════════
   QUIZ SYSTEM
════════════════════════════════════════════════════════════════ */
let _activeQuiz=null;

function showQuiz(cid,mid){
  const c=COURSES.find(x=>x.id===cid);
  const m=c?.modules?.find(x=>x.id===mid);
  const quiz=m?.quiz; if(!quiz) return;
  document.querySelectorAll('.lr').forEach(e=>e.classList.remove('active'));
  document.getElementById(`vq-${mid}`)?.classList.add('active');

  const prog=getProgress(CU.id,cid);
  const atts=prog.quizAttempts[mid]||[];
  const maxAtt=quiz.maxAttempts||3;
  const attLeft=maxAtt-atts.length;
  const passed=atts.some(a=>a.pass);

  if(passed){
    showQuizResult(cid,mid,atts[atts.length-1],atts); return;
  }
  if(attLeft<=0){
    document.getElementById('lessonArea').innerHTML=`
    <div class="qcard">
      <div class="qhead"><h2>Tentativas Esgotadas</h2><p>Você utilizou todas as ${maxAtt} tentativas disponíveis.</p></div>
      <div style="text-align:center;padding:24px">
        <div style="font-size:48px;margin-bottom:12px">🚫</div>
        <p style="font-size:15px;color:var(--t2);margin-bottom:18px">Entre em contato com o gestor para solicitar uma nova tentativa.</p>
        ${renderAttemptHistory(atts,quiz.minScore)}
      </div>
    </div>`; return;
  }

  _activeQuiz={cid,mid,quiz,answers:{},submitted:false};

  document.getElementById('lessonArea').innerHTML=`
  <div class="qcard">
    <div class="qhead">
      <h2>${quiz.title}</h2>
      <p>${quiz.questions.length} questão(ões) · Nota mínima: ${quiz.minScore.toFixed(1)} · Tentativa ${atts.length+1}/${maxAtt}</p>
    </div>
    ${quiz.questions.map((q,qi)=>`
    <div class="qb">
      <div class="qn">Questão ${qi+1} de ${quiz.questions.length}</div>
      <div class="qt">${q.txt}</div>
      ${q.opts.map((o,oi)=>`
      <div class="opt" id="qopt-${q.id}-${oi}" onclick="selOpt(${q.id},${oi})">
        <div class="ol">${'ABCD'[oi]}</div>${o}
      </div>`).join('')}
    </div>`).join('')}
    <div class="qfoot">
      <span class="qprog" id="qprog">0/${quiz.questions.length} respondidas</span>
      <button class="btn b-or" onclick="submitQuiz()">Finalizar Avaliação ✓</button>
    </div>
  </div>`;
}

function selOpt(qId,oi){
  if(_activeQuiz?.submitted) return;
  _activeQuiz.answers[qId]=oi;
  _activeQuiz.quiz.questions.find(q=>q.id===qId)?.opts.forEach((_,i)=>document.getElementById(`qopt-${qId}-${i}`)?.classList.remove('sel'));
  document.getElementById(`qopt-${qId}-${oi}`)?.classList.add('sel');
  const answered=Object.keys(_activeQuiz.answers).length;
  const total=_activeQuiz.quiz.questions.length;
  const el=document.getElementById('qprog');
  if(el) el.textContent=`${answered}/${total} respondidas`;
}

function submitQuiz(){
  const aq=_activeQuiz; if(!aq||aq.submitted) return;
  const {cid,mid,quiz}=aq;
  if(Object.keys(aq.answers).length<quiz.questions.length){ toast('⚠️ Responda todas as questões antes de finalizar.'); return; }
  aq.submitted=true;
  let cor=0;
  quiz.questions.forEach(q=>{
    const ans=aq.answers[q.id];
    q.opts.forEach((_,oi)=>{
      const el=document.getElementById(`qopt-${q.id}-${oi}`); if(!el) return;
      el.classList.remove('sel');
      if(oi===q.ok) el.classList.add('ok');
      else if(oi===ans&&ans!==q.ok) el.classList.add('err');
    });
    if(ans===q.ok) cor++;
  });
  const score=+(cor/quiz.questions.length*10).toFixed(1);
  const pass=score>=quiz.minScore;
  const prog=getProgress(CU.id,cid);
  if(!prog.quizAttempts[mid]) prog.quizAttempts[mid]=[];
  const att={ score, pass, correct:cor, total:quiz.questions.length, date:new Date().toISOString() };
  prog.quizAttempts[mid].push(att);
  saveProgress();
  showQuizResult(cid,mid,att,prog.quizAttempts[mid]);
}

function showQuizResult(cid,mid,lastAtt,allAtts){
  const c=COURSES.find(x=>x.id===cid);
  const m=c?.modules?.find(x=>x.id===mid);
  const quiz=m?.quiz;
  const {score,pass,correct,total}=lastAtt;
  const maxAtt=quiz?.maxAttempts||3;
  const attLeft=maxAtt-allAtts.length;
  const courseDone=isCourseComplete(CU.id,cid);
  const foot=document.getElementById('lessonArea');
  if(foot) foot.innerHTML=`
  <div class="qcard">
    <div class="qhead"><h2>${quiz?.title||'Resultado'}</h2></div>
    <div class="resbox">
      <div class="resc ${pass?'pass':'fail'}">${score.toFixed(1)}</div>
      <div class="ressub">${correct}/${total} corretas · mínimo ${quiz?.minScore?.toFixed(1)||'7.0'}</div>
      <div class="resmsg">${pass
        ?`🎉 <strong>Aprovado!</strong> ${courseDone?'Você concluiu todos os módulos! Já pode emitir seu certificado.':'Próximo módulo desbloqueado.'}`
        :`😔 <strong>Não aprovado.</strong> ${attLeft>0?`Você ainda tem <strong>${attLeft}</strong> tentativa(s). Revise o conteúdo e tente novamente.`:'Tentativas esgotadas. Contate o gestor.'}`
      }</div>
      <div style="display:flex;gap:8px;justify-content:center;flex-wrap:wrap">
        ${pass&&courseDone?`<button class="btn b-or" onclick="certificate()">🎓 Emitir Certificado</button>`:''}
        ${!pass&&attLeft>0?`<button class="btn b-gh" onclick="showQuiz(${cid},${mid})">Tentar Novamente</button>`:''}
        <button class="btn b-gh" onclick="courseViewer()">← Voltar ao Curso</button>
      </div>
    </div>
    ${renderAttemptHistory(allAtts,quiz?.minScore||7)}
  </div>`;
}

function renderAttemptHistory(atts,minScore){
  if(!atts||!atts.length) return '';
  return `<div style="margin-top:20px;padding-top:16px;border-top:1px solid var(--bdr-lt)">
    <div style="font-size:11px;font-weight:700;color:var(--t3);text-transform:uppercase;letter-spacing:1px;margin-bottom:10px">Histórico de Tentativas</div>
    ${atts.map((a,i)=>`
    <div class="attempt-row">
      <span style="font-size:11px;font-weight:700;color:var(--t3);width:22px">#${i+1}</span>
      <span class="att-score ${a.pass?'pass':'fail'}">${a.score.toFixed(1)}</span>
      <span style="flex:1;font-size:13px;color:var(--t2)">${a.correct}/${a.total} corretas</span>
      <span class="bdg ${a.pass?'bdg-ok':'bdg-off'}">${a.pass?'Aprovado':'Reprovado'}</span>
      <span style="font-size:11px;color:var(--t3)">${new Date(a.date).toLocaleDateString('pt-BR')}</span>
    </div>`).join('')}
  </div>`;
}

/* ════════════════════════════════════════════════════════════════
   CERTIFICATE (only if course complete)
════════════════════════════════════════════════════════════════ */
function certificate(){
  const cid=activeCourseId||CU.courseId;
  const c=COURSES.find(x=>x.id===cid);
  if(!c){ toast('⚠️ Selecione um curso primeiro.'); return; }
  if(!isCourseComplete(CU.id,cid)){ toast('⚠️ Conclua todos os módulos para emitir o certificado.'); return; }
  const avgScores=c.modules.map(m=>{
    const atts=(getProgress(CU.id,cid).quizAttempts[m.id]||[]);
    const best=atts.reduce((b,a)=>a.score>b.score?a:b,{score:0});
    return best.score;
  }).filter(s=>s>0);
  const avg=avgScores.length?+(avgScores.reduce((a,b)=>a+b,0)/avgScores.length).toFixed(1):0;
  const certHtml=`
  <div class="cert" id="certBlock">
    <div style="display:flex;align-items:center;justify-content:center;gap:12px;margin-bottom:10px">
      <div class="lm" style="width:40px;height:40px;font-size:14px">CAW</div>
      <div style="text-align:left"><div class="cert-co">CAW PROJETOS E CONSULTORIA INDUSTRIAL</div><div class="cert-cos">Programa de Treinamento Técnico Interno</div></div>
    </div>
    <div class="cert-h1">Certifi<em>cado</em> de Conclusão</div>
    <div class="cert-h2">Este documento certifica que</div>
    <div class="cert-nm">${CU.name}</div>
    <div class="cert-bd">concluiu com êxito o curso técnico industrial</div>
    <div class="cert-cs">${c.title}</div>
    <div style="font-size:13px;color:var(--t2);margin-bottom:28px">Carga Horária: ${c.hours}h · Nota Final: ${avg} · ${c.modules.length} módulo(s)</div>
    <div class="cert-ft">
      <div class="csig"><div class="csln"></div><div class="cssn">Hans</div><div class="cssr">Diretor · CAW Industrial</div></div>
      <div style="text-align:center">
        <div style="font-size:10px;color:var(--t3);text-transform:uppercase;letter-spacing:2px">Data de Conclusão</div>
        <div style="font-weight:800;font-size:14px;color:var(--t1);margin-top:2px">${new Date().toLocaleDateString('pt-BR',{day:'2-digit',month:'long',year:'numeric'})}</div>
      </div>
      <div class="csig"><div class="csln"></div><div class="cssn">Geraldo Andrade</div><div class="cssr">Gestor de T&D</div></div>
    </div>
  </div>`;
  document.getElementById('main').innerHTML=`
  <div class="pgh">
    <div><h1>Certificado</h1><div class="pgcr">Certificado de Conclusão — ${c.title}</div></div>
    <button class="btn b-or" onclick="printCert()">🖨 Imprimir / Baixar</button>
  </div>
  <div class="pgb" id="certContainer">${certHtml}</div>`;
  // Store for print
  document.getElementById('printArea').innerHTML=certHtml;
}

function printCert(){
  document.getElementById('printArea').style.display='flex';
  window.print();
  setTimeout(()=>document.getElementById('printArea').style.display='none',1000);
}

/* ════════════════════════════════════════════════════════════════
   RANKING
════════════════════════════════════════════════════════════════ */
function ranking(){
  const data=USERS.filter(u=>u.type==='colaborador'&&u.active).map(u=>{
    const courses=COURSES.filter(c=>c.id===u.courseId||!u.courseId);
    const scores=[];
    courses.forEach(c=>c.modules.forEach(m=>{
      const atts=getProgress(u.id,c.id).quizAttempts[m.id]||[];
      if(atts.length) scores.push(Math.max(...atts.map(a=>a.score)));
    }));
    const avg=scores.length?+(scores.reduce((a,b)=>a+b,0)/scores.length).toFixed(1):0;
    const done=courses.filter(c=>isCourseComplete(u.id,c.id)).length;
    return {u,avg,done};
  }).sort((a,b)=>b.avg-a.avg||b.done-a.done);

  page('Ranking','Colaboradores mais engajados',`
  <div style="max-width:640px">
    ${data.length?data.map(({u,avg,done},i)=>`
    <div class="rkr">
      <div class="rkp ${i<3?'top':''}">${i===0?'🥇':i===1?'🥈':i===2?'🥉':(i+1)}</div>
      <div class="rkav" style="background:${u.color||'#999'}">${u.ini||u.name[0]}</div>
      <div style="flex:1"><div class="rknm">${u.name}${u.id===CU.id?' <span style="background:var(--or);color:#fff;font-size:9px;padding:1px 7px;border-radius:10px;margin-left:5px">VOCÊ</span>':''}</div>
      <div class="rkdt">${u.sector||'—'} · ${done} concluído(s)</div></div>
      <div class="rksc">${avg>0?avg.toFixed(1):'—'}</div>
    </div>`).join(''):`<div style="text-align:center;padding:32px;color:var(--t3)">Nenhum dado disponível ainda.</div>`}
  </div>`);
}

/* ════════════════════════════════════════════════════════════════
   GESTOR PAGES (read-only)
════════════════════════════════════════════════════════════════ */
function roAlert(){ return `<div style="background:#EDE9FE;border:1px solid #C4B5FD;border-radius:8px;padding:11px 14px;margin-bottom:18px;font-size:13px;color:#5B21B6;display:flex;align-items:center;gap:8px"><strong>🔒 Modo Leitura.</strong> Acesse como Master para realizar edições.</div>`; }

function gDash(){
  const colabors=USERS.filter(u=>u.type==='colaborador'&&u.active);
  page('Dashboard Gestor','Visualização — sem permissão de edição',`
  ${roAlert()}
  <div class="krow">
    <div class="kpi"><div class="kico">👥</div><div class="kval">${colabors.length}</div><div class="klbl">Colaboradores</div></div>
    <div class="kpi"><div class="kico">📚</div><div class="kval">${COURSES.length}</div><div class="klbl">Cursos</div></div>
    <div class="kpi"><div class="kico">📦</div><div class="kval">${COURSES.reduce((s,c)=>s+(c.modules?.length||0),0)}</div><div class="klbl">Módulos</div></div>
    <div class="kpi"><div class="kico">🎓</div><div class="kval">${colabors.filter(u=>u.courseId&&isCourseComplete(u.id,u.courseId)).length}</div><div class="klbl">Certificados</div></div>
  </div>
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:16px">
    <div class="cht"><div class="chtt">Progresso dos Colaboradores</div>
      ${colabors.map(u=>`<div style="margin-bottom:10px">
        <div style="display:flex;justify-content:space-between;font-size:13px;font-weight:600;margin-bottom:4px;color:var(--t2)">
          <span>${u.name}</span><span style="color:var(--or)">${u.courseId?courseProgress(u.id,u.courseId):0}%</span>
        </div>
        <div class="pb" style="height:6px"><div class="pbf" style="width:${u.courseId?courseProgress(u.id,u.courseId):0}%"></div></div>
      </div>`).join('')}
    </div>
    <div class="cht"><div class="chtt">Cursos</div>
      ${COURSES.map(c=>`<div style="display:flex;align-items:center;justify-content:space-between;padding:8px 0;border-bottom:1px solid var(--bdr-lt)">
        <span style="font-size:13px;color:var(--t2)">${c.ico||'📚'} ${c.title}</span>
        <span class="bdg bdg-tag">${c.modules?.length||0} módulos</span>
      </div>`).join('')}
    </div>
  </div>`);
}

function gUsers(){
  const rows=USERS.filter(u=>u.type==='colaborador').map(u=>`<tr>
    <td><strong style="color:var(--t1)">${u.name}</strong><br><small style="color:var(--t3)">@${u.login}</small></td>
    <td>${u.role||'—'}</td><td>${u.sector||'—'}</td>
    <td>${u.courseId?`<span class="course-tag">${COURSES.find(c=>c.id===u.courseId)?.title||'—'}</span>`:'—'}</td>
    <td><span class="bdg ${u.active?'bdg-ok':'bdg-off'}">${u.active?'Ativo':'Inativo'}</span></td>
    <td><strong style="color:var(--or)">${u.courseId?courseProgress(u.id,u.courseId):0}%</strong></td>
  </tr>`).join('');
  page('Colaboradores','Visualização — sem permissão de edição',roAlert()+`<div style="overflow-x:auto"><table class="tbl"><thead><tr><th>Nome</th><th>Cargo</th><th>Setor</th><th>Curso</th><th>Status</th><th>Progresso</th></tr></thead><tbody>${rows}</tbody></table></div>`);
}

function gCourses(){
  const rows=COURSES.map(c=>`<tr>
    <td><div style="display:flex;align-items:center;gap:10px"><div style="font-size:26px">${c.ico||'📚'}</div><div><strong style="color:var(--t1)">${c.title}</strong><br><small style="color:var(--t3)">${c.instructor}</small></div></div></td>
    <td><span class="bdg bdg-tag">${c.category||'Geral'}</span></td>
    <td>${c.modules?.length||0} módulos</td><td>${c.hours}h</td><td><strong style="color:var(--or)">${c.minScore.toFixed(1)}</strong></td>
  </tr>`).join('');
  page('Cursos','Visualização — sem permissão de edição',roAlert()+`<div style="overflow-x:auto"><table class="tbl"><thead><tr><th>Curso</th><th>Categoria</th><th>Módulos</th><th>Carga H.</th><th>Nota Mín.</th></tr></thead><tbody>${rows}</tbody></table></div>`);
}

function gReports(){
  const colabors=USERS.filter(u=>u.type==='colaborador'&&u.active);
  page('Relatórios','Análise de desempenho',roAlert()+`
  <div class="krow">
    <div class="kpi"><div class="kico">📈</div><div class="kval">${Math.round(colabors.reduce((s,u)=>s+(u.courseId?courseProgress(u.id,u.courseId):0),0)/(colabors.length||1))}%</div><div class="klbl">Progresso Médio</div></div>
    <div class="kpi"><div class="kico">🎓</div><div class="kval">${colabors.filter(u=>u.courseId&&isCourseComplete(u.id,u.courseId)).length}</div><div class="klbl">Concluídos</div></div>
    <div class="kpi"><div class="kico">📚</div><div class="kval">${COURSES.length}</div><div class="klbl">Cursos</div></div>
    <div class="kpi"><div class="kico">📦</div><div class="kval">${COURSES.reduce((s,c)=>s+(c.modules?.length||0),0)}</div><div class="klbl">Módulos</div></div>
  </div>
  <div class="cht"><div class="chtt">Progresso Individual</div>
    <div style="overflow-x:auto"><table class="tbl" style="box-shadow:none;border:none">
      <thead><tr><th>Colaborador</th><th>Curso</th><th>Progresso</th><th>Aprovações</th><th>Status</th></tr></thead>
      <tbody>${colabors.map(u=>{
        const c=COURSES.find(x=>x.id===u.courseId);
        const pct=c?courseProgress(u.id,c.id):0;
        const passed=c?c.modules.filter(m=>isModulePassed(u.id,c.id,m.id)).length:0;
        const done=c&&isCourseComplete(u.id,c.id);
        return `<tr>
          <td><strong style="color:var(--t1)">${u.name}</strong></td>
          <td>${c?`<span class="course-tag">${c.title}</span>`:'—'}</td>
          <td><div style="display:flex;align-items:center;gap:8px"><div class="pb" style="width:80px;margin:0"><div class="pbf" style="width:${pct}%"></div></div><span style="font-size:12px;font-weight:700;color:var(--or)">${pct}%</span></div></td>
          <td>${c?`${passed}/${c.modules.length} módulos`:'—'}</td>
          <td><span class="bdg ${done?'bdg-ok':pct>0?'bdg-tag':'bdg-off'}">${done?'Concluído':pct>0?'Em andamento':'Não iniciado'}</span></td>
        </tr>`;}).join('')}
      </tbody>
    </table></div>
  </div>`);
}

/* ════════════════════════════════════════════════════════════════
   MASTER PAGES
════════════════════════════════════════════════════════════════ */
function mDash(){
  const colabors=USERS.filter(u=>u.type==='colaborador'&&u.active);
  page('Dashboard Master','Controle total da plataforma',`
  <div class="krow">
    <div class="kpi"><div class="kico">👥</div><div class="kval">${USERS.length}</div><div class="klbl">Total Usuários</div></div>
    <div class="kpi"><div class="kico">📚</div><div class="kval">${COURSES.length}</div><div class="klbl">Cursos</div></div>
    <div class="kpi"><div class="kico">📦</div><div class="kval">${COURSES.reduce((s,c)=>s+(c.modules?.length||0),0)}</div><div class="klbl">Módulos</div></div>
    <div class="kpi"><div class="kico">🎓</div><div class="kval">${colabors.filter(u=>u.courseId&&isCourseComplete(u.id,u.courseId)).length}</div><div class="klbl">Certificados</div></div>
  </div>
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:16px">
    <div class="cht"><div class="chtt">Conclusões por Mês</div>
      <div class="bch">${[['Out',55],['Nov',72],['Dez',68],['Jan',85],['Fev',91]].map(([m,v])=>`<div class="bg"><div class="bar" style="height:${v}%"></div><div class="brl">${m}</div></div>`).join('')}</div>
    </div>
    <div class="cht"><div class="chtt">Usuários por Tipo</div>
      ${[['master','Master','#92400E'],['gestor','Gestor','#5B21B6'],['colaborador','Colaborador','#FF6A00']].map(([t,l,c])=>{
        const cnt=USERS.filter(u=>u.type===t).length;
        return `<div style="display:flex;align-items:center;gap:10px;padding:8px 0;border-bottom:1px solid var(--bdr-lt)">
          <div style="width:10px;height:10px;border-radius:50%;background:${c}"></div>
          <span style="flex:1;font-size:13px;font-weight:600;color:var(--t2)">${l}</span>
          <strong style="color:var(--t1);font-size:16px">${cnt}</strong>
        </div>`;}).join('')}
    </div>
  </div>`,
  `<button class="btn b-or" style="font-size:12px;padding:9px 18px" onclick="go('mNewCourse')">+ Novo Curso</button>
   <button class="btn b-gh" style="font-size:12px;padding:9px 18px" onclick="go('mNewUser')">+ Novo Usuário</button>`);
}

/* ── MASTER: USUÁRIOS ─────────────────────────────────────────── */
function mUsers(){
  const rows=USERS.map(u=>{
    const tl={master:'Master',gestor:'Gestor',colaborador:'Colaborador'}[u.type];
    const tc={master:'ab-master',gestor:'ab-gestor',colaborador:'ab-colab'}[u.type];
    const c=COURSES.find(x=>x.id===u.courseId);
    return `<tr>
      <td><div style="display:flex;align-items:center;gap:9px">
        <div style="width:33px;height:33px;border-radius:8px;background:${u.color||'#999'};display:flex;align-items:center;justify-content:center;font-weight:800;font-size:12px;color:#fff;flex-shrink:0">${u.ini||u.name[0]}</div>
        <div><strong style="color:var(--t1)">${u.name}</strong><br><small style="color:var(--t3)">@${u.login}</small></div>
      </div></td>
      <td>${u.role||'—'}<br><small style="color:var(--t3)">${u.sector||'—'}</small></td>
      <td>${c?`<span class="course-tag">${c.title}</span>`:'<span style="color:var(--t3);font-size:12px">—</span>'}</td>
      <td><span class="abadge ${tc}">${tl}</span></td>
      <td><span class="bdg ${u.active?'bdg-ok':'bdg-off'}">${u.active?'Ativo':'Inativo'}</span></td>
      <td style="display:flex;gap:5px">
        <button class="btn b-sm" onclick="go('mNewUser');setTimeout(()=>loadUserEdit(${u.id}),50)">Editar</button>
        ${u.type!=='master'?`<button class="btn b-danger" onclick="toggleUser(${u.id})">${u.active?'Desativar':'Ativar'}</button>`:''}
      </td>
    </tr>`;}).join('');
  page('Usuários','Gerenciar todos os acessos',
    `<div style="overflow-x:auto"><table class="tbl"><thead><tr><th>Usuário</th><th>Cargo / Setor</th><th>Curso</th><th>Tipo</th><th>Status</th><th>Ações</th></tr></thead><tbody>${rows}</tbody></table></div>`,
    `<button class="btn b-or" style="font-size:12px;padding:9px 18px" onclick="go('mNewUser')">+ Novo Usuário</button>`);
}

function toggleUser(id){
  const u=USERS.find(x=>x.id===id); if(!u) return;
  u.active=!u.active; saveUsers();
  toast(u.active?'✅ Usuário ativado':'⛔ Usuário desativado'); mUsers();
}

function loadUserEdit(id){
  const u=USERS.find(x=>x.id===id); if(!u) return;
  document.getElementById('eu-name').value=u.name;
  document.getElementById('eu-login').value=u.login;
  document.getElementById('eu-role').value=u.role||'';
  document.getElementById('eu-sector').value=u.sector||'';
  if(document.getElementById('eu-course')) document.getElementById('eu-course').value=u.courseId||'';
  onCourseChange(u.courseId);
  selectAccess(u.type);
  document.getElementById('mNewUser-editId').value=id;
}

function mNewUser(){
  const courseOpts=COURSES.map(c=>`<option value="${c.id}">${c.ico||'📚'} ${c.title}</option>`).join('');
  document.getElementById('main').innerHTML=`
  <div class="pgh">
    <div><h1>Novo Usuário</h1><div class="pgcr">Master → Usuários → Cadastrar acesso</div></div>
    <button class="btn b-gh" style="font-size:12px;padding:8px 16px" onclick="go('mUsers')">← Voltar</button>
  </div>
  <div class="pgb"><div style="max-width:860px">
  <input type="hidden" id="mNewUser-editId" value="">

  <div class="fcard" style="margin-bottom:22px">
    <div class="form-section-label"><span class="form-section-num">1</span>Dados Pessoais e Login</div>
    <div class="form-cols-2" style="margin-bottom:20px">
      <div><label class="form-label">Nome Completo <span class="form-req">*</span></label>
        <input id="eu-name" type="text" class="form-input" style="font-size:16px;padding:14px 16px" placeholder="Ex: João da Silva">
      </div>
      <div><label class="form-label">Login <span class="form-req">*</span></label>
        <input id="eu-login" type="text" class="form-input" style="font-size:16px;padding:14px 16px" placeholder="joao.silva"
          oninput="this.value=this.value.toLowerCase().replace(/\\s+/g,'-')">
        <span class="form-hint">Sem espaços. Minúsculas. Ex: joao.silva</span>
      </div>
    </div>
    <div class="form-cols-2" style="margin-bottom:20px">
      <div><label class="form-label">Senha <span class="form-req">*</span></label>
        <div style="position:relative">
          <input id="eu-pass" type="password" class="form-input" style="font-size:16px;padding:14px 48px 14px 16px" placeholder="Mínimo 6 caracteres">
          <button type="button" onclick="togglePwd('eu-pass',this)" style="position:absolute;right:14px;top:50%;transform:translateY(-50%);background:none;border:none;cursor:pointer;font-size:18px;color:var(--t3)">👁</button>
        </div>
      </div>
      <div><label class="form-label">Confirmar Senha <span class="form-req">*</span></label>
        <div style="position:relative">
          <input id="eu-pass2" type="password" class="form-input" style="font-size:16px;padding:14px 48px 14px 16px" placeholder="Repetir senha">
          <button type="button" onclick="togglePwd('eu-pass2',this)" style="position:absolute;right:14px;top:50%;transform:translateY(-50%);background:none;border:none;cursor:pointer;font-size:18px;color:var(--t3)">👁</button>
        </div>
      </div>
    </div>
    <div class="form-cols-2">
      <div><label class="form-label">Cargo / Função</label>
        <input id="eu-role" type="text" class="form-input" style="font-size:15px;padding:12px 15px" placeholder="Operador CNC, Técnico...">
      </div>
      <div><label class="form-label">Setor / Departamento</label>
        <select id="eu-sector" class="form-input" style="font-size:15px;padding:12px 15px">
          <option value="">Selecione...</option>
          <option>Produção</option><option>Qualidade</option><option>Manutenção</option>
          <option>Segurança / SST</option><option>Engenharia</option><option>Gestão</option>
          <option>Diretoria</option><option>Administrativo</option>
        </select>
      </div>
    </div>
  </div>

  <div class="fcard" style="margin-bottom:22px">
    <div class="form-section-label"><span class="form-section-num">2</span>Vínculo de Curso e Nível de Acesso</div>
    <div class="form-info-box" style="margin-bottom:20px">
      <span style="font-size:20px">🔗</span>
      <div><strong>Curso determina o nível de acesso</strong>
      <p>Selecione o curso e o nível será sugerido automaticamente. Cursos de Gestão sugerem Gestor; demais sugerem Colaborador. Você pode alterar manualmente.</p></div>
    </div>
    <div style="margin-bottom:20px">
      <label class="form-label">Curso de Matrícula <span class="form-req">*</span></label>
      <select id="eu-course" class="form-input" style="font-size:15px;padding:12px 15px" onchange="onCourseChange(this.value)">
        <option value="">— Selecione um curso —</option>
        ${courseOpts}
      </select>
    </div>
    <div id="course-preview" style="display:none;background:var(--surf2);border:1px solid var(--bdr);border-radius:10px;padding:16px;margin-bottom:20px">
      <div style="display:flex;align-items:center;gap:12px">
        <div id="cp-ico" style="font-size:32px">📚</div>
        <div style="flex:1">
          <div id="cp-title" style="font-size:16px;font-weight:700;color:var(--t1)">—</div>
          <div id="cp-meta" style="font-size:13px;color:var(--t3);margin-top:3px">—</div>
        </div>
        <span id="cp-badge" class="abadge ab-colab">Colaborador</span>
      </div>
      <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-top:14px;padding-top:14px;border-top:1px solid var(--bdr-lt)">
        <div style="text-align:center"><div id="cp-hours" class="fpb-val">—</div><div class="fpb-lbl">Carga Horária</div></div>
        <div style="text-align:center"><div id="cp-score" class="fpb-val">—</div><div class="fpb-lbl">Nota Mínima</div></div>
        <div style="text-align:center"><div id="cp-mods" class="fpb-val">—</div><div class="fpb-lbl">Módulos</div></div>
      </div>
    </div>
    <div>
      <label class="form-label">Nível de Acesso <span class="form-req">*</span></label>
      <div class="form-cols-3" style="margin-top:10px">
        <div class="access-card" id="ac-colaborador" onclick="selectAccess('colaborador')">
          <div style="font-size:26px;margin-bottom:7px">🟠</div>
          <div style="font-weight:700;font-size:14px;color:var(--t1)">Colaborador</div>
          <div style="font-size:12px;color:var(--t3);margin-top:4px;line-height:1.5">Acessa cursos, faz avaliações e recebe certificado</div>
        </div>
        <div class="access-card" id="ac-gestor" onclick="selectAccess('gestor')">
          <div style="font-size:26px;margin-bottom:7px">🟣</div>
          <div style="font-weight:700;font-size:14px;color:var(--t1)">Gestor</div>
          <div style="font-size:12px;color:var(--t3);margin-top:4px;line-height:1.5">Visualiza relatórios e acompanha a equipe</div>
        </div>
        <div class="access-card" id="ac-master" onclick="selectAccess('master')">
          <div style="font-size:26px;margin-bottom:7px">🟡</div>
          <div style="font-weight:700;font-size:14px;color:var(--t1)">Master</div>
          <div style="font-size:12px;color:var(--t3);margin-top:4px;line-height:1.5">Acesso total: cria cursos e gerencia usuários</div>
        </div>
      </div>
      <input type="hidden" id="eu-type" value="colaborador">
    </div>
  </div>

  <div class="fcard" style="margin-bottom:22px">
    <div class="form-section-label"><span class="form-section-num">3</span>Informações Complementares</div>
    <div class="form-cols-2">
      <div><label class="form-label">E-mail</label><input id="eu-email" type="email" class="form-input" style="font-size:15px;padding:12px 15px" placeholder="nome@empresa.com.br"></div>
      <div><label class="form-label">Observações</label><input id="eu-obs" type="text" class="form-input" style="font-size:15px;padding:12px 15px" placeholder="Notas internas (opcional)"></div>
    </div>
  </div>

  <div class="form-actions">
    <button class="btn b-gh" style="padding:13px 28px" onclick="go('mUsers')">Cancelar</button>
    <button class="btn b-or" style="padding:14px 42px;font-size:14px" onclick="saveNewUser()">✅ Salvar Usuário</button>
  </div>
  </div></div>`;
  selectAccess('colaborador');
}

function togglePwd(id,btn){ const el=document.getElementById(id); if(!el) return; el.type=el.type==='password'?'text':'password'; btn.textContent=el.type==='password'?'👁':'🙈'; }

function onCourseChange(cid){
  const p=document.getElementById('course-preview'); if(!p) return;
  if(!cid){ p.style.display='none'; return; }
  const c=COURSES.find(x=>x.id==cid);
  if(!c){ p.style.display='none'; return; }
  p.style.display='block';
  document.getElementById('cp-ico').textContent=c.ico||'📚';
  document.getElementById('cp-title').textContent=c.title;
  document.getElementById('cp-meta').textContent=`${c.instructor} · ${c.category||'Geral'}`;
  document.getElementById('cp-hours').textContent=c.hours+'h';
  document.getElementById('cp-score').textContent=c.minScore.toFixed(1);
  document.getElementById('cp-mods').textContent=c.modules?.length||0;
  const autoType=['Gestão','Administração','RH'].includes(c.category)?'gestor':'colaborador';
  selectAccess(autoType);
}

function selectAccess(type){
  document.querySelectorAll('.access-card').forEach(el=>el.classList.remove('access-card-active'));
  document.getElementById('ac-'+type)?.classList.add('access-card-active');
  const ti=document.getElementById('eu-type'); if(ti) ti.value=type;
  const badge=document.getElementById('cp-badge');
  if(badge){ badge.className='abadge '+{master:'ab-master',gestor:'ab-gestor',colaborador:'ab-colab'}[type]; badge.textContent={master:'Master',gestor:'Gestor',colaborador:'Colaborador'}[type]; }
}

function saveNewUser(){
  const nm=document.getElementById('eu-name').value.trim();
  const lg=document.getElementById('eu-login').value.trim().toLowerCase();
  const ps=document.getElementById('eu-pass').value;
  const ps2=document.getElementById('eu-pass2').value;
  const rl=document.getElementById('eu-role').value.trim();
  const sc=document.getElementById('eu-sector').value.trim();
  const tp=document.getElementById('eu-type').value;
  const cid=document.getElementById('eu-course').value;
  const editId=document.getElementById('mNewUser-editId')?.value;

  if(!nm||!lg){ toast('⚠️ Preencha Nome e Login.'); return; }
  if(!editId&&!ps){ toast('⚠️ Preencha a senha.'); return; }
  if(ps&&ps!==ps2){ toast('⚠️ As senhas não coincidem.'); return; }
  if(ps&&ps.length<6){ toast('⚠️ Senha: mínimo 6 caracteres.'); return; }
  if(!cid&&tp==='colaborador'){ toast('⚠️ Selecione o curso de matrícula.'); return; }
  if(!editId&&USERS.find(u=>u.login===lg)){ toast('⚠️ Login já em uso.'); return; }

  const c=COURSES.find(x=>x.id==cid);
  const ini=nm.split(' ').filter(Boolean).map(w=>w[0]).join('').substring(0,2).toUpperCase();
  const colors=['#FF6A00','#3b82f6','#8b5cf6','#f59e0b','#10b981','#ef4444'];

  if(editId){
    const u=USERS.find(x=>x.id==editId);
    if(u){ Object.assign(u,{name:nm,login:lg,role:rl,sector:sc,type:tp,courseId:cid?Number(cid):null,ini,email:document.getElementById('eu-email')?.value||''});
      if(ps) u.pass=ps; saveUsers(); toast(`✅ Usuário "${nm}" atualizado!`); go('mUsers'); return; }
  }

  USERS.push({ id:Date.now(),name:nm,login:lg,pass:ps,role:rl||'Colaborador',sector:sc||'Geral',type:tp,courseId:cid?Number(cid):null,ini,email:document.getElementById('eu-email')?.value||'',color:colors[USERS.length%colors.length],active:true });
  saveUsers(); toast(`✅ Usuário "${nm}" cadastrado!`); go('mUsers');
}

/* ── MASTER: CURSOS ───────────────────────────────────────────── */
function mCourses(){
  const rows=COURSES.map(c=>{
    const totalL=c.modules?.reduce((s,m)=>s+m.lessons.length,0)||0;
    return `<tr>
      <td><div style="display:flex;align-items:center;gap:10px"><div style="font-size:28px">${c.ico||'📚'}</div><div>
        <strong style="color:var(--t1)">${c.title}</strong><br><small style="color:var(--t3)">👤 ${c.instructor}</small>
      </div></div></td>
      <td><span class="bdg bdg-tag">${c.category||'Geral'}</span></td>
      <td><strong style="color:var(--or)">${c.modules?.length||0}</strong><br><small style="color:var(--t3)">${totalL} aulas</small></td>
      <td>${c.hours}h</td><td><strong style="color:var(--or)">${c.minScore.toFixed(1)}</strong></td>
      <td style="display:flex;gap:5px">
        <button class="btn b-sm" onclick="editCourse(${c.id})">Editar</button>
        <button class="btn b-danger" onclick="deleteCourse(${c.id})">Excluir</button>
      </td>
    </tr>`;}).join('');
  page('Gestão de Cursos','Criar, editar e excluir cursos',
    `<div style="overflow-x:auto"><table class="tbl"><thead><tr><th>Curso</th><th>Categoria</th><th>Módulos</th><th>Carga H.</th><th>Nota Mín.</th><th>Ações</th></tr></thead><tbody>${rows}</tbody></table></div>`,
    `<button class="btn b-or" style="font-size:12px;padding:9px 18px" onclick="go('mNewCourse')">+ Novo Curso</button>`);
}

function deleteCourse(id){
  if(!confirm('Excluir este curso? Esta ação não pode ser desfeita.')) return;
  COURSES=COURSES.filter(c=>c.id!==id); saveCourses(); toast('🗑 Curso excluído.'); mCourses();
}

function editCourse(id){
  go('mNewCourse'); setTimeout(()=>{
    const c=COURSES.find(x=>x.id===id); if(!c) return;
    document.getElementById('nc-title').value=c.title;
    document.getElementById('nc-inst').value=c.instructor;
    document.getElementById('nc-cat').value=c.category||'';
    document.getElementById('nc-hours').value=c.hours;
    document.getElementById('nc-score').value=c.minScore;
    document.getElementById('nc-maxatt').value=c.maxAttempts||3;
    document.getElementById('nc-seq').value=c.sequential?'true':'false';
    document.getElementById('nc-ico').value=c.ico||'';
    document.getElementById('nc-editId').value=id;
    c.modules?.forEach(m=>addModule(m));
  },80);
}

function mNewCourse(){
  document.getElementById('main').innerHTML=`
  <div class="pgh">
    <div><h1>Novo Curso</h1><div class="pgcr">Master → Cursos → Criar</div></div>
    <button class="btn b-gh" style="font-size:12px;padding:8px 16px" onclick="go('mCourses')">← Voltar</button>
  </div>
  <div class="pgb"><div style="max-width:920px">
  <input type="hidden" id="nc-editId" value="">

  <div class="fcard" style="margin-bottom:22px">
    <div class="form-section-label"><span class="form-section-num">1</span>Identificação do Curso</div>
    <div style="margin-bottom:20px">
      <label class="form-label">Título do Curso <span class="form-req">*</span></label>
      <input id="nc-title" type="text" class="form-input" style="font-size:17px;padding:15px 16px"
        placeholder="Ex: NR-12 — Segurança em Máquinas e Equipamentos Industriais">
    </div>
    <div class="form-cols-3" style="margin-bottom:20px">
      <div><label class="form-label">Instrutor <span class="form-req">*</span></label>
        <input id="nc-inst" type="text" class="form-input" style="font-size:15px;padding:13px 15px" placeholder="Nome do instrutor">
      </div>
      <div><label class="form-label">Categoria</label>
        <select id="nc-cat" class="form-input" style="font-size:15px;padding:13px 15px">
          <option value="">Selecione...</option>
          <option>Segurança</option><option>Técnico</option><option>Qualidade</option>
          <option>Manutenção</option><option>Saúde</option><option>Gestão</option><option>Engenharia</option>
        </select>
      </div>
      <div><label class="form-label">Ícone</label>
        <input id="nc-ico" type="text" class="form-input" style="font-size:26px;text-align:center;padding:10px 15px" placeholder="⚙️" maxlength="4">
      </div>
    </div>
    <div><label class="form-label">Descrição / Ementa</label>
      <textarea id="nc-desc" class="form-input" rows="2" style="font-size:14px;resize:vertical"
        placeholder="Objetivo do curso, público-alvo e principais tópicos..."></textarea>
    </div>
  </div>

  <div class="fcard" style="margin-bottom:22px">
    <div class="form-section-label"><span class="form-section-num">2</span>Configurações de Aprovação</div>
    <div class="form-cols-3" style="margin-bottom:20px">
      <div><label class="form-label">Carga Horária</label>
        <div class="form-input-with-unit">
          <input id="nc-hours" type="number" min="1" max="999" value="16" class="form-input" style="font-size:16px;padding:13px 15px"
            oninput="document.getElementById('prev-hours').textContent=this.value+'h'">
          <span class="form-unit">horas</span>
        </div>
      </div>
      <div><label class="form-label">Nota Mínima para Aprovação</label>
        <div class="form-input-with-unit">
          <input id="nc-score" type="number" min="0" max="10" step="0.5" value="7.0" class="form-input" style="font-size:16px;padding:13px 15px"
            oninput="document.getElementById('prev-score').textContent=parseFloat(this.value||0).toFixed(1)">
          <span class="form-unit">/ 10</span>
        </div>
        <span class="form-hint">Aplicada a todos os módulos do curso</span>
      </div>
      <div><label class="form-label">Nº Máximo de Tentativas</label>
        <div class="form-input-with-unit">
          <input id="nc-maxatt" type="number" min="1" max="99" value="3" class="form-input" style="font-size:16px;padding:13px 15px"
            oninput="document.getElementById('prev-att').textContent=this.value+'x'">
          <span class="form-unit">vezes</span>
        </div>
      </div>
    </div>
    <div style="margin-bottom:20px">
      <label class="form-label">Liberação dos Módulos</label>
      <select id="nc-seq" class="form-input" style="font-size:15px;padding:13px 15px;max-width:380px"
        onchange="document.getElementById('prev-seq').textContent=this.value==='true'?'Sequencial':'Livre'">
        <option value="true">Sequencial — deve concluir um módulo para acessar o próximo</option>
        <option value="false">Livre — pode acessar todos os módulos sem ordem</option>
      </select>
    </div>
    <div class="form-preview-bar">
      <div class="fpb-item"><span class="fpb-ico">⏱</span><span class="fpb-val" id="prev-hours">16h</span><span class="fpb-lbl">Carga horária</span></div>
      <div class="fpb-item"><span class="fpb-ico">✅</span><span class="fpb-val" id="prev-score">7.0</span><span class="fpb-lbl">Nota mínima</span></div>
      <div class="fpb-item"><span class="fpb-ico">🔁</span><span class="fpb-val" id="prev-att">3x</span><span class="fpb-lbl">Tentativas</span></div>
      <div class="fpb-item"><span class="fpb-ico">🔒</span><span class="fpb-val" id="prev-seq">Sequencial</span><span class="fpb-lbl">Liberação</span></div>
      <div class="fpb-item"><span class="fpb-ico">📦</span><span class="fpb-val" id="prev-mods">0</span><span class="fpb-lbl">Módulos</span></div>
    </div>
  </div>

  <div class="fcard" style="margin-bottom:22px">
    <div class="form-section-label">
      <span class="form-section-num">3</span>
      Módulos, Aulas e Provas
      <button class="btn b-or" style="margin-left:auto;padding:8px 18px;font-size:12px" onclick="addModule()">+ Adicionar Módulo</button>
    </div>
    <div class="form-info-box" style="margin-bottom:18px">
      <span style="font-size:20px">📦</span>
      <div><strong>Como funciona a estrutura?</strong>
      <p>Cada módulo agrupa aulas (PDF, vídeo ou link) e possui sua própria prova. O aluno só pode fazer a prova após concluir todas as aulas do módulo. Os módulos seguem a ordem sequencial definida acima.</p></div>
    </div>
    <div id="modules-container">
      <div data-empty style="text-align:center;padding:32px;background:var(--surf2);border:2px dashed var(--bdr);border-radius:10px;color:var(--t3)">
        <div style="font-size:36px;margin-bottom:10px">📦</div>
        <div style="font-weight:700;font-size:15px;margin-bottom:4px">Nenhum módulo criado</div>
        <div style="font-size:13px">Clique em "+ Adicionar Módulo" para começar</div>
      </div>
    </div>
  </div>

  <div class="form-actions">
    <button class="btn b-gh" style="padding:13px 28px" onclick="go('mCourses')">Cancelar</button>
    <button class="btn b-or" style="padding:14px 42px;font-size:14px" onclick="saveCourse()">💾 Salvar e Publicar Curso</button>
  </div>
  </div></div>`;
  window._mods=[]; window._modCtr=0; window._lessCtr=0; window._qCtr=0;
}

let _UPLOADED={pdf:{},video:{}};

function addModule(prefill){
  window._modCtr=(window._modCtr||0)+1;
  const mid=window._modCtr;
  const cont=document.getElementById('modules-container');
  if(cont.querySelector('[data-empty]')) cont.innerHTML='';
  const el=document.createElement('div');
  el.id='mod-'+mid; el.className='module-block';
  el.innerHTML=`
  <div class="module-header">
    <div class="mod-num">${mid}</div>
    <input type="text" class="mod-title-inp" id="mod-t-${mid}"
      placeholder="Título do módulo (ex: Fundamentos da NR-12)"
      value="${prefill?.title||''}">
    <div style="display:flex;gap:6px;align-items:center;flex-shrink:0">
      <span style="font-size:11px;color:var(--t3)">Ordem:</span>
      <input type="number" min="1" value="${prefill?.order||mid}" id="mod-o-${mid}"
        style="width:56px;padding:6px 8px;border:1.5px solid var(--bdr);border-radius:6px;font-size:14px;font-weight:700;text-align:center;outline:none;font-family:'Barlow',sans-serif">
      <button class="btn b-danger" style="font-size:11px;padding:6px 10px" onclick="removeModule(${mid})">🗑</button>
    </div>
  </div>
  <div class="module-body">
    <div class="mod-section">
      <div class="mod-section-hd">
        <span style="font-weight:700;font-size:13px;color:var(--t1)">📖 Aulas do Módulo</span>
        <div style="display:flex;gap:6px;flex-wrap:wrap">
          <button class="btn b-sm" onclick="addLesson(${mid},'pdf')">+ PDF</button>
          <button class="btn b-sm" onclick="addLesson(${mid},'video')">+ Vídeo</button>
          <button class="btn b-sm" onclick="addLesson(${mid},'link')">+ Link</button>
        </div>
      </div>
      <div class="lessons-list" id="lessons-${mid}">
        <div class="list-empty">Nenhuma aula adicionada. Use os botões acima.</div>
      </div>
    </div>
    <div class="mod-section">
      <div class="mod-section-hd">
        <span style="font-weight:700;font-size:13px;color:var(--t1)">📝 Prova do Módulo</span>
        <div style="display:flex;align-items:center;gap:8px">
          <span style="font-size:11px;color:var(--t3);background:var(--surf2);padding:3px 8px;border-radius:6px;border:1px solid var(--bdr)">🔒 Liberada após concluir todas as aulas</span>
          <button class="btn b-sm" onclick="addQuestion(${mid})">+ Questão</button>
        </div>
      </div>
      <div style="margin-bottom:10px">
        <input type="text" class="form-input" id="quiz-t-${mid}" style="font-size:14px;padding:10px 13px"
          placeholder="Título da prova (ex: Avaliação — Módulo 1)"
          value="${prefill?.quiz?.title||''}">
      </div>
      <div class="questions-list" id="questions-${mid}">
        <div class="list-empty">Nenhuma questão adicionada. Clique em "+ Questão".</div>
      </div>
    </div>
  </div>`;
  cont.appendChild(el);
  // Prefill lessons and questions
  prefill?.lessons?.forEach(l=>addLesson(mid,l.type,l));
  prefill?.quiz?.questions?.forEach(q=>addQuestion(mid,q));
  updateModCount();
}

function removeModule(mid){
  document.getElementById('mod-'+mid)?.remove();
  updateModCount();
  const cont=document.getElementById('modules-container');
  if(!cont.children.length) cont.innerHTML='<div data-empty style="text-align:center;padding:32px;background:var(--surf2);border:2px dashed var(--bdr);border-radius:10px;color:var(--t3)"><div style="font-size:36px;margin-bottom:10px">📦</div><div style="font-weight:700;font-size:15px;margin-bottom:4px">Nenhum módulo criado</div><div style="font-size:13px">Clique em "+ Adicionar Módulo" para começar</div></div>';
}

function updateModCount(){ const el=document.getElementById('prev-mods'); if(el) el.textContent=document.querySelectorAll('.module-block').length; }

function addLesson(mid,type,prefill){
  window._lessCtr=(window._lessCtr||0)+1;
  const lid=window._lessCtr;
  const list=document.getElementById('lessons-'+mid); if(!list) return;
  list.querySelectorAll('.list-empty').forEach(e=>e.remove());
  const icons={pdf:'📄',video:'🎬',link:'🔗'};
  const labels={pdf:'PDF',video:'Vídeo',link:'Link Externo'};
  const el=document.createElement('div');
  el.id='less-'+lid; el.className='lesson-item';
  el.innerHTML=`
  <div class="lesson-item-left">
    <div class="lesson-type-ico">${icons[type]||'📎'}</div>
    <div style="flex:1;min-width:0">
      <div style="display:flex;align-items:center;gap:8px;margin-bottom:8px;flex-wrap:wrap">
        <span class="lesson-type-tag">${labels[type]||type}</span>
        <input type="text" class="form-input" id="lt-${lid}" style="flex:1;min-width:120px;font-size:14px;padding:8px 11px"
          placeholder="Título da aula" value="${prefill?.title||''}">
      </div>
      ${type!=='link'?`
      <div class="lesson-upload-row">
        <label class="lesson-upload-btn">
          <input type="file" accept="${type==='pdf'?'.pdf':'video/*'}" style="display:none" onchange="lessonFileChosen(${lid},this)">
          📎 Escolher ${type==='pdf'?'PDF':'vídeo'}
        </label>
        <span id="lf-${lid}" style="font-size:12px;color:var(--t3)">${prefill?.url?'✅ Arquivo carregado':'Nenhum arquivo'}</span>
      </div>`:`
      <input type="url" class="form-input" id="lurl-${lid}" style="font-size:14px;padding:8px 11px;margin-top:6px"
        placeholder="https://youtube.com/watch?v=..." value="${prefill?.url||''}">`}
      <textarea class="form-input" id="ldesc-${lid}" rows="2" style="margin-top:7px;font-size:13px;resize:vertical"
        placeholder="Descrição da aula (opcional)">${prefill?.text||''}</textarea>
    </div>
  </div>
  <button class="btn b-danger" style="align-self:flex-start;font-size:11px;padding:5px 8px;flex-shrink:0"
    onclick="document.getElementById('less-${lid}').remove()">✕</button>`;
  list.appendChild(el);
}

function lessonFileChosen(lid,input){
  const file=input.files[0]; if(!file) return;
  const url=URL.createObjectURL(file);
  input._objectUrl=url;
  const el=document.getElementById('lf-'+lid);
  if(el) el.textContent='✅ '+file.name+' ('+(file.size/1024/1024).toFixed(1)+'MB)';
  toast('✅ '+file.name+' carregado!');
}

function addQuestion(mid,prefill){
  window._qCtr=(window._qCtr||0)+1;
  const qid=window._qCtr;
  const list=document.getElementById('questions-'+mid); if(!list) return;
  list.querySelectorAll('.list-empty').forEach(e=>e.remove());
  const el=document.createElement('div');
  el.id='quest-'+qid; el.className='question-item';
  el.innerHTML=`
  <div style="display:flex;align-items:flex-start;gap:10px;margin-bottom:10px">
    <span class="q-num">${window._qCtr}</span>
    <input type="text" class="form-input" id="qtxt-${qid}" style="flex:1;font-size:14px;padding:9px 12px"
      placeholder="Enunciado da questão..." value="${prefill?.txt||''}">
    <button class="btn b-danger" style="font-size:11px;padding:5px 8px;flex-shrink:0"
      onclick="document.getElementById('quest-${qid}').remove()">✕</button>
  </div>
  <div style="background:var(--surf2);border-radius:8px;padding:12px;margin-left:36px">
    <div style="font-size:11px;font-weight:700;color:var(--t3);text-transform:uppercase;letter-spacing:1px;margin-bottom:8px">
      Alternativas — marque (●) a correta
    </div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px">
      ${['A','B','C','D'].map((l,i)=>`
      <div style="display:flex;align-items:center;gap:8px;background:var(--surf);border:1.5px solid var(--bdr);border-radius:7px;padding:8px 10px;transition:border-color .15s" id="qopt-wrap-${qid}-${i}">
        <input type="radio" name="qcor-${qid}" value="${i}" id="qr-${qid}-${i}"
          ${prefill&&prefill.ok===i?'checked':''}
          style="width:18px;height:18px;accent-color:var(--or);flex-shrink:0;cursor:pointer"
          onchange="document.querySelectorAll('[id^=qopt-wrap-${qid}-]').forEach(e=>{e.style.borderColor='var(--bdr)';e.style.background='var(--surf)'}); this.closest('[id^=qopt-wrap]').style.borderColor='var(--ok)'; this.closest('[id^=qopt-wrap]').style.background='rgba(22,163,74,.06)'">
        <label for="qr-${qid}-${i}" style="font-size:12px;font-weight:700;color:var(--t3);flex-shrink:0;cursor:pointer">${l})</label>
        <input type="text" class="form-input" id="qo-${qid}-${i}" style="flex:1;font-size:13px;padding:4px 8px;background:transparent;border:none;box-shadow:none"
          placeholder="Alternativa ${l}" value="${prefill?.opts?.[i]||''}">
      </div>`).join('')}
    </div>
  </div>`;
  list.appendChild(el);
  // Restore correct option highlight
  if(prefill?.ok!==undefined){
    const wrap=document.getElementById(`qopt-wrap-${qid}-${prefill.ok}`);
    if(wrap){ wrap.style.borderColor='var(--ok)'; wrap.style.background='rgba(22,163,74,.06)'; }
  }
}

function saveCourse(){
  const title=document.getElementById('nc-title')?.value?.trim();
  const inst=document.getElementById('nc-inst')?.value?.trim();
  if(!title||!inst){ toast('⚠️ Preencha Título e Instrutor.'); return; }
  const mEls=document.querySelectorAll('.module-block');
  if(!mEls.length){ toast('⚠️ Adicione pelo menos um módulo.'); return; }

  const score=parseFloat(document.getElementById('nc-score')?.value)||7.0;
  const maxAtt=parseInt(document.getElementById('nc-maxatt')?.value)||3;

  const modules=[];
  mEls.forEach((mel,mi)=>{
    const modId=parseInt(mel.id.replace('mod-',''));
    const modTitle=document.getElementById('mod-t-'+modId)?.value?.trim()||('Módulo '+(mi+1));
    const order=parseInt(document.getElementById('mod-o-'+modId)?.value)||mi+1;
    const quizTitle=document.getElementById('quiz-t-'+modId)?.value?.trim()||('Avaliação — '+modTitle);

    const lessons=[];
    mel.querySelectorAll('.lesson-item').forEach((lel,li)=>{
      const lid=lel.id.replace('less-','');
      const ltitle=document.getElementById('lt-'+lid)?.value?.trim()||('Aula '+(li+1));
      const ldesc=document.getElementById('ldesc-'+lid)?.value?.trim()||'';
      const lurl=document.getElementById('lurl-'+lid)?.value?.trim()||'';
      const fileInput=lel.querySelector('input[type=file]');
      const type=fileInput?(fileInput.accept.includes('video')?'video':'pdf'):'link';
      const url=fileInput?._objectUrl||lurl;
      lessons.push({id:li+1,title:ltitle,type,url,text:ldesc});
    });

    const questions=[];
    mel.querySelectorAll('.question-item').forEach((qel,qi)=>{
      const qid=qel.id.replace('quest-','');
      const qtxt=document.getElementById('qtxt-'+qid)?.value?.trim()||'';
      const opts=['A','B','C','D'].map((_,i)=>document.getElementById('qo-'+qid+'-'+i)?.value?.trim()||'');
      const checked=qel.querySelector('input[type=radio]:checked');
      const ok=checked?parseInt(checked.value):0;
      if(qtxt) questions.push({id:qi+1,txt:qtxt,opts,ok});
    });

    modules.push({id:modId,order,title:modTitle,lessons,quiz:{title:quizTitle,minScore:score,maxAttempts:maxAtt,questions}});
  });

  modules.sort((a,b)=>a.order-b.order);

  const editId=document.getElementById('nc-editId')?.value;
  const courseData={
    title,instructor:inst,
    category:document.getElementById('nc-cat')?.value?.trim()||'Geral',
    ico:document.getElementById('nc-ico')?.value?.trim()||'📚',
    hours:parseInt(document.getElementById('nc-hours')?.value)||16,
    minScore:score,maxAttempts:maxAtt,
    sequential:document.getElementById('nc-seq')?.value==='true',
    desc:document.getElementById('nc-desc')?.value?.trim()||'',
    modules,
  };

  if(editId){
    const idx=COURSES.findIndex(c=>c.id==editId);
    if(idx>-1){ COURSES[idx]={...COURSES[idx],...courseData}; saveCourses(); toast(`✅ Curso "${title}" atualizado!`); go('mCourses'); return; }
  }
  COURSES.push({id:Date.now(),...courseData}); saveCourses();
  toast(`✅ Curso "${title}" criado com ${modules.length} módulo(s)!`); go('mCourses');
}

/* ── MASTER: RELATÓRIOS ───────────────────────────────────────── */
function mReports(){
  const colabors=USERS.filter(u=>u.type==='colaborador'&&u.active);
  page('Relatórios','Análise completa de desempenho',`
  <div style="display:flex;gap:8px;margin-bottom:18px">
    <button class="btn b-or" onclick="toast('📊 Exportando PDF...')">📊 Exportar PDF</button>
    <button class="btn b-gh" onclick="toast('📋 Exportando Excel...')">📋 Exportar Excel</button>
  </div>
  <div class="krow">
    <div class="kpi"><div class="kico">📈</div><div class="kval">${Math.round(colabors.reduce((s,u)=>s+(u.courseId?courseProgress(u.id,u.courseId):0),0)/(colabors.length||1))}%</div><div class="klbl">Progresso Médio</div></div>
    <div class="kpi"><div class="kico">🎓</div><div class="kval">${colabors.filter(u=>u.courseId&&isCourseComplete(u.id,u.courseId)).length}</div><div class="klbl">Certificados</div></div>
    <div class="kpi"><div class="kico">📦</div><div class="kval">${COURSES.reduce((s,c)=>s+(c.modules?.length||0),0)}</div><div class="klbl">Módulos</div></div>
    <div class="kpi"><div class="kico">🔁</div><div class="kval">3x</div><div class="klbl">Tentativas Máx.</div></div>
  </div>
  <div class="cht"><div class="chtt">Desempenho Detalhado por Colaborador</div>
  <div style="overflow-x:auto"><table class="tbl" style="box-shadow:none;border:none">
    <thead><tr><th>Colaborador</th><th>Curso</th><th>Módulos Concluídos</th><th>Progresso</th><th>Melhor Nota</th><th>Status</th></tr></thead>
    <tbody>${colabors.map(u=>{
      const c=COURSES.find(x=>x.id===u.courseId);
      const pct=c?courseProgress(u.id,c.id):0;
      const done=c&&isCourseComplete(u.id,c.id);
      const passedMods=c?c.modules.filter(m=>isModulePassed(u.id,c.id,m.id)).length:0;
      const allScores=c?c.modules.flatMap(m=>(getProgress(u.id,c.id).quizAttempts[m.id]||[]).map(a=>a.score)):[];
      const best=allScores.length?Math.max(...allScores).toFixed(1):'—';
      return `<tr>
        <td><div style="display:flex;align-items:center;gap:8px">
          <div style="width:28px;height:28px;border-radius:6px;background:${u.color||'#999'};display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:800;color:#fff">${u.ini||u.name[0]}</div>
          <strong style="color:var(--t1)">${u.name}</strong>
        </div></td>
        <td>${c?`<span class="course-tag">${c.title}</span>`:'—'}</td>
        <td>${c?`${passedMods}/${c.modules.length}`:'—'}</td>
        <td><div style="display:flex;align-items:center;gap:8px"><div class="pb" style="width:80px;margin:0"><div class="pbf" style="width:${pct}%"></div></div><span style="font-size:12px;font-weight:700;color:var(--or)">${pct}%</span></div></td>
        <td><strong style="color:${parseFloat(best)>=(c?.minScore||7)?'var(--ok)':'var(--err)'}">${best}</strong></td>
        <td><span class="bdg ${done?'bdg-ok':pct>0?'bdg-tag':'bdg-off'}">${done?'Concluído':pct>0?'Em andamento':'Não iniciado'}</span></td>
      </tr>`;}).join('')}
    </tbody>
  </table></div></div>`);
}

/* ── MASTER: SEGURANÇA ────────────────────────────────────────── */
function mSecurity(){
  page('Segurança','Configurações e proteção da plataforma',`
  <div class="sec-info">
    <h3>🔐 Status de Proteção do Conteúdo</h3>
    ${[
      {ico:'🚫',l:'Download de materiais bloqueado',d:'PDFs e apostilas não podem ser baixados pelos colaboradores',s:'ok'},
      {ico:'🔒',l:'Cópia de texto desabilitada',d:'user-select:none aplicado globalmente na plataforma',s:'ok'},
      {ico:'🖱️',l:'Menu de contexto (botão direito) bloqueado',d:'oncontextmenu=false nos viewers de PDF',s:'ok'},
      {ico:'🎓',l:'Apenas certificado pode ser baixado',d:'Download disponível somente via impressão do certificado final',s:'ok'},
      {ico:'🔗',l:'URLs de arquivos não exibidas',d:'Blob URLs não persistem entre sessões; em produção use tokens temporários',s:'warn'},
      {ico:'📦',l:'Módulos com acesso sequencial',d:'Aluno só avança após concluir módulo anterior e sua prova',s:'ok'},
    ].map(i=>`<div class="sec-item">
      <div class="sec-item-info"><span class="sec-item-ico">${i.ico}</span>
      <div><div class="sec-item-label">${i.l}</div><div class="sec-item-desc">${i.d}</div></div></div>
      <span class="${i.s==='ok'?'sec-ok':'sec-warn'}">${i.s==='ok'?'Ativo':'Recomendado'}</span>
    </div>`).join('')}
  </div>
  <div class="sec-info">
    <h3>👥 Contas Ativas por Tipo</h3>
    ${[['master','Master','#92400E','ab-master'],['gestor','Gestor','#5B21B6','ab-gestor'],['colaborador','Colaborador','#FF6A00','ab-colab']].map(([t,l,c,cls])=>{
      const us=USERS.filter(u=>u.type===t&&u.active);
      return `<div style="padding:11px 0;border-bottom:1px solid var(--bdr-lt)">
        <div style="display:flex;align-items:center;gap:8px;margin-bottom:6px">
          <span class="abadge ${cls}">${l}</span>
          <strong>${us.length} usuário(s) ativo(s)</strong>
        </div>
        <div style="font-size:13px;color:var(--t2)">${us.map(u=>u.name).join(', ')||'—'}</div>
      </div>`;}).join('')}
  </div>
  <div style="display:flex;gap:8px">
    <button class="btn b-or" onclick="go('mNewUser')">+ Cadastrar Usuário</button>
    <button class="btn b-gh" onclick="go('mUsers')">Gerenciar Usuários</button>
  </div>`);
}

/* ════════════════════════════════════════════════════════════════
   CONTENT PROTECTION
════════════════════════════════════════════════════════════════ */
document.addEventListener('contextmenu',e=>{
  if(e.target.closest('.pdf-protected,.vwc,.cert')) e.preventDefault();
});
document.addEventListener('keydown',e=>{
  if((e.ctrlKey||e.metaKey)&&['s','p','u'].includes(e.key.toLowerCase())){
    if(document.getElementById('app').style.display!=='none') e.preventDefault();
  }
});
</script>
</body>
</html>
