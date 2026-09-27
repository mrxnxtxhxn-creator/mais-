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
  <!-- SheetJS (Excel Parser) & PapaParse (CSV) -->
  <script src="https://cdn.jsdelivr.net/npm/xlsx@0.18.5/dist/xlsx.full.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/papaparse@5.4.1/papaparse.min.js"></script>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
    body { font-family: 'Inter', sans-serif; }
    .sidebar-detail-transition { transition: transform 0.3s ease-in-out, margin-right 0.3s ease-in-out; }
  </style>
</head>
<body class="bg-slate-100 text-slate-800 flex h-screen overflow-hidden">

  <!-- SIDEBAR ESQUERDA (Navegação Geral) -->
  <aside class="w-64 bg-slate-900 text-white flex flex-col justify-between shrink-0 z-20">
    <div>
      <div class="p-4 border-b border-slate-800 flex items-center justify-between">
        <div class="bg-yellow-400 text-slate-900 px-2 py-1 rounded font-bold text-xs">Mercado Livre</div>
        <span class="text-xs text-slate-400 font-semibold tracking-wider">KUEHNE+NAGEL</span>
      </div>

      <!-- Links de Navegação com Troca de Ecrã -->
      <nav class="mt-4 px-2 space-y-1" id="mainNav">
        <button onclick="navegarPara('dashboard')" id="nav-dashboard" class="w-full flex items-center gap-3 px-3 py-2.5 bg-blue-600 text-white rounded-lg text-sm font-medium transition">
          <i data-lucide="layout-dashboard" class="w-5 h-5"></i> Dashboard
        </button>
        <button onclick="navegarPara('consultar')" id="nav-consultar" class="w-full flex items-center gap-3 px-3 py-2.5 text-slate-400 hover:bg-slate-800 hover:text-white rounded-lg text-sm font-medium transition">
          <i data-lucide="search" class="w-5 h-5"></i> Consultar ID
        </button>
        <button onclick="navegarPara('reatribuicao')" id="nav-reatribuicao" class="w-full flex items-center gap-3 px-3 py-2.5 text-slate-400 hover:bg-slate-800 hover:text-white rounded-lg text-sm font-medium transition">
          <i data-lucide="arrow-left-right" class="w-5 h-5"></i> Reatribuição
        </button>
        <button onclick="navegarPara('problemsolving')" id="nav-problemsolving" class="w-full flex items-center gap-3 px-3 py-2.5 text-slate-400 hover:bg-slate-800 hover:text-white rounded-lg text-sm font-medium transition">
          <i data-lucide="alert-triangle" class="w-5 h-5"></i> Problem Solving
        </button>
        <button onclick="navegarPara('performance')" id="nav-performance" class="w-full flex items-center gap-3 px-3 py-2.5 text-slate-400 hover:bg-slate-800 hover:text-white rounded-lg text-sm font-medium transition">
          <i data-lucide="bar-chart-2" class="w-5 h-5"></i> Performance
        </button>
        <button onclick="navegarPara('historico')" id="nav-historico" class="w-full flex items-center gap-3 px-3 py-2.5 text-slate-400 hover:bg-slate-800 hover:text-white rounded-lg text-sm font-medium transition">
          <i data-lucide="history" class="w-5 h-5"></i> Histórico
        </button>
        <button onclick="navegarPara('configuracoes')" id="nav-configuracoes" class="w-full flex items-center gap-3 px-3 py-2.5 text-slate-400 hover:bg-slate-800 hover:text-white rounded-lg text-sm font-medium transition">
          <i data-lucide="settings" class="w-5 h-5"></i> Configurações
        </button>
      </nav>
    </div>

    <div class="p-4 border-t border-slate-800 text-xs text-slate-400 space-y-1">
      <p class="font-bold text-slate-300">Juntos</p>
      <p>entregamos um amanhã melhor.</p>
    </div>
  </aside>

  <!-- ÁREA CENTRAL DE CONTEÚDO -->
  <div class="flex-1 flex flex-col min-w-0 overflow-hidden">

    <!-- HEADER SUPERIOR -->
    <header class="bg-white border-b border-slate-200 px-6 py-3 flex items-center justify-between shrink-0">
      <div>
        <h1 class="text-xl font-bold text-slate-900" id="headerTitle">Central de Reatribuição</h1>
        <p class="text-xs text-slate-500" id="headerSub">Gestão operacional de pacotes</p>
      </div>

      <div class="flex items-center gap-4 text-xs text-slate-500">
        <!-- Importador de Planilha CSV/XLSX -->
        <label class="flex items-center gap-1.5 bg-blue-50 text-blue-700 px-3 py-1.5 rounded-lg border border-blue-200 font-semibold cursor-pointer hover:bg-blue-100 transition">
          <i data-lucide="file-up" class="w-4 h-4"></i> Carregar Planilha
          <input type="file" id="fileInput" accept=".csv, .xlsx, .xls" class="hidden" onchange="carregarPlanilha(event)">
        </label>

        <div class="flex items-center gap-1.5">
          <i data-lucide="rotate-cw" class="w-4 h-4 cursor-pointer hover:text-slate-700" onclick="resetarDados()"></i>
          <span>Atualizado: <strong class="text-slate-700" id="lastUpdate">Agora</strong></span>
        </div>
      </div>
    </header>

    <!-- ÁREA DE ECRÃS VARIÁVEIS -->
    <div class="flex-1 flex overflow-hidden relative">

      <!-- SECÇÃO: DASHBOARD (PADRÃO) -->
      <main id="screen-dashboard" class="view-screen flex-1 p-6 overflow-y-auto space-y-6">

        <!-- BUSCA RÁPIDA -->
        <div class="flex gap-2">
          <div class="relative flex-1">
            <i data-lucide="search" class="w-5 h-5 absolute left-3 top-2.5 text-slate-400"></i>
            <input type="text" id="searchInput" onkeyup="aplicarFiltros()" placeholder="Digite um ID, rota, bairro, cidade..." class="w-full pl-10 pr-4 py-2 border border-slate-300 rounded-lg text-sm focus:outline-none focus:ring-2 focus:ring-blue-500 bg-white">
          </div>
          <button onclick="aplicarFiltros()" class="px-6 py-2 bg-slate-900 text-white rounded-lg text-sm font-semibold hover:bg-slate-800 transition">Consultar</button>
        </div>

        <!-- CARDS DE MÉTRICAS (KPIs) -->
        <div class="grid grid-cols-5 gap-4">
          <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm flex items-center gap-3">
            <div class="p-3 bg-blue-50 text-blue-600 rounded-lg"><i data-lucide="box" class="w-6 h-6"></i></div>
            <div>
              <p class="text-xs font-semibold text-slate-500">Total de IDs</p>
              <h3 class="text-xl font-bold text-slate-900" id="kpiTotal">0</h3>
            </div>
          </div>

          <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm flex items-center gap-3">
            <div class="p-3 bg-amber-50 text-amber-600 rounded-lg"><i data-lucide="alert-circle" class="w-6 h-6"></i></div>
            <div>
              <p class="text-xs font-semibold text-slate-500">Pendentes</p>
              <h3 class="text-xl font-bold text-amber-600" id="kpiPendentes">0</h3>
            </div>
          </div>

          <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm flex items-center gap-3">
            <div class="p-3 bg-red-50 text-red-600 rounded-lg"><i data-lucide="alert-octagon" class="w-6 h-6"></i></div>
            <div>
              <p class="text-xs font-semibold text-slate-500">Problem Solving</p>
              <h3 class="text-xl font-bold text-red-600" id="kpiPS">0</h3>
            </div>
          </div>

          <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm flex items-center gap-3">
            <div class="p-3 bg-indigo-50 text-indigo-600 rounded-lg"><i data-lucide="truck" class="w-6 h-6"></i></div>
            <div>
              <p class="text-xs font-semibold text-slate-500">Rotas</p>
              <h3 class="text-xl font-bold text-slate-900" id="kpiRotas">0</h3>
            </div>
          </div>

          <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm flex items-center gap-3">
            <div class="p-3 bg-emerald-50 text-emerald-600 rounded-lg"><i data-lucide="check-circle" class="w-6 h-6"></i></div>
            <div>
              <p class="text-xs font-semibold text-slate-500">At Station / Concluídos</p>
              <h3 class="text-xl font-bold text-emerald-600" id="kpiConcluidos">0</h3>
            </div>
          </div>
        </div>

        <!-- FILTROS MÚLTIPLOS DINÂMICOS -->
        <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm space-y-3">
          <div class="flex items-center gap-2 text-xs font-semibold text-slate-600">
            <i data-lucide="filter" class="w-4 h-4"></i> Filtros
          </div>

          <div class="grid grid-cols-5 gap-3" id="filterContainer">
            <select id="filterCidade" onchange="aplicarFiltros()" class="border border-slate-200 rounded-lg p-2 text-xs text-slate-600 bg-slate-50"><option value="">Cidade: Todas</option></select>
            <select id="filterBairro" onchange="aplicarFiltros()" class="border border-slate-200 rounded-lg p-2 text-xs text-slate-600 bg-slate-50"><option value="">Bairro: Todos</option></select>
            <select id="filterCluster" onchange="aplicarFiltros()" class="border border-slate-200 rounded-lg p-2 text-xs text-slate-600 bg-slate-50"><option value="">Cluster: Todos</option></select>
            <select id="filterStatus" onchange="aplicarFiltros()" class="border border-slate-200 rounded-lg p-2 text-xs text-slate-600 bg-slate-50"><option value="">Status: Todos</option></select>
            <select id="filterRota" onchange="aplicarFiltros()" class="border border-slate-200 rounded-lg p-2 text-xs text-slate-600 bg-slate-50"><option value="">Rota: Todas</option></select>
          </div>
          <div class="flex justify-end">
            <button onclick="limparFiltros()" class="flex items-center gap-2 border border-slate-300 text-slate-700 rounded-lg px-3 py-1.5 text-xs font-medium hover:bg-slate-50 transition">
              <i data-lucide="rotate-ccw" class="w-3.5 h-3.5"></i> Limpar filtros
            </button>
          </div>
        </div>

        <!-- GRÁFICOS OPERACIONAIS -->
        <div class="grid grid-cols-3 gap-4">
          <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm">
            <h4 class="text-xs font-bold text-slate-700 mb-3">Pacotes por Cluster</h4>
            <div class="h-44"><canvas id="barClusterChart"></canvas></div>
          </div>

          <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm">
            <h4 class="text-xs font-bold text-slate-700 mb-1">Status dos Pacotes</h4>
            <div class="h-44 relative"><canvas id="donutStatusChart"></canvas></div>
          </div>

          <div class="bg-white p-4 rounded-xl border border-slate-200 shadow-sm">
            <h4 class="text-xs font-bold text-slate-700 mb-3">Distribuição por Rota</h4>
            <div class="h-44"><canvas id="linePromessaChart"></canvas></div>
          </div>
        </div>

        <!-- TABELA DE PACOTES PARA REATRIBUIÇÃO -->
        <div class="bg-white rounded-xl border border-slate-200 shadow-sm overflow-hidden">
          <div class="p-4 border-b border-slate-100 flex items-center justify-between">
            <div class="flex items-center gap-3">
              <h3 class="text-sm font-bold text-slate-800 flex items-center gap-2">
                <i data-lucide="boxes" class="w-4 h-4 text-blue-600"></i> Pacotes em Exibição
              </h3>
              <span class="bg-blue-100 text-blue-700 text-xs font-semibold px-2.5 py-0.5 rounded-full" id="countRegistros">0 registros</span>
            </div>
          </div>

          <div class="overflow-x-auto">
            <table class="w-full text-left text-xs border-collapse">
              <thead class="bg-slate-50 text-slate-500 border-b border-slate-200">
                <tr>
                  <th class="p-3"><input type="checkbox" class="rounded"></th>
                  <th class="p-3">ID Pacote</th>
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
              <tbody class="divide-y divide-slate-100 text-slate-700 font-medium" id="tabelaCorpo"></tbody>
            </table>
          </div>
        </div>

      </main>

      <!-- SECÇÕES COMPLEMENTARES (MENU SECUNDÁRIO) -->
      <main id="screen-consultar" class="view-screen hidden flex-1 p-6 overflow-y-auto space-y-4">
        <h2 class="text-lg font-bold text-slate-800">Consulta Avançada de ID</h2>
        <div class="bg-white p-4 rounded-xl border border-slate-200">
          <input type="text" id="consultarIdInput" placeholder="Informe o ID do Pacote..." class="border p-2 rounded text-sm w-80">
          <button onclick="consultarIdDireto()" class="bg-blue-600 text-white px-4 py-2 rounded text-sm font-semibold">Pesquisar</button>
        </div>
      </main>

      <main id="screen-reatribuicao" class="view-screen hidden flex-1 p-6 overflow-y-auto">
        <h2 class="text-lg font-bold text-slate-800">Módulo de Reatribuição Operacional</h2>
        <p class="text-sm text-slate-500 mt-2">Área dedicada para envio e alteração em lote de rotas e gaiolas.</p>
      </main>

      <main id="screen-problemsolving" class="view-screen hidden flex-1 p-6 overflow-y-auto">
        <h2 class="text-lg font-bold text-slate-800">Tratativa de Problem Solving</h2>
        <p class="text-sm text-slate-500 mt-2">Lista de pacotes retidos ou com falha de triagem.</p>
      </main>

      <main id="screen-performance" class="view-screen hidden flex-1 p-6 overflow-y-auto">
        <h2 class="text-lg font-bold text-slate-800">Métricas de Performance</h2>
        <p class="text-sm text-slate-500 mt-2">Relatório de reatribuições e produtividade por operador.</p>
      </main>

      <main id="screen-historico" class="view-screen hidden flex-1 p-6 overflow-y-auto">
        <h2 class="text-lg font-bold text-slate-800">Histórico de Alterações</h2>
        <p class="text-sm text-slate-500 mt-2">Registo de logs e movimentações.</p>
      </main>

      <main id="screen-configuracoes" class="view-screen hidden flex-1 p-6 overflow-y-auto">
        <h2 class="text-lg font-bold text-slate-800">Configurações do Sistema</h2>
        <p class="text-sm text-slate-500 mt-2">Ajuste de mapeamento de colunas da planilha e preferências.</p>
      </main>

      <!-- SIDEBAR DIREITA (DETALHES DO PACOTE - ABRÍVEL/FECHÁVEL) -->
      <aside id="detailSidebar" class="w-80 bg-white border-l border-slate-200 p-4 flex flex-col justify-between shrink-0 overflow-y-auto space-y-4 absolute right-0 top-0 bottom-0 shadow-lg transform translate-x-full sidebar-detail-transition z-10">
        <div>
          <div class="flex items-center justify-between pb-3 border-b border-slate-100">
            <h3 class="font-bold text-slate-800 text-sm">Detalhes do Pacote</h3>
            <button onclick="fecharSidebarDireita()" class="text-slate-400 hover:text-slate-600 p-1 rounded-lg border hover:bg-slate-50">
              <i data-lucide="x" class="w-4 h-4"></i>
            </button>
          </div>

          <div class="mt-3 flex gap-1">
            <input type="text" id="sideSearchInput" class="w-full border border-slate-300 rounded-lg px-3 py-1.5 text-xs font-semibold text-slate-800">
            <button onclick="buscarPorIdSide()" class="bg-slate-900 text-white p-2 rounded-lg hover:bg-slate-800"><i data-lucide="search" class="w-4 h-4"></i></button>
          </div>

          <div class="mt-3 flex items-center justify-between">
            <span class="bg-amber-100 text-amber-700 text-xs font-bold px-2 py-0.5 rounded" id="detalheStatusBadge">-</span>
            <span class="text-xs font-bold text-slate-700 flex items-center gap-1">
              <div class="w-2 h-2 rounded-full bg-yellow-400"></div> Operação Mercado Livre
            </span>
          </div>

          <h2 class="text-lg font-bold text-slate-900 mt-2" id="detalheIdHeader">ID: -</h2>

          <div class="mt-4 space-y-2 text-xs">
            <p class="font-bold text-slate-700 border-b pb-1">Localização</p>
            <div class="grid grid-cols-2 gap-y-2 text-slate-600">
              <span>Cidade:</span> <strong class="text-slate-800" id="detalheCidade">-</strong>
              <span>Bairro:</span> <strong class="text-slate-800" id="detalheBairro">-</strong>
              <span>Cluster:</span> <strong class="text-slate-800" id="detalheCluster">-</strong>
              <span>CEP:</span> <strong class="text-slate-800" id="detalheCep">-</strong>
            </div>
          </div>

          <div class="mt-4 space-y-2 text-xs">
            <p class="font-bold text-slate-700 border-b pb-1">Operação</p>
            <div class="space-y-1.5 text-slate-600">
              <div class="flex justify-between"><span>Status:</span> <span class="text-amber-600 font-bold" id="detalheStatus">-</span></div>
              <div class="flex justify-between"><span>Promessa:</span> <strong class="text-slate-800" id="detalhePromessa">-</strong></div>
              <div class="flex justify-between"><span>Rota Sugerida:</span> <strong class="text-blue-600" id="detalheRotaAtual">-</strong></div>
              <div class="flex justify-between"><span>Transportadora:</span> <strong class="text-slate-800" id="detalheTransp">-</strong></div>
            </div>
          </div>

          <div class="mt-4 p-3 bg-emerald-50 border border-emerald-200 rounded-xl space-y-2">
            <div class="flex items-center gap-1.5 text-emerald-800 font-bold text-xs">
              <i data-lucide="lightbulb" class="w-4 h-4 text-emerald-600"></i> Sugestão de Reatribuição
            </div>
            <div class="text-xs text-slate-700 space-y-1">
              <p>Gaiola Recomendada: <strong class="text-emerald-800" id="detalheGaiola">G-01</strong></p>
              <p>Rota Recomendada: <strong class="text-emerald-800" id="detalheRotaSugerida">-</strong></p>
            </div>
            
            <button onclick="confirmarReatribuicao()" class="w-full mt-2 py-2 bg-emerald-600 text-white text-xs font-bold rounded-lg hover:bg-emerald-700 transition flex items-center justify-center gap-1.5 shadow-sm">
              <i data-lucide="check-circle-2" class="w-4 h-4"></i> Confirmar Reatribuição
            </button>
          </div>
        </div>
      </aside>

    </div>
  </div>

  <!-- LÓGICA E SCRIPTS DA APLICAÇÃO -->
  <script>
    // Base Inicial Mockada
    const pacotesMockPadrao = [
      { id: "12345678", cidade: "Queimados", bairro: "Centro", cluster: "R6", cep: "26385-000", promessa: "09/09/2026", status: "Pendente", rotaSugerida: "A25_PM1", gaiola: "G-034", transp: "Mercado Livre" },
      { id: "12345679", cidade: "Japeri", bairro: "Vila de Cava", cluster: "6", cep: "26400-110", promessa: "09/09/2026", status: "At Station", rotaSugerida: "A26_PM1", gaiola: "G-012", transp: "Mercado Livre" },
      { id: "12345680", cidade: "Nova Iguaçu", bairro: "Tinguá", cluster: "R10", cep: "26000-000", promessa: "10/09/2026", status: "Problem Solving", rotaSugerida: "A30_AM1", gaiola: "G-089", transp: "DHL" },
      { id: "12345681", cidade: "Queimados", bairro: "Centro", cluster: "10", cep: "26385-100", promessa: "09/09/2026", status: "Pendente", rotaSugerida: "A31_PM1", gaiola: "G-034", transp: "Mercado Livre" },
      { id: "12345682", cidade: "Seropédica", bairro: "Santa Rita", cluster: "R6", cep: "23890-000", promessa: "11/09/2026", status: "Em trânsito", rotaSugerida: "A28_PM1", gaiola: "G-055", transp: "Jadlog" },
      { id: "12345683", cidade: "Itaguaí", bairro: "Jardim América", cluster: "R10", cep: "23810-000", promessa: "12/09/2026", status: "At Station", rotaSugerida: "A32_AM1", gaiola: "G-022", transp: "DHL" }
    ];

    let basePacotes = [...pacotesMockPadrao];
    let pacotesFiltrados = [...pacotesMockPadrao];
    let barChartInstance = null;
    let donutChartInstance = null;
    let lineChartInstance = null;

    // Função de Troca de Ecrãs (Navegação)
    function navegarPara(menu) {
      document.querySelectorAll('.view-screen').forEach(el => el.classList.add('hidden'));
      document.querySelectorAll('#mainNav button').forEach(el => {
        el.classList.remove('bg-blue-600', 'text-white');
        el.classList.add('text-slate-400');
      });

      const activeNav = document.getElementById(`nav-${menu}`);
      const activeScreen = document.getElementById(`screen-${menu}`);

      if (activeNav && activeScreen) {
        activeNav.classList.add('bg-blue-600', 'text-white');
        activeNav.classList.remove('text-slate-400');
        activeScreen.classList.remove('hidden');
      }

      // Atualiza o título do topo conforme a secção
      const titulos = {
        dashboard: "Central de Reatribuição",
        consultar: "Consultar ID",
        reatribuicao: "Módulo de Reatribuição",
        problemsolving: "Problem Solving",
        performance: "Métricas de Performance",
        historico: "Histórico de Registos",
        configuracoes: "Configurações Gerais"
      };
      document.getElementById('headerTitle').innerText = titulos[menu] || "Sistema Operacional";
    }

    // Leitura Dinâmica de Planilhas (CSV / XLSX)
    function carregarPlanilha(event) {
      const file = event.target.files[0];
      if (!file) return;

      const fileExt = file.name.split('.').pop().toLowerCase();

      if (fileExt === 'csv') {
        Papa.parse(file, {
          header: true,
          skipEmptyLines: true,
          complete: function(results) { processarDadosImportados(results.data); }
        });
      } else if (fileExt === 'xlsx' || fileExt === 'xls') {
        const reader = new FileReader();
        reader.onload = function(e) {
          const data = new Uint8Array(e.target.result);
          const workbook = XLSX.read(data, { type: 'array' });
          const firstSheet = workbook.SheetNames[0];
          const excelData = XLSX.utils.sheet_to_json(workbook.Sheets[firstSheet]);
          processarDadosImportados(excelData);
        };
        reader.readAsArrayBuffer(file);
      }
    }

    function processarDadosImportados(data) {
      if (!data || data.length === 0) return alert("A planilha está vazia ou é inválida.");

      basePacotes = data.map((row, index) => ({
        id: String(row.ID || row.id || row.Pacote || `ID-${index + 1}`),
        cidade: row.Cidade || row.cidade || "N/A",
        bairro: row.Bairro || row.bairro || "N/A",
        cluster: row.Cluster || row.cluster || "N/A",
        cep: row.CEP || row.cep || "N/A",
        promessa: row.Promessa || row.promessa || "N/A",
        status: row.Status || row.status || "Pendente",
        rotaSugerida: row.Rota || row.rota || row.RotaSugerida || "A00_PM1",
        gaiola: row.Gaiola || row.gaiola || "G-00",
        transp: row.Transportadora || row.transp || "Mercado Livre"
      }));

      popularOpcoesFiltros();
      aplicarFiltros();
      alert(`Planilha importada com sucesso! ${basePacotes.length} registos carregados.`);
    }

    // Povoar Opções dos Dropdowns
    function popularOpcoesFiltros() {
      const extrairUnicos = (chave) => [...new Set(basePacotes.map(item => item[chave]))].filter(Boolean);

      const preencherSelect = (idSelect, lista, label) => {
        const select = document.getElementById(idSelect);
        select.innerHTML = `<option value="">${label}: Todos</option>`;
        lista.forEach(val => select.innerHTML += `<option value="${val}">${val}</option>`);
      };

      preencherSelect('filterCidade', extrairUnicos('cidade'), 'Cidade');
      preencherSelect('filterBairro', extrairUnicos('bairro'), 'Bairro');
      preencherSelect('filterCluster', extrairUnicos('cluster'), 'Cluster');
      preencherSelect('filterStatus', extrairUnicos('status'), 'Status');
      preencherSelect('filterRota', extrairUnicos('rotaSugerida'), 'Rota');
    }

    // Filtragem Geral
    function aplicarFiltros() {
      const termo = document.getElementById('searchInput').value.toLowerCase();
      const cidade = document.getElementById('filterCidade').value;
      const bairro = document.getElementById('filterBairro').value;
      const cluster = document.getElementById('filterCluster').value;
      const status = document.getElementById('filterStatus').value;
      const rota = document.getElementById('filterRota').value;

      pacotesFiltrados = basePacotes.filter(p => {
        const matchesBusca = p.id.toLowerCase().includes(termo) ||
                             p.cidade.toLowerCase().includes(termo) ||
                             p.bairro.toLowerCase().includes(termo) ||
                             p.rotaSugerida.toLowerCase().includes(termo);
        const matchesCidade = !cidade || p.cidade === cidade;
        const matchesBairro = !bairro || p.bairro === bairro;
        const matchesCluster = !cluster || p.cluster === cluster;
        const matchesStatus = !status || p.status === status;
        const matchesRota = !rota || p.rotaSugerida === rota;

        return matchesBusca && matchesCidade && matchesBairro && matchesCluster && matchesStatus && matchesRota;
      });

      renderTabela(pacotesFiltrados);
      atualizarKPIs(pacotesFiltrados);
      atualizarGraficos(pacotesFiltrados);
    }

    function limparFiltros() {
      document.getElementById('searchInput').value = '';
      document.querySelectorAll('#filterContainer select').forEach(s => s.value = '');
      aplicarFiltros();
    }

    // Atualização da Tabela com Clique nos IDs e Rotas
    function renderTabela(lista) {
      const corpo = document.getElementById('tabelaCorpo');
      corpo.innerHTML = '';

      document.getElementById('countRegistros').innerText = `${lista.length} registros`;

      lista.forEach(item => {
        let statusBadge = 'bg-slate-100 text-slate-700';
        if (item.status === 'Pendente') statusBadge = 'bg-amber-100 text-amber-700';
        else if (item.status === 'At Station') statusBadge = 'bg-cyan-100 text-cyan-700';
        else if (item.status === 'Problem Solving') statusBadge = 'bg-red-100 text-red-700';

        const tr = document.createElement('tr');
        tr.className = 'hover:bg-slate-50 transition cursor-pointer';

        tr.innerHTML = `
          <td class="p-3" onclick="event.stopPropagation()"><input type="checkbox" class="rounded"></td>
          <td class="p-3 font-bold text-blue-600 hover:underline" onclick="abrirSidebarDireita('${item.id}')">${item.id}</td>
          <td class="p-3">${item.cidade}</td>
          <td class="p-3">${item.bairro}</td>
          <td class="p-3">${item.cluster}</td>
          <td class="p-3">${item.promessa}</td>
          <td class="p-3"><span class="${statusBadge} px-2 py-0.5 rounded font-semibold text-[11px]">${item.status}</span></td>
          <td class="p-3 font-semibold text-blue-600 hover:underline" onclick="abrirSidebarDireita('${item.id}')">${item.rotaSugerida}</td>
          <td class="p-3">${item.transp}</td>
          <td class="p-3 text-center flex justify-center gap-2" onclick="event.stopPropagation()">
            <button onclick="abrirSidebarDireita('${item.id}')" class="bg-blue-600 text-white px-2 py-1 rounded hover:bg-blue-700 font-semibold text-[10px]">Ver</button>
          </td>
        `;
        corpo.appendChild(tr);
      });
      lucide.createIcons();
    }

    // Contadores KPIs
    function atualizarKPIs(lista) {
      document.getElementById('kpiTotal').innerText = lista.length;
      document.getElementById('kpiPendentes').innerText = lista.filter(p => p.status === 'Pendente').length;
      document.getElementById('kpiPS').innerText = lista.filter(p => p.status === 'Problem Solving').length;
      document.getElementById('kpiRotas').innerText = [...new Set(lista.map(p => p.rotaSugerida))].length;
      document.getElementById('kpiConcluidos').innerText = lista.filter(p => p.status === 'At Station' || p.status === 'Concluído').length;
    }

    // Sidebar Direita (Abrir / Fechar)
    function abrirSidebarDireita(id) {
      const item = basePacotes.find(p => p.id === id);
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

      document.getElementById('detailSidebar').classList.remove('translate-x-full');
    }

    function fecharSidebarDireita() {
      document.getElementById('detailSidebar').classList.add('translate-x-full');
    }

    function buscarPorIdSide() {
      const id = document.getElementById('sideSearchInput').value;
      abrirSidebarDireita(id);
    }

    function consultarIdDireto() {
      const id = document.getElementById('consultarIdInput').value;
      navegarPara('dashboard');
      abrirSidebarDireita(id);
    }

    function confirmarReatribuicao() {
      alert("Reatribuição realizada e registada no histórico!");
      fecharSidebarDireita();
    }

    function resetarDados() {
      basePacotes = [...pacotesMockPadrao];
      popularOpcoesFiltros();
      aplicarFiltros();
    }

    // Gestão de Gráficos Reativos
    function atualizarGraficos(lista) {
      // 1. Cluster
      const clusters = {};
      lista.forEach(p => clusters[p.cluster] = (clusters[p.cluster] || 0) + 1);

      if (barChartInstance) barChartInstance.destroy();
      barChartInstance = new Chart(document.getElementById('barClusterChart'), {
        type: 'bar',
        data: {
          labels: Object.keys(clusters),
          datasets: [{ data: Object.values(clusters), backgroundColor: '#3b82f6', borderRadius: 4 }]
        },
        options: { indexAxis: 'y', responsive: true, maintainAspectRatio: false, plugins: { legend: { display: false } } }
      });

      // 2. Status
      const statusMap = {};
      lista.forEach(p => statusMap[p.status] = (statusMap[p.status] || 0) + 1);

      if (donutChartInstance) donutChartInstance.destroy();
      donutChartInstance = new Chart(document.getElementById('donutStatusChart'), {
        type: 'doughnut',
        data: {
          labels: Object.keys(statusMap),
          datasets: [{ data: Object.values(statusMap), backgroundColor: ['#f59e0b', '#10b981', '#ef4444', '#0284c7'] }]
        },
        options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { position: 'right', labels: { boxWidth: 10, font: { size: 10 } } } }, cutout: '70%' }
      });

      // 3. Rotas
      const rotasMap = {};
      lista.forEach(p => rotasMap[p.rotaSugerida] = (rotasMap[p.rotaSugerida] || 0) + 1);

      if (lineChartInstance) lineChartInstance.destroy();
      lineChartInstance = new Chart(document.getElementById('linePromessaChart'), {
        type: 'bar',
        data: {
          labels: Object.keys(rotasMap),
          datasets: [{ data: Object.values(rotasMap), backgroundColor: '#6366f1', borderRadius: 4 }]
        },
        options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { display: false } } }
      });
    }

    // Inicialização
    window.onload = () => {
      popularOpcoesFiltros();
      aplicarFiltros();
    };
  </script>
</body>
</html>
