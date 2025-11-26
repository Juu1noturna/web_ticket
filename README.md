# web_ticket
Para garantir um atendimento organizado e ágil, utilize nosso sistema de tickets.
Ao retirar sua senha, informe seu nome completo e selecione o tipo de atendimento que você precisa:

* SG – Senha Geral
Utilize esta opção para atendimentos comuns, como informações, agendamentos e serviços gerais.

* SE – Senha para Exames
Escolha esta senha caso você esteja aqui para retirada de exames ou entrega de documentos relacionados.

* SP – Senha Prioritária
Esta senha é destinada a gestantes, idosos, pessoas com deficiência, pessoas com crianças de colo e demais atendimentos prioritários por lei.

Após retirar sua senha, aguarde ser chamado no painel ou pelo atendente.
Estamos à disposição para ajudar!

Para organizar melhor o fluxo e agilizar seu atendimento, utilize nosso sistema de tickets.
Ao retirar sua senha, informe seu nome completo e selecione o tipo de atendimento desejado:

* SG – Senha Geral
Atendimentos comuns, como informações, agendamentos e serviços gerais.
⏱ Tempo estimado de espera: 15 minutos

* SE – Senha de Exames
Para retirada de exames, entrega de documentos ou conferência de resultados.
⏱ Tempo estimado de espera: 10 minutos

* SP – Senha Prioritária
Destinada a gestantes, idosos, pessoas com deficiência, lactantes, pessoas com crianças de colo e demais prioridades por lei.
⏱ Tempo estimado de espera: 5 minutos

 # Modelo de Ficha de Atendimento (Gerada automaticamente)

FICHA DE ATENDIMENTO
Nome: __________
Tipo de Atendimento: ____ (SG / SE / SP)
Número da Senha: _____

📅 Data: //__
⏰ Hora da Emissão: :

⏱ Tempo Estimado para Atendimento:

SG – Senha Geral: 15 minutos

SE – Retirada de Exames: 10 minutos

SP – Prioritária: 5 minutos

Previsão aproximada de atendimento: 

# O cliente também pede que seja emitido relatório
diário e mensal, contendo:
 Quantitativo geral das senhas emitidas.
 Quantitativo geral das senhas atendidas.
 Quantitativo das senhas emitidas, por prioridade.
 Quantitativo das senhas atendidas, por prioridade.
 Relatório detalhado das senhas contendo, numeração,
tipo de senha, data e hora da emissão e data e hora do
atendimento, guichê responsável pelo SA, caso não tenha
sido atendida estes últimos campos ficarão em branco.
 Relatório do TM, que devido à variação aleatória no
atendimento poderá mudar.

