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
    <aside id="sidebar" class="w-64 bg-kn-navy text-white flex flex-col justify-between transition-all duration-300 z-20 shadow-lg flex-shrink-0">
        <div>
            <!-- Header Sidebar / Logo Kuehne+Nagel e Botão Toggle -->
            <div class="p-4 border-b border-white/10 flex items-center justify-between">
                <div class="flex items-center space-x-3">
                    <svg class="w-8 h-8 text-white flex-shrink-0" viewBox="0 0 100 100" fill="none" stroke="currentColor" stroke-width="8">
                        <circle cx="50" cy="50" r="42" />
                        <line x1="50" y1="25" x2="50" y2="75" />
                        <circle cx="50" cy="32" r="6" />
                        <path d="M28 58 C 28 72, 72 72, 72 58" />
                    </svg>
                    <div class="flex flex-col whitespace-nowrap">
                        <span class="font-bold tracking-wider text-sm leading-tight">KUEHNE+NAGEL</span>
                        <span class="text-[10px] text-slate-300 tracking-widest uppercase">Operations</span>
                    </div>
                </div>
                <!-- Botão para esconder/mostrar o menu -->
                <button onclick="toggleMenuLateral()" class="p-1 hover:bg-kn-blue rounded transition">
                    <i data-lucide="menu" class="w-5 h-5"></i>
                </button>
            </div>

            <!-- Navegação (Ocultável) -->
            <nav id="nav-menu" class="p-3 space-y-2 text-xs transition-all duration-300">
                
                <!-- Aba Operação -->
                <button onclick="mudarAba('operacao')" id="btn-aba-operacao" class="w-full flex items-center space-x-3 p-3 rounded-md bg-kn-blue text-white transition">
                    <i data-lucide="barcode" class="w-4 h-4"></i>
                    <span class="font-medium text-sm">Operação (Bipagem)</span>
                </button>

                <!-- Aba Gráficos -->
                <button onclick="mudarAba('graficos')" id="btn-aba-graficos" class="w-full flex items-center space-x-3 p-3 rounded-md hover:bg-kn-blue/50 text-slate-200 hover:text-white transition">
                    <i data-lucide="pie-chart" class="w-4 h-4"></i>
                    <span class="font-medium text-sm">Painel de Gráficos</span>
                </button>

                <hr class="border-white/10 my-2">

                <!-- Filtros rápidos para a tabela (aparecem apenas na aba operação, mas deixaremos acessíveis) -->
                <div class="space-y-1 pt-2">
                    <div class="text-[10px] text-slate-400 font-bold uppercase tracking-wider px-3 pb-1">Filtros da Tabela</div>
                    <a href="#" onclick="filtrarStatus('TODOS'); mudarAba('operacao');" class="flex items-center space-x-3 p-2 rounded hover:bg-kn-blue/40 text-slate-300">
                        <i data-lucide="list" class="w-3.5 h-3.5"></i> <span>Ver Todos</span>
                    </a>
                    <a href="#" onclick="filtrarStatus('SAIU_PARA_ENTREGA'); mudarAba('operacao');" class="flex items-center space-x-3 p-2 rounded hover:bg-kn-blue/40 text-slate-300">
                        <i data-lucide="truck" class="w-3.5 h-3.5"></i> <span>Saiu pra Entrega</span>
                    </a>
                    <a href="#" onclick="filtrarStatus('FICOU_NO_PISO'); mudarAba('operacao');" class="flex items-center space-x-3 p-2 rounded hover:bg-kn-blue/40 text-slate-300">
                        <i data-lucide="package-open" class="w-3.5 h-3.5"></i> <span>Ficou no Piso</span>
                    </a>
                </div>
            </nav>
        </div>

        <div class="p-4 border-t border-white/10 text-[11px] text-slate-300 text-center flex flex-col items-center justify-center space-y-1">
            <i data-lucide="code" class="w-4 h-4 mb-1"></i>
            <span class="font-semibold tracking-wide">Desenvolvido por Nathan</span>
            <span class="text-[9px] text-slate-500">Automação Pós Sorting v2.0</span>
        </div>
    </aside>

    <!-- ================= ÁREA DE CONTEÚDO ================= -->
    <main class="flex-1 flex flex-col overflow-y-auto relative">
        
        <!-- Header Superior -->
        <header class="bg-white border-b border-kn-gray px-8 py-4 flex items-center justify-between sticky top-0 z-10">
            <div>
                <h1 id="titulo-pagina" class="text-lg font-bold text-kn-navy tracking-tight">Registro e Reconciliação Operacional</h1>
                <p class="text-xs text-slate-500">Dados armazenados localmente no navegador</p>
            </div>
            
            <div class="flex items-center space-x-2">
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

            <!-- CARDS DE RESUMO (GARGALOS / KPIS) - Ficam visíveis em ambas as abas -->
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
                
                <!-- Card de Leitura / Digitação -->
                <div class="bg-white p-6 rounded-lg shadow-sm border border-kn-gray space-y-5 h-fit">
                    <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                        <h2 class="text-sm font-bold text-kn-navy uppercase tracking-wider">Bipador / Digitação</h2>
                        <span id="badge-ciclo" class="text-[11px] bg-kn-navy text-white px-2.5 py-0.5 rounded font-mono">Ciclo AM</span>
                    </div>

                    <div class="space-y-4">
                        <div>
                            <label class="text-xs font-semibold text-slate-500 uppercase">Código de Barras</label>
                            <div class="flex space-x-2 mt-1">
                                <input type="text" id="barcodeInput" autofocus placeholder="Bipe ou digite aqui..." class="w-full p-2.5 border border-slate-300 rounded font-mono text-sm focus:ring-2 focus:ring-kn-navy focus:border-kn-navy focus:outline-none">
                                <button onclick="processarBip()" class="bg-kn-navy hover:bg-kn-blue text-white px-4 py-2.5 rounded font-semibold text-xs transition">
                                    Registrar
                                </button>
                            </div>
                        </div>

                        <!-- Opções de Parâmetros -->
                        <div class="grid grid-cols-2 gap-3 pt-3 border-t border-slate-100">
                            <div>
                                <label class="text-xs font-semibold text-slate-500">Rota/Gaiola:</label>
                                <input type="text" id="atribuicaoInput" placeholder="Ex: Gaiola 01" class="w-full p-2 border border-slate-300 rounded text-xs mt-1 focus:outline-none focus:border-kn-navy">
                            </div>
                            <div>
                                <label class="text-xs font-semibold text-slate-500">Ciclo:</label>
                                <select id="selectCiclo" onchange="atualizarCicloBadge()" class="w-full p-2 border border-slate-300 rounded text-xs mt-1 bg-white focus:outline-none focus:border-kn-navy">
                                    <option value="AM">AM</option>
                                    <option value="PM">PM</option>
                                </select>
                            </div>
                        </div>

                        <div>
                            <label class="text-xs font-semibold text-slate-500">Status do Pacote:</label>
                            <select id="selectStatus" class="w-full p-2 border border-slate-300 rounded text-xs mt-1 bg-white focus:outline-none focus:border-kn-navy">
                                <option value="SAIU_PARA_ENTREGA">SAIU PARA ENTREGA</option>
                                <option value="FICOU_NO_PISO">FICOU NO PISO</option>
                            </select>
                        </div>
                    </div>
                </div>

                <!-- Tabela de Pacotes Persistidos -->
                <div class="bg-white p-6 rounded-lg shadow-sm border border-kn-gray lg:col-span-2 space-y-4">
                    <div class="flex justify-between items-center border-b border-slate-100 pb-3">
                        <h2 class="text-sm font-bold text-kn-navy uppercase tracking-wider">Histórico de Registros</h2>
                        <span id="contadorBips" class="text-xs font-semibold bg-slate-100 text-kn-navy px-3 py-1 rounded-full border border-slate-200">0 Pacotes</span>
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
                                </tr>
                            </thead>
                            <tbody id="tabelaBips" class="divide-y divide-slate-100">
                                <!-- Preenchido via JavaScript -->
                            </tbody>
                        </table>
                    </div>
                </div>
            </section>

            <!-- ================= ABA 2: GRÁFICOS ================= -->
            <section id="aba-graficos" class="hidden space-y-6 fade-in">
                <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                    
                    <!-- Gráfico Ciclo AM -->
                    <div class="bg-white p-6 rounded-lg shadow-sm border border-kn-gray">
                        <h2 class="text-sm font-bold text-kn-navy uppercase tracking-wider border-b border-slate-100 pb-3 mb-4">
                            Performance Operacional - Ciclo AM
                        </h2>
                        <div class="relative h-64">
                            <canvas id="graficoAM"></canvas>
                        </div>
                    </div>

                    <!-- Gráfico Ciclo PM -->
                    <div class="bg-white p-6 rounded-lg shadow-sm border border-kn-gray">
                        <h2 class="text-sm font-bold text-kn-navy uppercase tracking-wider border-b border-slate-100 pb-3 mb-4">
                            Performance Operacional - Ciclo PM
                        </h2>
                        <div class="relative h-64">
                            <canvas id="graficoPM"></canvas>
                        </div>
                    </div>

                </div>
            </section>

        </div>
    </main>

    <!-- Estilo extra para a animação das abas -->
    <style>
        .fade-in { animation: fadeIn 0.3s ease-in-out; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(5px); } to { opacity: 1; transform: translateY(0); } }
    </style>

    <!-- ================= JAVASCRIPT ================= -->
    <script>
        lucide.createIcons();
        
        const STORAGE_KEY = 'kn_logistica_dados';
        let dadosOperacao = carregardados();
        
        // Variáveis globais para os gráficos
        let chartAM = null;
        let chartPM = null;

        window.onload = function() {
            renderizarTabela(dadosOperacao);
            atualizarKPIs();
            renderizarGraficos();
        };

        // Função para esconder/mostrar o Menu Lateral
        function toggleMenuLateral() {
            const navMenu = document.getElementById('nav-menu');
            if (navMenu.classList.contains('hidden')) {
                navMenu.classList.remove('hidden');
            } else {
                navMenu.classList.add('hidden');
            }
        }

        // Sistema de Abas
        function mudarAba(aba) {
            const secOperacao = document.getElementById('aba-operacao');
            const secGraficos = document.getElementById('aba-graficos');
            const btnOperacao = document.getElementById('btn-aba-operacao');
            const btnGraficos = document.getElementById('btn-aba-graficos');

            if (aba === 'operacao') {
                secOperacao.classList.remove('hidden');
                secGraficos.classList.add('hidden');
                
                // Estilo ativo no botão Operação
                btnOperacao.classList.add('bg-kn-blue', 'text-white');
                btnOperacao.classList.remove('hover:bg-kn-blue/50', 'text-slate-200');
                
                // Remove estilo ativo do botão Gráficos
                btnGraficos.classList.remove('bg-kn-blue', 'text-white');
                btnGraficos.classList.add('hover:bg-kn-blue/50', 'text-slate-200');
                
                document.getElementById('barcodeInput').focus();
            } else if (aba === 'graficos') {
                secOperacao.classList.add('hidden');
                secGraficos.classList.remove('hidden');
                
                // Estilo ativo no botão Gráficos
                btnGraficos.classList.add('bg-kn-blue', 'text-white');
                btnGraficos.classList.remove('hover:bg-kn-blue/50', 'text-slate-200');
                
                // Remove estilo ativo do botão Operação
                btnOperacao.classList.remove('bg-kn-blue', 'text-white');
                btnOperacao.classList.add('hover:bg-kn-blue/50', 'text-slate-200');

                // Atualiza gráficos sempre que a aba for aberta
                renderizarGraficos();
            }
        }

        // Salvar no LocalStorage
        function salvardados() {
            localStorage.setItem(STORAGE_KEY, JSON.stringify(dadosOperacao));
            atualizarKPIs();
            renderizarGraficos(); // Mantém gráficos sincronizados
        }

        function carregardados() {
            const dadosSalvos = localStorage.getItem(STORAGE_KEY);
            return dadosSalvos ? JSON.parse(dadosSalvos) : [];
        }

        function atualizarCicloBadge() {
            const ciclo = document.getElementById('selectCiclo').value;
            document.getElementById('badge-ciclo').innerText = `Ciclo ${ciclo}`;
        }

        // Bipador Físico
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
            const status = document.getElementById('selectStatus').value;

            if (!barcode) return;

            const novoItem = {
                id: Date.now(),
                barcode: barcode,
                ciclo: ciclo,
                atribuicao: atribuicao,
                status: status,
                hora: new Date().toLocaleTimeString('pt-BR'),
                data: new Date().toLocaleDateString('pt-BR')
            };

            dadosOperacao.unshift(novoItem);
            salvardados();
            renderizarTabela(dadosOperacao);

            input.value = '';
            input.focus();
        }

        function renderizarTabela(lista) {
            const tbody = document.getElementById('tabelaBips');
            document.getElementById('contadorBips').innerText = `${lista.length} Pacotes`;

            if (lista.length === 0) {
                tbody.innerHTML = `<tr><td colspan="5" class="text-center py-8 text-slate-400">Nenhum pacote registrado.</td></tr>`;
                return;
            }

            tbody.innerHTML = lista.map(item => `
                <tr class="hover:bg-slate-50 font-mono">
                    <td class="px-4 py-2 font-bold text-slate-800">${item.barcode}</td>
                    <td class="px-4 py-2"><span class="px-2 py-0.5 text-[10px] rounded ${item.ciclo === 'AM' ? 'bg-blue-100 text-blue-900' : 'bg-slate-200 text-slate-800'}">${item.ciclo}</span></td>
                    <td class="px-4 py-2 text-slate-600 font-sans">${item.atribuicao}</td>
                    <td class="px-4 py-2 font-sans">
                        <span class="px-2 py-0.5 text-[10px] rounded ${item.status === 'SAIU_PARA_ENTREGA' ? 'bg-emerald-100 text-emerald-800' : 'bg-amber-100 text-amber-800'}">
                            ${item.status === 'SAIU_PARA_ENTREGA' ? 'SAÍDA' : 'PISO'}
                        </span>
                    </td>
                    <td class="px-4 py-2 text-slate-400 font-sans">${item.hora} (${item.data})</td>
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
            document.getElementById('kpiCiclos').innerText = `${am} (AM) / ${pm} (PM)`;
            document.getElementById('kpiPiso').innerText = piso;
            document.getElementById('kpiSaida').innerText = saida;
        }

        function filtrarStatus(status) {
            if (status === 'TODOS') {
                renderizarTabela(dadosOperacao);
            } else {
                const filtrados = dadosOperacao.filter(d => d.status === status);
                renderizarTabela(filtrados);
            }
        }

        function limparBase() {
            if (confirm("Tem certeza que deseja apagar todos os registros da memória local?")) {
                localStorage.removeItem(STORAGE_KEY);
                dadosOperacao = [];
                renderizarTabela(dadosOperacao);
                atualizarKPIs();
                renderizarGraficos();
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

        // ================= FUNÇÃO DE GRÁFICOS (CHART.JS) =================
        function renderizarGraficos() {
            // Conta os dados do Ciclo AM
            const amTotal = dadosOperacao.filter(d => d.ciclo === 'AM').length;
            const amSaida = dadosOperacao.filter(d => d.ciclo === 'AM' && d.status === 'SAIU_PARA_ENTREGA').length;
            const amPiso = dadosOperacao.filter(d => d.ciclo === 'AM' && d.status === 'FICOU_NO_PISO').length;

            // Conta os dados do Ciclo PM
            const pmTotal = dadosOperacao.filter(d => d.ciclo === 'PM').length;
            const pmSaida = dadosOperacao.filter(d => d.ciclo === 'PM' && d.status === 'SAIU_PARA_ENTREGA').length;
            const pmPiso = dadosOperacao.filter(d => d.ciclo === 'PM' && d.status === 'FICOU_NO_PISO').length;

            // Configuração visual padrão
            const cores = {
                total: '#004B93',   // Azul KN
                saida: '#10B981',   // Emerald
                piso: '#F59E0B'     // Amber
            };

            // Gráfico AM
            const ctxAM = document.getElementById('graficoAM').getContext('2d');
            if (chartAM) chartAM.destroy(); // Apaga o antigo antes de desenhar o novo
            
            chartAM = new Chart(ctxAM, {
                type: 'bar',
                data: {
                    labels: ['Total Lidos', 'Saíram pra Entrega', 'Ficaram no Piso'],
                    datasets: [{
                        label: 'Volume de Pacotes - AM',
                        data: [amTotal, amSaida, amPiso],
                        backgroundColor: [cores.total, cores.saida, cores.piso],
                        borderRadius: 4
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false } },
                    scales: { y: { beginAtZero: true, ticks: { stepSize: 1 } } }
                }
            });

            // Gráfico PM
            const ctxPM = document.getElementById('graficoPM').getContext('2d');
            if (chartPM) chartPM.destroy();

            chartPM = new Chart(ctxPM, {
                type: 'bar',
                data: {
                    labels: ['Total Lidos', 'Saíram pra Entrega', 'Ficaram no Piso'],
                    datasets: [{
                        label: 'Volume de Pacotes - PM',
                        data: [pmTotal, pmSaida, pmPiso],
                        backgroundColor: [cores.total, cores.saida, cores.piso],
                        borderRadius: 4
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false } },
                    scales: { y: { beginAtZero: true, ticks: { stepSize: 1 } } }
                }
            });
        }
    </script>
</body>
</html>
