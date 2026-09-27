<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Central de Reatribuição & Automação Pós-Sorting</title>
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

  <!-- ================= SIDEBAR ESQUERDA ================= -->
  <aside class="w-64 bg-slate-900 text-white flex flex-col justify-between shrink-0 z-20">
    <div>
      <div class="p-4 border-b border-slate-800 flex items-center justify-between">
        <div class="bg-yellow-400 text-slate-900 px-2 py-1 rounded font-bold text-xs">Mercado Livre</div>
        <span class="text-xs text-slate-400 font-semibold tracking-wider">KUEHNE+NAGEL</span>
      </div>

      <nav class="mt-4 px-2 space-y-1" id="mainNav">
        <div class="text-[10px] text-slate-500 font-bold uppercase tracking-wider px-3 pb-1 pt-2">Operação Pós-Sorting</div>
        <button onclick="navegarPara('bipagem')" id="nav-bipagem" class="w-full flex items-center gap-3 px-3 py-2.5 text-slate-400 hover:bg-slate-800 hover:text-white rounded-lg text-sm font-medium transition">
          <i data-lucide="scan-barcode" class="w-5 h-5"></i> Bipagem Inteligente
        </button>
        <button onclick="navegarPara('resumorotas')" id="nav-resumorotas" class="w-full flex items-center gap-3 px-3 py-2.5 text-slate-400 hover:bg-slate-800 hover:text-white rounded-lg text-sm font-medium transition">
          <i data-lucide="truck" class="w-5 h-5"></i> Resumo por Rota
        </button>
        
        <div class="text-[10px] text-slate-500 font-bold uppercase tracking-wider px-3 pb-1 pt-4">Gestão Operacional</div>
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
      </nav>
    </div>

    <div class="p-4 border-t border-slate-800 text-xs text-slate-400 space-y-1">
      <p class="font-bold text-slate-300">Automação Pós-Sorting</p>
      <p>Logistics Systems Integrado</p>
    </div>
  </aside>

  <!-- ================= ÁREA CENTRAL DE CONTEÚDO ================= -->
  <div class="flex-1 flex flex-col min-w-0 overflow-hidden">

    <!-- HEADER SUPERIOR -->
    <header class="bg-white border-b border-slate-200 px-6 py-3 flex items-center justify-between shrink-0">
      <div>
        <h1 class="text-xl font-bold text-slate-900" id="headerTitle">Central de Reatribuição</h1>
        <p class="text-xs text-slate-500" id="headerSub">Gestão operacional de pacotes</p>
      </div>

      <div class="flex items-center gap-4 text-xs text-slate-500">
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

    <div class="flex-1 flex overflow-hidden relative">

      <!-- ================= NOVA ABA: BIPAGEM INTELIGENTE ================= -->
      <main id="screen-bipagem" class="view-screen hidden flex-1 p-6 overflow-y-auto space-y-6 bg-slate-50">
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
            <div class="space-y-6">
                <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200 space-y-5">
                    <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                        <div class="flex items-center space-x-2">
                            <h2 class="text-xs font-bold text-slate-900 uppercase tracking-wider">Leitor Óptico</h2>
                        </div>
                        <span id="badge-ciclo" class="text-[10px] bg-slate-900 text-white px-2.5 py-1 rounded font-mono font-bold shadow-sm">CICLO AM</span>
                    </div>

                    <div id="feedbackAlerta" class="hidden p-3 rounded-lg text-xs font-medium border transition-all shadow-sm"></div>

                    <div class="space-y-4">
                        <div>
                            <label class="text-xs font-semibold text-slate-600 uppercase tracking-wide">Código de Barras</label>
                            <input type="text" id="barcodeInput" autofocus placeholder="Aguardando leitura..." class="w-full p-3 border border-slate-300 rounded-lg font-mono text-sm focus:ring-2 focus:ring-blue-600 focus:border-blue-600 focus:outline-none bg-slate-50 mt-1">
                            <span class="text-[11px] text-slate-400 mt-1.5 block leading-tight">⚡ 1º Bipe: Em Rota | 2º Bipe: Entregue</span>
                        </div>

                        <div class="grid grid-cols-2 gap-3 pt-3 border-t border-slate-100">
                            <div>
                                <label class="text-xs font-semibold text-slate-600">Rota / Gaiola:</label>
                                <input type="text" id="atribuicaoInput" placeholder="Ex: Gaiola 01" class="w-full p-2.5 border border-slate-300 rounded-lg text-xs mt-1 focus:outline-none focus:border-blue-600 bg-slate-50">
                            </div>
                            <div>
                                <label class="text-xs font-semibold text-slate-600">Ciclo Ativo:</label>
                                <select id="selectCiclo" onchange="atualizarCicloBadge()" class="w-full p-2.5 border border-slate-300 rounded-lg text-xs mt-1 bg-white focus:outline-none focus:border-blue-600 font-bold text-slate-900">
                                    <option value="AM">AM</option>
                                    <option value="PM">PM</option>
                                </select>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="bg-white p-6 rounded-xl shadow-sm border border-amber-200 space-y-4 bg-amber-50/20">
                    <div class="flex justify-between items-center border-b border-amber-100 pb-3">
                        <div class="flex items-center space-x-2">
                            <h2 class="text-xs font-bold text-amber-900 uppercase tracking-wider">Reconciliar Mercado Livre</h2>
                            <span class="bg-amber-500 text-white text-[9px] px-1.5 py-0.5 rounded font-bold uppercase">Auto Status</span>
                        </div>
                        <i data-lucide="shopping-bag" class="w-4 h-4 text-amber-600"></i>
                    </div>
                    <div>
                        <textarea id="mlTextInput" rows="3" placeholder="Cole aqui as linhas/tabela copiadas..." class="w-full p-3 border border-amber-300 rounded-lg font-mono text-xs mt-1 focus:ring-2 focus:ring-amber-500 focus:outline-none bg-white resize-none"></textarea>
                    </div>
                    <button onclick="processarPrintMercadoLivre()" class="w-full bg-amber-600 hover:bg-amber-700 text-white p-2.5 rounded-lg text-xs font-bold transition shadow-sm flex items-center justify-center space-x-2">
                        <i data-lucide="refresh-cw" class="w-4 h-4"></i>
                        <span>Reconciliar Status</span>
                    </button>
                </div>

                <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200 space-y-4">
                    <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                        <h2 class="text-xs font-bold text-slate-900 uppercase tracking-wider">Marcador em Massa (Entregue)</h2>
                        <i data-lucide="layers" class="w-4 h-4 text-slate-900"></i>
                    </div>
                    <div>
                        <textarea id="bulkInput" rows="2" placeholder="Cole vários IDs aqui..." class="w-full p-3 border border-slate-300 rounded-lg font-mono text-xs mt-1 focus:ring-2 focus:ring-blue-600 focus:outline-none bg-slate-50 resize-none"></textarea>
                    </div>
                    <button onclick="processarMassaEntregue()" class="w-full bg-slate-800 hover:bg-slate-900 text-white p-2.5 rounded-lg text-xs font-bold transition shadow-sm flex items-center justify-center space-x-2">
                        <i data-lucide="check-check" class="w-4 h-4"></i>
                        <span>Marcar Entregue em Massa</span>
                    </button>
                </div>
            </div>

            <!-- Tabela de Histórico da Bipagem -->
            <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200 lg:col-span-2 space-y-4">
                <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                    <div class="flex items-center space-x-3">
                        <h2 class="text-xs font-bold text-slate-900 uppercase tracking-wider">Histórico de Bipagem</h2>
                        <button onclick="copiarTodosIDs()" class="px-2.5 py-1 bg-blue-50 hover:bg-blue-600 hover:text-white text-blue-700 rounded text-xs font-semibold flex items-center space-x-1.5 transition">
                            <i data-lucide="copy" class="w-3.5 h-3.5"></i>
                            <span>Copiar Todos os IDs</span>
                        </button>
                    </div>
                    <span id="contadorBips" class="text-xs font-semibold bg-slate-100 text-slate-800 px-3 py-1 rounded-full border border-slate-200">0 Pacotes</span>
                </div>

                <div class="grid grid-cols-1 sm:grid-cols-3 gap-3 bg-slate-50 p-3 rounded-lg border border-slate-200">
                    <div>
                        <label class="text-[10px] font-bold text-slate-500 uppercase">Filtrar por ID / Rota</label>
                        <input type="text" id="filtroTexto" onkeyup="renderizarTabelaBipagem()" placeholder="Pesquisar..." class="w-full mt-1 p-2 bg-white border border-slate-300 rounded-md text-xs focus:outline-none focus:border-blue-600">
                    </div>
                    <div>
                        <label class="text-[10px] font-bold text-slate-500 uppercase">Status</label>
                        <select id="filtroStatus" onchange="renderizarTabelaBipagem()" class="w-full mt-1 p-2 bg-white border border-slate-300 rounded-md text-xs focus:outline-none focus:border-blue-600 font-medium">
                            <option value="">Todos os Status</option>
                            <option value="DESPACHAR">Despachar</option>
                            <option value="EM_ROTA_DE_ENTREGA">Em Rota de Entrega</option>
                            <option value="ENTREGUE">Entregue</option>
                            <option value="FALHA_NA_ENTREGA">Falha na Entrega</option>
                            <option value="SOLUCAO_DE_PROBLEMA">Solução de Problema</option>
                        </select>
                    </div>
                    <div>
                        <label class="text-[10px] font-bold text-slate-500 uppercase">Ciclo</label>
                        <select id="filtroCiclo" onchange="renderizarTabelaBipagem()" class="w-full mt-1 p-2 bg-white border border-slate-300 rounded-md text-xs focus:outline-none focus:border-blue-600 font-medium">
                            <option value="">Todos os Ciclos</option>
                            <option value="AM">Ciclo AM</option>
                            <option value="PM">Ciclo PM</option>
                        </select>
                    </div>
                </div>

                <div class="overflow-x-auto max-h-[500px]">
                    <table class="w-full text-left text-xs border-collapse">
                        <thead class="bg-slate-100 text-slate-600 font-bold uppercase border-b border-slate-200 sticky top-0">
                            <tr>
                                <th class="p-3">Pacote / ID</th>
                                <th class="p-3">Rota / Gaiola</th>
                                <th class="p-3">Ciclo</th>
                                <th class="p-3">Status</th>
                                <th class="p-3">Hora</th>
                                <th class="p-3 text-right">Ações</th>
                            </tr>
                        </thead>
                        <tbody id="tabelaHistoricoBipagem" class="divide-y divide-slate-100 font-mono">
                            <!-- Preenchido via JS -->
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
      </main>

      <!-- ================= NOVA ABA: RESUMO POR ROTA ================= -->
      <main id="screen-resumorotas" class="view-screen hidden flex-1 p-6 overflow-y-auto space-y-4 bg-slate-50">
        <div class="bg-white p-6 rounded-xl shadow-sm border border-slate-200">
            <div class="flex justify-between items-center border-b pb-3 mb-4">
                <h2 class="text-sm font-bold text-slate-900 uppercase tracking-wider">Resumo Agrupado por Rota (Bipagem)</h2>
                <span class="text-xs text-slate-400">Clique na rota para detalhes ou descarregar CSV</span>
            </div>
            <div class="overflow-x-auto">
                <table class="w-full text-left text-xs border-collapse">
                    <thead class="bg-slate-100 text-slate-600 font-bold uppercase border-b border-slate-200">
                        <tr>
                            <th class="p-3">Rota / Gaiola</th>
                            <th class="p-3">Total Pacotes</th>
                            <th class="p-3">Em Rota</th>
                            <th class="p-3">Entregue</th>
                            <th class="p-3">Despachar</th>
                            <th class="p-3">Falha</th>
                            <th class="p-3 text-right">Ações</th>
                        </tr>
                    </thead>
                    <tbody id="tabelaResumoRotasBipagem" class="divide-y divide-slate-100 font-mono">
                        <!-- Gerado dinamicamente -->
                    </tbody>
                </table>
            </div>
        </div>
      </main>

      <!-- ================= ABAS ORIGINAIS (Dashboard e outras) ================= -->
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

      <main id="screen-consultar" class="view-screen hidden flex-1 p-6 overflow-y-auto space-y-4">
        <h2 class="text-lg font-bold text-slate-800">Consulta Avançada de ID</h2>
        <div class="bg-white p-4 rounded-xl border border-slate-200">
          <input type="text" id="consultarIdInput" placeholder="Informe o ID do Pacote..." class="border p-2 rounded text-sm w-80">
          <button onclick="consultarIdDireto()" class="bg-blue-600 text-white px-4 py-2 rounded text-sm font-semibold">Pesquisar</button>
        </div>
      </main>
      <main id="screen-reatribuicao" class="view-screen hidden flex-1 p-6 overflow-y-auto">
        <h2 class="text-lg font-bold text-slate-800">Módulo de Reatribuição Operacional</h2>
      </main>
      <main id="screen-problemsolving" class="view-screen hidden flex-1 p-6 overflow-y-auto">
        <h2 class="text-lg font-bold text-slate-800">Tratativa de Problem Solving</h2>
      </main>
      <main id="screen-performance" class="view-screen hidden flex-1 p-6 overflow-y-auto">
        <h2 class="text-lg font-bold text-slate-800">Métricas de Performance</h2>
      </main>
      <main id="screen-historico" class="view-screen hidden flex-1 p-6 overflow-y-auto">
        <h2 class="text-lg font-bold text-slate-800">Histórico de Alterações</h2>
      </main>
      
      <!-- SIDEBAR DIREITA (Detalhes Dashboard Original) -->
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

  <!-- ================= MODAIS DA BIPAGEM INTELIGENTE ================= -->
  <!-- Modal Detalhes Rota -->
  <div id="modalRota" class="fixed inset-0 bg-slate-900/50 backdrop-blur-sm hidden items-center justify-center z-50 p-4">
      <div class="bg-white rounded-xl shadow-2xl max-w-2xl w-full p-6 space-y-4">
          <div class="flex justify-between items-center border-b pb-3">
              <div class="flex items-center space-x-2">
                  <i data-lucide="truck" class="w-5 h-5 text-slate-900"></i>
                  <h3 id="modalRotaTitulo" class="text-sm font-bold text-slate-900 uppercase tracking-wider">IDs da Rota</h3>
              </div>
              <button onclick="fecharModalRota()" class="text-slate-400 hover:text-slate-600">
                  <i data-lucide="x" class="w-5 h-5"></i>
              </button>
          </div>
          <div class="flex justify-between items-center bg-slate-50 p-2.5 rounded-lg border border-slate-200 text-xs">
              <span id="modalRotaContador" class="font-bold text-slate-700">0 Pacotes encontrados</span>
              <button onclick="copiarIDsModalRota()" class="bg-slate-900 hover:bg-slate-800 text-white px-3 py-1.5 rounded font-semibold flex items-center space-x-1.5 transition">
                  <i data-lucide="copy" class="w-3.5 h-3.5"></i>
                  <span>Copiar Lista de IDs</span>
              </button>
          </div>
          <div class="max-h-80 overflow-y-auto border border-slate-200 rounded-lg">
              <table class="w-full text-left text-xs font-mono">
                  <thead class="bg-slate-100 text-slate-600 uppercase border-b sticky top-0">
                      <tr>
                          <th class="p-2.5">ID do Pacote</th>
                          <th class="p-2.5">Ciclo</th>
                          <th class="p-2.5">Status</th>
                          <th class="p-2.5">Hora</th>
                      </tr>
                  </thead>
                  <tbody id="modalRotaTabela" class="divide-y divide-slate-100"></tbody>
              </table>
          </div>
          <div class="flex justify-end pt-2">
              <button onclick="fecharModalRota()" class="px-4 py-2 bg-slate-100 text-slate-600 hover:bg-slate-200 rounded-lg text-xs font-semibold transition">Fechar</button>
          </div>
      </div>
  </div>

  <!-- Modal Edição Manual (Bipagem) -->
  <div id="modalEditar" class="fixed inset-0 bg-slate-900/50 backdrop-blur-sm hidden items-center justify-center z-50 p-4">
      <div class="bg-white rounded-xl shadow-2xl max-w-md w-full p-6 space-y-4">
          <div class="flex justify-between items-center border-b pb-3">
              <div class="flex items-center space-x-2">
                  <i data-lucide="edit-3" class="w-4 h-4 text-slate-900"></i>
                  <h3 class="text-xs font-bold text-slate-900 uppercase tracking-wider">Editar Pacote Manualmente</h3>
              </div>
              <button onclick="fecharModalEditar()" class="text-slate-400 hover:text-slate-600">
                  <i data-lucide="x" class="w-5 h-5"></i>
              </button>
          </div>
          <input type="hidden" id="editIndex">
          <div>
              <label class="text-[10px] font-bold text-slate-500 uppercase">ID do Pacote</label>
              <input type="text" id="editId" readonly class="w-full p-2.5 bg-slate-100 border border-slate-200 rounded-lg text-xs font-mono font-bold text-slate-500 mt-1 cursor-not-allowed">
          </div>
          <div>
              <label class="text-[10px] font-bold text-slate-500 uppercase">Rota / Gaiola Manual</label>
              <input type="text" id="editRota" placeholder="Ex: Gaiola 05 / Rota X" class="w-full p-2.5 border border-slate-300 rounded-lg text-xs mt-1 focus:ring-2 focus:ring-blue-600 focus:outline-none">
          </div>
          <div class="grid grid-cols-2 gap-3">
              <div>
                  <label class="text-[10px] font-bold text-slate-500 uppercase">Ciclo Manual</label>
                  <select id="editCiclo" class="w-full p-2.5 border border-slate-300 rounded-lg text-xs mt-1 bg-white font-bold text-slate-900 focus:ring-2 focus:ring-blue-600 focus:outline-none">
                      <option value="AM">AM</option>
                      <option value="PM">PM</option>
                  </select>
              </div>
              <div>
                  <label class="text-[10px] font-bold text-slate-500 uppercase">Status Manual</label>
                  <select id="editStatus" class="w-full p-2.5 border border-slate-300 rounded-lg text-xs mt-1 bg-white font-semibold text-slate-700 focus:ring-2 focus:ring-blue-600 focus:outline-none">
                      <option value="DESPACHAR">DESPACHAR</option>
                      <option value="EM_ROTA_DE_ENTREGA">EM ROTA DE ENTREGA</option>
                      <option value="ENTREGUE">ENTREGUE</option>
                      <option value="FALHA_NA_ENTREGA">FALHA NA ENTREGA</option>
                      <option value="SOLUCAO_DE_PROBLEMA">SOLUÇÃO DE PROBLEMA</option>
                      <option value="NULO">NULO</option>
                  </select>
              </div>
          </div>
          <div class="flex justify-end space-x-2 pt-3 border-t">
              <button onclick="fecharModalEditar()" class="px-4 py-2 bg-slate-100 text-slate-600 hover:bg-slate-200 rounded-lg text-xs font-semibold transition">Cancelar</button>
              <button onclick="salvarEdicaoManual()" class="px-4 py-2 bg-slate-900 text-white hover:bg-slate-800 rounded-lg text-xs font-bold transition shadow-sm flex items-center space-x-1.5">
                  <i data-lucide="check" class="w-4 h-4"></i>
                  <span>Salvar Alterações</span>
              </button>
          </div>
      </div>
  </div>

  <!-- ================= LÓGICA E SCRIPTS DA APLICAÇÃO ================= -->
  <script>
    // --- ESTADO: Dashboard (Base Original) ---
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

    // --- ESTADO: Bipagem Inteligente (Novo Módulo) ---
    let pacotesBipagem = JSON.parse(localStorage.getItem('kn_pacotes')) || [];
    let rotaSelecionadaIDs = [];

    // --- FUNÇÕES DE NAVEGAÇÃO ---
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

      const titulos = {
        bipagem: "Bipagem Inteligente",
        resumorotas: "Resumo Agrupado por Rota",
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

    // ================= FUNÇÕES DO MÓDULO DE BIPAGEM =================
    
    function atualizarCicloBadge() {
        const ciclo = document.getElementById('selectCiclo').value;
        const badge = document.getElementById('badge-ciclo');
        badge.innerText = `CICLO ${ciclo}`;
        badge.className = `text-[10px] ${ciclo === 'AM' ? 'bg-amber-500' : 'bg-indigo-600'} text-white px-2.5 py-1 rounded font-mono font-bold shadow-sm`;
    }

    function processarBip(codigo) {
        if (!codigo) return;
        const ciclo = document.getElementById('selectCiclo').value;
        const rota = document.getElementById('atribuicaoInput').value.trim() || 'Sem Rota';
        const index = pacotesBipagem.findIndex(p => p.id === codigo);
        const agora = new Date().toLocaleTimeString('pt-BR', { hour: '2-digit', minute: '2-digit', second: '2-digit' });

        if (index === -1) {
            pacotesBipagem.unshift({ id: codigo, rota: rota, ciclo: ciclo, status: 'EM_ROTA_DE_ENTREGA', hora: agora, bips: 1 });
            exibirAlerta(`Pacote ${codigo} adicionado: EM ROTA`, 'sucesso');
        } else {
            pacotesBipagem[index].status = 'ENTREGUE';
            pacotesBipagem[index].bips += 1;
            pacotesBipagem[index].hora = agora;
            if(rota !== 'Sem Rota') pacotesBipagem[index].rota = rota;
            exibirAlerta(`Pacote ${codigo} atualizado: ENTREGUE`, 'sucesso');
        }
        salvarEAtualizarBipagem();
    }

    function processarPrintMercadoLivre() {
        const texto = document.getElementById('mlTextInput').value;
        if (!texto.trim()) return;
        const linhas = texto.split('\n');
        let atualizados = 0;

        linhas.forEach(linha => {
            const match = linha.match(/(MLB\d+|\d{10,})/i);
            if (match) {
                const id = match[0].toUpperCase();
                let status = 'DESPACHAR';
                if (linha.toLowerCase().includes('rota') || linha.toLowerCase().includes('caminho')) status = 'EM_ROTA_DE_ENTREGA';
                else if (linha.toLowerCase().includes('entregue') || linha.toLowerCase().includes('sucesso')) status = 'ENTREGUE';
                else if (linha.toLowerCase().includes('falha') || linha.toLowerCase().includes('cancelado')) status = 'FALHA_NA_ENTREGA';

                const idx = pacotesBipagem.findIndex(p => p.id === id);
                const cicloAtual = document.getElementById('selectCiclo').value;
                const rotaAtual = document.getElementById('atribuicaoInput').value.trim() || 'ML Import';

                if (idx !== -1) pacotesBipagem[idx].status = status;
                else pacotesBipagem.unshift({ id: id, rota: rotaAtual, ciclo: cicloAtual, status: status, hora: new Date().toLocaleTimeString('pt-BR', { hour: '2-digit', minute: '2-digit' }), bips: 1 });
                atualizados++;
            }
        });
        document.getElementById('mlTextInput').value = '';
        exibirAlerta(`${atualizados} pacotes reconciliados!`, 'sucesso');
        salvarEAtualizarBipagem();
    }

    function processarMassaEntregue() {
        const idsText = document.getElementById('bulkInput').value;
        if (!idsText.trim()) return;
        const ids = idsText.split('\n').map(id => id.trim()).filter(id => id !== '');
        const ciclo = document.getElementById('selectCiclo').value;
        const rota = document.getElementById('atribuicaoInput').value.trim() || 'Entregue';
        const agora = new Date().toLocaleTimeString('pt-BR', { hour: '2-digit', minute: '2-digit' });
        let atualizados = 0;

        ids.forEach(id => {
            const idx = pacotesBipagem.findIndex(p => p.id === id);
            if (idx !== -1) {
                pacotesBipagem[idx].status = 'ENTREGUE';
                pacotesBipagem[idx].hora = agora;
            } else pacotesBipagem.unshift({ id: id, rota: rota, ciclo: ciclo, status: 'ENTREGUE', hora: agora, bips: 1 });
            atualizados++;
        });
        document.getElementById('bulkInput').value = '';
        exibirAlerta(`${atualizados} IDs marcados como Entregue!`, 'sucesso');
        salvarEAtualizarBipagem();
    }

    function exibirAlerta(msg, tipo) {
        const alerta = document.getElementById('feedbackAlerta');
        alerta.innerText = msg;
        alerta.className = 'p-3 rounded-lg text-xs font-medium border transition-all shadow-sm';
        if (tipo === 'sucesso') alerta.classList.add('bg-emerald-100', 'text-emerald-700', 'border-emerald-200');
        else alerta.classList.add('bg-amber-100', 'text-amber-700', 'border-amber-200');
        alerta.classList.remove('hidden');
        setTimeout(() => alerta.classList.add('hidden'), 3000);
    }

    function salvarEAtualizarBipagem() {
        localStorage.setItem('kn_pacotes', JSON.stringify(pacotesBipagem));
        renderizarTabelaBipagem();
        renderizarResumoRotas();
    }

    function renderizarTabelaBipagem() {
        const filtroTexto = document.getElementById('filtroTexto').value.toLowerCase();
        const filtroStatus = document.getElementById('filtroStatus').value;
        const filtroCiclo = document.getElementById('filtroCiclo').value;
        const tbody = document.getElementById('tabelaHistoricoBipagem');
        tbody.innerHTML = '';

        const filtrados = pacotesBipagem.filter(p => {
            const textoMatch = p.id.toLowerCase().includes(filtroTexto) || p.rota.toLowerCase().includes(filtroTexto);
            const statusMatch = filtroStatus === '' || p.status === filtroStatus;
            const cicloMatch = filtroCiclo === '' || p.ciclo === filtroCiclo;
            return textoMatch && statusMatch && cicloMatch;
        });

        document.getElementById('contadorBips').innerText = `${filtrados.length} Pacotes`;

        filtrados.forEach((p) => {
            const originalIndex = pacotesBipagem.indexOf(p);
            let corStatus = 'bg-slate-100 text-slate-600';
            if (p.status === 'EM_ROTA_DE_ENTREGA') corStatus = 'bg-emerald-100 text-emerald-700';
            else if (p.status === 'ENTREGUE') corStatus = 'bg-green-100 text-green-800 font-bold';
            else if (p.status === 'DESPACHAR') corStatus = 'bg-sky-100 text-sky-700';
            else if (p.status === 'FALHA_NA_ENTREGA') corStatus = 'bg-rose-100 text-rose-700';
            else if (p.status === 'SOLUCAO_DE_PROBLEMA') corStatus = 'bg-purple-100 text-purple-700';
            let corCiclo = p.ciclo === 'AM' ? 'text-amber-500' : 'text-indigo-500';

            tbody.innerHTML += `
                <tr class="hover:bg-slate-50 transition border-b border-slate-100">
                    <td class="p-3 font-bold text-slate-900">${p.id}</td>
                    <td class="p-3">${p.rota}</td>
                    <td class="p-3 font-bold ${corCiclo}">${p.ciclo}</td>
                    <td class="p-3"><span class="px-2 py-1 rounded text-[10px] font-bold tracking-wide ${corStatus}">${p.status.replace(/_/g, ' ')}</span></td>
                    <td class="p-3 text-slate-500">${p.hora}</td>
                    <td class="p-3 text-right">
                        <button onclick="abrirModalEditar(${originalIndex})" class="p-1.5 text-blue-600 hover:bg-blue-50 rounded transition ml-1" title="Editar"><i data-lucide="edit-2" class="w-4 h-4"></i></button>
                        <button onclick="excluirPacote(${originalIndex})" class="p-1.5 text-rose-600 hover:bg-rose-50 rounded transition ml-1" title="Excluir"><i data-lucide="trash" class="w-4 h-4"></i></button>
                    </td>
                </tr>
            `;
        });
        lucide.createIcons();
    }

    function renderizarResumoRotas() {
        const tbody = document.getElementById('tabelaResumoRotasBipagem');
        tbody.innerHTML = '';
        const agrupamento = {};
        pacotesBipagem.forEach(p => {
            if (!agrupamento[p.rota]) agrupamento[p.rota] = { total: 0, emRota: 0, entregue: 0, despachar: 0, falha: 0 };
            agrupamento[p.rota].total++;
            if (p.status === 'EM_ROTA_DE_ENTREGA') agrupamento[p.rota].emRota++;
            if (p.status === 'ENTREGUE') agrupamento[p.rota].entregue++;
            if (p.status === 'DESPACHAR') agrupamento[p.rota].despachar++;
            if (p.status === 'FALHA_NA_ENTREGA') agrupamento[p.rota].falha++;
        });

        const rotasChaves = Object.keys(agrupamento).sort();
        if (rotasChaves.length === 0) {
            tbody.innerHTML = `<tr><td colspan="7" class="p-4 text-center text-slate-400 font-sans">Nenhum pacote registrado nas rotas.</td></tr>`;
            return;
        }

        rotasChaves.forEach(rota => {
            const d = agrupamento[rota];
            tbody.innerHTML += `
                <tr class="hover:bg-slate-50 transition border-b border-slate-100">
                    <td class="p-3 font-bold text-slate-900">
                        <button onclick="verIDsRota('${rota.replace(/'/g, "\\'")}')" class="hover:underline flex items-center space-x-1.5 text-left text-blue-600">
                            <i data-lucide="eye" class="w-3.5 h-3.5"></i>
                            <span>${rota}</span>
                        </button>
                    </td>
                    <td class="p-3 font-semibold">${d.total}</td>
                    <td class="p-3 text-emerald-600 font-semibold">${d.emRota}</td>
                    <td class="p-3 text-green-700 font-semibold">${d.entregue}</td>
                    <td class="p-3 text-sky-600 font-semibold">${d.despachar}</td>
                    <td class="p-3 text-rose-600 font-semibold">${d.falha}</td>
                    <td class="p-3 text-right">
                        <button onclick="exportarCSVRota('${rota.replace(/'/g, "\\'")}')" title="Baixar CSV" class="px-2 py-1 bg-slate-100 hover:bg-slate-200 text-slate-700 rounded border border-slate-300 text-xs font-semibold inline-flex items-center space-x-1 transition">
                            <i data-lucide="download" class="w-3.5 h-3.5"></i> <span>CSV</span>
                        </button>
                    </td>
                </tr>
            `;
        });
        lucide.createIcons();
    }

    // -- Funções Modais da Bipagem --
    function verIDsRota(nomeRota) {
        const pacotesRota = pacotesBipagem.filter(p => p.rota === nomeRota);
        rotaSelecionadaIDs = pacotesRota.map(p => p.id);
        document.getElementById('modalRotaTitulo').innerText = `Pacotes na Rota: ${nomeRota}`;
        document.getElementById('modalRotaContador').innerText = `${pacotesRota.length} Pacotes`;
        const tbody = document.getElementById('modalRotaTabela');
        tbody.innerHTML = '';
        pacotesRota.forEach(p => {
            tbody.innerHTML += `
                <tr class="hover:bg-slate-50 border-b border-slate-100">
                    <td class="p-2.5 font-bold text-slate-900">${p.id}</td>
                    <td class="p-2.5">${p.ciclo}</td>
                    <td class="p-2.5">${p.status.replace(/_/g, ' ')}</td>
                    <td class="p-2.5 text-slate-500">${p.hora}</td>
                </tr>
            `;
        });
        document.getElementById('modalRota').classList.remove('hidden');
        document.getElementById('modalRota').classList.add('flex');
        lucide.createIcons();
    }
    function fecharModalRota() { document.getElementById('modalRota').classList.add('hidden'); document.getElementById('modalRota').classList.remove('flex'); }
    function copiarIDsModalRota() {
        if (rotaSelecionadaIDs.length === 0) return;
        navigator.clipboard.writeText(rotaSelecionadaIDs.join('\n')).then(() => alert('IDs copiados com sucesso!'));
    }
    function exportarCSVRota(nomeRota) {
        const dadosRota = pacotesBipagem.filter(p => p.rota === nomeRota);
        if (dadosRota.length === 0) return;
        let csvContent = "data:text/csv;charset=utf-8,ID,ROTA,CICLO,STATUS,HORA\n";
        dadosRota.forEach(p => csvContent += `${p.id},${p.rota},${p.ciclo},${p.status},${p.hora}\n`);
        const encodedUri = encodeURI(csvContent);
        const link = document.createElement("a");
        link.setAttribute("href", encodedUri);
        link.setAttribute("download", `Rota_${nomeRota.replace(/[^a-z0-9]/gi, '_')}.csv`);
        document.body.appendChild(link);
        link.click(); document.body.removeChild(link);
    }
    function abrirModalEditar(index) {
        const p = pacotesBipagem[index];
        document.getElementById('editIndex').value = index;
        document.getElementById('editId').value = p.id;
        document.getElementById('editRota').value = p.rota;
        document.getElementById('editCiclo').value = p.ciclo;
        document.getElementById('editStatus').value = p.status;
        document.getElementById('modalEditar').classList.remove('hidden');
        document.getElementById('modalEditar').classList.add('flex');
    }
    function fecharModalEditar() { document.getElementById('modalEditar').classList.add('hidden'); document.getElementById('modalEditar').classList.remove('flex'); }
    function salvarEdicaoManual() {
        const index = document.getElementById('editIndex').value;
        if (index !== '') {
            pacotesBipagem[index].rota = document.getElementById('editRota').value || 'Sem Rota';
            pacotesBipagem[index].ciclo = document.getElementById('editCiclo').value;
            pacotesBipagem[index].status = document.getElementById('editStatus').value;
            fecharModalEditar();
            salvarEAtualizarBipagem();
        }
    }
    function excluirPacote(index) {
        if (confirm('Excluir este pacote do histórico de bipagem?')) {
            pacotesBipagem.splice(index, 1);
            salvarEAtualizarBipagem();
        }
    }
    function copiarTodosIDs() {
        const ids = pacotesBipagem.map(p => p.id).join('\n');
        if(ids) navigator.clipboard.writeText(ids).then(() => alert('Todos os IDs copiados!'));
    }

    // ================= FUNÇÕES DO DASHBOARD (ORIGINAL) =================
    
    function carregarPlanilha(event) {
      const file = event.target.files[0];
      if (!file) return;
      const fileExt = file.name.split('.').pop().toLowerCase();

      if (fileExt === 'csv') {
        Papa.parse(file, { header: true, skipEmptyLines: true, complete: function(results) { processarDadosImportados(results.data); } });
      } else if (fileExt === 'xlsx' || fileExt === 'xls') {
        const reader = new FileReader();
        reader.onload = function(e) {
          const data = new Uint8Array(e.target.result);
          const workbook = XLSX.read(data, { type: 'array' });
          const excelData = XLSX.utils.sheet_to_json(workbook.Sheets[workbook.SheetNames[0]]);
          processarDadosImportados(excelData);
        };
        reader.readAsArrayBuffer(file);
      }
    }

    function processarDadosImportados(data) {
      if (!data || data.length === 0) return alert("Planilha vazia ou inválida.");
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
      alert(`Planilha importada! ${basePacotes.length} registos carregados.`);
    }

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

    function aplicarFiltros() {
      const termo = document.getElementById('searchInput').value.toLowerCase();
      const cidade = document.getElementById('filterCidade').value;
      const bairro = document.getElementById('filterBairro').value;
      const cluster = document.getElementById('filterCluster').value;
      const status = document.getElementById('filterStatus').value;
      const rota = document.getElementById('filterRota').value;

      pacotesFiltrados = basePacotes.filter(p => {
        const matchesBusca = p.id.toLowerCase().includes(termo) || p.cidade.toLowerCase().includes(termo) || p.bairro.toLowerCase().includes(termo) || p.rotaSugerida.toLowerCase().includes(termo);
        const matchesCidade = !cidade || p.cidade === cidade;
        const matchesBairro = !bairro || p.bairro === bairro;
        const matchesCluster = !cluster || p.cluster === cluster;
        const matchesStatus = !status || p.status === status;
        const matchesRota = !rota || p.rotaSugerida === rota;
        return matchesBusca && matchesCidade && matchesBairro && matchesCluster && matchesStatus && matchesRota;
      });

      renderTabelaDashboard(pacotesFiltrados);
      atualizarKPIsDashboard(pacotesFiltrados);
      atualizarGraficos(pacotesFiltrados);
    }

    function limparFiltros() {
      document.getElementById('searchInput').value = '';
      document.querySelectorAll('#filterContainer select').forEach(s => s.value = '');
      aplicarFiltros();
    }

    function renderTabelaDashboard(lista) {
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

    function atualizarKPIsDashboard(lista) {
      document.getElementById('kpiTotal').innerText = lista.length;
      document.getElementById('kpiPendentes').innerText = lista.filter(p => p.status === 'Pendente').length;
      document.getElementById('kpiPS').innerText = lista.filter(p => p.status === 'Problem Solving').length;
      document.getElementById('kpiRotas').innerText = [...new Set(lista.map(p => p.rotaSugerida))].length;
      document.getElementById('kpiConcluidos').innerText = lista.filter(p => p.status === 'At Station' || p.status === 'Concluído').length;
    }

    // Sidebar de Detalhes
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
    function fecharSidebarDireita() { document.getElementById('detailSidebar').classList.add('translate-x-full'); }
    function buscarPorIdSide() { abrirSidebarDireita(document.getElementById('sideSearchInput').value); }
    function consultarIdDireto() { navegarPara('dashboard'); abrirSidebarDireita(document.getElementById('consultarIdInput').value); }
    function confirmarReatribuicao() { alert("Reatribuição registada!"); fecharSidebarDireita(); }
    function resetarDados() { basePacotes = [...pacotesMockPadrao]; popularOpcoesFiltros(); aplicarFiltros(); }

    function atualizarGraficos(lista) {
      const clusters = {};
      lista.forEach(p => clusters[p.cluster] = (clusters[p.cluster] || 0) + 1);
      if (barChartInstance) barChartInstance.destroy();
      barChartInstance = new Chart(document.getElementById('barClusterChart'), {
        type: 'bar', data: { labels: Object.keys(clusters), datasets: [{ data: Object.values(clusters), backgroundColor: '#3b82f6', borderRadius: 4 }] },
        options: { indexAxis: 'y', responsive: true, maintainAspectRatio: false, plugins: { legend: { display: false } } }
      });

      const statusMap = {};
      lista.forEach(p => statusMap[p.status] = (statusMap[p.status] || 0) + 1);
      if (donutChartInstance) donutChartInstance.destroy();
      donutChartInstance = new Chart(document.getElementById('donutStatusChart'), {
        type: 'doughnut', data: { labels: Object.keys(statusMap), datasets: [{ data: Object.values(statusMap), backgroundColor: ['#f59e0b', '#10b981', '#ef4444', '#0284c7'] }] },
        options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { position: 'right', labels: { boxWidth: 10, font: { size: 10 } } } }, cutout: '70%' }
      });

      const rotasMap = {};
      lista.forEach(p => rotasMap[p.rotaSugerida] = (rotasMap[p.rotaSugerida] || 0) + 1);
      if (lineChartInstance) lineChartInstance.destroy();
      lineChartInstance = new Chart(document.getElementById('linePromessaChart'), {
        type: 'bar', data: { labels: Object.keys(rotasMap), datasets: [{ data: Object.values(rotasMap), backgroundColor: '#6366f1', borderRadius: 4 }] },
        options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { display: false } } }
      });
    }

    // ================= INICIALIZAÇÃO GERAL =================
    window.onload = () => {
      // Inicia Dashboard (Código 2)
      popularOpcoesFiltros();
      aplicarFiltros();
      
      // Inicia Bipagem Inteligente (Código 1)
      lucide.createIcons();
      atualizarCicloBadge();
      renderizarTabelaBipagem();
      renderizarResumoRotas();
      
      // Listener do Input de Código de Barras
      document.getElementById('barcodeInput').addEventListener('keypress', function(e) {
          if (e.key === 'Enter') {
              processarBip(this.value.trim());
              this.value = '';
          }
      });
      
      // Abrir na tela de Bipagem por padrão (Opcional, ou mantenha dashboard)
      // navegarPara('bipagem'); 
    };
  </script>
</body>
</html>
