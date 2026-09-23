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

    <!-- ================= SIDEBAR CORPORATIVA ================= -->
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
    </aside>

    <!-- ================= ÁREA DE CONTEÚDO PRINCIPAL ================= -->
    <main class="flex-1 flex flex-col overflow-y-auto bg-slate-50">
        
        <header class="bg-white border-b border-kn-border px-8 py-4 flex flex-wrap items-center justify-between sticky top-0 z-10 shadow-sm gap-4">
            <div>
                <h1 class="text-base font-bold text-kn-navy tracking-tight flex items-center gap-2">
                    <span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span>
                    Automação Pós-Sorting
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

            <!-- CARDS DE KPIS -->
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
                                    <input type="text" id="atribuicaoInput" placeholder="Ex: vb1" class="w-full p-2.5 border border-slate-300 rounded-lg text-xs mt-1 focus:outline-none focus:border-kn-navy bg-slate-50/50">
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
                            <textarea id="mlTextInput" rows="3" placeholder="Cole aqui as linhas/tabela copiadas..." class="w-full p-3 border border-amber-300 rounded-lg font-mono text-xs mt-1 focus:ring-2 focus:ring-amber-500 focus:outline-none bg-white resize-none"></textarea>
                        </div>
                        <button onclick="processarPrintMercadoLivre()" class="w-full bg-amber-600 hover:bg-amber-700 text-white p-2.5 rounded-lg text-xs font-bold transition shadow-sm flex items-center justify-center space-x-2">
                            <i data-lucide="refresh-cw" class="w-4 h-4"></i>
                            <span>Reconciliar Status</span>
                        </button>
                    </div>

                    <!-- Verificação em Massa -->
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-kn-border space-y-4">
                        <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                            <h2 class="text-xs font-bold text-kn-navy uppercase tracking-wider">Marcador em Massa (No Piso)</h2>
                            <i data-lucide="layers" class="w-4 h-4 text-kn-navy"></i>
                        </div>
                        <div>
                            <textarea id="bulkInput" rows="3" placeholder="Cole vários IDs aqui..." class="w-full p-3 border border-slate-300 rounded-lg font-mono text-xs mt-1 focus:ring-2 focus:ring-kn-navy focus:outline-none bg-slate-50/50 resize-none"></textarea>
                        </div>
                        <button onclick="processarMassaPiso()" class="w-full bg-slate-700 hover:bg-slate-800 text-white p-2.5 rounded-lg text-xs font-bold transition shadow-sm flex items-center justify-center space-x-2">
                            <i data-lucide="check-check" class="w-4 h-4"></i>
                            <span>Marcar IDs no Piso</span>
                        </button>
                    </div>
                </div>

                <!-- Tabela de Histórico -->
                <div class="bg-white p-6 rounded-xl shadow-sm border border-kn-border lg:col-span-2 space-y-4">
                    <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                        <div class="flex items-center space-x-3">
                            <h2 class="text-xs font-bold text-kn-navy uppercase tracking-wider">Histórico de Movimentações</h2>
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
                                <option value="ENTREGUE">Entregue</option>
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

            <!-- ABAS DE GRAFICOS (Estrutura mantida para evitar falhas visuais) -->
            <section id="aba-graficos-geral" class="hidden"><div class="p-5 text-center text-slate-500 text-sm">Visualização Gráfica em Breve</div></section>
            <section id="aba-graficos-am" class="hidden"><div class="p-5 text-center text-slate-500 text-sm">Visualização Gráfica AM em Breve</div></section>
            <section id="aba-graficos-pm" class="hidden"><div class="p-5 text-center text-slate-500 text-sm">Visualização Gráfica PM em Breve</div></section>

        </div>
    </main>

    <!-- ================= MODAL DE EDIÇÃO MANUAL ================= -->
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
                <input type="text" id="editRota" class="w-full p-2.5 border border-slate-300 rounded-lg text-xs mt-1 focus:ring-2 focus:ring-kn-navy focus:outline-none">
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
                        <option value="ENTREGUE">ENTREGUE</option>
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

    <!-- ================= SCRIPT ROBUSTO ================= -->
    <script>
        let pacotes = [];
        
        // Bloqueio de segurança 1: Impedir falha de JSON.parse se o cache estiver corrompido
        try {
            const cache = localStorage.getItem('kn_pacotes');
            if (cache) {
                pacotes = JSON.parse(cache);
            }
        } catch(e) {
            console.error("Dados corrompidos no cache foram limpos.", e);
            pacotes = [];
        }

        // Bloqueio de segurança 2: Garantir que Eventos não falhem na inicialização
        document.addEventListener('DOMContentLoaded', () => {
            try { lucide.createIcons(); } catch(e) {}
            atualizarCicloBadge();
            renderizarTabela();
            atualizarKPIs();
            renderizarResumoRotas();
            
            const barcodeInput = document.getElementById('barcodeInput');
            if (barcodeInput) {
                barcodeInput.addEventListener('keydown', function(e) {
                    if (e.key === 'Enter') {
                        e.preventDefault();
                        const val = String(this.value || '').trim();
                        if (val) {
                            processarBip(val);
                            this.value = '';
                        }
                    }
                });
            }
        });

        function salvarNoLocalStorage() {
            localStorage.setItem('kn_pacotes', JSON.stringify(pacotes));
            renderizarTabela();
            atualizarKPIs();
            renderizarResumoRotas();
        }

        // Bloqueio de segurança 3: Conversões para String seguras no processarBip
        function processarBip(codigoRaw) {
            const codigo = String(codigoRaw || '').trim();
            if (!codigo) return;
            
            const atribuicao = document.getElementById('atribuicaoInput').value.trim();
            const ciclo = document.getElementById('selectCiclo').value;
            const horaStr = new Date().toLocaleTimeString('pt-BR');

            const index = pacotes.findIndex(p => String(p.id || '').toUpperCase() === codigo.toUpperCase());

            if (index !== -1) {
                // Segundo Bipe
                pacotes[index].status = 'FICOU_NO_PISO';
                pacotes[index].hora = horaStr;
                pacotes[index].ciclo = ciclo;
                if (atribuicao) pacotes[index].rota = atribuicao;
                mostrarAlerta('Pacote atualizado: FICOU NO PISO', 'warning');
            } else {
                // Primeiro Bipe
                pacotes.push({
                    id: codigo,
                    rota: atribuicao,
                    ciclo: ciclo,
                    status: 'EM_ROTA_DE_ENTREGA',
                    hora: horaStr,
                    dataCriacao: new Date().toISOString()
                });
                mostrarAlerta('Pacote Adicionado: EM ROTA DE ENTREGA', 'success');
            }
            salvarNoLocalStorage();
        }

        // Tratamento da aba e botões
        function mudarAba(abaId) {
            try {
                // Esconde todas as seções
                ['aba-operacao', 'aba-rotas', 'aba-graficos-geral', 'aba-graficos-am', 'aba-graficos-pm'].forEach(id => {
                    const el = document.getElementById(id);
                    if (el) el.classList.add('hidden');
                });
                
                // Remove destaque dos botões
                ['btn-aba-operacao', 'btn-aba-rotas', 'btn-aba-graficos-geral', 'btn-aba-graficos-am', 'btn-aba-graficos-pm'].forEach(id => {
                    const btn = document.getElementById(id);
                    if (btn) {
                        btn.classList.remove('bg-kn-blue', 'text-white', 'shadow-sm');
                        btn.classList.add('text-slate-300', 'hover:bg-white/5');
                    }
                });

                // Mostra aba ativa
                const abaAtiva = document.getElementById(`aba-${abaId}`);
                const btnAtivo = document.getElementById(`btn-aba-${abaId}`);
                
                if (abaAtiva) abaAtiva.classList.remove('hidden');
                
                if (btnAtivo) {
                    btnAtivo.classList.remove('text-slate-300', 'hover:bg-white/5');
                    btnAtivo.classList.add('bg-kn-blue', 'text-white', 'shadow-sm');
                }
            } catch (e) {
                console.error("Erro ao mudar aba:", e);
            }
        }

        function atualizarCicloBadge() {
            const select = document.getElementById('selectCiclo');
            const badge = document.getElementById('badge-ciclo');
            if (!select || !badge) return;
            badge.textContent = `CICLO ${select.value}`;
            if (select.value === 'AM') {
                badge.className = "text-[10px] bg-amber-500 text-white px-2.5 py-1 rounded font-mono font-bold shadow-sm";
            } else {
                badge.className = "text-[10px] bg-indigo-600 text-white px-2.5 py-1 rounded font-mono font-bold shadow-sm";
            }
        }

        function mostrarAlerta(msg, tipo) {
            const alerta = document.getElementById('feedbackAlerta');
            if (!alerta) return;
            alerta.textContent = msg;
            alerta.classList.remove('hidden', 'bg-emerald-50', 'text-emerald-700', 'border-emerald-200', 'bg-amber-50', 'text-amber-700', 'border-amber-200');
            
            if (tipo === 'success') {
                alerta.classList.add('bg-emerald-50', 'text-emerald-700', 'border-emerald-200');
            } else {
                alerta.classList.add('bg-amber-50', 'text-amber-700', 'border-amber-200');
            }
            
            setTimeout(() => { alerta.classList.add('hidden'); }, 3000);
        }

        // Bloqueio de segurança 4: Conversões e proteção de undefinds no Render
        function renderizarTabela() {
            try {
                const tabela = document.getElementById('tabelaHistorico');
                if (!tabela) return;
                
                const filtroTexto = String(document.getElementById('filtroTexto').value || '').toLowerCase();
                const filtroStatus = document.getElementById('filtroStatus').value;
                const filtroCiclo = document.getElementById('filtroCiclo').value;

                let filtrados = pacotes.filter(p => {
                    const idSeguro = String(p.id || '');
                    const rotaSegura = String(p.rota || '');
                    const statusSeguro = String(p.status || '');
                    const cicloSeguro = String(p.ciclo || '');

                    const matchTexto = idSeguro.toLowerCase().includes(filtroTexto) || rotaSegura.toLowerCase().includes(filtroTexto);
                    const matchStatus = filtroStatus === "" || statusSeguro === filtroStatus;
                    const matchCiclo = filtroCiclo === "" || cicloSeguro === filtroCiclo;
                    return matchTexto && matchStatus && matchCiclo;
                });

                tabela.innerHTML = '';
                document.getElementById('contadorBips').textContent = `${filtrados.length} Pacotes`;

                // Renderiza do mais recente pro mais antigo
                [...filtrados].reverse().forEach((p) => {
                    const realIndex = pacotes.findIndex(item => String(item.id) === String(p.id));
                    
                    const tr = document.createElement('tr');
                    tr.className = 'hover:bg-slate-50 transition border-b border-slate-50/50';

                    let statusClass = 'bg-slate-100 text-slate-700';
                    const pStatus = String(p.status || '');
                    if (pStatus === 'EM_ROTA_DE_ENTREGA') statusClass = 'bg-emerald-100 text-emerald-700 border-emerald-200';
                    else if (pStatus === 'FICOU_NO_PISO') statusClass = 'bg-amber-100 text-amber-700 border-amber-200';
                    else if (pStatus === 'FALHA_NA_ENTREGA') statusClass = 'bg-rose-100 text-rose-700 border-rose-200';
                    else if (pStatus === 'SOLUCAO_DE_PROBLEMA') statusClass = 'bg-purple-100 text-purple-700 border-purple-200';
                    else if (pStatus === 'DESPACHAR') statusClass = 'bg-sky-100 text-sky-700 border-sky-200';

                    let cicloClass = String(p.ciclo || '') === 'AM' ? 'text-amber-600 bg-amber-50 border-amber-200' : 'text-indigo-600 bg-indigo-50 border-indigo-200';

                    tr.innerHTML = `
                        <td class="p-3 font-bold text-kn-navy">${String(p.id || '')}</td>
                        <td class="p-3">
                            <span class="bg-slate-100 border border-slate-200 text-slate-600 px-2 py-0.5 rounded text-[10px] font-bold uppercase">${String(p.rota || 'Sem Rota')}</span>
                        </td>
                        <td class="p-3">
                            <span class="border px-2 py-0.5 rounded text-[10px] font-bold uppercase ${cicloClass}">${String(p.ciclo || '')}</span>
                        </td>
                        <td class="p-3">
                            <span class="border px-2 py-1 rounded-md text-[10px] font-bold tracking-wide ${statusClass}">
                                ${pStatus.replace(/_/g, ' ')}
                            </span>
                        </td>
                        <td class="p-3 text-slate-400 text-xs">${String(p.hora || '')}</td>
                        <td class="p-3 text-right">
                            <button onclick="abrirModalEditar(${realIndex})" class="p-1.5 bg-slate-100 text-slate-500 hover:bg-kn-navy hover:text-white rounded transition shadow-sm" title="Editar Manualmente">
                                <i data-lucide="edit-3" class="w-3.5 h-3.5"></i>
                            </button>
                            <button onclick="excluirBip(${realIndex})" class="p-1.5 bg-rose-50 text-rose-500 hover:bg-rose-500 hover:text-white rounded transition ml-1 shadow-sm" title="Remover">
                                <i data-lucide="trash-2" class="w-3.5 h-3.5"></i>
                            </button>
                        </td>
                    `;
                    tabela.appendChild(tr);
                });
                lucide.createIcons();
            } catch(e) {
                console.error("Erro ao renderizar tabela", e);
            }
        }

        // Funções de Modal e Edição
        function abrirModalEditar(index) {
            const p = pacotes[index];
            if (!p) return;

            document.getElementById('editIndex').value = index;
            document.getElementById('editId').value = String(p.id || '');
            document.getElementById('editRota').value = String(p.rota || '');
            document.getElementById('editCiclo').value = String(p.ciclo || 'AM');
            document.getElementById('editStatusPara resolver os erros ao adicionar IDs, editar manualmente e navegar pelas abas, preciso analisar a estrutura do código ou as fórmulas que controlam essas funções. 

As capturas de tela mostram a interface do painel "KUEHNE+NAGEL CONTROL TOWER" com o menu de navegação[cite: 2] e a tela de "Bipagem Inteligente" com o campo de código de barras e seleção de ciclo[cite: 1], mas não expõem a lógica por trás do sistema. Quando outras abas param de responder de repente, isso frequentemente indica um erro sintático no script principal (como no JavaScript) que "quebra" a execução da página inteira, impedindo o funcionamento das rotinas de edição manual, inserção de IDs e dos links de navegação[cite: 1, 2].

Por favor, forneça as seguintes informações para que eu possa gerar a correção exata:

*   **Código Fonte:** Cole o trecho do código (HTML/JavaScript, configuração do AppSheet ou script) responsável pelo input "CÓDIGO DE BARRAS"[cite: 1] e pela estrutura do menu lateral[cite: 2].
*   **Console de Erros:** Caso a aplicação esteja rodando em um navegador, pressione F12, acesse a aba "Console" e verifique se há alguma mensagem de erro sendo exibida ao tentar bipar um código ou clicar em uma das abas que não estão funcionando.

Qual é a tecnologia específica ou plataforma (ex: HTML/JS, AppSheet) que você está editando no momento para que eu envie o código formatado na linguagem correta?
