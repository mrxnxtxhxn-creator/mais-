<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Central de Reatribuição - Gestão Operacional de Pacotes</title>
  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Chart.js -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <!-- Lucide Icons -->
  <script src="https://unpkg.com/lucide@latest"></script>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
    body { font-family: 'Inter', sans-serif; }
  </style>
</head>
<body class="bg-slate-100 text-slate-800 flex h-screen overflow-hidden">

  <!-- SIDEBAR (Navegação Esquerda) -->
  <aside class="w-64 bg-slate-900 text-white flex flex-col justify-between shrink-0">
    <div>
      <!-- Header Logos -->
      <div class="p-4 border-b border-slate-800 flex items-center justify-between">
        <div class="bg-yellow-400 text-slate-900 px-2 py-1 rounded font-bold text-xs">Mercado Livre</div>
        <span class="text-xs text-slate-400 font-semibold tracking-wider">KUEHNE+NAGEL</span>
      </div>

      <!-- Menu Navigation -->
      <nav class="mt-4 px-2 space-y-1">
        <a href="#" class="flex items-center gap-3 px-3 py-2.5 bg-blue-600 text-white rounded-lg text-sm font-medium">
          <i data-lucide="layout-dashboard" class="w-5 h-5"></i> Dashboard
        </a>
        <a href="#" class="flex items-center gap-3 px-3 py-2.5 text-slate-400 hover:bg-slate-800 hover:text-white rounded-lg text-sm font-medium transition">
          <i data-lucide="search" class="w-5 h-5"></i> Consultar ID
        </a>
        <a href="#" class="flex items-center gap-3 px-3 py-2.5 text-slate-400 hover:bg-slate-800 hover:text-white rounded-lg text-sm font-medium transition">
          <i data-lucide="arrow-left-right" class="w-5 h-5"></i> Reatribuição
        </a>
        <a href="#" class="flex items-center gap-3 px-3 py-2.5 text-slate-400 hover:bg-slate-800 hover:text-white rounded-lg text-sm font-medium transition">
          <i data-lucide="alert-triangle" class="w-5 h-5"></i> Problem Solving
        </a>
        <a href="#" class="flex items-center gap-3 px-3 py-2.5 text-slate-400 hover:bg-slate-800 hover:text-white rounded-lg text-sm font-medium transition">
          <i data-lucide="bar-chart-2" class="w-5 h-5"></i> Performance
        </a>
        <a href="#" class="flex items-center gap-3 px-3 py-2.5 text-slate-400 hover:bg-slate-800 hover:text-white rounded-lg text-sm font-medium transition">
          <i data-lucide="history" class="w-5 h-5"></i> Histórico
        </a>
        <a href="#" class="flex items-center gap-3 px-3 py-2.5 text-slate-400 hover:bg-slate-800 hover:text-white rounded-lg text-sm font-medium transition">
          <i data-lucide="settings" class="w-5 h-5"></i> Configurações
        </a>
      </nav>
    </div>

    <!-- Sidebar Footer -->
    <div class="p-4 border-t border-slate-800 text-xs text-slate-400 space-y-1">
      <p class="font-bold text-slate-300">Juntos</p>
      <p>entregamos um amanhã melhor.</p>
    </div>
  </aside>

  <!-- PAINEL PRINCIPAL + SIDEBAR DIREITA -->
  <div class="flex-1 flex flex-col min-w-0 overflow-hidden">

    <!-- HEADER SUPERIOR -->
    <header class="bg-white border-b border-slate-200 px-6 py-3 flex items-center justify-between shrink-0">
      <div>
        <h1 class="text-xl font-bold text-slate-900">Central de Reatribuição</h1>
        <p class="text-xs text-slate-500">Gestão operacional de pacotes</p>
      </div>

      <div class="flex items-center gap-4 text-xs text-slate-500">
        <div class="flex items-center gap-1.5">
          <i data-lucide="rotate-cw" class="w-4 h-4 cursor-pointer hover:text-slate-700" onclick="window.location.reload()"></i>
          <span>Atualizado em: <strong class="text-slate-700" id="lastUpdate">05/09/2026 15:42</strong></span>
        </div>
        <button class="p-1 hover:bg-slate-100 rounded-lg"><i data-lucide="sliders-horizontal" class="w-4 h-4"></i></button>
        <button class="p-1 hover:bg-slate-100 rounded-lg"><i data-lucide="x" class="w-4 h-4"></i></button>
      </div>
    </header>

    <!-- CONTEÚDO (DASHBOARD + DETALHES) -->
    <div class="flex-1 flex overflow-hidden">
      
      <!-- DASHBOARD CENTRAL -->
      <main class="flex-1 p-6 overflow-y-auto space-y-6">

        <!-- BUSCA GERAL -->
        <div class="flex gap-2">
          <div class="relative flex-1">
            <i data-lucide="search" class="w-5 h-5 absolute left-3 top-2.5 text-slate-400"></i>
            <input type="text" id="searchInput" onkeyup="filtrarTabela()" placeholder="Digite um ID, rota, bairro, cidade ou placa..." class="w-full pl-10 pr-4 py-2 border border-slate-300 rounded-lg text-sm focus:outline-none focus:ring-2 focus:ring-blue-500 bg-white">
          </div>
          <button onclick="filtrarTabela()" class="px-6 py-2 bg-slate-900 text-white rounded-lg text-sm font-semibold hover:bg-slate-800 transition">Consultar</button>
        </div>

        <!-- CARDS DE MÉTRICAS (KPIs) -->
        <div class="grid grid-cols-5 gap-4">
          <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm flex items-center gap-3">
            <div class="p-3 bg-blue-50 text-blue-600 rounded-lg"><i data-lucide="box" class="w-6 h-6"></i></div>
            <div>
              <p class="text-xs font-semibold text-slate-500">Total de IDs</p>
              <h3 class="text-xl font-bold text-slate-900">4.093</h3>
              <span class="text-[10px] text-slate-400">100%</span>
            </div>
          </div>

          <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm flex items-center gap-3">
            <div class="p-3 bg-amber-50 text-amber-600 rounded-lg"><i data-lucide="alert-circle" class="w-6 h-6"></i></div>
            <div>
              <p class="text-xs font-semibold text-slate-500">Pendentes</p>
              <h3 class="text-xl font-bold text-amber-600">820</h3>
              <span class="text-[10px] text-amber-500 font-medium">20,0%</span>
            </div>
          </div>

          <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm flex items-center gap-3">
            <div class="p-3 bg-red-50 text-red-600 rounded-lg"><i data-lucide="alert-octagon" class="w-6 h-6"></i></div>
            <div>
              <p class="text-xs font-semibold text-slate-500">Problem Solving</p>
              <h3 class="text-xl font-bold text-red-600">147</h3>
              <span class="text-[10px] text-red-500 font-medium">3,6%</span>
            </div>
          </div>

          <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm flex items-center gap-3">
            <div class="p-3 bg-indigo-50 text-indigo-600 rounded-lg"><i data-lucide="truck" class="w-6 h-6"></i></div>
            <div>
              <p class="text-xs font-semibold text-slate-500">Rotas</p>
              <h3 class="text-xl font-bold text-slate-900">126</h3>
              <span class="text-[10px] text-slate-400">-</span>
            </div>
          </div>

          <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm flex items-center gap-3">
            <div class="p-3 bg-emerald-50 text-emerald-600 rounded-lg"><i data-lucide="check-circle" class="w-6 h-6"></i></div>
            <div>
              <p class="text-xs font-semibold text-slate-500">Reatribuições</p>
              <h3 class="text-xl font-bold text-emerald-600">3.126</h3>
              <span class="text-[10px] text-emerald-500 font-medium">76,4%</span>
            </div>
          </div>
        </div>

        <!-- FILTROS MÚLTIPLOS -->
        <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm space-y-3">
          <div class="flex items-center gap-2 text-xs font-semibold text-slate-600">
            <i data-lucide="filter" class="w-4 h-4"></i> Filtros
          </div>

          <div class="grid grid-cols-5 gap-3">
            <select class="border border-slate-200 rounded-lg p-2 text-xs text-slate-600 bg-slate-50 focus:bg-white"><option>Data: Todos</option></select>
            <select class="border border-slate-200 rounded-lg p-2 text-xs text-slate-600 bg-slate-50 focus:bg-white"><option>Ciclo: Todos</option></select>
            <select class="border border-slate-200 rounded-lg p-2 text-xs text-slate-600 bg-slate-50 focus:bg-white"><option>Cluster: Todos</option></select>
            <select class="border border-slate-200 rounded-lg p-2 text-xs text-slate-600 bg-slate-50 focus:bg-white"><option>Status: Todos</option></select>
            <select class="border border-slate-200 rounded-lg p-2 text-xs text-slate-600 bg-slate-50 focus:bg-white"><option>Promessa: Todos</option></select>
            <select class="border border-slate-200 rounded-lg p-2 text-xs text-slate-600 bg-slate-50 focus:bg-white"><option>Cidade: Todos</option></select>
            <select class="border border-slate-200 rounded-lg p-2 text-xs text-slate-600 bg-slate-50 focus:bg-white"><option>Bairro: Todos</option></select>
            <select class="border border-slate-200 rounded-lg p-2 text-xs text-slate-600 bg-slate-50 focus:bg-white"><option>Transportadora: Todos</option></select>
            <select class="border border-slate-200 rounded-lg p-2 text-xs text-slate-600 bg-slate-50 focus:bg-white"><option>Rota: Todos</option></select>
            
            <button onclick="limparFiltros()" class="flex items-center justify-center gap-2 border border-slate-300 text-slate-700 rounded-lg p-2 text-xs font-medium hover:bg-slate-50 transition">
              <i data-lucide="rotate-ccw" class="w-3.5 h-3.5"></i> Limpar filtros
            </button>
          </div>
        </div>

        <!-- GRÁFICOS OPERACIONAIS -->
        <div class="grid grid-cols-3 gap-4">
          <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm">
            <h4 class="text-xs font-bold text-slate-700 mb-3">Pacotes por Cluster</h4>
            <div class="h-44">
              <canvas id="barClusterChart"></canvas>
            </div>
          </div>

          <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm flex flex-col justify-between">
            <h4 class="text-xs font-bold text-slate-700 mb-1">Status dos Pacotes</h4>
            <div class="h-44 relative flex items-center justify-center">
              <canvas id="donutStatusChart"></canvas>
            </div>
          </div>

          <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm">
            <h4 class="text-xs font-bold text-slate-700 mb-3">Promessa x Quantidade</h4>
            <div class="h-44">
              <canvas id="linePromessaChart"></canvas>
            </div>
          </div>
        </div>

        <!-- TABELA DE PACOTES PARA REATRIBUIÇÃO -->
        <div class="bg-white rounded-xl border border-slate-200 shadow-sm overflow-hidden">
          <div class="p-4 border-b border-slate-100 flex items-center justify-between">
            <div class="flex items-center gap-3">
              <h3 class="text-sm font-bold text-slate-800 flex items-center gap-2">
                <i data-lucide="boxes" class="w-4 h-4 text-blue-600"></i> Pacotes para Reatribuição
              </h3>
              <span class="bg-blue-100 text-blue-700 text-xs font-semibold px-2.5 py-0.5 rounded-full" id="countRegistros">820 registros</span>
            </div>
          </div>

          <!-- Tabela com IDs Reais -->
          <div class="overflow-x-auto">
            <table class="w-full text-left text-xs border-collapse" id="pacotesTable">
              <thead class="bg-slate-50 text-slate-500 border-b border-slate-200">
                <tr>
                  <th class="p-3"><input type="checkbox" class="rounded text-blue-600"></th>
                  <th class="p-3">ID</th>
                  <th class="p-3">Cidade</th>
                  <th class="p-3">Bairro</th>
                  <th class="p-3">Cluster</th>
                  <th class="p-3">Promessa</th>
                  <th class="p-3">Status</th>
                  <th class="p-3">Rota Sugerida</th>
                  <th class="p-3">Transportadora</th>
                  <th class="p-3 text-center">Ações</th>
                </tr>
              </thead>
              <tbody class="divide-y divide-slate-100 text-slate-700 font-medium" id="tabelaCorpo">
                <!-- Preenchido via JavaScript -->
              </tbody>
            </table>
          </div>

          <!-- Paginação -->
          <div class="p-3 bg-slate-50 border-t border-slate-200 flex items-center justify-between text-xs text-slate-500">
            <div class="flex items-center gap-1">
              <button class="px-2 py-1 border rounded bg-white">&lt;</button>
              <button class="px-2 py-1 border rounded bg-blue-600 text-white font-bold">1</button>
              <button class="px-2 py-1 border rounded bg-white">2</button>
              <button class="px-2 py-1 border rounded bg-white">3</button>
              <button class="px-2 py-1 border rounded bg-white">4</button>
              <span>... 82</span>
              <button class="px-2 py-1 border rounded bg-white">&gt;</button>
            </div>
            <span>Itens por página: <b>10</b></span>
          </div>
        </div>

      </main>

      <!-- SIDEBAR DIREITA (DETALHE DO PACOTE SELECIONADO) -->
      <aside class="w-80 bg-white border-l border-slate-200 p-4 flex flex-col justify-between shrink-0 overflow-y-auto space-y-4">
        
        <div>
          <div class="flex items-center justify-between pb-3 border-b border-slate-100">
            <h3 class="font-bold text-slate-800 text-sm">Detalhe do Pacote</h3>
            <button class="text-slate-400 hover:text-slate-600"><i data-lucide="x" class="w-4 h-4"></i></button>
          </div>

          <!-- Busca de ID na Sidebar -->
          <div class="mt-3 flex gap-1">
            <input type="text" id="sideSearchInput" value="12345678" class="w-full border border-slate-300 rounded-lg px-3 py-1.5 text-xs font-semibold text-slate-800">
            <button onclick="buscarPorIdSide()" class="bg-slate-900 text-white p-2 rounded-lg hover:bg-slate-800"><i data-lucide="search" class="w-4 h-4"></i></button>
          </div>

          <div class="mt-3 flex items-center justify-between">
            <span class="bg-amber-100 text-amber-700 text-xs font-bold px-2 py-0.5 rounded" id="detalheStatusBadge">Pendente</span>
            <span class="text-xs font-bold text-slate-700 flex items-center gap-1">
              <div class="w-2 h-2 rounded-full bg-yellow-400"></div> Mercado Livre
            </span>
          </div>

          <h2 class="text-lg font-bold text-slate-900 mt-2" id="detalheIdHeader">ID: 12345678</h2>

          <!-- Localização -->
          <div class="mt-4 space-y-2 text-xs">
            <p class="font-bold text-slate-700 border-b pb-1">Localização</p>
            <div class="grid grid-cols-2 gap-y-2 text-slate-600">
              <span class="flex items-center gap-1"><i data-lucide="map-pin" class="w-3.5 h-3.5 text-slate-400"></i> Cidade:</span>
              <strong class="text-slate-800" id="detalheCidade">Queimados</strong>
              <span class="flex items-center gap-1"><i data-lucide="navigation" class="w-3.5 h-3.5 text-slate-400"></i> Bairro:</span>
              <strong class="text-slate-800" id="detalheBairro">Centro</strong>
              <span class="flex items-center gap-1"><i data-lucide="layers" class="w-3.5 h-3.5 text-slate-400"></i> Cluster:</span>
              <strong class="text-slate-800" id="detalheCluster">R6</strong>
              <span class="flex items-center gap-1"><i data-lucide="mail" class="w-3.5 h-3.5 text-slate-400"></i> CEP:</span>
              <strong class="text-slate-800" id="detalheCep">26385-000</strong>
            </div>
          </div>

          <!-- Operação -->
          <div class="mt-4 space-y-2 text-xs">
            <p class="font-bold text-slate-700 border-b pb-1">Operação</p>
            <div class="space-y-1.5 text-slate-600">
              <div class="flex justify-between"><span>Status:</span> <span class="text-amber-600 font-bold" id="detalheStatus">Pendente</span></div>
              <div class="flex justify-between"><span>Descrição:</span> <strong class="text-slate-800">Produto eletrônico</strong></div>
              <div class="flex justify-between"><span>Promessa:</span> <strong class="text-slate-800" id="detalhePromessa">09/09/2026</strong></div>
              <div class="flex justify-between"><span>Rota atual:</span> <strong class="text-slate-800" id="detalheRotaAtual">A25_PM1</strong></div>
              <div class="flex justify-between"><span>Transportadora:</span> <strong class="text-slate-800" id="detalheTransp">Mercado Livre</strong></div>
            </div>
          </div>

          <!-- Recomendação Inteligente -->
          <div class="mt-4 p-3 bg-emerald-50 border border-emerald-200 rounded-xl space-y-2">
            <div class="flex items-center gap-1.5 text-emerald-800 font-bold text-xs">
              <i data-lucide="lightbulb" class="w-4 h-4 text-emerald-600"></i> Recomendação
            </div>
            <div class="text-xs text-slate-700 space-y-1">
              <p>Gaiola sugerida: <strong class="text-emerald-800" id="detalheGaiola">G-034</strong></p>
              <p>Rota sugerida: <strong class="text-emerald-800" id="detalheRotaSugerida">A27_PM1</strong></p>
              <p>Cluster: <strong class="text-slate-800" id="detalheRecCluster">R6</strong></p>
              <p>Bairro: <strong class="text-slate-800" id="detalheRecBairro">Centro</strong></p>
            </div>
            
            <button onclick="confirmarReatribuicao()" class="w-full mt-2 py-2 bg-emerald-600 text-white text-xs font-bold rounded-lg hover:bg-emerald-700 transition flex items-center justify-center gap-1.5 shadow-sm">
              <i data-lucide="check-circle-2" class="w-4 h-4"></i> Confirmar Reatribuição
            </button>
          </div>

          <!-- Histórico -->
          <div class="mt-4 space-y-2 text-xs">
            <p class="font-bold text-slate-700 border-b pb-1 flex items-center gap-1">
              <i data-lucide="clock" class="w-3.5 h-3.5"></i> Histórico do ID
            </p>
            <ul class="space-y-2 text-[11px] text-slate-600" id="detalheHistorico">
              <li class="flex gap-2"><span class="text-slate-400">05/09 10:24</span> <span>Inclusão na base</span></li>
              <li class="flex gap-2"><span class="text-slate-400">05/09 12:37</span> <span>Status alterado para Pendente</span></li>
              <li class="flex gap-2"><span class="text-slate-400">05/09 14:02</span> <span>Sugerida reatribuição</span></li>
            </ul>
          </div>
        </div>

      </aside>

    </div>

  </div>

  <!-- SCRIPT DE DADOS E LÓGICA LOCAL -->
  <script>
    // Base de dados mockada (Simula o banco de dados local)
    const pacotesMock = [
      { id: "12345678", cidade: "Queimados", bairro: "Centro", cluster: "R6", cep: "26385-000", promessa: "09/09/2026", status: "Pendente", rotaSugerida: "A25_PM1", gaiola: "G-034", transp: "Mercado Livre" },
      { id: "12345679", cidade: "Japeri", bairro: "Vila de Cava", cluster: "6", cep: "26400-110", promessa: "09/09/2026", status: "At Station", rotaSugerida: "A26_PM1", gaiola: "G-012", transp: "Mercado Livre" },
      { id: "12345680", cidade: "Nova Iguaçu", bairro: "Tinguá", cluster: "R10", cep: "26000-000", promessa: "10/09/2026", status: "Problem Solving", rotaSugerida: "A30_AM1", gaiola: "G-089", transp: "DHL" },
      { id: "12345681", cidade: "Queimados", bairro: "Centro", cluster: "10", cep: "26385-100", promessa: "09/09/2026", status: "Pendente", rotaSugerida: "A31_PM1", gaiola: "G-034", transp: "Mercado Livre" },
      { id: "12345682", cidade: "Seropédica", bairro: "Santa Rita", cluster: "R6", cep: "23890-000", promessa: "11/09/2026", status: "Em trânsito", rotaSugerida: "A28_PM1", gaiola: "G-055", transp: "Jadlog" },
      { id: "12345683", cidade: "Itaguaí", bairro: "Jardim América", cluster: "R10", cep: "23810-000", promessa: "12/09/2026", status: "At Station", rotaSugerida: "A32_AM1", gaiola: "G-022", transp: "DHL" },
      { id: "12345684", cidade: "Queimados", bairro: "Parque Estoril", cluster: "6", cep: "26383-000", promessa: "09/09/2026", status: "Pendente", rotaSugerida: "A25_PM1", gaiola: "G-034", transp: "Mercado Livre" },
      { id: "12345685", cidade: "Nova Iguaçu", bairro: "Vila de Cava", cluster: "10", cep: "26080-000", promessa: "10/09/2026", status: "Problem Solving", rotaSugerida: "A30_AM1", gaiola: "G-089", transp: "Jadlog" }
    ];

    // Renderizar Tabela Inicial
    function renderTabela(lista) {
      const corpo = document.getElementById('tabelaCorpo');
      corpo.innerHTML = '';

      lista.forEach(item => {
        let statusBadge = '';
        if (item.status === 'Pendente') statusBadge = 'bg-amber-100 text-amber-700';
        else if (item.status === 'At Station') statusBadge = 'bg-cyan-100 text-cyan-700';
        else if (item.status === 'Problem Solving') statusBadge = 'bg-red-100 text-red-700';
        else statusBadge = 'bg-emerald-100 text-emerald-700';

        const tr = document.createElement('tr');
        tr.className = 'hover:bg-slate-50 transition cursor-pointer';
        tr.onclick = () => carregarDetalhes(item.id);

        tr.innerHTML = `
          <td class="p-3" onclick="event.stopPropagation()"><input type="checkbox" class="rounded"></td>
          <td class="p-3 font-semibold text-slate-900">${item.id}</td>
          <td class="p-3">${item.cidade}</td>
          <td class="p-3">${item.bairro}</td>
          <td class="p-3">${item.cluster}</td>
          <td class="p-3">${item.promessa}</td>
          <td class="p-3"><span class="${statusBadge} px-2 py-0.5 rounded font-semibold text-[11px]">${item.status}</span></td>
          <td class="p-3 text-blue-600 font-semibold">${item.rotaSugerida}</td>
          <td class="p-3">${item.transp}</td>
          <td class="p-3 text-center flex justify-center gap-2" onclick="event.stopPropagation()">
            <button onclick="carregarDetalhes('${item.id}')" class="bg-blue-600 text-white px-3 py-1 rounded hover:bg-blue-700 font-semibold">Ver</button>
            <button class="text-slate-400 hover:text-slate-600"><i data-lucide="more-vertical" class="w-4 h-4"></i></button>
          </td>
        `;
        corpo.appendChild(tr);
      });
      lucide.createIcons();
    }

    // Carregar Detalhes do Pacote Selecionado
    function carregarDetalhes(id) {
      const item = pacotesMock.find(p => p.id === id);
      if (!item) return;

      document.getElementById('sideSearchInput').value = item.id;
      document.getElementById('detalheIdHeader').innerText = `ID: ${item.id}`;
      document.getElementById('detalheCidade').innerText = item.cidade;
      document.getElementById('detalheBairro').innerText = item.bairro;
      document.getElementById('detalheCluster').innerText = item.cluster;
      document.getElementById('detalheCep').innerText = item.cep;
      document.getElementById('detalheStatus').innerText = item.status;
      document.getElementById('detalheStatusBadge').innerText = item.status;
      document.getElementById('detalhePromessa').innerText = item.promessa;
      document.getElementById('detalheRotaAtual').innerText = item.rotaSugerida;
      document.getElementById('detalheTransp').innerText = item.transp;
      document.getElementById('detalheGaiola').innerText = item.gaiola;
      document.getElementById('detalheRotaSugerida').innerText = item.rotaSugerida;
      document.getElementById('detalheRecCluster').innerText = item.cluster;
      document.getElementById('detalheRecBairro').innerText = item.bairro;
    }

    // Filtro de Busca
    function filtrarTabela() {
      const termo = document.getElementById('searchInput').value.toLowerCase();
      const filtrados = pacotesMock.filter(p => 
        p.id.toLowerCase().includes(termo) ||
        p.cidade.toLowerCase().includes(termo) ||
        p.bairro.toLowerCase().includes(termo) ||
        p.rotaSugerida.toLowerCase().includes(termo)
      );
      renderTabela(filtrados);
    }

    function limparFiltros() {
      document.getElementById('searchInput').value = '';
      renderTabela(pacotesMock);
    }

    function buscarPorIdSide() {
      const id = document.getElementById('sideSearchInput').value;
      carregarDetalhes(id);
    }

    function confirmarReatribuicao() {
      alert("Reatribuição confirmada com sucesso!");
    }

    // Inicialização da Tabela e Gráficos
    window.onload = () => {
      renderTabela(pacotesMock);
      carregarDetalhes("12345678");

      // Gráficos Chart.js
      new Chart(document.getElementById('barClusterChart'), {
        type: 'bar',
        data: {
          labels: ['Cluster 6', 'Cluster R6', 'Cluster 10', 'Cluster R10', 'Outros'],
          datasets: [{
            data: [820, 640, 510, 430, 693],
            backgroundColor: ['#3b82f6', '#f97316', '#14b8a6', '#a855f7', '#94a3b8'],
            borderRadius: 4
          }]
        },
        options: { indexAxis: 'y', responsive: true, maintainAspectRatio: false, plugins: { legend: { display: false } } }
      });

      new Chart(document.getElementById('donutStatusChart'), {
        type: 'doughnut',
        data: {
          labels: ['Em trânsito', 'At Station', 'Problem Solving', 'Pendente', 'Outros'],
          datasets: [{
            data: [540, 210, 147, 380, 2816],
            backgroundColor: ['#0284c7', '#10b981', '#ef4444', '#f59e0b', '#cbd5e1']
          }]
        },
        options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { position: 'right', labels: { boxWidth: 10, font: { size: 10 } } } }, cutout: '70%' }
      });

      new Chart(document.getElementById('linePromessaChart'), {
        type: 'line',
        data: {
          labels: ['08/09', '09/09', '10/09', '11/09', '12/09', '13/09', '14/09'],
          datasets: [{
            data: [260, 280, 380, 330, 250, 190, 170],
            borderColor: '#0284c7',
            backgroundColor: 'rgba(2, 132, 199, 0.1)',
            fill: true,
            tension: 0.3
          }]
        },
        options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { display: false } } }
      });
    };
  </script>
</body>
</html>
