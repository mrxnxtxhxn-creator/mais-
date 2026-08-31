<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KUEHNE+NAGEL | Automação Pós-Sorting</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        kn: {
                            navy: '#003366',
                            blue: '#004B93',
                            light: '#F8FAFC',
                            surface: '#FFFFFF',
                            border: '#E2E8F0',
                            accent: '#0055A5'
                        }
                    }
                }
            }
        }
    </script>
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <!-- Chart.js -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head>
<body class="bg-kn-light flex h-screen overflow-hidden font-sans text-slate-800">

    <!-- ================= SIDEBAR CORPORATIVA (KUEHNE+NAGEL) ================= -->
    <aside class="w-64 bg-kn-navy text-white flex flex-col justify-between z-20 shadow-xl flex-shrink-0">
        <div class="flex-1 flex flex-col overflow-hidden">
            
            <!-- Logo Oficial K+N -->
            <div class="p-5 border-b border-white/10 flex items-center justify-between bg-[#002850]">
                <div class="flex items-center space-x-3">
                    <svg class="w-8 h-8 text-white flex-shrink-0" viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="8">
                        <circle cx="50" cy="50" r="42" />
                        <line x1="50" y1="20" x2="50" y2="72" />
                        <circle cx="50" cy="28" r="6" fill="currentColor" />
                        <path d="M26 62 C 26 78, 74 78, 74 62" stroke-width="8" />
                    </svg>
                    <div class="flex flex-col">
                        <span class="font-bold tracking-wider text-xs leading-tight">KUEHNE+NAGEL</span>
                        <span class="text-[9px] text-slate-300 tracking-widest uppercase font-semibold">Control Tower</span>
                    </div>
                </div>
            </div>

            <!-- Navegação Enterprise -->
            <nav id="nav-menu" class="p-3 space-y-1.5 text-xs overflow-y-auto flex-1">
                <div class="text-[9px] text-slate-400 font-bold uppercase tracking-wider px-3 pb-1 pt-2">Operação Last Mile</div>
                
                <button onclick="mudarAba('operacao')" id="btn-aba-operacao" class="w-full flex items-center space-x-3 p-3 rounded-lg bg-kn-blue text-white transition shadow-sm font-medium">
                    <i data-lucide="scan-barcode" class="w-4 h-4"></i>
                    <span>Bipagem Inteligente</span>
                </button>

                <button onclick="mudarAba('rotas')" id="btn-aba-rotas" class="w-full flex items-center space-x-3 p-3 rounded-lg hover:bg-white/5 text-slate-300 hover:text-white transition font-medium">
                    <i data-lucide="truck" class="w-4 h-4"></i>
                    <span>Resumo por Rota</span>
                </button>

                <div class="text-[9px] text-slate-400 font-bold uppercase tracking-wider px-3 pb-1 pt-5">Business Intelligence</div>
                
                <button onclick="mudarAba('graficos-geral')" id="btn-aba-graficos-geral" class="w-full flex items-center space-x-3 p-3 rounded-lg hover:bg-white/5 text-slate-300 hover:text-white transition font-medium">
                    <i data-lucide="pie-chart" class="w-4 h-4"></i>
                    <span>Visão Comparativa</span>
                </button>

                <button onclick="mudarAba('graficos-am')" id="btn-aba-graficos-am" class="w-full flex items-center space-x-3 p-3 rounded-lg hover:bg-white/5 text-slate-300 hover:text-white transition font-medium">
                    <i data-lucide="sun" class="w-4 h-4"></i>
                    <span>Painel Ciclo AM</span>
                </button>

                <button onclick="mudarAba('graficos-pm')" id="btn-aba-graficos-pm" class="w-full flex items-center space-x-3 p-3 rounded-lg hover:bg-white/5 text-slate-300 hover:text-white transition font-medium">
                    <i data-lucide="moon" class="w-4 h-4"></i>
                    <span>Painel Ciclo PM</span>
                </button>
            </nav>
        </div>

        <!-- Rodapé Assinatura Nathan -->
        <div class="p-4 border-t border-white/10 text-[11px] text-slate-300 text-center flex flex-col items-center justify-center space-y-1 bg-[#002850]">
            <i data-lucide="code-2" class="w-4 h-4 text-sky-400 mb-0.5"></i>
            <span class="font-semibold tracking-wide text-white">Desenvolvido por Nathan</span>
            <span class="text-[9px] text-slate-400">Logistics Systems v2.6</span>
        </div>
    </aside>

    <!-- ================= ÁREA DE CONTEÚDO PRINCIPAL ================= -->
    <main class="flex-1 flex flex-col overflow-y-auto bg-slate-50">
        
        <!-- Header Superior -->
        <header class="bg-white border-b border-kn-border px-8 py-4 flex flex-wrap items-center justify-between sticky top-0 z-10 shadow-sm gap-4">
            <div>
                <h1 class="text-base font-bold text-kn-navy tracking-tight flex items-center gap-2">
                    <span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span>
                    Automação de Reconciliação Pós-Sorting
                </h1>
                <p class="text-xs text-slate-500">Módulo de controle integrado Last Mile</p>
            </div>
            
            <!-- Botões de Exportação e Ações -->
            <div class="flex items-center space-x-2 flex-wrap gap-y-2">
                <div class="flex items-center bg-slate-100 p-1 rounded-lg border border-slate-200 space-x-1">
                    <button onclick="exportarCSV('AM')" class="hover:bg-sky-500 hover:text-white text-slate-700 bg-white px-2.5 py-1.5 rounded text-xs font-semibold flex items-center space-x-1 transition shadow-xs">
                        <i data-lucide="sun" class="w-3.5 h-3.5 text-amber-500"></i>
                        <span>CSV AM</span>
                    </button>
                    <button onclick="exportarCSV('PM')" class="hover:bg-indigo-600 hover:text-white text-slate-700 bg-white px-2.5 py-1.5 rounded text-xs font-semibold flex items-center space-x-1 transition shadow-xs">
                        <i data-lucide="moon" class="w-3.5 h-3.5 text-indigo-500"></i>
                        <span>CSV PM</span>
                    </button>
                    <button onclick="exportarCSV('TODOS')" class="hover:bg-kn-navy hover:text-white text-slate-700 bg-white px-2.5 py-1.5 rounded text-xs font-semibold flex items-center space-x-1 transition shadow-xs">
                        <i data-lucide="download" class="w-3.5 h-3.5 text-slate-600"></i>
                        <span>CSV Geral</span>
                    </button>
                </div>
                <button onclick="limparBase()" class="bg-white border border-rose-200 text-rose-600 hover:bg-rose-50 px-3 py-2 rounded-lg text-xs font-semibold flex items-center space-x-1.5 transition shadow-sm">
                    <i data-lucide="trash-2" class="w-3.5 h-3.5"></i>
                    <span>Zerar Dados</span>
                </button>
            </div>
        </header>

        <div class="p-8 space-y-6 max-w-7xl mx-auto w-full">

            <!-- CARDS DE KPIS EXECUTIVOS -->
            <div class="grid grid-cols-2 md:grid-cols-6 gap-3">
                <div class="bg-white p-4 rounded-xl shadow-sm border border-kn-border border-l-4 border-l-kn-navy">
                    <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider">Total</span>
                    <div id="kpiTotal" class="text-xl font-black text-slate-800 mt-1">0</div>
                </div>
                <div class="bg-white p-4 rounded-xl shadow-sm border border-kn-border border-l-4 border-l-sky-500">
                    <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider">Despachar</span>
                    <div id="kpiDespachar" class="text-xl font-black text-sky-600 mt-1">0</div>
                </div>
                <div class="bg-white p-4 rounded-xl shadow-sm border border-kn-border border-l-4 border-l-emerald-500">
                    <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider">Em Rota</span>
                    <div id="kpiEmRota" class="text-xl font-black text-emerald-600 mt-1">0</div>
                </div>
                <div class="bg-white p-4 rounded-xl shadow-sm border border-kn-border border-l-4 border-l-amber-500">
                    <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider">No Piso</span>
                    <div id="kpiPiso" class="text-xl font-black text-amber-600 mt-1">0</div>
                </div>
                <div class="bg-white p-4 rounded-xl shadow-sm border border-kn-border border-l-4 border-l-rose-500">
                    <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider">Falha Entrega</span>
                    <div id="kpiFalha" class="text-xl font-black text-rose-600 mt-1">0</div>
                </div>
                <div class="bg-white p-4 rounded-xl shadow-sm border border-kn-border border-l-4 border-l-purple-500">
                    <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider">Solução Prob.</span>
                    <div id="kpiSolucao" class="text-xl font-black text-purple-600 mt-1">0</div>
                </div>
            </div>

            <!-- ================= ABA 1: BIPAGEM INTELIGENTE ================= -->
            <section id="aba-operacao" class="grid grid-cols-1 lg:grid-cols-3 gap-6 fade-in">
                
                <div class="space-y-6">
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-kn-border space-y-5">
                        <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                            <div class="flex items-center space-x-2">
                                <h2 class="text-xs font-bold text-kn-navy uppercase tracking-wider">Leitor Óptico</h2>
                                <button onclick="copiarTodosIDs()" title="Copiar todos os IDs escaneados" class="px-2 py-0.5 bg-sky-50 hover:bg-sky-100 text-sky-700 rounded border border-sky-200 text-[10px] font-bold flex items-center space-x-1 transition">
                                    <i data-lucide="copy" class="w-3 h-3"></i>
                                    <span>Copiar IDs</span>
                                </button>
                            </div>
                            <span id="badge-ciclo" class="text-[10px] bg-kn-navy text-white px-2.5 py-1 rounded font-mono font-bold shadow-sm">CICLO AM</span>
                        </div>

                        <div id="feedbackAlerta" class="hidden p-3 rounded-lg text-xs font-medium border transition-all shadow-sm"></div>

                        <div class="space-y-4">
                            <div>
                                <div class="flex justify-between items-center">
                                    <label class="text-xs font-semibold text-slate-600 uppercase tracking-wide">Código de Barras</label>
                                </div>
                                <div class="mt-1">
                                    <input type="text" id="barcodeInput" autofocus placeholder="Aguardando leitura..." class="w-full p-3 border border-slate-300 rounded-lg font-mono text-sm focus:ring-2 focus:ring-kn-navy focus:border-kn-navy focus:outline-none bg-slate-50/50">
                                </div>
                                <span class="text-[11px] text-slate-400 mt-1.5 block leading-tight">⚡ 1º Bipe: Em Rota de Entrega | 2º Bipe: Ficou no Piso</span>
                            </div>

                            <div class="grid grid-cols-2 gap-3 pt-3 border-t border-slate-100">
                                <div>
                                    <label class="text-xs font-semibold text-slate-600">Rota / Gaiola:</label>
                                    <input type="text" id="atribuicaoInput" placeholder="Ex: Gaiola 01" class="w-full p-2.5 border border-slate-300 rounded-lg text-xs mt-1 focus:outline-none focus:border-kn-navy bg-slate-50/50">
                                </div>
                                <div>
                                    <label class="text-xs font-semibold text-slate-600">Ciclo Ativo:</label>
                                    <select id="selectCiclo" onchange="atualizarCicloBadge()" class="w-full p-2.5 border border-slate-300 rounded-lg text-xs mt-1 bg-white focus:outline-none focus:border-kn-navy font-bold text-kn-navy">
                                        <option value="AM">AM</option>
                                        <option value="PM">PM</option>
                                    </select>
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Reconciliação Mercado Livre -->
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-amber-200 space-y-4 bg-amber-50/20">
                        <div class="flex justify-between items-center border-b border-amber-100 pb-3">
                            <div class="flex items-center space-x-2">
                                <h2 class="text-xs font-bold text-amber-900 uppercase tracking-wider">Reconciliar Mercado Livre</h2>
                                <span class="bg-amber-500 text-white text-[9px] px-1.5 py-0.5 rounded font-bold uppercase">Auto Status</span>
                            </div>
                            <i data-lucide="shopping-bag" class="w-4 h-4 text-amber-600"></i>
                        </div>
                        <div>
                            <label class="text-xs font-semibold text-slate-700 uppercase tracking-wide">Cole o texto/print copiado do ML</label>
                            <textarea id="mlTextInput" rows="4" placeholder="Cole aqui as linhas/tabela do Mercado Livre...&#10;Ex:&#10;MLB12345 - Despachar&#10;MLB98765 - Em rota de entrega" class="w-full p-3 border border-amber-300 rounded-lg font-mono text-xs mt-1 focus:ring-2 focus:ring-amber-500 focus:outline-none bg-white resize-none"></textarea>
                        </div>
                        <button onclick="processarPrintMercadoLivre()" class="w-full bg-amber-600 hover:bg-amber-700 text-white p-2.5 rounded-lg text-xs font-bold transition shadow-sm flex items-center justify-center space-x-2">
                            <i data-lucide="refresh-cw" class="w-4 h-4"></i>
                            <span>Reconciliar Status com Mercado Livre</span>
                        </button>
                    </div>

                    <!-- Verificação em Massa (Piso) -->
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-kn-border space-y-4">
                        <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                            <h2 class="text-xs font-bold text-kn-navy uppercase tracking-wider">Marcador em Massa (No Piso)</h2>
                            <i data-lucide="layers" class="w-4 h-4 text-kn-navy"></i>
                        </div>
                        <div>
                            <label class="text-xs font-semibold text-slate-600 uppercase tracking-wide">Cole os IDs (um por linha)</label>
                            <textarea id="bulkInput" rows="3" placeholder="Cole vários IDs aqui..." class="w-full p-3 border border-slate-300 rounded-lg font-mono text-xs mt-1 focus:ring-2 focus:ring-kn-navy focus:outline-none bg-slate-50/50 resize-none"></textarea>
                        </div>
                        <button onclick="processarMassaPiso()" class="w-full bg-slate-700 hover:bg-slate-800 text-white p-2.5 rounded-lg text-xs font-bold transition shadow-sm flex items-center justify-center space-x-2">
                            <i data-lucide="check-check" class="w-4 h-4"></i>
                            <span>Marcar IDs no Piso em Massa</span>
                        </button>
                    </div>
                </div>

                <!-- Tabela de Histórico -->
                <div class="bg-white p-6 rounded-xl shadow-sm border border-kn-border lg:col-span-2 space-y-4">
                    <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                        <div class="flex items-center space-x-3">
                            <h2 class="text-xs font-bold text-kn-navy uppercase tracking-wider">Histórico de Movimentações</h2>
                            <button onclick="copiarTodosIDs()" class="px-2.5 py-1 bg-kn-navy/10 hover:bg-kn-navy hover:text-white text-kn-navy rounded text-xs font-semibold flex items-center space-x-1.5 transition">
                                <i data-lucide="copy" class="w-3.5 h-3.5"></i>
                                <span>Copiar Todos os IDs</span>
                            </button>
                        </div>
                        <span id="contadorBips" class="text-xs font-semibold bg-slate-100 text-kn-navy px-3 py-1 rounded-full border border-slate-200">0 Pacotes</span>
                    </div>

                    <!-- Filtros -->
                    <div class="grid grid-cols-1 sm:grid-cols-3 gap-3 bg-slate-50 p-3 rounded-lg border border-slate-200">
                        <div>
                            <label class="text-[10px] font-bold text-slate-500 uppercase">Filtrar por ID / Rota</label>
                            <input type="text" id="filtroTexto" onkeyup="aplicarFiltros()" placeholder="Pesquisar..." class="w-full mt-1 p-2 bg-white border border-slate-300 rounded-md text-xs focus:outline-none focus:border-kn-navy">
                        </div>
                        <div>
                            <label class="text-[10px] font-bold text-slate-500 uppercase">Status</label>
                            <select id="filtroStatus" onchange="aplicarFiltros()" class="w-full mt-1 p-2 bg-white border border-slate-300 rounded-md text-xs focus:outline-none focus:border-kn-navy font-medium">
                                <option value="">Todos os Status</option>
                                <option value="DESPACHAR">Despachar</option>
                                <option value="EM_ROTA_DE_ENTREGA">Em Rota de Entrega</option>
                                <option value="FICOU_NO_PISO">Ficou no Piso</option>
                                <option value="FALHA_NA_ENTREGA">Falha na Entrega</option>
                                <option value="SOLUCAO_DE_PROBLEMA">Solução de Problema</option>
                                <option value="NULO">Status Nulo</option>
                            </select>
                        </div>
                        <div>
                            <label class="text-[10px] font-bold text-slate-500 uppercase">Ciclo</label>
                            <select id="filtroCiclo" onchange="aplicarFiltros()" class="w-full mt-1 p-2 bg-white border border-slate-300 rounded-md text-xs focus:outline-none focus:border-kn-navy font-medium">
                                <option value="">Todos os Ciclos</option>
                                <option value="AM">Ciclo AM</option>
                                <option value="PM">Ciclo PM</option>
                            </select>
                        </div>
                    </div>

                    <div class="overflow-x-auto max-h-[480px]">
                        <table class="w-full text-xs text-left text-slate-600">
                            <thead class="text-[10px] text-kn-navy uppercase bg-slate-50 border-b border-slate-200 sticky top-0 font-bold">
                                <tr>
                                    <th class="px-4 py-3">Código de Barras</th>
                                    <th class="px-4 py-3">Ciclo</th>
                                    <th class="px-4 py-3">Atribuição / Rota</th>
                                    <th class="px-4 py-3">Status</th>
                                    <th class="px-4 py-3">Horário</th>
                                </tr>
                            </thead>
                            <tbody id="tabelaBips" class="divide-y divide-slate-100">
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <!-- ================= ABA 2: RESUMO POR ROTA ================= -->
            <section id="aba-rotas" class="hidden space-y-6 fade-in">
                <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-kn-border space-y-4">
                        <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                            <h2 class="text-xs font-bold text-kn-navy uppercase tracking-wider">Rotas Mapeadas</h2>
                            <i data-lucide="truck" class="w-4 h-4 text-kn-navy"></i>
                        </div>
                        <p class="text-[11px] text-slate-500">Clique em uma rota para visualizar os pacotes e seus status individuais.</p>
                        
                        <div id="listaCardsRotas" class="space-y-2 max-h-[500px] overflow-y-auto pr-1"></div>
                    </div>

                    <div class="bg-white p-6 rounded-xl shadow-sm border border-kn-border lg:col-span-2 space-y-4">
                        <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                            <div class="flex items-center space-x-2">
                                <h2 class="text-xs font-bold text-kn-navy uppercase tracking-wider">Pacotes da Rota:</h2>
                                <span id="tituloRotaSelecionada" class="text-xs font-black text-kn-blue bg-sky-50 px-2.5 py-1 rounded border border-sky-200">Selecione uma rota</span>
                            </div>
                            <span id="contadorRotaSelecionada" class="text-xs font-semibold bg-slate-100 text-kn-navy px-3 py-1 rounded-full border border-slate-200">0 Pacotes</span>
                        </div>

                        <div class="overflow-x-auto max-h-[480px]">
                            <table class="w-full text-xs text-left text-slate-600">
                                <thead class="text-[10px] text-kn-navy uppercase bg-slate-50 border-b border-slate-200 sticky top-0 font-bold">
                                    <tr>
                                        <th class="px-4 py-3">Código de Barras</th>
                                        <th class="px-4 py-3">Ciclo</th>
                                        <th class="px-4 py-3">Status Atual</th>
                                        <th class="px-4 py-3">Horário</th>
                                    </tr>
                                </thead>
                                <tbody id="tabelaDetalhesRota" class="divide-y divide-slate-100">
                                    <tr><td colspan="4" class="px-4 py-8 text-center text-slate-400">Clique em uma rota no painel ao lado para visualizar os IDs.</td></tr>
                                </tbody>
                            </table>
                        </div>
                    </div>
                </div>
            </section>

            <!-- ================= ABA 3: VISÃO COMPARATIVA GERAL ================= -->
            <section id="aba-graficos-geral" class="hidden space-y-6 fade-in">
                <div class="bg-white p-6 rounded-xl shadow-sm border border-kn-border">
                    <h2 class="text-xs font-bold text-kn-navy uppercase tracking-wider border-b border-slate-100 pb-3 mb-4">
                        Comparativo Geral de Performance: Ciclo AM vs Ciclo PM
                    </h2>
                    <div class="relative h-96 w-full">
                        <canvas id="graficoGeral"></canvas>
                    </div>
                </div>
            </section>

            <!-- ================= ABA 4: PAINEL CICLO AM ================= -->
            <section id="aba-graficos-am" class="hidden space-y-6 fade-in">
                <div class="bg-white p-6 rounded-xl shadow-sm border border-kn-border">
                    <h2 class="text-xs font-bold text-kn-navy uppercase tracking-wider border-b border-slate-100 pb-3 mb-4">
                        Analytics Operacional - Distribuição de Status do Ciclo AM
                    </h2>
                    <div class="relative h-96 w-full">
                        <canvas id="graficoAM"></canvas>
                    </div>
                </div>
            </section>

            <!-- ================= ABA 5: PAINEL CICLO PM ================= -->
            <section id="aba-graficos-pm" class="hidden space-y-6 fade-in">
                <div class="bg-white p-6 rounded-xl shadow-sm border border-kn-border">
                    <h2 class="text-xs font-bold text-kn-navy uppercase tracking-wider border-b border-slate-100 pb-3 mb-4">
                        Analytics Operacional - Distribuição de Status do Ciclo PM
                    </h2>
                    <div class="relative h-96 w-full">
                        <canvas id="graficoPM"></canvas>
                    </div>
                </div>
            </section>

        </div>
    </main>

    <style>
        .fade-in { animation: fadeIn 0.2s ease-in-out; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(3px); } to { opacity: 1; transform: translateY(0); } }
    </style>

    <!-- ================= SCRIPTS DE LÓGICA E CHART.JS ================= -->
    <script>
        lucide.createIcons();
        
        const STORAGE_KEY = 'kn_logistica_dados';
        let dadosOperacao = carregardados();
        let rotaAtivaSelecionada = null;
        
        let chartAM = null;
        let chartPM = null;
        let chartGeral = null;

        const STATUS_MAP = {
            'DESPACHAR': { label: 'Despachar', class: 'bg-sky-100 text-sky-800 border-sky-300' },
            'EM_ROTA_DE_ENTREGA': { label: 'Em Rota de Entrega', class: 'bg-emerald-100 text-emerald-800 border-emerald-300' },
            'FICOU_NO_PISO': { label: 'Ficou no Piso', class: 'bg-amber-100 text-amber-800 border-amber-300' },
            'FALHA_NA_ENTREGA': { label: 'Falha na Entrega', class: 'bg-rose-100 text-rose-800 border-rose-300' },
            'SOLUCAO_DE_PROBLEMA': { label: 'Solução de Problema', class: 'bg-purple-100 text-purple-800 border-purple-300' },
            'NULO': { label: 'Status Nulo', class: 'bg-slate-100 text-slate-700 border-slate-300' }
        };

        window.onload = function() {
            aplicarFiltros();
            atualizarKPIs();
            document.getElementById('barcodeInput').focus();
        };

        function mudarAba(abaSelecionada) {
            const abas = ['operacao', 'rotas', 'graficos-geral', 'graficos-am', 'graficos-pm'];
            
            abas.forEach(aba => {
                document.getElementById('aba-' + aba).classList.add('hidden');
                const btn = document.getElementById('btn-aba-' + aba);
                if (btn) {
                    btn.classList.remove('bg-kn-blue', 'text-white', 'shadow-sm');
                    btn.classList.add('hover:bg-white/5', 'text-slate-300');
                }
            });

            document.getElementById('aba-' + abaSelecionada).classList.remove('hidden');
            const btnAtivo = document.getElementById('btn-aba-' + abaSelecionada);
            if (btnAtivo) {
                btnAtivo.classList.add('bg-kn-blue', 'text-white', 'shadow-sm');
                btnAtivo.classList.remove('hover:bg-white/5', 'text-slate-300');
            }

            if (abaSelecionada === 'rotas') {
                renderizarAbaRotas();
            } else if (abaSelecionada.startsWith('graficos')) {
                setTimeout(renderizarGraficos, 60); 
            } else {
                document.getElementById('barcodeInput').focus();
            }
        }

        function salvarDados() {
            localStorage.setItem(STORAGE_KEY, JSON.stringify(dadosOperacao));
            atualizarKPIs();
            renderizarGraficos();
            if (!document.getElementById('aba-rotas').classList.contains('hidden')) {
                renderizarAbaRotas();
            }
        }

        function carregardados() {
            const dadosSalvos = localStorage.getItem(STORAGE_KEY);
            return dadosSalvos ? JSON.parse(dadosSalvos) : [];
        }

        function atualizarCicloBadge() {
            const ciclo = document.getElementById('selectCiclo').value;
            document.getElementById('badge-ciclo').innerText = `CICLO ${ciclo}`;
            document.getElementById('barcodeInput').focus();
        }

        function mostrarAlerta(mensagem, tipo) {
            const alerta = document.getElementById('feedbackAlerta');
            alerta.classList.remove('hidden', 'bg-emerald-50', 'border-emerald-200', 'text-emerald-800', 'bg-amber-50', 'border-amber-200', 'text-amber-800', 'bg-blue-50', 'border-blue-200', 'text-blue-800');
            
            if (tipo === 'success') alerta.classList.add('bg-emerald-50', 'border-emerald-200', 'text-emerald-800');
            else if (tipo === 'info') alerta.classList.add('bg-blue-50', 'border-blue-200', 'text-blue-800');
            else alerta.classList.add('bg-amber-50', 'border-amber-200', 'text-amber-800');
            
            alerta.innerText = mensagem;
            setTimeout(() => { alerta.classList.add('hidden'); }, 3500);
        }

        function copiarTodosIDs() {
            if (dadosOperacao.length === 0) {
                mostrarAlerta('⚠️ Nenhum ID disponível para copiar.', 'warning');
                return;
            }
            const listaIDs = [...new Set(dadosOperacao.map(item => item.barcode))].join('\n');
            navigator.clipboard.writeText(listaIDs).then(() => {
                mostrarAlerta(`📋 ${dadosOperacao.length} ID(s) copiado(s) com sucesso!`, 'info');
            });
        }

        document.getElementById('barcodeInput').addEventListener('keypress', function (e) {
            if (e.key === 'Enter') {
                e.preventDefault();
                processarBip();
            }
        });

        function processarBip() {
            const input = document.getElementById('barcodeInput');
            const barcode = input.value.trim();
            const atribuicao = document.getElementById('atribuicaoInput').value.trim() || 'Sem Rota';
            const ciclo = document.getElementById('selectCiclo').value;

            if (!barcode) return;

            let itemExistente = dadosOperacao.find(d => d.barcode === barcode && d.ciclo === ciclo);

            if (!itemExistente) {
                const novoItem = {
                    id: Date.now() + Math.random(),
                    barcode: barcode,
                    ciclo: ciclo,
                    atribuicao: atribuicao,
                    status: 'EM_ROTA_DE_ENTREGA',
                    hora: new Date().toLocaleTimeString('pt-BR'),
                    data: new Date().toLocaleDateString('pt-BR')
                };
                dadosOperacao.unshift(novoItem);
                mostrarAlerta(`✅ Pacote ${barcode} cadastrado como Em Rota (1º Bipe).`, 'success');
            } else {
                if (itemExistente.status === 'EM_ROTA_DE_ENTREGA') {
                    itemExistente.status = 'FICOU_NO_PISO';
                    mostrarAlerta(`⚠️ Pacote ${barcode} alterado para Ficou no Piso (2º Bipe).`, 'warning');
                } else {
                    itemExistente.status = 'EM_ROTA_DE_ENTREGA';
                    mostrarAlerta(`✅ Pacote ${barcode} retornado para Em Rota.`, 'success');
                }
                itemExistente.hora = new Date().toLocaleTimeString('pt-BR');
                itemExistente.atribuicao = atribuicao;
            }

            input.value = '';
            salvarDados();
            aplicarFiltros();
            input.focus();
        }

        function processarMassaPiso() {
            const texto = document.getElementById('bulkInput').value.trim();
            if (!texto) return;

            const linhas = texto.split('\n');
            let count = 0;
            const ciclo = document.getElementById('selectCiclo').value;

            linhas.forEach(linha => {
                const barcode = linha.trim();
                if (barcode) {
                    let item = dadosOperacao.find(d => d.barcode === barcode && d.ciclo === ciclo);
                    if (item) {
                        item.status = 'FICOU_NO_PISO';
                        count++;
                    } else {
                        dadosOperacao.unshift({
                            id: Date.now() + Math.random(),
                            barcode: barcode,
                            ciclo: ciclo,
                            atribuicao: 'Massa / Piso',
                            status: 'FICOU_NO_PISO',
                            hora: new Date().toLocaleTimeString('pt-BR'),
                            data: new Date().toLocaleDateString('pt-BR')
                        });
                        count++;
                    }
                }
            });

            document.getElementById('bulkInput').value = '';
            salvarDados();
            aplicarFiltros();
            mostrarAlerta(`📦 ${count} pacote(s) marcado(s) como 'Ficou no Piso' em massa.`, 'success');
        }

        function processarPrintMercadoLivre() {
            const texto = document.getElementById('mlTextInput').value.trim();
            if (!texto) {
                mostrarAlerta('⚠️ Cole o conteúdo do Mercado Livre primeiro.', 'warning');
                return;
            }

            const linhas = texto.split('\n');
            let atualizados = 0;
            const ciclo = document.getElementById('selectCiclo').value;

            linhas.forEach(linha => {
                // Tenta extrair ID (ex: MLB...) e status textual
                const matchId = linha.match(/(MLB\d+|\b\d{8,}\b)/i);
                if (matchId) {
                    const barcode = matchId[0];
                    let novoStatus = 'EM_ROTA_DE_ENTREGA';

                    const lower = linha.toLowerCase();
                    if (lower.includes('despachar') || lower.includes('pendente')) novoStatus = 'DESPACHAR';
                    else if (lower.includes('piso') || lower.includes('ficou')) novoStatus = 'FICOU_NO_PISO';
                    else if (lower.includes('falha') || lower.includes('não entregue')) novoStatus = 'FALHA_NA_ENTREGA';
                    else if (lower.includes('problema') || lower.includes('solução')) novoStatus = 'SOLUCAO_DE_PROBLEMA';

                    let item = dadosOperacao.find(d => d.barcode === barcode && d.ciclo === ciclo);
                    if (item) {
                        item.status = novoStatus;
                        atualizados++;
                    } else {
                        dadosOperacao.unshift({
                            id: Date.now() + Math.random(),
                            barcode: barcode,
                            ciclo: ciclo,
                            atribuicao: 'Reconciliação ML',
                            status: novoStatus,
                            hora: new Date().toLocaleTimeString('pt-BR'),
                            data: new Date().toLocaleDateString('pt-BR')
                        });
                        atualizados++;
                    }
                }
            });

            document.getElementById('mlTextInput').value = '';
            salvarDados();
            aplicarFiltros();
            mostrarAlerta(`🔄 Reconciliação concluída! ${atualizados} pacote(s) atualizados com dados do Mercado Livre.`, 'success');
        }

        function aplicarFiltros() {
            const texto = document.getElementById('filtroTexto').value.toLowerCase();
            const statusFiltro = document.getElementById('filtroStatus').value;
            const cicloFiltro = document.getElementById('filtroCiclo').value;

            const filtrados = dadosOperacao.filter(item => {
                const matchTexto = item.barcode.toLowerCase().includes(texto) || item.atribuicao.toLowerCase().includes(texto);
                const matchStatus = !statusFiltro || item.status === statusFiltro;
                const matchCiclo = !cicloFiltro || item.ciclo === cicloFiltro;
                return matchTexto && matchStatus && matchCiclo;
            });

            const tbody = document.getElementById('tabelaBips');
            tbody.innerHTML = '';

            if (filtrados.length === 0) {
                tbody.innerHTML = `<tr><td colspan="5" class="px-4 py-8 text-center text-slate-400">Nenhum registro encontrado.</td></tr>`;
            } else {
                filtrados.forEach(item => {
                    const statusObj = STATUS_MAP[item.status] || STATUS_MAP['NULO'];
                    const tr = document.createElement('tr');
                    tr.className = 'hover:bg-slate-50/80 transition';
                    tr.innerHTML = `
                        <td class="px-4 py-3 font-mono font-bold text-slate-700">${item.barcode}</td>
                        <td class="px-4 py-3"><span class="px-2 py-0.5 rounded font-mono font-bold text-[10px] ${item.ciclo === 'AM' ? 'bg-sky-100 text-sky-800' : 'bg-indigo-100 text-indigo-800'}">${item.ciclo}</span></td>
                        <td class="px-4 py-3 font-medium text-slate-700">${item.atribuicao}</td>
                        <td class="px-4 py-3"><span class="px-2.5 py-1 rounded-full text-[10px] font-bold border ${statusObj.class}">${statusObj.label}</span></td>
                        <td class="px-4 py-3 text-slate-400">${item.hora}</td>
                    `;
                    tbody.appendChild(tr);
                });
            }
            document.getElementById('contadorBips').innerText = `${filtrados.length} Pacote(s)`;
        }

        function atualizarKPIs() {
            document.getElementById('kpiTotal').innerText = dadosOperacao.length;
            document.getElementById('kpiDespachar').innerText = dadosOperacao.filter(d => d.status === 'DESPACHAR').length;
            document.getElementById('kpiEmRota').innerText = dadosOperacao.filter(d => d.status === 'EM_ROTA_DE_ENTREGA').length;
            document.getElementById('kpiPiso').innerText = dadosOperacao.filter(d => d.status === 'FICOU_NO_PISO').length;
            document.getElementById('kpiFalha').innerText = dadosOperacao.filter(d => d.status === 'FALHA_NA_ENTREGA').length;
            document.getElementById('kpiSolucao').innerText = dadosOperacao.filter(d => d.status === 'SOLUCAO_DE_PROBLEMA').length;
        }

        function renderizarAbaRotas() {
            const rotasMap = {};
            dadosOperacao.forEach(item => {
                const rot = item.atribuicao || 'Sem Rota';
                if (!rotasMap[rot]) rotasMap[rot] = [];
                rotasMap[rot].push(item);
            });

            const container = document.getElementById('listaCardsRotas');
            container.innerHTML = '';

            const rotasKeys = Object.keys(rotasMap);
            if (rotasKeys.length === 0) {
                container.innerHTML = `<div class="p-4 text-center text-xs text-slate-400">Nenhuma rota mapeada.</div>`;
                return;
            }

            rotasKeys.forEach(rota => {
                const qtd = rotasMap[rota].length;
                const div = document.createElement('div');
                div.className = `p-3 rounded-lg border cursor-pointer transition flex justify-between items-center ${rotaAtivaSelecionada === rota ? 'bg-sky-50 border-sky-300 shadow-sm' : 'bg-white border-slate-200 hover:bg-slate-50'}`;
                div.onclick = () => selecionarRota(rota, rotasMap[rota]);
                div.innerHTML = `
                    <div class="flex items-center space-x-2">
                        <i data-lucide="map-pin" class="w-4 h-4 text-kn-navy"></i>
                        <span class="text-xs font-bold text-slate-700">${rota}</span>
                    </div>
                    <span class="text-xs font-semibold px-2.5 py-0.5 rounded-full bg-slate-100 text-kn-navy">${qtd} pacotes</span>
                `;
                container.appendChild(div);
            });
            lucide.createIcons();
        }

        function selecionarRota(rotaName, listaItens) {
            rotaAtivaSelecionada = rotaName;
            document.getElementById('tituloRotaSelecionada').innerText = rotaName;
            document.getElementById('contadorRotaSelecionada').innerText = `${listaItens.length} Pacotes`;

            const tbody = document.getElementById('tabelaDetalhesRota');
            tbody.innerHTML = '';

            listaItens.forEach(item => {
                const statusObj = STATUS_MAP[item.status] || STATUS_MAP['NULO'];
                const tr = document.createElement('tr');
                tr.className = 'hover:bg-slate-50 transition';
                tr.innerHTML = `
                    <td class="px-4 py-3 font-mono font-bold text-slate-700">${item.barcode}</td>
                    <td class="px-4 py-3"><span class="px-2 py-0.5 rounded font-mono font-bold text-[10px] ${item.ciclo === 'AM' ? 'bg-sky-100 text-sky-800' : 'bg-indigo-100 text-indigo-800'}">${item.ciclo}</span></td>
                    <td class="px-4 py-3"><span class="px-2.5 py-1 rounded-full text-[10px] font-bold border ${statusObj.class}">${statusObj.label}</span></td>
                    <td class="px-4 py-3 text-slate-400">${item.hora}</td>
                `;
                tbody.appendChild(tr);
            });
            renderizarAbaRotas();
        }

        function renderizarGraficos() {
            // Ciclo AM
            const ctxAM = document.getElementById('graficoAM');
            if (ctxAM) {
                if (chartAM) chartAM.destroy();
                const amDados = dadosOperacao.filter(d => d.ciclo === 'AM');
                chartAM = new Chart(ctxAM, {
                    type: 'doughnut',
                    data: {
                        labels: ['Despachar', 'Em Rota', 'No Piso', 'Falha', 'Solução'],
                        datasets: [{
                            data: [
                                amDados.filter(d => d.status === 'DESPACHAR').length,
                                amDados.filter(d => d.status === 'EM_ROTA_DE_ENTREGA').length,
                                amDados.filter(d => d.status === 'FICOU_NO_PISO').length,
                                amDados.filter(d => d.status === 'FALHA_NA_ENTREGA').length,
                                amDados.filter(d => d.status === 'SOLUCAO_DE_PROBLEMA').length
                            ],
                            backgroundColor: ['#0ea5e9', '#10b981', '#f59e0b', '#f43f5e', '#a855f7']
                        }]
                    },
                    options: { responsive: true, maintainAspectRatio: false }
                });
            }

            // Ciclo PM
            const ctxPM = document.getElementById('graficoPM');
            if (ctxPM) {
                if (chartPM) chartPM.destroy();
                const pmDados = dadosOperacao.filter(d => d.ciclo === 'PM');
                chartPM = new Chart(ctxPM, {
                    type: 'doughnut',
                    data: {
                        labels: ['Despachar', 'Em Rota', 'No Piso', 'Falha', 'Solução'],
                        datasets: [{
                            data: [
                                pmDados.filter(d => d.status === 'DESPACHAR').length,
                                pmDados.filter(d => d.status === 'EM_ROTA_DE_ENTREGA').length,
                                pmDados.filter(d => d.status === 'FICOU_NO_PISO').length,
                                pmDados.filter(d => d.status === 'FALHA_NA_ENTREGA').length,
                                pmDados.filter(d => d.status === 'SOLUCAO_DE_PROBLEMA').length
                            ],
                            backgroundColor: ['#0ea5e9', '#10b981', '#f59e0b', '#f43f5e', '#a855f7']
                        }]
                    },
                    options: { responsive: true, maintainAspectRatio: false }
                });
            }

            // Gráfico Geral Comparativo
            const ctxGeral = document.getElementById('graficoGeral');
            if (ctxGeral) {
                if (chartGeral) chartGeral.destroy();
                chartGeral = new Chart(ctxGeral, {
                    type: 'bar',
                    data: {
                        labels: ['Despachar', 'Em Rota', 'No Piso', 'Falha Entrega', 'Solução Problema'],
                        datasets: [
                            {
                                label: 'Ciclo AM',
                                data: [
                                    dadosOperacao.filter(d => d.ciclo === 'AM' && d.status === 'DESPACHAR').length,
                                    dadosOperacao.filter(d => d.ciclo === 'AM' && d.status === 'EM_ROTA_DE_ENTREGA').length,
                                    dadosOperacao.filter(d => d.ciclo === 'AM' && d.status === 'FICOU_NO_PISO').length,
                                    dadosOperacao.filter(d => d.ciclo === 'AM' && d.status === 'FALHA_NA_ENTREGA').length,
                                    dadosOperacao.filter(d => d.ciclo === 'AM' && d.status === 'SOLUCAO_DE_PROBLEMA').length
                                ],
                                backgroundColor: '#0284c7'
                            },
                            {
                                label: 'Ciclo PM',
                                data: [
                                    dadosOperacao.filter(d => d.ciclo === 'PM' && d.status === 'DESPACHAR').length,
                                    dadosOperacao.filter(d => d.ciclo === 'PM' && d.status === 'EM_ROTA_DE_ENTREGA').length,
                                    dadosOperacao.filter(d => d.ciclo === 'PM' && d.status === 'FICOU_NO_PISO').length,
                                    dadosOperacao.filter(d => d.ciclo === 'PM' && d.status === 'FALHA_NA_ENTREGA').length,
                                    dadosOperacao.filter(d => d.ciclo === 'PM' && d.status === 'SOLUCAO_DE_PROBLEMA').length
                                ],
                                backgroundColor: '#6366f1'
                            }
                        ]
                    },
                    options: { responsive: true, maintainAspectRatio: false }
                });
            }
        }

        function exportarCSV(tipoCiclo) {
            if (dadosOperacao.length === 0) {
                mostrarAlerta('⚠️ Não há dados para exportar.', 'warning');
                return;
            }

            let dadosFiltrados = dadosOperacao;
            if (tipoCiclo === 'AM' || tipoCiclo === 'PM') {
                dadosFiltrados = dadosOperacao.filter(d => d.ciclo === tipoCiclo);
            }

            if (dadosFiltrados.length === 0) {
                mostrarAlerta(`⚠️ Nenhum dado encontrado para o ciclo ${tipoCiclo}.`, 'warning');
                return;
            }

            let csvContent = "data:text/csv;charset=utf-8,Codigo de Barras;Ciclo;Atribuicao/Rota;Status;Horario;Data\n";
            dadosFiltrados.forEach(row => {
                csvContent += `${row.barcode};${row.ciclo};${row.atribuicao};${row.status};${row.hora};${row.data}\n`;
            });

            const encodedUri = encodeURI(csvContent);
            const link = document.createElement("a");
            link.setAttribute("href", encodedUri);
            link.setAttribute("download", `KN_PosSorting_${tipoCiclo}_${new Date().toISOString().slice(0,10)}.csv`);
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            mostrarAlerta(`📥 CSV do ${tipoCiclo} exportado com sucesso!`, 'success');
        }

        function limparBase() {
            if (confirm("Tem certeza que deseja apagar todos os registros da operação?")) {
                dadosOperacao = [];
                localStorage.removeItem(STORAGE_KEY);
                aplicarFiltros();
                atualizarKPIs();
                renderizarGraficos();
                mostrarAlerta('🗑️ Base de dados limpa com sucesso.', 'info');
            }
        }
    </script>
</body>
</html>
