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
            const ids = document.getElementById('bulkInput').value.split('\n').map(i => i.trim()).filter(Boolean);
            if (ids.length === 0) return;

            const cicloAtual = document.getElementById('selectCiclo').value;
            let alterados = 0;

            ids.forEach(id => {
                const idx = pacotes.findIndex(p => p.id === id);
                if (idx !== -1) {
                    pacotes[idx].status = 'FICOU_NO_PISO';
                } else {
                    pacotes.unshift({
                        id: id,
                        rota: 'Massa Piso',
                        ciclo: cicloAtual,
                        status: 'FICOU_NO_PISO',
                        hora: new Date().toLocaleTimeString('pt-BR', { hour: '2-digit', minute: '2-digit' }),
                        bips: 1
                    });
                }
                alterados++;
            });

            document.getElementById('bulkInput').value = '';
            exibirAlerta(`${alterados} pacotes marcados como FICOU NO PISO!`, 'aviso');
            salvarEAtualizar();
        }

        // ================= EDIÇÃO MANUAL (MODAL) =================
        function abrirModalEditar(index) {
            const item = pacotes[index];
            document.getElementById('editIndex').value = index;
            document.getElementById('editId').value = item.id;
            document.getElementById('editRota').value = item.rota;
            document.getElementById('editCiclo').value = item.ciclo;
            document.getElementById('editStatus').value = item.status;

            document.getElementById('modalEditar').classList.remove('hidden');
            document.getElementById('modalEditar').classList.add('flex');
        }

        function fecharModalEditar() {
            document.getElementById('modalEditar').classList.add('hidden');
            document.getElementById('modalEditar').classList.remove('flex');
        }

        function salvarEdicaoManual() {
            const index = document.getElementById('editIndex').value;
            if (index === '' || index === null) return;

            // Atualiza os dados manualmente fornecidos
            pacotes[index].rota = document.getElementById('editRota').value.trim() || 'Sem Rota';
            pacotes[index].ciclo = document.getElementById('editCiclo').value;
            pacotes[index].status = document.getElementById('editStatus').value;

            fecharModalEditar();
            exibirAlerta(`Pacote ${pacotes[index].id} alterado manualmente com sucesso!`, 'sucesso');
            salvarEAtualizar();
        }

        function excluirPacote(index) {
            if (confirm('Deseja realmente remover este pacote?')) {
                pacotes.splice(index, 1);
                salvarEAtualizar();
            }
        }

        // Renderização e Atualização UI
        function salvarEAtualizar() {
            localStorage.setItem('kn_pacotes', JSON.stringify(pacotes));
            renderizarTabela();
            atualizarKPIs();
            renderizarResumoRotas();
            if (document.getElementById('aba-graficos-geral').classList.contains('hidden') === false) renderizarGraficos();
        }

        function renderizarTabela() {
            const tbody = document.getElementById('tabelaHistorico');
            const filtroTexto = document.getElementById('filtroTexto').value.toLowerCase();
            const filtroStatus = document.getElementById('filtroStatus').value;
            const filtroCiclo = document.getElementById('filtroCiclo').value;

            tbody.innerHTML = '';

            const filtrados = pacotes.filter(p => {
                const matchTexto = p.id.toLowerCase().includes(filtroTexto) || p.rota.toLowerCase().includes(filtroTexto);
                const matchStatus = !filtroStatus || p.status === filtroStatus;
                const matchCiclo = !filtroCiclo || p.ciclo === filtroCiclo;
                return matchTexto && matchStatus && matchCiclo;
            });

            document.getElementById('contadorBips').innerText = `${filtrados.length} Pacotes`;

            filtrados.forEach((item, index) => {
                const realIndex = pacotes.indexOf(item);
                const tr = document.createElement('tr');
                tr.className = 'hover:bg-slate-50 transition border-b border-slate-100';

                tr.innerHTML = `
                    <td class="p-3 font-bold text-slate-800">${item.id}</td>
                    <td class="p-3 text-slate-600">${item.rota}</td>
                    <td class="p-3 font-bold">
                        <span class="px-2 py-0.5 rounded text-[10px] ${item.ciclo === 'AM' ? 'bg-amber-100 text-amber-800' : 'bg-indigo-100 text-indigo-800'}">
                            ${item.ciclo}
                        </span>
                    </td>
                    <td class="p-3">${getBadgeStatus(item.status)}</td>
                    <td class="p-3 text-slate-400 text-[11px]">${item.hora}</td>
                    <td class="p-3 text-right space-x-1">
                        <button onclick="abrirModalEditar(${realIndex})" title="Editar Manualmente Rota, Ciclo ou Status" class="p-1 text-slate-500 hover:text-kn-navy hover:bg-slate-200 rounded transition">
                            <i data-lucide="edit-3" class="w-4 h-4"></i>
                        </button>
                        <button onclick="excluirPacote(${realIndex})" title="Excluir" class="p-1 text-slate-400 hover:text-rose-600 hover:bg-rose-50 rounded transition">
                            <i data-lucide="trash-2" class="w-4 h-4"></i>
                        </button>
                    </td>
                `;
                tbody.appendChild(tr);
            });

            lucide.createIcons();
        }

        function getBadgeStatus(status) {
            const mapa = {
                'DESPACHAR': '<span class="bg-sky-100 text-sky-800 px-2 py-0.5 rounded text-[10px] font-bold">DESPACHAR</span>',
                'EM_ROTA_DE_ENTREGA': '<span class="bg-emerald-100 text-emerald-800 px-2 py-0.5 rounded text-[10px] font-bold">EM ROTA</span>',
                'FICOU_NO_PISO': '<span class="bg-amber-100 text-amber-800 px-2 py-0.5 rounded text-[10px] font-bold">NO PISO</span>',
                'FALHA_NA_ENTREGA': '<span class="bg-rose-100 text-rose-800 px-2 py-0.5 rounded text-[10px] font-bold">FALHA</span>',
                'SOLUCAO_DE_PROBLEMA': '<span class="bg-purple-100 text-purple-800 px-2 py-0.5 rounded text-[10px] font-bold">SOLUÇÃO PROB.</span>',
                'NULO': '<span class="bg-slate-200 text-slate-700 px-2 py-0.5 rounded text-[10px] font-bold">NULO</span>'
            };
            return mapa[status] || `<span class="bg-slate-100 text-slate-600 px-2 py-0.5 rounded text-[10px]">${status}</span>`;
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

            const rotasMap = {};
            pacotes.forEach(p => {
                const r = p.rota || 'Sem Rota';
                if (!rotasMap[r]) {
                    rotasMap[r] = { total: 0, emRota: 0, piso: 0, despachar: 0, falha: 0 };
                }
                rotasMap[r].total++;
                if (p.status === 'EM_ROTA_DE_ENTREGA') rotasMap[r].emRota++;
                if (p.status === 'FICOU_NO_PISO') rotasMap[r].piso++;
                if (p.status === 'DESPACHAR') rotasMap[r].despachar++;
                if (p.status === 'FALHA_NA_ENTREGA') rotasMap[r].falha++;
            });

            Object.keys(rotasMap).forEach(rota => {
                const d = rotasMap[rota];
                const tr = document.createElement('tr');
                tr.className = 'border-b border-slate-100 hover:bg-slate-50';
                tr.innerHTML = `
                    <td class="p-3 font-bold text-slate-800">${rota}</td>
                    <td class="p-3">${d.total}</td>
                    <td class="p-3 text-emerald-600 font-bold">${d.emRota}</td>
                    <td class="p-3 text-amber-600 font-bold">${d.piso}</td>
                    <td class="p-3 text-sky-600 font-bold">${d.despachar}</td>
                    <td class="p-3 text-rose-600 font-bold">${d.falha}</td>
                `;
                tbody.appendChild(tr);
            });
        }

        // Alternar Navegação entre Abas
        function mudarAba(abaId) {
            ['operacao', 'rotas', 'graficos-geral', 'graficos-am', 'graficos-pm'].forEach(id => {
                const sec = document.getElementById(`aba-${id}`);
                const btn = document.getElementById(`btn-aba-${id}`);
                if (sec) sec.classList.add('hidden');
                if (btn) {
                    btn.classList.remove('bg-kn-blue', 'text-white');
                    btn.classList.add('text-slate-300', 'hover:bg-white/5');
                }
            });

            document.getElementById(`aba-${abaId}`).classList.remove('hidden');
            const activeBtn = document.getElementById(`btn-aba-${abaId}`);
            if (activeBtn) {
                activeBtn.classList.add('bg-kn-blue', 'text-white');
                activeBtn.classList.remove('text-slate-300', 'hover:bg-white/5');
            }

            if (abaId.startsWith('graficos')) {
                renderizarGraficos();
            }
        }

        // Gráficos Chart.js
        function renderizarGraficos() {
            const ctxGeral = document.getElementById('chartGeralStatus').getContext('2d');
            const ctxCiclos = document.getElementById('chartGeralCiclos').getContext('2d');
            const ctxAM = document.getElementById('chartAM').getContext('2d');
            const ctxPM = document.getElementById('chartPM').getContext('2d');

            if (charts.geral) charts.geral.destroy();
            if (charts.ciclos) charts.ciclos.destroy();
            if (charts.am) charts.am.destroy();
            if (charts.pm) charts.pm.destroy();

            const countStatus = (lista, st) => lista.filter(p => p.status === st).length;

            charts.geral = new Chart(ctxGeral, {
                type: 'doughnut',
                data: {
                    labels: ['Em Rota', 'No Piso', 'Despachar', 'Falha'],
                    datasets: [{
                        data: [
                            countStatus(pacotes, 'EM_ROTA_DE_ENTREGA'),
                            countStatus(pacotes, 'FICOU_NO_PISO'),
                            countStatus(pacotes, 'DESPACHAR'),
                            countStatus(pacotes, 'FALHA_NA_ENTREGA')
                        ],
                        backgroundColor: ['#10B981', '#F59E0B', '#0EA5E9', '#EF4444']
                    }]
                }
            });

            charts.ciclos = new Chart(ctxCiclos, {
                type: 'bar',
                data: {
                    labels: ['AM', 'PM'],
                    datasets: [{
                        label: 'Volume por Ciclo',
                        data: [
                            pacotes.filter(p => p.ciclo === 'AM').length,
                            pacotes.filter(p => p.ciclo === 'PM').length
                        ],
                        backgroundColor: ['#F59E0B', '#6366F1']
                    }]
                }
            });

            const amList = pacotes.filter(p => p.ciclo === 'AM');
            charts.am = new Chart(ctxAM, {
                type: 'bar',
                data: {
                    labels: ['Em Rota', 'No Piso', 'Despachar', 'Falha'],
                    datasets: [{
                        label: 'Ciclo AM',
                        data: [countStatus(amList, 'EM_ROTA_DE_ENTREGA'), countStatus(amList, 'FICOU_NO_PISO'), countStatus(amList, 'DESPACHAR'), countStatus(amList, 'FALHA_NA_ENTREGA')],
                        backgroundColor: '#F59E0B'
                    }]
                }
            });

            const pmList = pacotes.filter(p => p.ciclo === 'PM');
            charts.pm = new Chart(ctxPM, {
                type: 'bar',
                data: {
                    labels: ['Em Rota', 'No Piso', 'Despachar', 'Falha'],
                    datasets: [{
                        label: 'Ciclo PM',
                        data: [countStatus(pmList, 'EM_ROTA_DE_ENTREGA'), countStatus(pmList, 'FICOU_NO_PISO'), countStatus(pmList, 'DESPACHAR'), countStatus(pmList, 'FALHA_NA_ENTREGA')],
                        backgroundColor: '#6366F1'
                    }]
                }
            });
        }

        // Utilitários de Cópia e Exportação CSV
        function copiarTodosIDs() {
            if (pacotes.length === 0) return alert('Nenhum pacote registrado.');
            const text = pacotes.map(p => p.id).join('\n');
            navigator.clipboard.writeText(text).then(() => {
                exibirAlerta('Todos os IDs foram copiados para a área de transferência!', 'sucesso');
            });
        }

        function exportarCSV(filtroCiclo) {
            let dados = pacotes;
            if (filtroCiclo !== 'TODOS') {
                dados = pacotes.filter(p => p.ciclo === filtroCiclo);
            }

            if (dados.length === 0) return alert('Nenhum dado encontrado para exportação.');

            let csv = 'ID,Rota,Ciclo,Status,Hora\n';
            dados.forEach(p => {
                csv += `"${p.id}","${p.rota}","${p.ciclo}","${p.status}","${p.hora}"\n`;
            });

            const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
            const link = document.createElement('a');
            link.href = URL.createObjectURL(blob);
            link.download = `KN_Relatorio_${filtroCiclo}_${new Date().toISOString().slice(0, 10)}.csv`;
            link.click();
        }

        function limparBase() {
            if (confirm('Tem certeza de que deseja apagar TODOS os registros salvos?')) {
                pacotes = [];
                salvarEAtualizar();
                exibirAlerta('Base de dados zerada com sucesso.', 'aviso');
            }
        }

        function exibirAlerta(msg, tipo) {
            const el = document.getElementById('feedbackAlerta');
            el.innerText = msg;
            el.classList.remove('hidden', 'bg-emerald-50', 'text-emerald-800', 'border-emerald-200', 'bg-amber-50', 'text-amber-800', 'border-amber-200');

            if (tipo === 'sucesso') {
                el.classList.add('bg-emerald-50', 'text-emerald-800', 'border-emerald-200');
            } else {
                el.classList.add('bg-amber-50', 'text-amber-800', 'border-amber-200');
            }

            setTimeout(() => el.classList.add('hidden'), 3500);
        }
    </script>
</body>
</html>
