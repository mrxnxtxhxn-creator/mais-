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
                <button onclick="toggleMenuLateral()" class="p-1.5 hover:bg-white/10 rounded transition text-slate-300 hover:text-white">
                    <i data-lucide="menu" class="w-5 h-5"></i>
                </button>
            </div>

            <!-- Navegação Enterprise -->
            <nav id="nav-menu" class="p-3 space-y-1.5 text-xs overflow-y-auto flex-1">
                <div class="text-[9px] text-slate-400 font-bold uppercase tracking-wider px-3 pb-1 pt-2">Operação Last Mile</div>
                
                <button onclick="mudarAba('operacao')" id="btn-aba-operacao" class="w-full flex items-center space-x-3 p-3 rounded-lg bg-kn-blue text-white transition shadow-sm font-medium">
                    <i data-lucide="scan-barcode" class="w-4 h-4"></i>
                    <span>Bipagem Inteligente</span>
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
            <span class="text-[9px] text-slate-400">Logistics Systems v2.5</span>
        </div>
    </aside>

    <!-- ================= ÁREA DE CONTEÚDO PRINCIPAL ================= -->
    <main class="flex-1 flex flex-col overflow-y-auto bg-slate-50">
        
        <!-- Header Superior -->
        <header class="bg-white border-b border-kn-border px-8 py-4 flex items-center justify-between sticky top-0 z-10 shadow-sm">
            <div>
                <h1 class="text-base font-bold text-kn-navy tracking-tight flex items-center gap-2">
                    <span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span>
                    Automação de Reconciliação Pós-Sorting
                </h1>
                <p class="text-xs text-slate-500">Módulo de controle integrado Last Mile</p>
            </div>
            
            <div class="flex items-center space-x-3">
                <button onclick="exportarCSV()" class="border border-kn-border hover:border-kn-navy text-kn-navy bg-white hover:bg-slate-50 px-3.5 py-2 rounded-lg text-xs font-semibold flex items-center space-x-2 transition shadow-sm">
                    <i data-lucide="download" class="w-3.5 h-3.5"></i>
                    <span>Exportar Relatório CSV</span>
                </button>
                <button onclick="limparBase()" class="bg-white border border-rose-200 text-rose-600 hover:bg-rose-50 px-3.5 py-2 rounded-lg text-xs font-semibold flex items-center space-x-2 transition shadow-sm">
                    <i data-lucide="trash-2" class="w-3.5 h-3.5"></i>
                    <span>Zerar Dados</span>
                </button>
            </div>
        </header>

        <div class="p-8 space-y-6 max-w-7xl mx-auto w-full">

            <!-- CARDS DE KPIS EXECUTIVOS -->
            <div class="grid grid-cols-1 md:grid-cols-4 gap-4">
                <div class="bg-white p-5 rounded-xl shadow-sm border border-kn-border border-l-4 border-l-kn-navy">
                    <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider">Total Processado</span>
                    <div id="kpiTotal" class="text-2xl font-black text-slate-800 mt-1">0</div>
                </div>
                <div class="bg-white p-5 rounded-xl shadow-sm border border-kn-border border-l-4 border-l-sky-500">
                    <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider">Volume AM / PM</span>
                    <div id="kpiCiclos" class="text-2xl font-black text-slate-800 mt-1">0 / 0</div>
                </div>
                <div class="bg-white p-5 rounded-xl shadow-sm border border-kn-border border-l-4 border-l-amber-500">
                    <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider">Retido no Piso</span>
                    <div id="kpiPiso" class="text-2xl font-black text-amber-600 mt-1">0</div>
                </div>
                <div class="bg-white p-5 rounded-xl shadow-sm border border-kn-border border-l-4 border-l-emerald-500">
                    <span class="text-[10px] font-bold text-slate-400 uppercase tracking-wider">Saiu para Entrega</span>
                    <div id="kpiSaida" class="text-2xl font-black text-emerald-600 mt-1">0</div>
                </div>
            </div>

            <!-- ================= ABA 1: BIPAGEM INTELIGENTE ================= -->
            <section id="aba-operacao" class="grid grid-cols-1 lg:grid-cols-3 gap-6 fade-in">
                
                <!-- Coluna Esquerda: Leitor Óptico + Verificação em Massa -->
                <div class="space-y-6">
                    <!-- Caixa de Leitura / Input Individual -->
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-kn-border space-y-5">
                        <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                            <h2 class="text-xs font-bold text-kn-navy uppercase tracking-wider">Leitor Óptico</h2>
                            <span id="badge-ciclo" class="text-[10px] bg-kn-navy text-white px-2.5 py-1 rounded font-mono font-bold shadow-sm">CICLO AM</span>
                        </div>

                        <!-- Alerta de Feedback Dinâmico -->
                        <div id="feedbackAlerta" class="hidden p-3 rounded-lg text-xs font-medium border transition-all shadow-sm"></div>

                        <div class="space-y-4">
                            <div>
                                <label class="text-xs font-semibold text-slate-600 uppercase tracking-wide">Código de Barras</label>
                                <div class="mt-1">
                                    <input type="text" id="barcodeInput" autofocus placeholder="Aguardando leitura..." class="w-full p-3 border border-slate-300 rounded-lg font-mono text-sm focus:ring-2 focus:ring-kn-navy focus:border-kn-navy focus:outline-none bg-slate-50/50">
                                </div>
                                <span class="text-[11px] text-slate-400 mt-1.5 block leading-tight">⚡ 1º Bipe: Sai para Rota | 2º Bipe (Repetido): Fica no Piso</span>
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

                    <!-- Verificação em Massa (Piso) -->
                    <div class="bg-white p-6 rounded-xl shadow-sm border border-kn-border space-y-4">
                        <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                            <h2 class="text-xs font-bold text-kn-navy uppercase tracking-wider">Verificação em Massa (Piso)</h2>
                            <i data-lucide="layers" class="w-4 h-4 text-kn-navy"></i>
                        </div>
                        <div>
                            <label class="text-xs font-semibold text-slate-600 uppercase tracking-wide">Cole os IDs (um por linha)</label>
                            <textarea id="bulkInput" rows="4" placeholder="Cole vários IDs aqui...&#10;Ex: ID001&#10;ID002" class="w-full p-3 border border-slate-300 rounded-lg font-mono text-xs mt-1 focus:ring-2 focus:ring-kn-navy focus:outline-none bg-slate-50/50 resize-none"></textarea>
                            <span class="text-[10px] text-slate-400 mt-1 block">Muda automaticamente para "Ficou no Piso" em qualquer ciclo (AM/PM).</span>
                        </div>
                        <button onclick="processarMassaPiso()" class="w-full bg-amber-600 hover:bg-amber-700 text-white p-2.5 rounded-lg text-xs font-bold transition shadow-sm flex items-center justify-center space-x-2">
                            <i data-lucide="check-check" class="w-4 h-4"></i>
                            <span>Marcar IDs no Piso em Massa</span>
                        </button>
                    </div>
                </div>

                <!-- Tabela de Histórico e Filtros -->
                <div class="bg-white p-6 rounded-xl shadow-sm border border-kn-border lg:col-span-2 space-y-4">
                    <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                        <h2 class="text-xs font-bold text-kn-navy uppercase tracking-wider">Histórico de Movimentações</h2>
                        <span id="contadorBips" class="text-xs font-semibold bg-slate-100 text-kn-navy px-3 py-1 rounded-full border border-slate-200">0 Pacotes</span>
                    </div>

                    <!-- Barra de Filtros Avançados -->
                    <div class="grid grid-cols-1 sm:grid-cols-3 gap-3 bg-slate-50 p-3 rounded-lg border border-slate-200">
                        <div>
                            <label class="text-[10px] font-bold text-slate-500 uppercase">Filtrar por ID / Rota</label>
                            <input type="text" id="filtroTexto" onkeyup="aplicarFiltros()" placeholder="Pesquisar..." class="w-full mt-1 p-2 bg-white border border-slate-300 rounded-md text-xs focus:outline-none focus:border-kn-navy">
                        </div>
                        <div>
                            <label class="text-[10px] font-bold text-slate-500 uppercase">Status</label>
                            <select id="filtroStatus" onchange="aplicarFiltros()" class="w-full mt-1 p-2 bg-white border border-slate-300 rounded-md text-xs focus:outline-none focus:border-kn-navy font-medium">
                                <option value="">Todos os Status</option>
                                <option value="SAIU_PARA_ENTREGA">Saída para Entrega</option>
                                <option value="FICOU_NO_PISO">Ficou no Piso</option>
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

                    <div class="overflow-x-auto max-h-[360px]">
                        <table class="w-full text-xs text-left text-slate-600">
                            <thead class="text-[10px] text-kn-navy uppercase bg-slate-50 border-b border-slate-200 sticky top-0 font-bold">
                                <tr>
                                    <th class="px-4 py-3">Código de Barras</th>
                                    <th class="px-4 py-3">Ciclo</th>
                                    <th class="px-4 py-3">Atribuição</th>
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

            <!-- ================= ABA 2: GRÁFICOS GERAL (Comparativo) ================= -->
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

            <!-- ================= ABA 3: GRÁFICOS AM ================= -->
            <section id="aba-graficos-am" class="hidden space-y-6 fade-in">
                <div class="bg-white p-6 rounded-xl shadow-sm border border-kn-border">
                    <h2 class="text-xs font-bold text-kn-navy uppercase tracking-wider border-b border-slate-100 pb-3 mb-4">
                        Analytics Operacional - Ciclo AM
                    </h2>
                    <div class="relative h-96 w-full">
                        <canvas id="graficoAM"></canvas>
                    </div>
                </div>
            </section>

            <!-- ================= ABA 4: GRÁFICOS PM ================= -->
            <section id="aba-graficos-pm" class="hidden space-y-6 fade-in">
                <div class="bg-white p-6 rounded-xl shadow-sm border border-kn-border">
                    <h2 class="text-xs font-bold text-kn-navy uppercase tracking-wider border-b border-slate-100 pb-3 mb-4">
                        Analytics Operacional - Ciclo PM
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

    <!-- ================= SCRIPTS ================= -->
    <script>
        lucide.createIcons();
        
        const STORAGE_KEY = 'kn_logistica_dados';
        let dadosOperacao = carregardados();
        
        let chartAM = null;
        let chartPM = null;
        let chartGeral = null;

        window.onload = function() {
            aplicarFiltros();
            atualizarKPIs();
            document.getElementById('barcodeInput').focus();
        };

        function toggleMenuLateral() {
            const navMenu = document.getElementById('nav-menu');
            navMenu.classList.toggle('hidden');
        }

        function mudarAba(abaSelecionada) {
            const abas = ['operacao', 'graficos-geral', 'graficos-am', 'graficos-pm'];
            
            abas.forEach(aba => {
                document.getElementById('aba-' + aba).classList.add('hidden');
                const btn = document.getElementById('btn-aba-' + aba);
                btn.classList.remove('bg-kn-blue', 'text-white', 'shadow-sm');
                btn.classList.add('hover:bg-white/5', 'text-slate-300');
            });

            document.getElementById('aba-' + abaSelecionada).classList.remove('hidden');
            const btnAtivo = document.getElementById('btn-aba-' + abaSelecionada);
            btnAtivo.classList.add('bg-kn-blue', 'text-white', 'shadow-sm');
            btnAtivo.classList.remove('hover:bg-white/5', 'text-slate-300');

            if (abaSelecionada.includes('graficos')) {
                setTimeout(renderizarGraficos, 50); 
            } else {
                document.getElementById('barcodeInput').focus();
            }
        }

        function salvardados() {
            localStorage.setItem(STORAGE_KEY, JSON.stringify(dadosOperacao));
            atualizarKPIs();
            renderizarGraficos(); 
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
            alerta.classList.remove('hidden', 'bg-emerald-50', 'border-emerald-200', 'text-emerald-800', 'bg-amber-50', 'border-amber-200', 'text-amber-800');
            
            if (tipo === 'success') {
                alerta.classList.add('bg-emerald-50', 'border-emerald-200', 'text-emerald-800');
            } else {
                alerta.classList.add('bg-amber-50', 'border-amber-200', 'text-amber-800');
            }
            alerta.innerText = mensagem;

            setTimeout(() => {
                alerta.classList.add('hidden');
            }, 3500);
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
                    status: 'SAIU_PARA_ENTREGA',
                    hora: new Date().toLocaleTimeString('pt-BR'),
                    data: new Date().toLocaleDateString('pt-BR')
                };
                dadosOperacao.unshift(novoItem);
                mostrarAlerta(`✅ [${ciclo}] ${barcode} -> SAIU PARA ENTREGA`, 'success');
            } else {
                itemExistente.status = 'FICOU_NO_PISO';
                itemExistente.hora = new Date().toLocaleTimeString('pt-BR');
                if (atribuicao !== 'Sem Rota') {
                    itemExistente.atribuicao = atribuicao;
                }
                mostrarAlerta(`⚠️ [${ciclo}] ID repetido! Atualizado para -> FICOU NO PISO`, 'warning');
            }

            salvardados();
            aplicarFiltros();

            input.value = '';
            input.focus();
        }

        function processarMassaPiso() {
            const textarea = document.getElementById('bulkInput');
            const linhas = textarea.value.split('\n').map(l => l.trim()).filter(l => l.length > 0);
            
            if (linhas.length === 0) {
                alert("Cole pelo menos um ID para processar.");
                return;
            }

            let alterados = 0;
            linhas.forEach(barcode => {
                // Atualiza em qualquer ciclo (AM ou PM) onde o ID for encontrado
                let itensEncontrados = dadosOperacao.filter(d => d.barcode === barcode);
                itensEncontrados.forEach(item => {
                    item.status = 'FICOU_NO_PISO';
                    item.hora = new Date().toLocaleTimeString('pt-BR');
                    alterados++;
                });
            });

            salvardados();
            aplicarFiltros();
            textarea.value = '';
            mostrarAlerta(`⚙️ ${alterados} registro(s) atualizado(s) para 'Ficou no Piso' em massa.`, 'warning');
        }

        function aplicarFiltros() {
            const texto = document.getElementById('filtroTexto').value.toLowerCase();
            const statusFiltro = document.getElementById('filtroStatus').value;
            const cicloFiltro = document.getElementById('filtroCiclo').value;

            let filtrados = dadosOperacao.filter(item => {
                const matchTexto = item.barcode.toLowerCase().includes(texto) || item.atribuicao.toLowerCase().includes(texto);
                const matchStatus = !statusFiltro || item.status === statusFiltro;
                const matchCiclo = !cicloFiltro || item.ciclo === cicloFiltro;
                return matchTexto && matchStatus && matchCiclo;
            });

            renderizarTabela(filtrados);
        }

        function renderizarTabela(lista) {
            const tbody = document.getElementById('tabelaBips');
            document.getElementById('contadorBips').innerText = `${lista.length} Registros Exibidos`;

            if (lista.length === 0) {
                tbody.innerHTML = `<tr><td colspan="5" class="text-center py-10 text-slate-400 font-medium">Nenhum registro encontrado com esses filtros.</td></tr>`;
                return;
            }

            tbody.innerHTML = lista.map(item => `
                <tr class="hover:bg-slate-50/80 font-mono border-b border-slate-100 transition">
                    <td class="px-4 py-3 font-bold text-slate-800">${item.barcode}</td>
                    <td class="px-4 py-3"><span class="px-2 py-0.5 text-[10px] rounded font-semibold ${item.ciclo === 'AM' ? 'bg-sky-100 text-sky-900' : 'bg-indigo-100 text-indigo-900'}">${item.ciclo}</span></td>
                    <td class="px-4 py-3 text-slate-600 font-sans">${item.atribuicao}</td>
                    <td class="px-4 py-3 font-sans">
                        <span class="px-2 py-1 text-[10px] rounded font-bold ${item.status === 'SAIU_PARA_ENTREGA' ? 'bg-emerald-100 text-emerald-800' : 'bg-amber-100 text-amber-800'}">
                            ${item.status === 'SAIU_PARA_ENTREGA' ? 'SAÍDA' : 'PISO'}
                        </span>
                    </td>
                    <td class="px-4 py-3 text-slate-400 font-sans">${item.hora}</td>
                </tr>
            `).join('');
        }

        function atualizarKPIs() {
            const total = dadosOperacao.length;
            const am = dadosOperacao.filter(d => d.ciclo === 'AM').length;
            const pm = dadosOperacao.filter(d => d.ciclo === 'PM').length;
            const piso = dadosOperacao.filter(d => d.status === 'FICOU_NO_PISO').length;
            const saida = dadosOperacao.filter(d => d.status === 'SAIU_PARA_ENTREGA').length;

            document.getElementById('kpiTotal').innerText = total;
            document.getElementById('kpiCiclos').innerText = `${am} / ${pm}`;
            document.getElementById('kpiPiso').innerText = piso;
            document.getElementById('kpiSaida').innerText = saida;
        }

        function limparBase() {
            if (confirm("Tem certeza que deseja apagar todos os registros da memória local?")) {
                localStorage.removeItem(STORAGE_KEY);
                dadosOperacao = [];
                aplicarFiltros();
                atualizarKPIs();
                renderizarGraficos();
                document.getElementById('barcodeInput').focus();
            }
        }

        function exportarCSV() {
            if (dadosOperacao.length === 0) {
                alert("Não há dados para exportar.");
                return;
            }

            let csv = 'CodigoDeBarras;Ciclo;Atribuicao;Status;Hora;Data\n';
            dadosOperacao.forEach(item => {
                csv += `${item.barcode};${item.ciclo};${item.atribuicao};${item.status};${item.hora};${item.data}\n`;
            });

            const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
            const link = document.createElement('a');
            link.href = URL.createObjectURL(blob);
            link.setAttribute('download', `Relatorio_Logistica_KN_${new Date().toISOString().slice(0,10)}.csv`);
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        }

        function renderizarGraficos() {
            const amTotal = dadosOperacao.filter(d => d.ciclo === 'AM').length;
            const amSaida = dadosOperacao.filter(d => d.ciclo === 'AM' && d.status === 'SAIU_PARA_ENTREGA').length;
            const amPiso = dadosOperacao.filter(d => d.ciclo === 'AM' && d.status === 'FICOU_NO_PISO').length;

            const pmTotal = dadosOperacao.filter(d => d.ciclo === 'PM').length;
            const pmSaida = dadosOperacao.filter(d => d.ciclo === 'PM' && d.status === 'SAIU_PARA_ENTREGA').length;
            const pmPiso = dadosOperacao.filter(d => d.ciclo === 'PM' && d.status === 'FICOU_NO_PISO').length;

            const cores = { total: '#003366', saida: '#10B981', piso: '#F59E0B' };

            const canvasGeral = document.getElementById('graficoGeral');
            if (canvasGeral) {
                const ctxGeral = canvasGeral.getContext('2d');
                if (chartGeral) chartGeral.destroy();
                chartGeral = new Chart(ctxGeral, {
                    type: 'bar',
                    data: {
                        labels: ['Total Lidos', 'Saíram pra Entrega', 'Ficaram no Piso'],
                        datasets: [
                            { label: 'Ciclo AM', data: [amTotal, amSaida, amPiso], backgroundColor: '#0ea5e9', borderRadius: 6 },
                            { label: 'Ciclo PM', data: [pmTotal, pmSaida, pmPiso], backgroundColor: '#003366', borderRadius: 6 }
                        ]
                    },
                    options: { responsive: true, maintainAspectRatio: false, scales: { y: { beginAtZero: true, ticks: { stepSize: 1 } } } }
                });
            }

            const canvasAM = document.getElementById('graficoAM');
            if (canvasAM) {
                const ctxAM = canvasAM.getContext('2d');
                if (chartAM) chartAM.destroy();
                chartAM = new Chart(ctxAM, {
                    type: 'bar',
                    data: {
                        labels: ['Volume AM'],
                        datasets: [
                            { label: 'Total Lidos', data: [amTotal], backgroundColor: cores.total, borderRadius: 6 },
                            { label: 'Saiu para Entrega', data: [amSaida], backgroundColor: cores.saida, borderRadius: 6 },
                            { label: 'Ficou no Piso', data: [amPiso], backgroundColor: cores.piso, borderRadius: 6 }
                        ]
                    },
                    options: { responsive: true, maintainAspectRatio: false, scales: { y: { beginAtZero: true, ticks: { stepSize: 1 } } } }
                });
            }

            const canvasPM = document.getElementById('graficoPM');
            if (canvasPM) {
                const ctxPM = canvasPM.getContext('2d');
                if (chartPM) chartPM.destroy();
                chartPM = new Chart(ctxPM, {
                    type: 'bar',
                    data: {
                        labels: ['Volume PM'],
                        datasets: [
                            { label: 'Total Lidos', data: [pmTotal], backgroundColor: cores.total, borderRadius: 6 },
                            { label: 'Saiu para Entrega', data: [pmSaida], backgroundColor: cores.saida, borderRadius: 6 },
                            { label: 'Ficou no Piso', data: [pmPiso], backgroundColor: cores.piso, borderRadius: 6 }
                        ]
                    },
                    options: { responsive: true, maintainAspectRatio: false, scales: { y: { beginAtZero: true, ticks: { stepSize: 1 } } } }
                });
            }
        }
    </script>
</body>
</html>
