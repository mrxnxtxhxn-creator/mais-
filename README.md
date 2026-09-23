

Kn pos sorting · HTML
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
 
        <div class="p-4 border-t border-white/10 text-[11px] text-slate-300 text-center flex flex-col items-center justify-center space-y-1 bg-[#002850]">
            <i data-lucide="code-2" class="w-4 h-4 text-sky-400 mb-0.5"></i>
            <span class="font-semibold tracking-wide text-white">Desenvolvido por Nathan</span>
            <span class="text-[9px] text-slate-400">Logistics Systems v2.6</span>
        </div>
    </aside>
 
    <!-- ================= ÁREA DE CONTEÚDO PRINCIPAL ================= -->
    <main class="flex-1 flex flex-col overflow-y-auto bg-slate-50">
        
        <header class="bg-white border-b border-kn-border px-8 py-4 flex flex-wrap items-center justify-between sticky top-0 z-10 shadow-sm gap-4">
            <div>
                <h1 class="text-base font-bold text-kn-navy tracking-tight flex items-center gap-2">
                    <span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span>
                    Automação de Reconciliação Pós-Sorting
                </h1>
                <p class="text-xs text-slate-500">Módulo de controle integrado Last Mile</p>
            </div>
            
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
            <section id="aba-operacao" class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                
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
                                <label class="text-xs font-semibold text-slate-600 uppercase tracking-wide">Código de Barras</label>
                                <input type="text" id="barcodeInput" autofocus placeholder="Aguardando leitura..." class="w-full p-3 border border-slate-300 rounded-lg font-mono text-sm focus:ring-2 focus:ring-kn-navy focus:border-kn-navy focus:outline-none bg-slate-50/50 mt-1">
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
                            <input type="text" id="filtroTexto" onkeyup="renderizarTabela()" placeholder="Pesquisar..." class="w-full mt-1 p-2 bg-white border border-slate-300 rounded-md text-xs focus:outline-none focus:border-kn-navy">
                        </div>
                        <div>
                            <label class="text-[10px] font-bold text-slate-500 uppercase">Status</label>
                            <select id="filtroStatus" onchange="renderizarTabela()" class="w-full mt-1 p-2 bg-white border border-slate-300 rounded-md text-xs focus:outline-none focus:border-kn-navy font-medium">
                                <option value="">Todos os Status</option>
                                <option value="DESPACHAR">Despachar</option>
                                <option value="EM_ROTA_DE_ENTREGA">Em Rota de Entrega</option>
                                <option value="FICOU_NO_PISO">Ficou no Piso</option>
                                <option value="ENTREGUE">Entregue</option>
                                <option value="FALHA_NA_ENTREGA">Falha na Entrega</option>
                                <option value="SOLUCAO_DE_PROBLEMA">Solução de Problema</option>
                                <option value="NULO">Status Nulo</option>
                            </select>
                        </div>
                        <div>
                            <label class="text-[10px] font-bold text-slate-500 uppercase">Ciclo</label>
                            <select id="filtroCiclo" onchange="renderizarTabela()" class="w-full mt-1 p-2 bg-white border border-slate-300 rounded-md text-xs focus:outline-none focus:border-kn-navy font-medium">
                                <option value="">Todos os Ciclos</option>
                                <option value="AM">Ciclo AM</option>
                                <option value="PM">Ciclo PM</option>
                            </select>
                        </div>
                    </div>
 
                    <div class="overflow-x-auto max-h-[480px]">
                        <table class="w-full text-left text-xs">
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
                            <tbody id="tabelaHistorico" class="divide-y divide-slate-100 font-mono">
                                <!-- Linhas renderizadas via JS -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>
 
            <!-- ================= ABA 2: RESUMO POR ROTA ================= -->
            <section id="aba-rotas" class="hidden bg-white p-6 rounded-xl shadow-sm border border-kn-border space-y-4">
                <h2 class="text-xs font-bold text-kn-navy uppercase tracking-wider border-b pb-3">Resumo Agrupado por Rota</h2>
                <div class="overflow-x-auto">
                    <table class="w-full text-left text-xs">
                        <thead class="bg-slate-100 text-slate-600 font-bold uppercase border-b border-slate-200">
                            <tr>
                                <th class="p-3">Rota</th>
                                <th class="p-3">Total Pacotes</th>
                                <th class="p-3">Em Rota</th>
                                <th class="p-3">No Piso</th>
                                <th class="p-3">Despachar</th>
                                <th class="p-3">Falha</th>
                            </tr>
                        </thead>
                        <tbody id="tabelaRotas" class="divide-y divide-slate-100 font-mono">
                            <!-- Gerado dinamicamente -->
                        </tbody>
                    </table>
                </div>
            </section>
 
            <!-- ================= ABAS BI / GRÁFICOS ================= -->
            <section id="aba-graficos-geral" class="hidden space-y-6">
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div class="bg-white p-5 rounded-xl border border-kn-border shadow-sm">
                        <h3 class="text-xs font-bold text-kn-navy uppercase tracking-wider mb-4">Distribuição Geral de Status</h3>
                        <canvas id="chartGeralStatus" class="max-h-64"></canvas>
                    </div>
                    <div class="bg-white p-5 rounded-xl border border-kn-border shadow-sm">
                        <h3 class="text-xs font-bold text-kn-navy uppercase tracking-wider mb-4">Volume Ciclo AM vs PM</h3>
                        <canvas id="chartGeralCiclos" class="max-h-64"></canvas>
                    </div>
                </div>
            </section>
 
            <section id="aba-graficos-am" class="hidden bg-white p-5 rounded-xl border border-kn-border shadow-sm">
                <h3 class="text-xs font-bold text-kn-navy uppercase tracking-wider mb-4">Status Exclusivo - Ciclo AM</h3>
                <canvas id="chartAM" class="max-h-72"></canvas>
            </section>
 
            <section id="aba-graficos-pm" class="hidden bg-white p-5 rounded-xl border border-kn-border shadow-sm">
                <h3 class="text-xs font-bold text-kn-navy uppercase tracking-wider mb-4">Status Exclusivo - Ciclo PM</h3>
                <canvas id="chartPM" class="max-h-72"></canvas>
            </section>
 
        </div>
    </main>
 
    <!-- ================= MODAL DE EDIÇÃO MANUAL (CICLO, ROTA E STATUS) ================= -->
    <div id="modalEditar" class="fixed inset-0 bg-slate-900/50 backdrop-blur-sm hidden items-center justify-center z-50 p-4">
        <div class="bg-white rounded-xl shadow-2xl max-w-md w-full p-6 space-y-4">
            <div class="flex justify-between items-center border-b pb-3">
                <div class="flex items-center space-x-2">
                    <i data-lucide="edit-3" class="w-4 h-4 text-kn-navy"></i>
                    <h3 class="text-xs font-bold text-kn-navy uppercase tracking-wider">Editar Pacote Manualmente</h3>
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
                <input type="text" id="editRota" placeholder="Ex: Gaiola 05 / Rota X" class="w-full p-2.5 border border-slate-300 rounded-lg text-xs mt-1 focus:ring-2 focus:ring-kn-navy focus:outline-none">
            </div>
 
            <div>
                <label class="text-[10px] font-bold text-slate-500 uppercase">Nome do Log</label>
                <input type="text" id="editLog" placeholder="Ex: Log 03" class="w-full p-2.5 border border-slate-300 rounded-lg text-xs mt-1 focus:ring-2 focus:ring-kn-navy focus:outline-none">
            </div>
 
            <div>
                <label class="text-[10px] font-bold text-slate-500 uppercase">Nome do Motorista</label>
                <input type="text" id="editMotorista" placeholder="Ex: João Silva" class="w-full p-2.5 border border-slate-300 rounded-lg text-xs mt-1 focus:ring-2 focus:ring-kn-navy focus:outline-none">
            </div>
 
            <div>
                <label class="text-[10px] font-bold text-slate-500 uppercase">Nome da Empresa</label>
                <input type="text" id="editEmpresa" placeholder="Ex: Transportadora XYZ" class="w-full p-2.5 border border-slate-300 rounded-lg text-xs mt-1 focus:ring-2 focus:ring-kn-navy focus:outline-none">
            </div>
 
            <div class="grid grid-cols-2 gap-3">
                <div>
                    <label class="text-[10px] font-bold text-slate-500 uppercase">Ciclo Manual</label>
                    <select id="editCiclo" class="w-full p-2.5 border border-slate-300 rounded-lg text-xs mt-1 bg-white font-bold text-kn-navy focus:ring-2 focus:ring-kn-navy focus:outline-none">
                        <option value="AM">AM</option>
                        <option value="PM">PM</option>
                    </select>
                </div>
                <div>
                    <label class="text-[10px] font-bold text-slate-500 uppercase">Status Manual</label>
                    <select id="editStatus" class="w-full p-2.5 border border-slate-300 rounded-lg text-xs mt-1 bg-white font-semibold text-slate-700 focus:ring-2 focus:ring-kn-navy focus:outline-none">
                        <option value="DESPACHAR">DESPACHAR</option>
                        <option value="EM_ROTA_DE_ENTREGA">EM ROTA DE ENTREGA</option>
                        <option value="FICOU_NO_PISO">FICOU NO PISO</option>
                        <option value="ENTREGUE">ENTREGUE</option>
                        <option value="FALHA_NA_ENTREGA">FALHA NA ENTREGA</option>
                        <option value="SOLUCAO_DE_PROBLEMA">SOLUÇÃO DE PROBLEMA</option>
                        <option value="NULO">NULO</option>
                    </select>
                </div>
            </div>
 
            <div class="flex justify-end space-x-2 pt-3 border-t">
                <button onclick="fecharModalEditar()" class="px-4 py-2 bg-slate-100 text-slate-600 hover:bg-slate-200 rounded-lg text-xs font-semibold transition">Cancelar</button>
                <button onclick="salvarEdicaoManual()" class="px-4 py-2 bg-kn-navy text-white hover:bg-kn-blue rounded-lg text-xs font-bold transition shadow-sm flex items-center space-x-1.5">
                    <i data-lucide="check" class="w-4 h-4"></i>
                    <span>Salvar Alterações</span>
                </button>
            </div>
        </div>
    </div>
 
    <!-- ================= SCRIPT DE LÓGICA E ESTADO ================= -->
    <script>
        // Estado Global
        let pacotes = JSON.parse(localStorage.getItem('kn_pacotes')) || [];
        let charts = {};
 
        // Inicialização
        document.addEventListener('DOMContentLoaded', () => {
            lucide.createIcons();
            atualizarCicloBadge();
            renderizarTabela();
            atualizarKPIs();
            renderizarResumoRotas();
            
            document.getElementById('barcodeInput').addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    processarBip(this.value.trim());
                    this.value = '';
                }
            });
        });
 
        // Alternância de Ciclo Badge
        function atualizarCicloBadge() {
            const ciclo = document.getElementById('selectCiclo').value;
            const badge = document.getElementById('badge-ciclo');
            badge.innerText = `CICLO ${ciclo}`;
            badge.className = `text-[10px] ${ciclo === 'AM' ? 'bg-amber-500' : 'bg-indigo-600'} text-white px-2.5 py-1 rounded font-mono font-bold shadow-sm`;
        }
 
        // Lógica de Leitura por Bip
        function processarBip(codigo) {
            if (!codigo) return;
 
            const ciclo = document.getElementById('selectCiclo').value;
            const rota = document.getElementById('atribuicaoInput').value.trim() || 'Sem Rota';
            const index = pacotes.findIndex(p => p.id === codigo);
 
            const agora = new Date().toLocaleTimeString('pt-BR', { hour: '2-digit', minute: '2-digit', second: '2-digit' });
 
            if (index === -1) {
                // 1º Bipe: Em Rota
                pacotes.unshift({
                    id: codigo,
                    rota: rota,
                    ciclo: ciclo,
                    status: 'EM_ROTA_DE_ENTREGA',
                    hora: agora,
                    bips: 1
                });
                exibirAlerta(`Pacote ${codigo} adicionado: EM ROTA`, 'sucesso');
            } else {
                // 2º Bipe: Ficou no piso
                pacotes[index].status = 'FICOU_NO_PISO';
                pacotes[index].bips += 1;
                pacotes[index].hora = agora;
                if(rota !== 'Sem Rota') pacotes[index].rota = rota;
                exibirAlerta(`Pacote ${codigo} atualizado: FICOU NO PISO`, 'aviso');
            }
 
            salvarEAtualizar();
        }
 
        // Processar Texto/Print do ML
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
 
                    if (linha.toLowerCase().includes('rota') || linha.toLowerCase().includes('caminho')) {
                        status = 'EM_ROTA_DE_ENTREGA';
                    } else if (linha.toLowerCase().includes('piso') || linha.toLowerCase().includes('retido')) {
                        status = 'FICOU_NO_PISO';
                    } else if (linha.toLowerCase().includes('falha') || linha.toLowerCase().includes('cancelado')) {
                        status = 'FALHA_NA_ENTREGA';
                    }
 
                    const idx = pacotes.findIndex(p => p.id === id);
                    const cicloAtual = document.getElementById('selectCiclo').value;
                    const rotaAtual = document.getElementById('atribuicaoInput').value.trim() || 'ML Import';
 
                    if (idx !== -1) {
                        pacotes[idx].status = status;
                    } else {
                        pacotes.unshift({
                            id: id,
                            rota: rotaAtual,
                            ciclo: cicloAtual,
                            status: status,
                            hora: new Date().toLocaleTimeString('pt-BR', { hour: '2-digit', minute: '2-digit' }),
                            bips: 1
                        });
                    }
                    atualizados++;
                }
            });
 
            document.getElementById('mlTextInput').value = '';
            exibirAlerta(`${atualizados} pacotes reconciliados com sucesso!`, 'sucesso');
            salvarEAtualizar();
        }
 
        // Processar Massa Piso
        function processarMassaPiso() {
            const idsText = document.getElementById('bulkInput').value;
            if (!idsText.trim()) return;
            
            const ids = idsText.split('\n').map(id => id.trim()).filter(id => id !== '');
            const ciclo = document.getElementById('selectCiclo').value;
            const rota = document.getElementById('atribuicaoInput').value.trim() || 'No Piso';
            const agora = new Date().toLocaleTimeString('pt-BR', { hour: '2-digit', minute: '2-digit' });
            let atualizados = 0;
 
            ids.forEach(id => {
                const idx = pacotes.findIndex(p => p.id === id);
                if (idx !== -1) {
                    pacotes[idx].status = 'FICOU_NO_PISO';
                    pacotes[idx].hora = agora;
                } else {
                    pacotes.unshift({
                        id: id,
                        rota: rota,
                        ciclo: ciclo,
                        status: 'FICOU_NO_PISO',
                        hora: agora,
                        bips: 1
                    });
                }
                atualizados++;
            });
 
            document.getElementById('bulkInput').value = '';
            exibirAlerta(`${atualizados} IDs marcados no piso em massa!`, 'aviso');
            salvarEAtualizar();
        }
 
        // Utilitários e Atualizações da Interface
        function exibirAlerta(msg, tipo) {
            const alerta = document.getElementById('feedbackAlerta');
            alerta.innerText = msg;
            
            alerta.className = 'p-3 rounded-lg text-xs font-medium border transition-all shadow-sm';
            if (tipo === 'sucesso') {
                alerta.classList.add('bg-emerald-100', 'text-emerald-700', 'border-emerald-200');
            } else {
                alerta.classList.add('bg-amber-100', 'text-amber-700', 'border-amber-200');
            }
            
            alerta.classList.remove('hidden');
            setTimeout(() => {
                alerta.classList.add('hidden');
            }, 3000);
        }
 
        function salvarEAtualizar() {
            localStorage.setItem('kn_pacotes', JSON.stringify(pacotes));
            renderizarTabela();
            atualizarKPIs();
            renderizarResumoRotas();
            atualizarGraficosSeVisivel();
        }
 
        function renderizarTabela() {
            const filtroTexto = document.getElementById('filtroTexto').value.toLowerCase();
            const filtroStatus = document.getElementById('filtroStatus').value;
            const filtroCiclo = document.getElementById('filtroCiclo').value;
            const tbody = document.getElementById('tabelaHistorico');
            tbody.innerHTML = '';
 
            const filtrados = pacotes.filter(p => {
                const textoMatch = p.id.toLowerCase().includes(filtroTexto) || p.rota.toLowerCase().includes(filtroTexto);
                const statusMatch = filtroStatus === '' || p.status === filtroStatus;
                const cicloMatch = filtroCiclo === '' || p.ciclo === filtroCiclo;
                return textoMatch && statusMatch && cicloMatch;
            });
 
            document.getElementById('contadorBips').innerText = `${filtrados.length} Pacotes`;
 
            filtrados.forEach((p) => {
                // Precisamos do index original no array principal para editar/excluir
                const originalIndex = pacotes.indexOf(p);
                
                let corStatus = 'bg-slate-100 text-slate-600';
                if (p.status === 'EM_ROTA_DE_ENTREGA') corStatus = 'bg-emerald-100 text-emerald-700';
                else if (p.status === 'FICOU_NO_PISO') corStatus = 'bg-amber-100 text-amber-700';
                else if (p.status === 'ENTREGUE') corStatus = 'bg-teal-100 text-teal-700';
                else if (p.status === 'DESPACHAR') corStatus = 'bg-sky-100 text-sky-700';
                else if (p.status === 'FALHA_NA_ENTREGA') corStatus = 'bg-rose-100 text-rose-700';
                else if (p.status === 'SOLUCAO_DE_PROBLEMA') corStatus = 'bg-purple-100 text-purple-700';
 
                let corCiclo = p.ciclo === 'AM' ? 'text-amber-500' : 'text-indigo-500';
 
                tbody.innerHTML += `
                    <tr class="hover:bg-slate-50 transition border-b border-slate-100">
                        <td class="p-3 font-bold text-kn-navy">${p.id}</td>
                        <td class="p-3">${p.rota}</td>
                        <td class="p-3 font-bold ${corCiclo}">${p.ciclo}</td>
                        <td class="p-3">
                            <span class="px-2 py-1 rounded text-[10px] font-bold tracking-wide ${corStatus}">
                                ${p.status.replace(/_/g, ' ')}
                            </span>
                        </td>
                        <td class="p-3 text-slate-500">${p.hora}</td>
                        <td class="p-3 text-right">
                            <button onclick="abrirModalEditar(${originalIndex})" class="p-1.5 text-sky-600 hover:bg-sky-50 rounded transition ml-1" title="Editar"><i data-lucide="edit-2" class="w-4 h-4"></i></button>
                            <button onclick="excluirPacote(${originalIndex})" class="p-1.5 text-rose-600 hover:bg-rose-50 rounded transition ml-1" title="Excluir"><i data-lucide="trash" class="w-4 h-4"></i></button>
                        </td>
                    </tr>
                `;
            });
            lucide.createIcons();
        }
 
        function atualizarKPIs() {
            document.getElementById('kpiTotal').innerText = pacotes.length;
            document.getElementById('kpiDespachar').innerText = pacotes.filter(p => p.status === 'DESPACHAR').length;
            document.getElementById('kpiEmRota').innerText = pacotes.filter(p => p.status === 'EM_ROTA_DE_ENTREGA').length;
            document.getElementById('kpiPiso').innerText = pacotes.filter(p => p.status === 'FICOU_NO_PISO').length;
            document.getElementById('kpiFalha').innerText = pacotes.filter(p => p.status === 'FALHA_NA_ENTREGA').length;
            document.getElementById('kpiSolucao').innerText = pacotes.filter(p => p.status === 'SOLUCAO_DE_PROBLEMA').length;
        }
 
        function renderizarResumoRotas() {
            const tbody = document.getElementById('tabelaRotas');
            tbody.innerHTML = '';
            
            const agrupamento = {};
            pacotes.forEach(p => {
                if (!agrupamento[p.rota]) {
                    agrupamento[p.rota] = { total: 0, emRota: 0, noPiso: 0, despachar: 0, falha: 0 };
                }
                agrupamento[p.rota].total++;
                if (p.status === 'EM_ROTA_DE_ENTREGA') agrupamento[p.rota].emRota++;
                if (p.status === 'FICOU_NO_PISO') agrupamento[p.rota].noPiso++;
                if (p.status === 'DESPACHAR') agrupamento[p.rota].despachar++;
                if (p.status === 'FALHA_NA_ENTREGA') agrupamento[p.rota].falha++;
            });
 
            Object.keys(agrupamento).sort().forEach(rota => {
                const d = agrupamento[rota];
                tbody.innerHTML += `
                    <tr class="hover:bg-slate-50 transition border-b border-slate-100">
                        <td class="p-3 font-bold text-kn-navy">${rota}</td>
                        <td class="p-3 font-semibold">${d.total}</td>
                        <td class="p-3 text-emerald-600 font-semibold">${d.emRota}</td>
                        <td class="p-3 text-amber-600 font-semibold">${d.noPiso}</td>
                        <td class="p-3 text-sky-600 font-semibold">${d.despachar}</td>
                        <td class="p-3 text-rose-600 font-semibold">${d.falha}</td>
                    </tr>
                `;
            });
        }
 
        // Funções da Modal de Edição Manual
        function abrirModalEditar(index) {
            const p = pacotes[index];
            document.getElementById('editIndex').value = index;
            document.getElementById('editId').value = p.id;
            document.getElementById('editRota').value = p.rota;
            document.getElementById('editLog').value = p.log || '';
            document.getElementById('editMotorista').value = p.motorista || '';
            document.getElementById('editEmpresa').value = p.empresa || '';
            document.getElementById('editCiclo').value = p.ciclo;
            document.getElementById('editStatus').value = p.status;
            
            document.getElementById('modalEditar').classList.remove('hidden');
            document.getElementById('modalEditar').classList.add('flex');
        }
 
        function fecharModalEditar() {
            document.getElementById('modalEditar').classList.add('hidden');
            document.getElementById('modalEditar').classList.remove('flex');
        }
 
        function salvarEdicaoManual() {
            const index = document.getElementById('editIndex').value;
            if (index !== '') {
                pacotes[index].rota = document.getElementById('editRota').value || 'Sem Rota';
                pacotes[index].log = document.getElementById('editLog').value.trim();
                pacotes[index].motorista = document.getElementById('editMotorista').value.trim();
                pacotes[index].empresa = document.getElementById('editEmpresa').value.trim();
                pacotes[index].ciclo = document.getElementById('editCiclo').value;
                pacotes[index].status = document.getElementById('editStatus').value;
                
                fecharModalEditar();
                salvarEAtualizar();
            }
        }
 
        function excluirPacote(index) {
            if (confirm('Tem certeza que deseja excluir este pacote do histórico?')) {
                pacotes.splice(index, 1);
                salvarEAtualizar();
            }
        }
 
        // Funções de Utilitários (CSV, Área de Transferência)
        function copiarTodosIDs() {
            const ids = pacotes.map(p => p.id).join('\n');
            if(ids) {
                navigator.clipboard.writeText(ids).then(() => {
                    alert('Todos os IDs copiados para a área de transferência!');
                });
            }
        }
 
        function limparBase() {
            if (confirm('Você está prestes a ZERAR toda a base de dados. Esta ação não pode ser desfeita. Confirmar?')) {
                pacotes = [];
                salvarEAtualizar();
            }
        }
 
        function exportarCSV(tipoCiclo) {
            let dadosExportar = pacotes;
            if (tipoCiclo !== 'TODOS') {
                dadosExportar = pacotes.filter(p => p.ciclo === tipoCiclo);
            }
 
            if (dadosExportar.length === 0) {
                alert('Nenhum dado encontrado para exportar.');
                return;
            }
 
            let csvContent = "data:text/csv;charset=utf-8,ID,ROTA,CICLO,STATUS,HORA\n";
            dadosExportar.forEach(p => {
                csvContent += `${p.id},${p.rota},${p.ciclo},${p.status},${p.hora}\n`;
            });
 
            const encodedUri = encodeURI(csvContent);
            const link = document.createElement("a");
            link.setAttribute("href", encodedUri);
            link.setAttribute("download", `Exportacao_LastMile_${tipoCiclo}.csv`);
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        }
 
        // Navegação de Abas
        function mudarAba(abaDestino) {
            const abas = ['operacao', 'rotas', 'graficos-geral', 'graficos-am', 'graficos-pm'];
            
            abas.forEach(aba => {
                const section = document.getElementById(`aba-${aba}`);
                const btn = document.getElementById(`btn-aba-${aba}`);
                
                if (aba === abaDestino) {
                    section.classList.remove('hidden');
                    btn.classList.add('bg-kn-blue', 'text-white', 'shadow-sm');
                    btn.classList.remove('hover:bg-white/5', 'text-slate-300');
                } else {
                    section.classList.add('hidden');
                    btn.classList.remove('bg-kn-blue', 'text-white', 'shadow-sm');
                    btn.classList.add('hover:bg-white/5', 'text-slate-300');
                }
            });
 
            if (abaDestino.includes('graficos')) {
                atualizarGraficos();
            }
        }
 
        // Atualização Condicional de Gráficos
        function atualizarGraficosSeVisivel() {
            const abasGraficosVisiveis = !document.getElementById('aba-graficos-geral').classList.contains('hidden') ||
                                         !document.getElementById('aba-graficos-am').classList.contains('hidden') ||
                                         !document.getElementById('aba-graficos-pm').classList.contains('hidden');
            if (abasGraficosVisiveis) {
                atualizarGraficos();
            }
        }
 
        // Chart.js Implementação
        function atualizarGraficos() {
            // Destroi os gráficos antigos se existirem para evitar sobreposição
            if (charts.geralStatus) charts.geralStatus.destroy();
            if (charts.geralCiclos) charts.geralCiclos.destroy();
            if (charts.am) charts.am.destroy();
            if (charts.pm) charts.pm.destroy();
 
            const calcularDados = (lista) => [
                lista.filter(p => p.status === 'DESPACHAR').length,
                lista.filter(p => p.status === 'EM_ROTA_DE_ENTREGA').length,
                lista.filter(p => p.status === 'FICOU_NO_PISO').length,
                lista.filter(p => p.status === 'ENTREGUE').length,
                lista.filter(p => p.status === 'FALHA_NA_ENTREGA').length,
                lista.filter(p => p.status === 'SOLUCAO_DE_PROBLEMA').length
            ];
 
            const pacotesAM = pacotes.filter(p => p.ciclo === 'AM');
            const pacotesPM = pacotes.filter(p => p.ciclo === 'PM');
            
            const labelsStatus = ['Despachar', 'Em Rota', 'No Piso', 'Entregue', 'Falha', 'Solução Prob.'];
            const coresStatus = ['#0284c7', '#10b981', '#f59e0b', '#0d9488', '#e11d48', '#9333ea'];
 
            // Gráfico Geral de Status
            const ctxGeral = document.getElementById('chartGeralStatus').getContext('2d');
            charts.geralStatus = new Chart(ctxGeral, {
                type: 'doughnut',
                data: {
                    labels: labelsStatus,
                    datasets: [{
                        data: calcularDados(pacotes),
                        backgroundColor: coresStatus,
                        borderWidth: 0
                    }]
                },
                options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { position: 'right' } } }
            });
 
            // Gráfico de Volume de Ciclos
            const ctxCiclos = document.getElementById('chartGeralCiclos').getContext('2d');
            charts.geralCiclos = new Chart(ctxCiclos, {
                type: 'pie',
                data: {
                    labels: ['Ciclo AM', 'Ciclo PM'],
                    datasets: [{
                        data: [pacotesAM.length, pacotesPM.length],
                        backgroundColor: ['#f59e0b', '#6366f1'],
                        borderWidth: 0
                    }]
                },
                options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { position: 'right' } } }
            });
 
            // Gráfico Ciclo AM
            const ctxAM = document.getElementById('chartAM').getContext('2d');
            charts.am = new Chart(ctxAM, {
                type: 'bar',
                data: {
                    labels: labelsStatus,
                    datasets: [{
                        label: 'Pacotes',
                        data: calcularDados(pacotesAM),
                        backgroundColor: coresStatus,
                        borderWidth: 0
                    }]
                },
                options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { display: false } } }
            });
 
            // Gráfico Ciclo PM
            const ctxPM = document.getElementById('chartPM').getContext('2d');
            charts.pm = new Chart(ctxPM, {
                type: 'bar',
                data: {
                    labels: labelsStatus,
                    datasets: [{
                        label: 'Pacotes',
                        data: calcularDados(pacotesPM),
                        backgroundColor: coresStatus,
                        borderWidth: 0
                    }]
                },
                options: { responsive: true, maintainAspectRatio: false, plugins: { legend: { display: false } } }
            });
        }
    </script>
</body>
</html>
 