<!DOCTYPE HTML>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Ficha de Atendimento - Sistema</title>
  <style>
    :root{font-family:system-ui,-apple-system,'Segoe UI',Roboto,'Helvetica Neue',Arial}
    body{margin:0;padding:20px;background:#116bc5;color:#000000}
    .container{max-width:1100px;margin:0 auto}
    h1{font-size:1.6rem;margin:0 0 14px}
    .card{background:#ffffff;border-radius:8px;box-shadow:0 6px 18px rgba(0, 255, 8, 0.266);padding:16px;margin-bottom:16px}
    label{display:block;margin:8px 0 4px;font-size:0.9rem} 
    input,select,button{padding:8px;border-radius:6px;border:1px solid #069317;font-size:0.95rem}
    .row{display:flex;gap:12px;align-items:center}
    .row .col{flex:1}
    table{width:100%;border-collapse:collapse;margin-top:12px}
    th,td{padding:8px;border-bottom:1px solid #2b7fd3;text-align:left}
    .muted{color:rgb(0, 0, 224)}
    .actions{display:flex;gap:8px;flex-wrap:wrap}
    .small{font-size:0.85rem}
    .btn{cursor:pointer}
    .success{background:#00df52}
    .danger{background:#f61000}
    .badge{display:inline-block;padding:4px 8px;border-radius:999px;font-size:0.8rem}
  </style>
</head>
<body>
  <div class="container">
    <h1>Ficha de Atendimento — Sistema (HTML5 + JavaScript)</h1>

    <div class="card">
      <strong>Emitir nova senha</strong>
      <div class="row" style="margin-top:8px">
        <div class="col">
          <label>Nome (opcional):</label>
          <input id="inputNome" placeholder="Nome do cliente" />
        </div>
        <div style="width:180px">
          <label>Tipo de Atendimento:</label>
          <select id="selectTipo">
            <option value="SG">SG — Senha Geral</option>
            <option value="SE">SE — Retirada de Exames</option>
            <option value="SP">SP — Prioritária</option>
          </select>
        </div>
        <div style="width:170px">
          <label>Emitir senha</label>
          <button id="btnEmitir" class="btn">Emitir</button>
        </div>
      </div>
      <p class="muted small">Tempos estimados: SG 15 min • SE 10 min • SP 5 min (previsão aproximada)</p>
    </div>

    <div class="card">
      <strong>Lista de senhas emitidas</strong>
      <div class="actions" style="margin-top:8px">
        <button id="btnAtenderProxima" class="btn">Atender próxima (prioriza SP)</button>
        <button id="btnLimpar" class="btn">Limpar dados (apaga localStorage)</button>
        <button id="btnExportCSV" class="btn">Exportar CSV</button>
      </div>

      <table id="tableSenhas">
        <thead>
          <tr><th>#</th><th>Nome</th><th>Tipo</th><th>Emitida</th><th>Atendida</th><th>Guichê</th><th>Tempo (min)</th><th>Acões</th></tr>
        </thead>
        <tbody></tbody>
      </table>
    </div>

    <div class="card">
      <strong>Relatórios</strong>
      <div style="display:flex;gap:12px;margin-top:8px;flex-wrap:wrap">
        <div style="min-width:220px">
          <label>Relatório Diário (data):</label>
          <input type="date" id="reportDate" />
        </div>
        <div style="min-width:220px">
          <label>Relatório Mensal (mês):</label>
          <input type="month" id="reportMonth" />
        </div>
        <div style="align-self:end">
          <button id="btnGerarDiario">Gerar Diário</button>
          <button id="btnGerarMensal">Gerar Mensal</button>
        </div>
      </div>

      <div id="reportArea" style="margin-top:12px"></div>
    </div>
  </div>

<script>
   
// Modelo simples de sistema de senhas — persistência em localStorage
const LS_KEY = 'ficha_senhas_v1';
let db = loadDB();
let nextNumber = db.nextNumber || 1;

// DOM
const tbody = document.querySelector('#tableSenhas tbody');
const inputNome = document.getElementById('inputNome');
const selectTipo = document.getElementById('selectTipo');
const btnEmitir = document.getElementById('btnEmitir');
const btnAtenderProxima = document.getElementById('btnAtenderProxima');
const btnLimpar = document.getElementById('btnLimpar');
const btnExportCSV = document.getElementById('btnExportCSV');
const reportDate = document.getElementById('reportDate');
const reportMonth = document.getElementById('reportMonth');
const btnGerarDiario = document.getElementById('btnGerarDiario');
const btnGerarMensal = document.getElementById('btnGerarMensal');
const reportArea = document.getElementById('reportArea');

btnEmitir.addEventListener('click', emitirSenha);
btnAtenderProxima.addEventListener('click', atenderProxima);
btnLimpar.addEventListener('click', limparDados);
btnExportCSV.addEventListener('click', exportCSV);
btnGerarDiario.addEventListener('click', ()=>gerarRelatorio('diario'));
btnGerarMensal.addEventListener('click', ()=>gerarRelatorio('mensal'));

render();

function loadDB(){
  try{
    const raw = localStorage.getItem(LS_KEY);
    if(raw) return JSON.parse(raw);
  }catch(e){}
  return {tickets:[], nextNumber:1};
}
function saveDB(){
  db.nextNumber = nextNumber;
  localStorage.setItem(LS_KEY, JSON.stringify(db));
}

function emitirSenha(){
  const nome = inputNome.value.trim();
  const tipo = selectTipo.value;
  const numero = nextNumber++;
  const now = new Date();
  const ticket = {
    id: numero,
    nome: nome || '',
    tipo,
    emitida: now.toISOString(),
    atendida: null,
    guiche: '',
  };
  db.tickets.push(ticket);
  saveDB();
  inputNome.value = '';
  render();
}

function render(){
  tbody.innerHTML = '';
  // sort by id asc
  db.tickets.slice().sort((a,b)=>a.id-b.id).forEach(t=>{
    const tr = document.createElement('tr');
    const emitida = formatDate(t.emitida);
    const atendida = t.atendida ? formatDate(t.atendida) : '';
    const tempoMin = t.atendida ? Math.round((new Date(t.atendida)-new Date(t.emitida))/60000) : '';
    tr.innerHTML = `
      <td>${t.id}</td>
      <td>${escapeHtml(t.nome)}</td>
      <td>${t.tipo}</td>
      <td>${emitida}</td>
      <td>${atendida}</td>
      <td>${t.guiche || ''}</td>
      <td>${tempoMin}</td>
      <td>
        ${t.atendida ? '' : `<button onclick="atender(${t.id})">Atender</button>`}
        <button onclick="remover(${t.id})">Remover</button>
      </td>
    `;
    tbody.appendChild(tr);
  });
}

// Expor funções para uso inline buttons
window.atender = function(id){
  const guiche = prompt('Informe o guichê responsável (ex: G1):','G1');
  if(guiche===null) return; // cancelou
  const t = db.tickets.find(x=>x.id===id);
  if(!t) return alert('Senha não encontrada');
  t.atendida = new Date().toISOString();
  t.guiche = guiche;
  saveDB(); render();
}

window.remover = function(id){
  if(!confirm('Remover esta senha?')) return;
  db.tickets = db.tickets.filter(x=>x.id!==id);
  saveDB(); render();
}

function atenderProxima(){
  // prioriza SP -> SE -> SG e a mais antiga de cada
  const pendientes = db.tickets.filter(t=>!t.atendida);
  if(pendientes.length===0) return alert('Não há senhas pendentes.');
  const ordem = ['SP','SE','SG'];
  let escolhido = null;
  for(const tipo of ordem){
    const achado = pendientes.filter(t=>t.tipo===tipo).sort((a,b)=>new Date(a.emitida)-new Date(b.emitida))[0];
    if(achado){ escolhido = achado; break; }
  }
  if(!escolhido) { escolhido = pendientes.sort((a,b)=>new Date(a.emitida)-new Date(b.emitida))[0]; }
  const guiche = prompt('Atendendo próxima. Informe o guichê (ex: G1):','G1');
  if(guiche===null) return;
  escolhido.atendida = new Date().toISOString();
  escolhido.guiche = guiche;
  saveDB(); render();
}

function limparDados(){
  if(!confirm('Apagar todos os registros e reiniciar números?')) return;
  db = {tickets:[], nextNumber:1}; nextNumber = 1; saveDB(); render(); reportArea.innerHTML='';
}

function exportCSV(){
  if(db.tickets.length===0) return alert('Sem dados para exportar.');
  const rows = [['id','nome','tipo','emitida','atendida','guiche']];
  db.tickets.forEach(t=>rows.push([t.id, t.nome, t.tipo, t.emitida, t.atendida||'', t.guiche||'']));
  const csv = rows.map(r=>r.map(cell=>`"${String(cell).replace(/"/g,'""')}"`).join(',')).join('\n');
  const blob = new Blob([csv],{type:'text/csv;utf-8'});
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a'); a.href = url; a.download = 'senhas_export.csv'; document.body.appendChild(a); a.click(); a.remove(); URL.revokeObjectURL(url);
}

function gerarRelatorio(tipo){
  if(tipo==='diario'){
    const val = reportDate.value; if(!val) return alert('Escolha uma data para o relatório diário.');
    const dayStart = new Date(val+'T00:00:00');
    const dayEnd = new Date(val+'T23:59:59');
    const tickets = db.tickets.filter(t=>{
      const d = new Date(t.emitida);
      return d>=dayStart && d<=dayEnd;
    });
    mostrarRelatorio(tickets,'Diário', val);
  } else {
    const val = reportMonth.value; if(!val) return alert('Escolha um mês para o relatório mensal.');
    // val like YYYY-MM
    const [y,m] = val.split('-').map(Number);
    const start = new Date(y,m-1,1,0,0,0);
    const end = new Date(y,m,0,23,59,59);
    const tickets = db.tickets.filter(t=>{
      const d = new Date(t.emitida);
      return d>=start && d<=end;
    });
    mostrarRelatorio(tickets,'Mensal', val);
  }
}

function mostrarRelatorio(tickets,title,periodLabel){
  // Quantitativos
  const totalEmitidas = tickets.length;
  const totalAtendidas = tickets.filter(t=>t.atendida).length;
  const tipos = ['SG','SE','SP'];
  const emitidasPorTipo = {};
  const atendidasPorTipo = {};
  tipos.forEach(tp=>{ emitidasPorTipo[tp] = tickets.filter(t=>t.tipo===tp).length; atendidasPorTipo[tp] = tickets.filter(t=>t.tipo===tp && t.atendida).length; });
  // Detalhado
  const detalhado = tickets.slice().sort((a,b)=>a.id-b.id).map(t=>({
    id:t.id, tipo:t.tipo, emitida:t.emitida, atendida:t.atendida||'', guiche:t.guiche||''
  }));
  // Relatório do TM (Tempo Médio) — calcular tempo médio das senhas atendidas em minutos
  const atendidos = tickets.filter(t=>t.atendida);
  const tempos = atendidos.map(t=> (new Date(t.atendida)-new Date(t.emitida))/60000 );
  const tm = tempos.length ? (tempos.reduce((a,b)=>a+b,0)/tempos.length) : 0;

  // Monta HTML
  let html = `<div><h3>Relatório ${title} — ${periodLabel}</h3>`;
  html += `<p><strong>Total emitidas:</strong> ${totalEmitidas} &nbsp; <strong>Total atendidas:</strong> ${totalAtendidas}</p>`;
  html += `<p><strong>Emitidas por prioridade:</strong> ${tipos.map(tp=>`${tp}: ${emitidasPorTipo[tp]}`).join(' • ')}</p>`;
  html += `<p><strong>Atendidas por prioridade:</strong> ${tipos.map(tp=>`${tp}: ${atendidasPorTipo[tp]}`).join(' • ')}</p>`;
  html += `<p><strong>Tempo médio (TM) de atendimento (min):</strong> ${tm?tm.toFixed(1):'—'}</p>`;
  html += `<details><summary>Relatório detalhado (${detalhado.length} itens)</summary>`;
  html += `<table style="width:100%;margin-top:8px;border-collapse:collapse"><thead><tr><th>#</th><th>Tipo</th><th>Emitida</th><th>Atendida</th><th>Guichê</th></tr></thead><tbody>`;
  detalhado.forEach(d=>{
    html += `<tr><td>${d.id}</td><td>${d.tipo}</td><td>${formatDate(d.emitida)}</td><td>${d.atendida?formatDate(d.atendida):''}</td><td>${d.guiche}</td></tr>`;
  });
  html += `</tbody></table></details>`;
  html += `<p class="muted small">Observação: o "Relatório do TM" é calculado a partir das senhas atendidas no período. Como o atendimento é dependente do fluxo real, o TM pode variar.</p>`;
  html += `<div style="margin-top:8px"><button onclick='downloadRelatorioCSV(${JSON.stringify(detalhado)})'>Baixar detalhado (CSV)</button></div>`;
  html += `</div>`;
  reportArea.innerHTML = html;
}

function downloadRelatorioCSV(arr){
  if(!arr || !arr.length) return alert('Sem dados detalhados.');
  const rows = [['id','tipo','emitida','atendida','guiche']];
  arr.forEach(r=>rows.push([r.id,r.tipo,r.emitida,r.atendida||'',r.guiche||'']));
  const csv = rows.map(r=>r.map(cell=>`"${String(cell).replace(/"/g,'""')}"`).join(',')).join('\n');
  const blob = new Blob([csv],{type:'text/csv;utf-8'});
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a'); a.href = url; a.download = 'relatorio_detalhado.csv'; document.body.appendChild(a); a.click(); a.remove(); URL.revokeObjectURL(url);
}

function formatDate(isot){ if(!isot) return ''; const d = new Date(isot); return d.toLocaleString(); }
function escapeHtml(s){ return String(s||'').replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;'); }

// Utility to allow calling downloadRelatorioCSV with the object passed from innerHTML onclick
window.downloadRelatorioCSV = function(obj){
  // when onclick is inline and obj becomes string, try to parse
  if(typeof obj === 'string'){
    try{ obj = JSON.parse(obj); }catch(e){ obj = []; }
  }
  downloadRelatorioCSV(obj);
}

// initialize nextNumber if coming from saved DB
if(db.nextNumber) nextNumber = db.nextNumber;

</script>
</body>
</html>
