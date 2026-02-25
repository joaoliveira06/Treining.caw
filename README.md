<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CAW Projetos — Plataforma de Treinamento Industrial</title>
<link href="https://fonts.googleapis.com/css2?family=Barlow:wght@300;400;500;600;700;800;900&family=Barlow+Condensed:wght@700;800;900&display=swap" rel="stylesheet">
<style>
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
body{font-family:'Barlow',sans-serif;background:var(--bg);color:var(--t1);overflow-x:hidden;user-select:none;-webkit-user-select:none;}
img{pointer-events:none;-webkit-user-drag:none}
#landing{display:block}#app{display:none}
.lnav{position:fixed;top:0;left:0;right:0;z-index:100;display:flex;align-items:center;justify-content:space-between;padding:0 60px;height:64px;background:rgba(255,255,255,.97);backdrop-filter:blur(12px);border-bottom:1px solid var(--bdr);box-shadow:var(--s1)}
.logo{display:flex;align-items:center;gap:10px}
.lb{font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:18px;letter-spacing:2px;color:var(--t1);line-height:1}
.ls{font-size:9px;font-weight:600;letter-spacing:2.5px;color:var(--or);text-transform:uppercase}
.lnav-links{display:flex;gap:24px;align-items:center}
.lnav-links a{text-decoration:none;color:var(--t2);font-size:13px;font-weight:600;transition:color .2s}
.lnav-links a:hover{color:var(--or)}
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
.lfoot{background:var(--surf);border-top:1px solid var(--bdr);padding:26px 60px;display:flex;align-items:center;justify-content:space-between}
.lfoot-c{font-size:13px;color:var(--t3)}
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
.abadge{display:inline-flex;align-items:center;gap:5px;padding:3px 10px;border-radius:20px;font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.5px}
.ab-master{background:#FEF3C7;color:#92400E;border:1px solid #FDE68A}
.ab-gestor{background:#EDE9FE;color:#5B21B6;border:1px solid #C4B5FD}
.ab-colab{background:var(--or-lt);color:var(--or);border:1px solid rgba(255,106,0,.2)}
.bdg{display:inline-block;padding:2px 8px;border-radius:20px;font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:.5px}
.bdg-ok{background:rgba(22,163,74,.1);color:#16a34a}
.bdg-off{background:var(--bdr-lt);color:var(--t3)}
.bdg-tag{background:var(--or-lt);color:var(--or)}
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
.krow{display:grid;gap:16px;margin-bottom:24px}
.kpi{background:var(--surf);border:1px solid var(--bdr);border-radius:12px;padding:20px;display:flex;flex-direction:column;align-items:center;text-align:center;transition:all .2s}
.kpi:hover{border-color:var(--or);box-shadow:var(--s2)}
.kico{width:44px;height:44px;border-radius:10px;background:var(--or-lt);display:flex;align-items:center;justify-content:center;font-size:20px;margin-bottom:12px}
.kval{font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:28px;color:var(--t1);line-height:1}
.klbl{font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:1px;color:var(--t3);margin-top:4px}
.tw{background:var(--surf);border:1px solid var(--bdr);border-radius:10px;overflow:hidden;box-shadow:var(--s1)}
table{width:100%;border-collapse:collapse}
th{background:var(--surf2);padding:12px 16px;text-align:left;font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:1px;color:var(--t3);border-bottom:1px solid var(--bdr)}
td{padding:14px 16px;font-size:13px;color:var(--t2);border-bottom:1px solid var(--bdr-lt)}
tr:last-child td{border-bottom:none}
tr:hover td{background:rgba(255,106,0,.02)}
.cgrid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:20px}
.cc{background:var(--surf);border:1px solid var(--bdr);border-radius:12px;overflow:hidden;cursor:pointer;transition:all .2s;display:flex;flex-direction:column;box-shadow:var(--s1)}
.cc:hover{transform:translateY(-3px);border-color:var(--or);box-shadow:var(--s2)}
.cth{height:100px;background:linear-gradient(45deg,var(--or),#FF8C40);padding:20px;display:flex;align-items:center;justify-content:space-between;position:relative}
.cth-ico{font-size:40px;opacity:.9}
.ctag{background:rgba(255,255,255,.2);backdrop-filter:blur(4px);padding:4px 10px;border-radius:20px;font-size:10px;font-weight:800;color:#fff;text-transform:uppercase;letter-spacing:.5px}
.cbody{padding:20px;flex:1;display:flex;flex-direction:column}
.ctitle{font-family:'Barlow Condensed',sans-serif;font-weight:800;font-size:18px;color:var(--t1);line-height:1.2;margin-bottom:8px}
.cinst{font-size:12px;color:var(--t3);margin-bottom:16px}
.pb{height:6px;background:var(--bdr-lt);border-radius:10px;overflow:hidden;margin-bottom:8px}
.pbf{height:100%;background:var(--or);transition:width .4s ease}
.pi{display:flex;justify-content:space-between;font-size:11px;font-weight:700;margin-bottom:16px}
.pi-p{color:var(--or)}.pi-m{color:var(--t3)}
.cpill{align-self:flex-start;padding:4px 12px;border-radius:20px;font-size:10px;font-weight:800;text-transform:uppercase;letter-spacing:.5px}
.p-ns{background:var(--bdr-lt);color:var(--t3)}
.p-ip{background:var(--or-lt);color:var(--or)}
.p-cp{background:rgba(22,163,74,.1);color:#16a34a}
.vwr{display:flex;height:calc(100vh - 120px);gap:20px}
.vws{width:320px;background:var(--surf);border:1px solid var(--bdr);border-radius:12px;display:flex;flex-direction:column;overflow:hidden}
.vwsh{padding:20px;border-bottom:1px solid var(--bdr);background:var(--surf2)}
.vwsh h3{font-family:'Barlow Condensed',sans-serif;font-weight:800;font-size:16px;text-transform:uppercase}
.vwc{flex:1;background:var(--surf);border:1px solid var(--bdr);border-radius:12px;overflow-y:auto;position:relative}
.mg{border-bottom:1px solid var(--bdr-lt)}
.mgl{padding:12px 20px;background:var(--surf2);font-size:12px;font-weight:700;color:var(--t2);display:flex;align-items:center;justify-content:space-between}
.lr{padding:12px 20px;display:flex;align-items:center;gap:10px;cursor:pointer;font-size:13px;color:var(--t2);transition:all .15s;border-left:3px solid transparent}
.lr:hover{background:var(--or-lt)}
.lr.active{background:var(--or-lt);color:var(--or);font-weight:700;border-left-color:var(--or)}
.lr.done .li{color:var(--ok)}
.lr-locked{opacity:.5;cursor:not-allowed}
.lr-quiz{background:rgba(255,106,0,.03);border-top:1px dashed var(--bdr)}
.vci{padding:30px}
.vbox{width:100%;aspect-ratio:16/9;background:#000;border-radius:8px;margin-bottom:24px;overflow:hidden}
.vtxt{font-size:15px;line-height:1.8;color:var(--t2)}
.vtxt h2{color:var(--t1);margin:24px 0 12px;font-family:'Barlow Condensed',sans-serif;font-weight:800;text-transform:uppercase}
.vnav{margin-top:40px;padding-top:24px;border-top:1px solid var(--bdr);display:flex;justify-content:space-between}
.fgrp{margin-bottom:16px}
.sh{display:flex;align-items:center;justify-content:space-between;margin-bottom:20px;margin-top:32px}
.sh h2{font-family:'Barlow Condensed',sans-serif;font-weight:800;font-size:20px;text-transform:uppercase;color:var(--t1)}
.toast{position:fixed;bottom:30px;left:50%;transform:translateX(-50%) translateY(100px);background:var(--t1);color:#fff;padding:12px 24px;border-radius:8px;font-size:13px;font-weight:600;z-index:1000;transition:all .3s cubic-bezier(0.18, 0.89, 0.32, 1.28);opacity:0}
.toast.show{transform:translateX(-50%) translateY(0);opacity:1}
</style>
</head>
<body>
<div id="landing">
<nav class="lnav">
  <div class="logo">
    <img src="https://files.manuscdn.com/user_upload_by_module/session_file/310519663187515352/TGtmyIpbwEAcIwlJ.png" style="height:40px;width:auto;object-fit:contain" alt="CAW Logo">
  </div>
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
  <div class="logo">
    <img src="https://files.manuscdn.com/user_upload_by_module/session_file/310519663187515352/TGtmyIpbwEAcIwlJ.png" style="height:32px;width:auto;object-fit:contain" alt="CAW Logo">
  </div>
  <div class="lfoot-c">© 2025 CAW Projetos e Consultoria Industrial. Todos os direitos reservados.</div>
</footer>
</div>

<div class="ov" id="loginModal" onclick="if(event.target===this)closeLogin()">
<div class="modal">
  <button class="mx" onclick="closeLogin()">×</button>
  <div style="display:flex;align-items:center;gap:10px;margin-bottom:22px">
    <img src="https://files.manuscdn.com/user_upload_by_module/session_file/310519663187515352/TGtmyIpbwEAcIwlJ.png" style="height:34px;width:auto;object-fit:contain" alt="CAW Logo">
    <div>
      <div style="font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:17px;letter-spacing:1.5px;color:var(--t1)">CAW Projetos</div>
      <div style="font-size:10px;letter-spacing:2px;color:var(--or);text-transform:uppercase;font-weight:600">Plataforma de Treinamento</div>
    </div>
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

<div id="app">
<div class="shell">
  <aside class="sidebar" id="sidebar">
    <div class="sbh">
      <img src="https://files.manuscdn.com/user_upload_by_module/session_file/310519663187515352/TGtmyIpbwEAcIwlJ.png" style="height:32px;width:auto;object-fit:contain" alt="CAW Logo">
    </div>
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
let CU = null;
const DEFAULT_COURSES = [
  { id:1, title:'NR-12: Segurança em Máquinas', instructor:'Eng. Carlos Mendes', category:'Segurança', ico:'⚙️', hours:16, minScore:7.0, maxAttempts:3, sequential:true,
    modules:[
      { id:1, order:1, title:'Fundamentos da NR-12',
        lessons:[
          {id:1,title:'Introdução à NR-12',type:'pdf',url:'',text:'A NR-12 estabelece os requisitos mínimos para prevenção de acidentes em máquinas e equipamentos industriais. É obrigatória para todos os setores que utilizem máquinas.'},
          {id:2,title:'Zonas de Perigo e Risco',type:'video',url:'',text:'Identificação e classification de zonas de perigo conforme a norma. Compreenda como mapear os riscos na sua área.'},
        ],
        quiz:{ title:'Avaliação — Módulo 1', minScore:7.0, maxAttempts:3, questions:[
          {id:1,txt:'O que é considerado zona de perigo conforme a NR-12?',opts:['Área de manutenção','Local de descanso','Espaço com risco de acidente por parte móvel','Corredor de saída'],ok:2},
          {id:2,txt:'A NR-12 se aplica a:',opts:['Apenas máquinas pesadas','Todos os equipamentos e máquinas industriais','Somente equipamentos elétricos','Apenas tornos CNC'],ok:1},
        ]}
      }
    ]
  },
  { id:2, title:'Eficiência Energética em Sistemas de Ar Comprimido', instructor:'Eng. Roberto Silva', category:'Energia', ico:'⚡', hours:12, minScore:7.0, maxAttempts:3, sequential:true,
    modules:[
      { id:1, order:1, title:'Geração e Tratamento',
        lessons:[
          {id:1,title:'Tipos de Compressores',type:'pdf',url:'',text:'Visão geral sobre compressores de pistão, parafuso e centrífugos.'},
        ],
        quiz:{ title:'Avaliação — Módulo 1', minScore:7.0, maxAttempts:3, questions:[
          {id:1,txt:'Qual tipo de compressor é mais comum em indústrias para uso contínuo?',opts:['Pistão','Parafuso','Manual','Bomba'],ok:1},
        ]}
      }
    ]
  },
  { id:3, title:'Gestão de Manutenção Industrial', instructor:'Eng. Marcos Oliveira', category:'Gestão', ico:'🛠️', hours:20, minScore:7.0, maxAttempts:3, sequential:true,
    modules:[
      { id:1, order:1, title:'Estratégias de Manutenção',
        lessons:[
          {id:1,title:'Preventiva vs Preditiva',type:'pdf',url:'',text:'Diferenças fundamentais e quando aplicar cada estratégia para otimizar custos.'},
        ],
        quiz:{ title:'Avaliação — Módulo 1', minScore:7.0, maxAttempts:3, questions:[
          {id:1,txt:'A manutenção preditiva baseia-se em:',opts:['Tempo de uso','Quebra inesperada','Monitoramento de condições','Troca de peças novas'],ok:2},
        ]}
      }
    ]
  }
];
let COURSES = JSON.parse(localStorage.getItem('caw_courses')||'null') || DEFAULT_COURSES;
function saveCourses(){ localStorage.setItem('caw_courses', JSON.stringify(COURSES)); }
const DEFAULT_USERS = [
  { id:1, name:'Hans', login:'hans', pass:'Hans7411', role:'Diretor', sector:'Diretoria', type:'master', ini:'H', color:'#92400E', courseId:null, active:true },
  { id:2, name:'Geraldo Andrade', login:'geraldo', pass:'Ger@2025', role:'Gestor de T&D', sector:'Gestão', type:'gestor', ini:'GA', color:'#5B21B6', courseId:null, active:true },
  { id:3, name:'João Silva', login:'joao', pass:'Joao@2025', role:'Operador CNC', sector:'Produção', type:'colaborador', ini:'JS', color:'#FF6A00', courseId:1, active:true },
  { id:4, name:'Maria Fernanda', login:'maria', pass:'Maria@2025', role:'Técnica de Qualidade', sector:'Qualidade', type:'colaborador', ini:'MF', color:'#3b82f6', courseId:3, active:true },
  { id:5, name:'Ana Paula Ramos', login:'ana', pass:'Ana@2025', role:'Coord. Segurança', sector:'SST', type:'colaborador', ini:'AP', color:'#f59e0b', courseId:1, active:true },
];
let USERS = JSON.parse(localStorage.getItem('caw_users')||'null') || DEFAULT_USERS;
function saveUsers(){ localStorage.setItem('caw_users', JSON.stringify(USERS)); }
let PROGRESS = JSON.parse(localStorage.getItem('caw_progress')||'{}');
function saveProgress(){ localStorage.setItem('caw_progress', JSON.stringify(PROGRESS)); }
function getProgress(uid, cid){
  if(!PROGRESS[uid]) PROGRESS[uid]={};
  if(!PROGRESS[uid][cid]) PROGRESS[uid][cid]={ completedLessons:[], quizAttempts:{} };
  return PROGRESS[uid][cid];
}
function isLessonDone(uid, cid, mid, lid){ return getProgress(uid,cid).completedLessons.includes(`${mid}-${lid}`); }
function isModuleLessonsDone(uid, cid, m){ return m.lessons.every(l=>isLessonDone(uid,cid,m.id,l.id)); }
function isModulePassed(uid, cid, mid){ const atts = getProgress(uid,cid).quizAttempts[mid]||[]; return atts.some(a=>a.pass); }
function isCourseComplete(uid, cid){ const c=COURSES.find(x=>x.id===cid); if(!c) return false; return c.modules.every(m=>isModuleLessonsDone(uid,cid,m)&&isModulePassed(uid,cid,m.id)); }
function courseProgress(uid, cid){ const c=COURSES.find(x=>x.id===cid); if(!c) return 0; const totalLessons=c.modules.reduce((s,m)=>s+m.lessons.length,0); const doneLessons=getProgress(uid,cid).completedLessons.length; return totalLessons?Math.round(doneLessons/totalLessons*100):0; }
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
function logout(){ CU=null; document.getElementById('app').style.display='none'; document.getElementById('landing').style.display='block'; window.scrollTo(0,0); }
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
let activeCourseId=null, activeModId=null;
function go(pg, ...args){
  document.querySelectorAll('.ni').forEach(e=>e.classList.remove('active'));
  const el=document.getElementById('n-'+pg); if(el) el.classList.add('active');
  const R={ dashboard,myCourses,courseViewer,ranking,certificate,gDash,gUsers,gCourses,gReports,mDash,mUsers,mNewUser,mCourses,mNewCourse,mReports,mSecurity };
  R[pg]?.(...args);
}
function page(title,crumb,body,actions=''){
  document.getElementById('main').innerHTML=`<div class="pgh"><div><h1>${title}</h1><div class="pgcr">${crumb}</div></div><div style="display:flex;gap:8px;align-items:center">${actions}</div></div><div class="pgb">${body}</div>`;
}
function toast(msg, dur=3200){ const t=document.getElementById('toast'); t.textContent=msg; t.classList.add('show'); clearTimeout(t._tid); t._tid=setTimeout(()=>t.classList.remove('show'),dur); }
function cc(c, uid){
  const pct=courseProgress(uid||CU.id, c.id);
  const done=isCourseComplete(uid||CU.id,c.id);
  const status=done?'completed':pct>0?'in-progress':'not-started';
  const lbl={completed:'Concluído','in-progress':'Em andamento','not-started':'Não iniciado'};
  const cls={completed:'p-cp','in-progress':'p-ip','not-started':'p-ns'};
  const mods=c.modules?.length||0;
  return `<div class="cc" onclick="activeCourseId=${c.id};go('courseViewer')"><div class="cth"><div class="cth-ico">${c.ico||'📚'}</div><div class="ctag">${c.category||'Geral'}</div></div><div class="cbody"><div class="ctitle">${c.title}</div><div class="cinst">👤 ${c.instructor}</div><div class="pb"><div class="pbf" style="width:${pct}%"></div></div><div class="pi"><span class="pi-p">${pct}%</span><span class="pi-m">${c.hours}h · ${mods} módulo(s)</span></div><span class="cpill ${cls[status]}">${lbl[status]}</span></div></div>`;
}
function dashboard(){
  const userCourses = CU.courseId ? COURSES.filter(c=>c.id===CU.courseId) : COURSES;
  const done=userCourses.filter(c=>isCourseComplete(CU.id,c.id)).length;
  document.getElementById('main').innerHTML=`<div class="pgh"><div><h1>Dashboard</h1><div class="pgcr">Meu painel de aprendizado</div></div></div><div class="pgb"><div class="krow" style="grid-template-columns:repeat(3,1fr)"><div class="kpi"><div class="kico">📚</div><div class="kval">${userCourses.length}</div><div class="klbl">Cursos</div></div><div class="kpi"><div class="kico">✅</div><div class="kval">${done}</div><div class="klbl">Concluídos</div></div><div class="kpi"><div class="kico">⭐</div><div class="kval">${done===userCourses.length&&userCourses.length>0?'100%':courseProgress(CU.id,CU.courseId||0)+'%'}</div><div class="klbl">Progresso</div></div></div><div class="sh"><h2>Meus Cursos</h2></div><div class="cgrid">${userCourses.map(c=>cc(c)).join('')}</div></div>`;
}
function myCourses(){
  const userCourses = CU.courseId ? COURSES.filter(c=>c.id===CU.courseId) : COURSES;
  document.getElementById('main').innerHTML=`<div class="pgh"><div><h1>Meus Cursos</h1><div class="pgcr">Cursos disponíveis para você</div></div></div><div class="pgb"><div class="cgrid">${userCourses.map(c=>cc(c)).join('')}</div></div>`;
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
  let sbHtml='';
  modules.forEach((m,mi)=>{
    const prevOk = mi===0 || (isModuleLessonsDone(uid,cid,modules[mi-1]) && isModulePassed(uid,cid,modules[mi-1].id));
    const modLocked = c.sequential && !prevOk && mi>0;
    const allLessDone = isModuleLessonsDone(uid,cid,m);
    const quizPassed = isModulePassed(uid,cid,m.id);
    sbHtml+=`<div class="mg"><div class="mgl" style="${modLocked?'opacity:.55':''}"><span>${modLocked?'🔒 ':allLessDone&&quizPassed?'✅ ':'📦 '}<strong>${m.order||mi+1}.</strong> ${m.title}</span></div>`;
    m.lessons.forEach((l,li)=>{
      const done=isLessonDone(uid,cid,m.id,l.id);
      const lLocked = modLocked || (c.sequential&&li>0&&!isLessonDone(uid,cid,m.id,m.lessons[li-1].id));
      const ico=l.type==='pdf'?'📄':l.type==='video'?'🎬':'📎';
      const lid=`vl-${m.id}-${l.id}`;
      sbHtml+=`<div class="lr ${done?'done':''} ${lLocked?'lr-locked':''}" id="${lid}" onclick="${lLocked?`toast('🔒 Conclua a aula anterior primeiro.')`:`showLesson(${cid},${m.id},${l.id})`}"><span class="li">${done?'✅':'⭕'}</span>${l.title}<span class="lt">${ico} ${l.type.toUpperCase()}</span></div>`;
    });
    const qLocked = modLocked || !allLessDone;
    const atts = prog.quizAttempts[m.id]||[];
    sbHtml+=`<div class="lr lr-quiz ${qLocked?'lr-locked':''}" id="vq-${m.id}" onclick="${qLocked?`toast('📝 Conclua todas as aulas deste módulo para liberar a prova.')`:`showQuiz(${cid},${m.id})`}"><span class="li">${quizPassed?'✅':'📝'}</span>${m.quiz?.title||'Avaliação do Módulo'}<span class="lt" style="${quizPassed?'color:var(--ok)':qLocked?'color:var(--err)':''}">${quizPassed?'APROVADO':qLocked?'BLOQUEADO':atts.length?'TENTAR NOVO':'DISPONÍVEL'}</span></div></div>`;
  });
  document.getElementById('main').innerHTML=`<div class="pgh"><div><h1>${c.title}</h1><div class="pgcr">Meus Cursos → ${c.title}</div></div><button class="btn b-gh" style="font-size:11px;padding:7px 14px" onclick="go('myCourses')">← Voltar</button></div><div class="vwr"><div class="vws"><div class="vwsh"><h3>Conteúdo do Curso</h3><div style="margin-top:8px"><div class="pb"><div class="pbf" style="width:${pct}%"></div></div><div style="font-size:11px;color:var(--t3);margin-top:3px">${pct}% · ${modules.length} módulo(s)</div></div></div>${sbHtml}</div><div class="vwc"><div class="vci" id="lessonArea"><div style="text-align:center;padding:48px 20px;color:var(--t3)"><div style="font-size:48px;margin-bottom:14px">📖</div><div style="font-size:16px;font-weight:700;color:var(--t1);margin-bottom:6px">Bem-vindo, ${CU.name.split(' ')[0]}!</div><p style="font-size:14px">Selecione uma aula no menu lateral para começar.</p></div></div></div></div>`;
  for(const m of modules){ for(const l of m.lessons){ if(!isLessonDone(uid,cid,m.id,l.id)){ showLesson(cid,m.id,l.id); return; } } }
}
function showLesson(cid,mid,lid){
  const c=COURSES.find(x=>x.id===cid);
  const m=c?.modules?.find(x=>x.id===mid);
  const l=m?.lessons?.find(x=>x.id===lid);
  if(!l) return;
  document.querySelectorAll('.lr').forEach(e=>e.classList.remove('active'));
  document.getElementById(`vl-${mid}-${lid}`)?.classList.add('active');
  let mediaHtml='';
  if(l.type==='video'){
    if(l.url){ let src=l.url; const yt=l.url.match(/(?:youtube\.com\/watch\?v=|youtu\.be\/)([a-zA-Z0-9_-]{11})/); if(yt) src=`https://www.youtube.com/embed/${yt[1]}`; mediaHtml=`<div class="vbox"><iframe src="${src}" style="width:100%;height:100%;border:none" allowfullscreen></iframe></div>`; }
    else { mediaHtml=`<div class="vbox" style="display:flex;align-items:center;justify-content:center;color:#fff;flex-direction:column;gap:10px"><div style="font-size:40px">🎥</div><div>Vídeo não disponível</div></div>`; }
  } else if(l.type==='pdf'){
    mediaHtml=`<div class="vbox" style="aspect-ratio:auto;height:600px"><iframe src="${l.url||'https://www.w3.org/WAI/ER/tests/xhtml/testfiles/resources/pdf/dummy.pdf'}#toolbar=0" style="width:100%;height:100%;border:none"></iframe></div>`;
  }
  document.getElementById('lessonArea').innerHTML=`<div class="seye">${m.title} · Aula ${l.id}</div><h2 style="font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:28px;text-transform:uppercase;margin-bottom:20px">${l.title}</h2>${mediaHtml}<div class="vtxt">${l.text||'Nenhum texto adicional para esta aula.'}</div><div class="vnav"><button class="btn b-gh" style="opacity:0;pointer-events:none">Anterior</button><button class="btn b-ok" onclick="completeLesson(${cid},${mid},${lid})">Concluir Aula e Continuar ✅</button></div>`;
  document.getElementById('lessonArea').scrollIntoView({behavior:'smooth'});
}
function completeLesson(cid,mid,lid){
  const prog = getProgress(CU.id, cid);
  const key = `${mid}-${lid}`;
  if(!prog.completedLessons.includes(key)){ prog.completedLessons.push(key); saveProgress(); toast('✅ Aula concluída!'); }
  courseViewer();
}
function showQuiz(cid,mid){
  const c=COURSES.find(x=>x.id===cid);
  const m=c?.modules?.find(x=>x.id===mid);
  if(!m?.quiz) return;
  document.querySelectorAll('.lr').forEach(e=>e.classList.remove('active'));
  document.getElementById(`vq-${mid}`)?.classList.add('active');
  let qHtml = m.quiz.questions.map((q,idx)=>`<div class="fgrp" style="margin-bottom:30px;padding:20px;background:var(--surf2);border-radius:10px"><div style="font-weight:700;margin-bottom:15px;font-size:15px;color:var(--t1)">${idx+1}. ${q.txt}</div><div style="display:flex;flex-direction:column;gap:10px">${q.opts.map((o,oidx)=>`<label style="display:flex;align-items:center;gap:10px;cursor:pointer;padding:8px 12px;background:var(--surf);border:1.5px solid var(--bdr);border-radius:6px;font-size:14px"><input type="radio" name="q${idx}" value="${oidx}"> ${o}</label>`).join('')}</div></div>`).join('');
  document.getElementById('lessonArea').innerHTML=`<div class="seye">${m.title}</div><h2 style="font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:28px;text-transform:uppercase;margin-bottom:10px">${m.quiz.title}</h2><p style="margin-bottom:30px;color:var(--t3);font-size:14px">Responda todas as questões abaixo. Você precisa de no mínimo ${c.minScore} para ser aprovado.</p><div id="quizForm">${qHtml}</div><div style="text-align:right"><button class="btn b-or" onclick="submitQuiz(${cid},${mid})">Enviar Avaliação →</button></div>`;
}
function submitQuiz(cid,mid){
  const c=COURSES.find(x=>x.id===cid);
  const m=c?.modules?.find(x=>x.id===mid);
  const qs = m.quiz.questions;
  let correct = 0;
  for(let i=0; i<qs.length; i++){ const sel = document.querySelector(`input[name="q${i}"]:checked`); if(sel && parseInt(sel.value) === qs[i].ok) correct++; }
  const score = (correct / qs.length) * 10;
  const pass = score >= c.minScore;
  const prog = getProgress(CU.id, cid);
  if(!prog.quizAttempts[mid]) prog.quizAttempts[mid]=[];
  prog.quizAttempts[mid].push({score, date:new Date().toISOString(), pass});
  saveProgress();
  const msg = pass ? `🎉 PARABÉNS! Você foi aprovado com nota ${score.toFixed(1)}.` : `❌ Que pena. Sua nota foi ${score.toFixed(1)}, abaixo do mínimo (${c.minScore}). Tente novamente!`;
  document.getElementById('lessonArea').innerHTML=`<div style="text-align:center;padding:40px 0"><div style="font-size:60px;margin-bottom:20px">${pass?'🏆':'📚'}</div><h2 style="font-family:'Barlow Condensed',sans-serif;font-weight:900;font-size:32px;text-transform:uppercase;margin-bottom:10px">${pass?'Aprovado!':'Tente Novamente'}</h2><p style="font-size:18px;color:var(--t2);margin-bottom:30px">${msg}</p><button class="btn b-or" onclick="courseViewer()">Continuar</button></div>`;
}
function ranking(){
  const sorted = [...USERS].filter(u=>u.type==='colaborador').map(u=>{ const c = COURSES.find(x=>x.id===u.courseId); const pct = c ? courseProgress(u.id, c.id) : 0; return {...u, pct}; }).sort((a,b)=>b.pct - a.pct);
  let rows = sorted.map((u,idx)=>`<tr><td style="width:50px;font-weight:800;color:var(--or)">#${idx+1}</td><td><div style="display:flex;align-items:center;gap:10px"><div class="uav" style="background:${u.color};width:28px;height:28px;font-size:10px">${u.ini}</div><div><strong>${u.name}</strong><div style="font-size:11px;color:var(--t3)">${u.sector}</div></div></div></td><td>${u.pct}%</td><td><div class="pb" style="width:100px;margin-bottom:0"><div class="pbf" style="width:${u.pct}%"></div></div></td></tr>`).join('');
  page('Ranking','Classificação de aprendizado',`<div class="tw"><table><thead><tr><th>Pos</th><th>Colaborador</th><th>Progresso</th><th>Geral</th></tr></thead><tbody>${rows}</tbody></table></div>`);
}
function certificate(){}
function gDash(){
  const colabs = USERS.filter(u=>u.type==='colaborador');
  const avgProg = colabs.length ? Math.round(colabs.reduce((s,u)=>s+courseProgress(u.id, u.courseId||0),0)/colabs.length) : 0;
  page('Painel do Gestor','Visão geral da equipe','',`<button class="btn b-or" style="font-size:11px;padding:7px 14px" onclick="go('gReports')">Gerar Relatório PDF</button>`);
  document.getElementById('main').innerHTML+=`<div class="krow" style="grid-template-columns:repeat(4,1fr)"><div class="kpi"><div class="kico">👥</div><div class="kval">${colabs.length}</div><div class="klbl">Colaboradores</div></div><div class="kpi"><div class="kico">📚</div><div class="kval">${COURSES.length}</div><div class="klbl">Cursos Ativos</div></div><div class="kpi"><div class="kico">📈</div><div class="kval">${avgProg}%</div><div class="klbl">Média de Progresso</div></div><div class="kpi"><div class="kico">✅</div><div class="kval">${colabs.filter(u=>isCourseComplete(u.id, u.courseId||0)).length}</div><div class="klbl">Concluídos</div></div></div><div class="sh"><h2>Status da Equipe</h2></div><div class="tw"><table><thead><tr><th>Nome</th><th>Setor</th><th>Curso Alocado</th><th>Progresso</th><th>Status</th></tr></thead><tbody>${colabs.map(u=>{ const c = COURSES.find(x=>x.id===u.courseId); const pct = c ? courseProgress(u.id, c.id) : 0; const done = c ? isCourseComplete(u.id, c.id) : false; return `<tr><td><strong>${u.name}</strong></td><td>${u.sector}</td><td>${c?.title||'—'}</td><td>${pct}%</td><td><span class="bdg ${done?'bdg-ok':'bdg-tag'}">${done?'Concluído':'Em curso'}</span></td></tr>`; }).join('')}</tbody></table></div>`;
}
function gUsers(){
  const colabs = USERS.filter(u=>u.type==='colaborador');
  page('Colaboradores','Gerenciamento de acessos',`<div class="tw"><table><thead><tr><th>Nome</th><th>Setor</th><th>Função</th><th>Último Acesso</th><th>Ações</th></tr></thead><tbody>${colabs.map(u=>`<tr><td><strong>${u.name}</strong></td><td>${u.sector}</td><td>${u.role}</td><td>Hoje</td><td><button class="b-sm">Ver Detalhes</button></td></tr>`).join('')}</tbody></table></div>`);
}
function gCourses(){ page('Catálogo de Cursos','Cursos disponíveis na plataforma',`<div class="cgrid">${COURSES.map(c=>cc(c)).join('')}</div>`); }
function gReports(){
  page('Relatórios Técnicos','Análise de desempenho por setor',`<div style="display:grid;grid-template-columns:repeat(2,1fr);gap:20px"><div class="kpi" style="align-items:flex-start;text-align:left"><div class="kico">📄</div><h3>Relatório de Progresso Mensal</h3><p style="font-size:12px;color:var(--t3);margin:10px 0 20px">Resumo completo de todos os colaboradores, horas de treinamento e notas.</p><button class="btn b-gh" onclick="toast('Relatório sendo gerado...')">Download PDF</button></div><div class="kpi" style="align-items:flex-start;text-align:left"><div class="kico">📊</div><h3>Matriz de Competências</h3><p style="font-size:12px;color:var(--t3);margin:10px 0 20px">Visualização por setor das habilidades técnicas adquiridas via treinamentos.</p><button class="btn b-gh" onclick="toast('Relatório sendo gerado...')">Download PDF</button></div></div>`);
}
function mDash(){
  page('Painel Master','Controle total do sistema','',`<button class="btn b-or" style="font-size:11px;padding:7px 14px" onclick="go('mNewUser')">+ Novo Usuário</button>`);
  document.getElementById('main').innerHTML+=`<div class="krow" style="grid-template-columns:repeat(4,1fr)"><div class="kpi"><div class="kico">👥</div><div class="kval">${USERS.length}</div><div class="klbl">Total Usuários</div></div><div class="kpi"><div class="kico">📚</div><div class="kval">${COURSES.length}</div><div class="klbl">Total Cursos</div></div><div class="kpi"><div class="kico">🏢</div><div class="kval">5</div><div class="klbl">Setores</div></div><div class="kpi"><div class="kico">🔐</div><div class="kval">Ativa</div><div class="klbl">Segurança</div></div></div><div class="sh"><h2>Usuários Recentes</h2></div><div class="tw"><table><thead><tr><th>Usuário</th><th>Tipo</th><th>Setor</th><th>Status</th><th>Ações</th></tr></thead><tbody>${USERS.map(u=>`<tr><td><strong>${u.name}</strong><div style="font-size:11px;color:var(--t3)">${u.login}</div></td><td><span class="abadge ab-${u.type}">${u.type}</span></td><td>${u.sector}</td><td><span class="bdg bdg-ok">Ativo</span></td><td><button class="b-sm">Editar</button></td></tr>`).join('')}</tbody></table></div>`;
}
function mUsers(){
  page('Usuários','Gestão de todos os acessos',`<div class="tw"><table><thead><tr><th>Nome</th><th>Tipo</th><th>Login</th><th>Senha</th><th>Ações</th></tr></thead><tbody>${USERS.map(u=>`<tr><td><strong>${u.name}</strong></td><td><span class="abadge ab-${u.type}">${u.type}</span></td><td>${u.login}</td><td><code>${u.pass}</code></td><td><button class="b-sm">Editar</button> <button class="b-danger">Suspender</button></td></tr>`).join('')}</tbody></table></div>`);
}
function mNewUser(){
  page('Novo Usuário','Cadastrar colaborador ou gestor',`<div class="tw" style="max-width:600px;padding:30px"><div class="fgrp"><label class="flbl">Nome Completo</label><input type="text" class="finp" placeholder="Ex: Ricardo Souza"></div><div style="display:grid;grid-template-columns:1fr 1fr;gap:16px"><div class="fgrp"><label class="flbl">Login</label><input type="text" class="finp" placeholder="ricardo.souza"></div><div class="fgrp"><label class="flbl">Senha</label><input type="text" class="finp" value="Caw@2025"></div></div><div style="display:grid;grid-template-columns:1fr 1fr;gap:16px"><div class="fgrp"><label class="flbl">Tipo</label><select class="finp"><option>colaborador</option><option>gestor</option><option>master</option></select></div><div class="fgrp"><label class="flbl">Setor</label><select class="finp"><option>Produção</option><option>Qualidade</option><option>SST</option><option>Logística</option></select></div></div><button class="btn b-or" style="width:100%;justify-content:center;margin-top:10px" onclick="toast('✅ Usuário criado com sucesso!')">Criar Usuário</button></div>`);
}
function mCourses(){
  page('Gestão de Cursos','Configuração de conteúdo e sequenciamento',`<div class="tw"><table><thead><tr><th>Curso</th><th>Instrutor</th><th>Módulos</th><th>Sequencial</th><th>Ações</th></tr></thead><tbody>${COURSES.map(c=>`<tr><td><strong>${c.title}</strong></td><td>${c.instructor}</td><td>${c.modules.length}</td><td>${c.sequential?'Sim':'Não'}</td><td><button class="b-sm">Editar Conteúdo</button></td></tr>`).join('')}</tbody></table></div>`);
}
function mNewCourse(){
  page('Novo Curso','Criação de trilha de aprendizado',`<div class="tw" style="max-width:800px;padding:30px"><div class="fgrp"><label class="flbl">Título do Curso</label><input type="text" class="finp" placeholder="Ex: Operação de Empilhadeira"></div><div style="display:grid;grid-template-columns:1fr 1fr;gap:16px"><div class="fgrp"><label class="flbl">Instrutor</label><input type="text" class="finp" placeholder="Nome do Responsável"></div><div class="fgrp"><label class="flbl">Carga Horária (h)</label><input type="number" class="finp" value="8"></div></div><div class="dbox" style="background:var(--surf2);border-style:dashed;text-align:center;padding:40px"><div style="font-size:24px;margin-bottom:10px">📂</div><p>Arraste os arquivos (PDF/MP4) para criar os módulos automaticamente</p></div><button class="btn b-or" style="width:100%;justify-content:center;margin-top:10px" onclick="toast('✅ Estrutura de curso criada!')">Salvar Rascunho</button></div>`);
}
function mReports(){ gReports(); }
function mSecurity(){
  page('Segurança','Logs e proteção de conteúdo',`<div class="tw" style="padding:20px;margin-bottom:20px"><h3 style="margin-bottom:15px">Configurações de Proteção</h3><label style="display:flex;align-items:center;gap:10px;margin-bottom:10px;font-size:14px"><input type="checkbox" checked disabled> Bloquear botão direito do mouse</label><label style="display:flex;align-items:center;gap:10px;margin-bottom:10px;font-size:14px"><input type="checkbox" checked disabled> Impedir seleção de texto</label><label style="display:flex;align-items:center;gap:10px;margin-bottom:10px;font-size:14px"><input type="checkbox" checked disabled> Marca d'água dinâmica (User ID)</label></div><div class="sh"><h2>Logs de Acesso</h2></div><div class="tw"><table><thead><tr><th>Data/Hora</th><th>Usuário</th><th>Ação</th><th>IP</th></tr></thead><tbody><tr><td>25/02/2025 09:41</td><td>Hans</td><td>Login efetuado</td><td>192.168.1.45</td></tr><tr><td>25/02/2025 09:38</td><td>João Silva</td><td>Aula concluída (NR-12)</td><td>10.0.0.122</td></tr><tr><td>25/02/2025 09:15</td><td>Ana Paula</td><td>Tentativa de prova (Módulo 1)</td><td>10.0.0.15</td></tr></tbody></table></div>`);
}
window.onload = () => {};
</script>
</body>
</html>
