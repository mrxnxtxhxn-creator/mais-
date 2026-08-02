<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KUEHNE+NAGEL - Automação Pós Sorting</title>
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
                            light: '#F4F6F8',
                            gray: '#E2E8F0'
                        }
                    }
                }
            }
        }
    </script>
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <!-- Chart.js para os Gráficos -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head>
<body class="bg-kn-light flex h-screen overflow-hidden font-sans text-slate-800">

    <!-- ================= SIDEBAR ================= -->
    <!-- Corrigido: em vez de sumir por completo, colapsa para uma trilha de ícones -->
    <aside id="sidebar" class="w-64 bg-kn-navy text-white flex flex-col justify-between z-20 shadow-lg flex-shrink-0 transition-all duration-200">
        <div class="flex-1 flex flex-col overflow-hidden">
            
            <div class="p-4 border-b border-white/10 flex items-center justify-between bg-kn-navy z-30">
                <div id="logo-area" class="flex items-center space-x-3 overflow-hidden">
                    <svg class="w-8 h-8 text-white flex-shrink-0" viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="8">
                        <circle cx="50" cy="50" r="42" />
                        <line x1="50" y1="25" x2="50" y2="75" />
                        <circle cx="50" cy="32" r="6" />
                        <path d="M28 58 C 28 72, 72 72, 72 58" />
                    </svg>
                    <div id="logo-text" class="flex flex-col whitespace-nowrap">
                        <span class="font-bold tracking-wider text-sm leading-tight">KUEHNE+NAGEL</span>
                        <span class="text-[10px] text-slate-300 tracking-widest uppercase">Operations</span>
                    </div>
                </div>
                <button onclick="toggleMenuLateral()" title="Recolher/expandir menu" class="p-1 hover:bg-kn-blue rounded transition focus:outline-none flex-shrink-0">
                    <i data-lucide="panel-left-close" id="icon-toggle" class="w-5 h-5"></i>
                </button>
            </div>

            <nav id="nav-menu" class="p-3 space-y-1.5 text-xs overflow-y-auto flex-1">
                
                <div class="nav-label text-[10px] text-slate-400 font-bold uppercase tracking-wider px-3 pb-1 pt-2">Operacional</div>
                <button onclick="mudarAba('operacao')" id="btn-aba-operacao" title="Bipagem do Piso" class="w-full flex items-center space-x-3 p-3 rounded-md bg-kn-blue text-white transition">
                    <i data-lucide="barcode" class="w-4 h-4 flex-shrink-0"></i>
                    <span class="nav-text font-medium text-sm whitespace-nowrap">Bipagem do Piso</span>
                </button>

                <div class="nav-label text-[10px] text-slate-400 font-bold uppercase tracking-wider px-3 pb-1 pt-4">Dashboards</div>
                
                <button onclick="mudarAba('graficos-geral')" id="btn-aba-graficos-geral" title="Visão Geral" class="w-full flex items-center space-x-3 p-3 rounded-md hover:bg-kn-blue/50 text-slate-200 hover:text-white transition">
                    <i data-lucide="layout-dashboard" class="w-4 h-4 flex-shrink-0"></i>
                    <span class="nav-text font-medium text-sm whitespace-nowrap">Visão Geral (Comparativo)</span>
                </button>

                <button onclick="mudarAba('graficos-am')" id="btn-aba-graficos-am" title="Ciclo AM" class="w-full flex items-center space-x-3 p-3 rounded-md hover:bg-kn-blue/50 text-slate-200 hover:text-white transition">
                    <i data-lucide="sun" class="w-4 h-4 flex-shrink-0"></i>
                    <span class="nav-text font-medium text-sm whitespace-nowrap">Ciclo AM</span>
                </button>

                <button onclick="mudarAba('graficos-pm')" id="btn-aba-graficos-pm" title="Ciclo PM" class="w-full flex items-center space-x-3 p-3 rounded-md hover:bg-kn-blue/50 text-slate-200 hover:text-white transition">
                    <i data-lucide="moon" class="w-4 h-4 flex-shrink-0"></i>
                    <span class="nav-text font-medium text-sm whitespace-nowrap">Ciclo PM</span>
                </button>
                
            </nav>
        </div>

        <div class="p-4 border-t border-white/10 text-[11px] text-slate-300 text-center flex flex-col items-center justify-center space-y-1 bg-kn-navy">
            <i data-lucide="code" class="w-4 h-4 mb-1"></i>
            <span class="nav-text font-semibold tracking-wide text-white whitespace-nowrap">Desenvolvido por Nathan</span>
            <span class="nav-text text-[9px] text-slate-400 whitespace-nowrap">Automação Pós Sorting v2.2</span>
        </div>
    </aside>

    <!-- ================= ÁREA DE CONTEÚDO ================= -->
    <main class="flex-1 flex flex-col overflow-y-auto relative">
        
        <header class="bg-white border-b border-kn-gray px-8 py-4 flex items-center justify-between sticky top-0 z-10">
            <div>
                <h1 id="titulo-pagina" class="text-lg font-bold text-kn-navy tracking-tight">Registro e Reconciliação Operacional</h1>
                <p class="text-xs text-slate-500">Dados armazenados localmente no navegador</p>
            </div>
            
            <div class="flex items-center space-x-2">
                <input type="date" id="filtroData" class="border border-slate-300 rounded text-xs px-2 py-2" onchange="aplicarFiltroData()">
                <button onclick="limparFiltroData()" class="text-xs text-slate-500 hover:text-kn-navy px-2">Limpar filtro</button>
                <button onclick="exportarCSV()" class="border border-kn-navy text-kn-navy hover:bg-kn-navy hover:text-white px-3 py-2 rounded text-xs font-semibold flex items-center space-x-1.5 transition">
                    <i data-lucide="download" class="w-3.5 h-3.5"></i>
                    <span>Exportar CSV</span>
                </button>
                <button onclick="limparBase()" class="bg-rose-50 border border-rose-200 text-rose-700 hover:bg-rose-600 hover:text-white px-3 py-2 rounded text-xs font-semibold flex items-center space-x-1.5 transition">
                    <i data-lucide="trash-2" class="w-3.5 h-3.5"></i>
                    <span>Limpar Tudo</span>
                </button>
            </div>
        </header>

        <div class="p-8 space-y-6">

            <div class="grid grid-cols-1 md:grid-cols-4 gap-4">
                <div class="bg-white p-4 rounded-lg shadow-sm border border-kn-gray border-l-4 border-l-kn-navy">
                    <span class="text-[11px] font-bold text-slate-400 uppercase">Total Bipado</span>
                    <div id="kpiTotal" class="text-2xl font-bold text-slate-800 mt-1">0</div>
                </div>
                <div class="bg-white p-4 rounded-lg shadow-sm border border-kn-gray border-l-4 border-l-blue-500">
                    <span class="text-[11px] font-bold text-slate-400 uppercase">Ciclo AM / PM</span>
                    <div id="kpiCiclos" class="text-2xl font-bold text-slate-800 mt-1">0 / 0</div>
                </div>
                <div class="bg-white p-4 rounded-lg shadow-sm border border-kn-gray border-l-4 border-l-amber-500">
                    <span class="text-[11px] font-bold text-slate-400 uppercase">Ficou no Piso</span>
                    <div id="kpiPiso" class="text-2xl font-bold text-amber-600 mt-1">0</div>
                </div>
                <div class="bg-white p-4 rounded-lg shadow-sm border border-kn-gray border-l-4 border-l-emerald-500">
                    <span class="text-[11px] font-bold text-slate-400 uppercase">Saiu pra Entrega</span>
                    <div id="kpiSaida" class="text-2xl font-bold text-emerald-600 mt-1">0</div>
                </div>
            </div>

            <!-- ================= ABA 1: OPERAÇÃO (BIPAGEM) ================= -->
            <section id="aba-operacao" class="grid grid-cols-1 lg:grid-cols-3 gap-6 fade-in">
                
                <div class="bg-white p-6 rounded-lg shadow-sm border border-kn-gray space-y-5 h-fit">
                    <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                        <h2 class="text-sm font-bold text-kn-navy uppercase tracking-wider">Bipador Inteligente</h2>
                        <span id="badge-ciclo" class="text-[11px] bg-kn-navy text-white px-2.5 py-0.5 rounded font-mono">Ciclo AM</span>
                    </div>

                    <div id="feedbackAlerta" class="hidden p-3 rounded text-xs font-medium border transition-all"></div>

                    <div class="space-y-4">
                        <div>
                            <label class="text-xs font-semibold text-slate-500 uppercase">Código de Barras</label>
                            <div class="flex space-x-2 mt-1">
                                <input type="text" id="barcodeInput" autofocus placeholder="Bipe o pacote aqui..." class="w-full p-2.5 border border-slate-300 rounded font-mono text-sm focus:ring-2 focus:ring-kn-navy focus:border-kn-navy focus:outline-none">
                                <button onclick="processarBip()" class="bg-kn-navy hover:bg-kn-blue text-white px-4 py-2.5 rounded font-semibold text-xs transition">Registrar</button>
                            </div>
                            <span class="text-[10px] text-slate-400 mt-1 block">Registro automático ao bipar — 1º Bipe = Saiu para Rota | 2º Bipe (Repetido) = Ficou no Piso</span>
                        </div>

                        <div class="grid grid-cols-2 gap-3 pt-3 border-t border-slate-100">
                            <div>
                                <label class="text-xs font-semibold text-slate-500">Rota/Gaiola:</label>
                                <input type="text" id="atribuicaoInput" placeholder="Ex: Gaiola 01" class="w-full p-2 border border-slate-300 rounded text-xs mt-1 focus:outline-none focus:border-kn-navy">
                            </div>
                            <div>
                                <label class="text-xs font-semibold text-slate-500">Ciclo Atual:</label>
                                <select id="selectCiclo" onchange="atualizarCicloBadge()" class="w-full p-2 border border-slate-300 rounded text-xs mt-1 bg-white focus:outline-none focus:border-kn-navy font-bold text-kn-navy">
                                    <option value="AM">AM</option>
                                    <option value="PM">PM</option>
                                </select>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="bg-white p-6 rounded-lg shadow-sm border border-kn-gray lg:col-span-2 space-y-4">
                    <div class="flex justify-between items-center border-b border-slate-100 pb-3 gap-3">
                        <h2 class="text-sm font-bold text-kn-navy uppercase tracking-wider whitespace-nowrap">Histórico de Registros</h2>
                        <input type="text" id="buscaHistorico" oninput="filtrarHistorico()" placeholder="Buscar código ou rota..." class="border border-slate-300 rounded text-xs px-2 py-1.5 w-48">
                        <span id="contadorBips" class="text-xs font-semibold bg-slate-100 text-kn-navy px-3 py-1 rounded-full border border-slate-200 whitespace-nowrap">0 Pacotes</span>
                    </div>

                    <div class="overflow-x-auto max-h-96">
                        <table class="w-full text-xs text-left text-slate-600">
                            <thead class="text-[11px] text-kn-navy uppercase bg-slate-50 border-b border-slate-200 sticky top-0">
                                <tr>
                                    <th class="px-4 py-2.5">Código de Barras</th>
                                    <th class="px-4 py-2.5">Ciclo</th>
                                    <th class="px-4 py-2.5">Atribuição</th>
                                    <th class="px-4 py-2.5">Status</th>
                                    <th class="px-4 py-2.5">Data/Hora</th>
                                    <th class="px-4 py-2.5"></th>
                                </tr>
                            </thead>
                            <tbody id="tabelaBips" class="divide-y divide-slate-100">
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <section id="aba-graficos-geral" class="hidden space-y-6 fade-in">
                <div class="bg-white p-6 rounded-lg shadow-sm border border-kn-gray">
                    <h2 class="text-sm font-bold text-kn-navy uppercase tracking-wider border-b border-slate-100 pb-3 mb-4">
                        Comparativo Geral de Operação: Ciclo AM vs Ciclo PM
                    </h2>
                    <div class="relative h-96 w-full">
                        <canvas id="graficoGeral"></canvas>
                    </div>
                </div>
            </section>

            <section id="aba-graficos-am" class="hidden space-y-6 fade-in">
                <div class="bg-white p-6 rounded-lg shadow-sm border border-kn-gray">
                    <h2 class="text-sm font-bold text-kn-navy uppercase tracking-wider border-b border-slate-100 pb-3 mb-4">
                        Performance Operacional Isolada - Ciclo AM
                    </h2>
                    <div class="relative h-96 w-full">
                        <canvas id="graficoAM"></canvas>
                    </div>
                </div>
            </section>

            <section id="aba-graficos-pm" class="hidden space-y-6 fade-in">
                <div class="bg-white p-6 rounded-lg shadow-sm border border-kn-gray">
                    <h2 class="text-sm font-bold text-kn-navy uppercase tracking-wider border-b border-slate-100 pb-3 mb-4">
                        Performance Operacional Isolada - Ciclo PM
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

        #sidebar.collapsed { width: 4.5rem; }
        #sidebar.collapsed .nav-text,
        #sidebar.collapsed #logo-text { display: none; }
        #sidebar.collapsed nav .nav-label { display: none; }
        #sidebar.collapsed nav button { justify-content: center; }
        #sidebar.collapsed #logo-area { justify-content: center; }
    </style>

    <!-- ================= JAVASCRIPT ================= -->
    <script>
        // safeIcons: se o Lucide (CDN externa) falhar ao carregar, chamar
        // lucide.createIcons() direto quebra TODO o resto do script (inclusive
        // o registro do evento de Enter no campo de bipagem). Isso era a causa
        // mais provável do "travamento" relatado antes.
        function safeIcons() {
            try {
                if (window.lucide) window.lucide.createIcons();
            } catch (e) {
                console.warn('Ícones não carregaram, app segue funcionando.', e);
            }
        }
        safeIcons();
        
        const STORAGE_KEY = 'kn_logistica_dados';
        let dadosOperacao = carregardados();
        let filtroDataAtual = ''; // dd/mm/aaaa

        let chartAM = null;
        let chartPM = null;
        let chartGeral = null;

        window.onload = function() {
            filtrarHistorico();
            atualizarKPIs();
            document.getElementById('barcodeInput').focus();
        };

        // Sidebar corrigida: colapsa para trilha de ícones em vez de sumir por completo
        function toggleMenuLateral() {
            const sidebar = document.getElementById('sidebar');
            const icon = document.getElementById('icon-toggle');
            const colapsado = sidebar.classList.toggle('collapsed');
            icon.setAttribute('data-lucide', colapsado ? 'panel-left-open' : 'panel-left-close');
            safeIcons();
        }

        function mudarAba(abaSelecionada) {
            const abas = ['operacao', 'graficos-geral', 'graficos-am', 'graficos-pm'];
            
            abas.forEach(aba => {
                document.getElementById('aba-' + aba).classList.add('hidden');
                const btn = document.getElementById('btn-aba-' + aba);
                btn.classList.remove('bg-kn-blue', 'text-white');
                btn.classList.add('hover:bg-kn-blue/50', 'text-slate-200');
            });

            document.getElementById('aba-' + abaSelecionada).classList.remove('hidden');
            const btnAtivo = document.getElementById('btn-aba-' + abaSelecionada);
            btnAtivo.classList.add('bg-kn-blue', 'text-white');
            btnAtivo.classList.remove('hover:bg-kn-blue/50', 'text-slate-200');

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
            document.getElementById('badge-ciclo').innerText = `Ciclo ${ciclo}`;
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

        // Auto-registro: scanners de código de barras despejam os caracteres
        // muito rápido e param. Detectamos essa pausa (debounce) e registramos
        // sozinho, sem precisar de Enter nem clique no botão — fluxo de alto
        // volume não pode parar pra confirmar cada pacote.
        const AUTO_BIP_PAUSA_MS = 300;
        let timerAutoBip = null;

        const campoBarcode = document.getElementById('barcodeInput');

        campoBarcode.addEventListener('input', function () {
            if (timerAutoBip) clearTimeout(timerAutoBip);
            const valorAtual = campoBarcode.value.trim();
            if (!valorAtual) return;

            timerAutoBip = setTimeout(() => {
                // Só dispara se o valor não mudou nesse meio tempo
                if (campoBarcode.value.trim() === valorAtual) {
                    processarBip();
                }
            }, AUTO_BIP_PAUSA_MS);
        });

        // Enter continua funcionando como atalho manual (digitação avulsa)
        campoBarcode.addEventListener('keypress', function (e) {
            if (e.key === 'Enter') {
                e.preventDefault();
                if (timerAutoBip) clearTimeout(timerAutoBip);
                processarBip();
            }
        });

        function processarBip() {
            const input = document.getElementById('barcodeInput');
            const barcode = input.value.trim();
            const atribuicao = document.getElementById('atribuicaoInput').value.trim() || 'Sem Rota';
            const ciclo = document.getElementById('selectCiclo').value;

            if (!barcode) return;

            const hoje = new Date().toLocaleDateString('pt-BR');

            // Corrigido: a checagem de duplicidade agora considera também a DATA,
            // não só o ciclo. Sem isso, um código bipado hoje no AM colidiria
            // com o mesmo código bipado num AM de outro dia (falso "ficou no piso").
            let itemExistente = dadosOperacao.find(d => d.barcode === barcode && d.ciclo === ciclo && d.data === hoje);

            if (!itemExistente) {
                const novoItem = {
                    id: Date.now(),
                    barcode: barcode,
                    ciclo: ciclo,
                    atribuicao: atribuicao,
                    status: 'SAIU_PARA_ENTREGA',
                    hora: new Date().toLocaleTimeString('pt-BR'),
                    data: hoje
                };
                dadosOperacao.unshift(novoItem);
                mostrarAlerta(`✅ [${ciclo}] ${barcode} registrado -> SAIU PARA ENTREGA`, 'success');
            } else {
                itemExistente.status = 'FICOU_NO_PISO';
                itemExistente.hora = new Date().toLocaleTimeString('pt-BR');
                if (atribuicao !== 'Sem Rota') {
                    itemExistente.atribuicao = atribuicao;
                }
                mostrarAlerta(`⚠️ [${ciclo}] ID repetido detectado! Atualizado para -> FICOU NO PISO`, 'warning');
            }

            salvardados();
            filtrarHistorico();

            input.value = '';
            input.focus();
        }

        function listaFiltradaPorData() {
            if (!filtroDataAtual) return dadosOperacao;
            return dadosOperacao.filter(d => d.data === filtroDataAtual);
        }

        function filtrarHistorico() {
            const termo = document.getElementById('buscaHistorico').value.trim().toLowerCase();
            const base = listaFiltradaPorData();
            const filtrado = base.filter(item =>
                item.barcode.toLowerCase().includes(termo) ||
                item.atribuicao.toLowerCase().includes(termo)
            );
            renderizarTabela(filtrado);
        }

        function renderizarTabela(lista) {
            const tbody = document.getElementById('tabelaBips');
            document.getElementById('contadorBips').innerText = `${lista.length} Pacotes`;

            if (lista.length === 0) {
                tbody.innerHTML = `<tr><td colspan="6" class="text-center py-8 text-slate-400">Nenhum pacote registrado.</td></tr>`;
                return;
            }

            tbody.innerHTML = lista.map(item => `
                <tr class="hover:bg-slate-50 font-mono border-b border-slate-50 last:border-0">
                    <td class="px-4 py-2 font-bold text-slate-800">${item.barcode}</td>
                    <td class="px-4 py-2"><span class="px-2 py-0.5 text-[10px] rounded ${item.ciclo === 'AM' ? 'bg-blue-100 text-blue-900' : 'bg-slate-200 text-slate-800'}">${item.ciclo}</span></td>
                    <td class="px-4 py-2 text-slate-600 font-sans">${item.atribuicao}</td>
                    <td class="px-4 py-2 font-sans">
                        <span class="px-2 py-0.5 text-[10px] rounded ${item.status === 'SAIU_PARA_ENTREGA' ? 'bg-emerald-100 text-emerald-800' : 'bg-amber-100 text-amber-800'}">
                            ${item.status === 'SAIU_PARA_ENTREGA' ? 'SAÍDA' : 'PISO'}
                        </span>
                    </td>
                    <td class="px-4 py-2 text-slate-400 font-sans">${item.data} ${item.hora}</td>
                    <td class="px-4 py-2 font-sans">
                        <button onclick="excluirRegistro(${item.id})" title="Excluir" class="text-slate-400 hover:text-rose-600">
                            <i data-lucide="trash-2" class="w-3.5 h-3.5"></i>
                        </button>
                    </td>
                </tr>
            `).join('');
            safeIcons();
        }

        function excluirRegistro(id) {
            if (!confirm('Excluir este registro?')) return;
            dadosOperacao = dadosOperacao.filter(d => d.id !== id);
            salvardados();
            filtrarHistorico();
        }

        function aplicarFiltroData() {
            const valor = document.getElementById('filtroData').value; // yyyy-mm-dd
            if (!valor) { filtroDataAtual = ''; }
            else {
                const [ano, mes, dia] = valor.split('-');
                filtroDataAtual = `${dia}/${mes}/${ano}`;
            }
            filtrarHistorico();
            atualizarKPIs();
        }

        function limparFiltroData() {
            document.getElementById('filtroData').value = '';
            filtroDataAtual = '';
            filtrarHistorico();
            atualizarKPIs();
        }

        function atualizarKPIs() {
            const base = listaFiltradaPorData();
            const total = base.length;
            const am = base.filter(d => d.ciclo === 'AM').length;
            const pm = base.filter(d => d.ciclo === 'PM').length;
            const piso = base.filter(d => d.status === 'FICOU_NO_PISO').length;
            const saida = base.filter(d => d.status === 'SAIU_PARA_ENTREGA').length;

            document.getElementById('kpiTotal').innerText = total;
            document.getElementById('kpiCiclos').innerText = `${am} (AM) / ${pm} (PM)`;
            document.getElementById('kpiPiso').innerText = piso;
            document.getElementById('kpiSaida').innerText = saida;
        }

        function limparBase() {
            if (confirm("Tem certeza que deseja apagar todos os registros da memória local?")) {
                localStorage.removeItem(STORAGE_KEY);
                dadosOperacao = [];
                filtrarHistorico();
                atualizarKPIs();
                renderizarGraficos();
                document.getElementById('barcodeInput').focus();
            }
        }

        function exportarCSV() {
            const base = listaFiltradaPorData();
            if (base.length === 0) {
                alert("Não há dados para exportar.");
                return;
            }

            let csv = 'CodigoDeBarras;Ciclo;Atribuicao;Status;Hora;Data\n';
            base.forEach(item => {
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

        // ================= FUNÇÃO DE GRÁFICOS (CHART.JS) =================
        function renderizarGraficos() {
            const base = listaFiltradaPorData();

            const amTotal = base.filter(d => d.ciclo === 'AM').length;
            const amSaida = base.filter(d => d.ciclo === 'AM' && d.status === 'SAIU_PARA_ENTREGA').length;
            const amPiso = base.filter(d => d.ciclo === 'AM' && d.status === 'FICOU_NO_PISO').length;

            const pmTotal = base.filter(d => d.ciclo === 'PM').length;
            const pmSaida = base.filter(d => d.ciclo === 'PM' && d.status === 'SAIU_PARA_ENTREGA').length;
            const pmPiso = base.filter(d => d.ciclo === 'PM' && d.status === 'FICOU_NO_PISO').length;

            const cores = { total: '#004B93', saida: '#10B981', piso: '#F59E0B' };

            const canvasGeral = document.getElementById('graficoGeral');
            if (canvasGeral) {
                const ctxGeral = canvasGeral.getContext('2d');
                if (chartGeral) chartGeral.destroy();
                chartGeral = new Chart(ctxGeral, {
                    type: 'bar',
                    data: {
                        labels: ['Total Lidos', 'Saíram pra Entrega', 'Ficaram no Piso'],
                        datasets: [
                            { label: 'Ciclo AM', data: [amTotal, amSaida, amPiso], backgroundColor: '#0ea5e9', borderRadius: 4 },
                            { label: 'Ciclo PM', data: [pmTotal, pmSaida, pmPiso], backgroundColor: '#003366', borderRadius: 4 }
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
                            { label: 'Total Lidos', data: [amTotal], backgroundColor: cores.total, borderRadius: 4 },
                            { label: 'Saiu para Entrega', data: [amSaida], backgroundColor: cores.saida, borderRadius: 4 },
                            { label: 'Ficou no Piso', data: [amPiso], backgroundColor: cores.piso, borderRadius: 4 }
                        ]
                    },
                    options: { responsive: true, maintainAspectRatio: false, scales: { y: { beginAtZero: true, ticks: { stepSize: 1 } } } }
                });
            }

            // Corrigido: antes era `new Chart(chartPM ? null : ctxPM, ...)`, o que
            // sempre passava null como contexto (chartPM nunca voltava a ser
            // "falsy" depois do primeiro destroy) e quebrava o gráfico PM.
            const canvasPM = document.getElementById('graficoPM');
            if (canvasPM) {
                const ctxPM = canvasPM.getContext('2d');
                if (chartPM) chartPM.destroy();
                chartPM = new Chart(ctxPM, {
                    type: 'bar',
                    data: {
                        labels: ['Volume PM'],
                        datasets: [
                            { label: 'Total Lidos', data: [pmTotal], backgroundColor: cores.total, borderRadius: 4 },
                            { label: 'Saiu para Entrega', data: [pmSaida], backgroundColor: cores.saida, borderRadius: 4 },
                            { label: 'Ficou no Piso', data: [pmPiso], backgroundColor: cores.piso, borderRadius: 4 }
                        ]
                    },
                    options: { responsive: true, maintainAspectRatio: false, scales: { y: { beginAtZero: true, ticks: { stepSize: 1 } } } }
                });
            }
        }
    </script>
</body>
</html>
