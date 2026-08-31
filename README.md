<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Automação Pós-Sorting</title>
    <!-- Bibliotecas externas: HTML5 QR/Barcode Scanner + Chart.js -->
    <script src="https://unpkg.com/html5-qrcode"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    
    <style>
        * { box-sizing: border-box; font-family: 'Segoe UI', Arial, sans-serif; }
        body { background-color: #f1f5f9; margin: 0; padding: 20px; color: #0f172a; }
        
        /* Navegação */
        .tabs-nav { display: flex; gap: 8px; margin-bottom: 20px; background: #ffffff; padding: 10px; border-radius: 8px; box-shadow: 0 1px 3px rgba(0,0,0,0.1); }
        .tab-btn { padding: 12px 20px; border: none; background: #e2e8f0; color: #334155; font-weight: 600; cursor: pointer; border-radius: 6px; transition: 0.2s; }
        .tab-btn.active { background-color: #2563eb; color: #ffffff; }

        /* Conteúdo das Abas */
        .tab-content { display: none; background: #ffffff; padding: 20px; border-radius: 8px; box-shadow: 0 2px 4px rgba(0,0,0,0.05); }
        .tab-content.active { display: block; }

        /* Container do Leitor de Código de Barras */
        .scanner-container { max-width: 500px; margin: 0 auto 20px auto; }
        #reader { width: 100%; border-radius: 8px; overflow: hidden; border: 2px dashed #cbd5e1; }

        /* Card de Informações do Código de Barras */
        .barcode-info-card { background: #f8fafc; border: 1px solid #e2e8f0; border-left: 5px solid #2563eb; padding: 15px; border-radius: 6px; margin-top: 15px; }
        .barcode-info-card h3 { margin-top: 0; color: #1e293b; font-size: 1.1rem; }
        .info-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(140px, 1fr)); gap: 10px; }
        .info-item { background: #ffffff; padding: 8px 12px; border-radius: 4px; border: 1px solid #cbd5e1; }
        .info-item label { display: block; font-size: 0.75rem; color: #64748b; font-weight: bold; }
        .info-item span { font-size: 0.95rem; font-weight: 600; color: #0f172a; }

        /* Entrada Manual e Controles */
        .manual-input { display: flex; gap: 10px; margin-top: 15px; }
        .manual-input input { flex: 1; padding: 10px; border: 1px solid #cbd5e1; border-radius: 6px; }
        .manual-input button { padding: 10px 20px; background: #10b981; color: white; border: none; border-radius: 6px; cursor: pointer; font-weight: bold; }

        /* Canvas do Gráfico */
        .chart-container { position: relative; height: 350px; width: 100%; max-width: 750px; margin: 0 auto; }
    </style>
</head>
<body>

    <!-- Navegação entre Abas -->
    <div class="tabs-nav">
        <button class="tab-btn active" onclick="trocarAba(event, 'aba-bipagem')">Bipagem / Código de Barras</button>
        <button class="tab-btn" onclick="trocarAba(event, 'aba-ciclo-am-pm')">Painel Ciclo AM e PM</button>
    </div>

    <!-- ABA 1: Bipagem e Código de Barras -->
    <div id="aba-bipagem" class="tab-content active">
        <h2>Leitor de Código de Barras</h2>
        
        <div class="scanner-container">
            <div id="reader"></div>
        </div>

        <div class="manual-input">
            <input type="text" id="input-codigo-manual" placeholder="Digite ou bipe o código de barras aqui..." autofocus>
            <button onclick="processarCodigoManual()">Registrar</button>
        </div>

        <!-- Exibição das Informações do Último Código Lido -->
        <div class="barcode-info-card">
            <h3>Último Pacote Identificado</h3>
            <div class="info-grid">
                <div class="info-item">
                    <label>Código de Barras / ID</label>
                    <span id="info-id">Nenhum pacote lido</span>
                </div>
                <div class="info-item">
                    <label>Turno Atribuído</label>
                    <span id="info-ciclo">-</span>
                </div>
                <div class="info-item">
                    <label>Status</label>
                    <span id="info-status">-</span>
                </div>
                <div class="info-item">
                    <label>Horário</label>
                    <span id="info-hora">-</span>
                </div>
            </div>
        </div>
    </div>

    <!-- ABA 2: Painel Ciclo AM e PM -->
    <div id="aba-ciclo-am-pm" class="tab-content">
        <h2>Métricas do Ciclo AM vs PM</h2>
        <div class="chart-container">
            <canvas id="canvasCicloAMPM"></canvas>
        </div>
    </div>

    <script>
        // Array com histórico de pacotes processados
        let historicoPacotes = [];
        let instanciaGraficoCiclo = null;
        let html5QrcodeScanner = null;

        // Inicializa o leitor e os eventos ao carregar a página
        window.addEventListener('DOMContentLoaded', () => {
            iniciarLeitorCodigoBarras();
            
            // Listener para bipagem via leitor físico (Enter dispara o registro)
            document.getElementById('input-codigo-manual').addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    processarCodigoManual();
                }
            });
        });

        // Configuração da Câmera / Leitor de Código de Barras
        function iniciarLeitorCodigoBarras() {
            html5QrcodeScanner = new Html5QrcodeScanner("reader", { 
                fps: 10, 
                qrbox: { width: 250, height: 150 } 
            });
            html5QrcodeScanner.render(onScanSuccess, onScanFailure);
        }

        // Callback ao escanear com sucesso via câmera
        function onScanSuccess(decodedText) {
            registrarPacote(decodedText);
        }

        function onScanFailure(error) {
            // Ignora falhas de quadro contínuas
        }

        // Registro via campo de texto (Leitor Bipador Físico)
        function processarCodigoManual() {
            const input = document.getElementById('input-codigo-manual');
            const codigo = input.value.trim();
            if (codigo) {
                registrarPacote(codigo);
                input.value = '';
                input.focus();
            }
        }

        // Processa o Código de Barras e Atualiza a Interface
        function registrarPacote(codigo) {
            const agora = new Date();
            const hora = agora.getHours();
            // Define o ciclo com base no horário (AM: antes das 12h | PM: a partir das 12h)
            const ciclo = hora < 12 ? 'AM' : 'PM';
            const horaFormatada = agora.toLocaleTimeString('pt-BR');

            const novoPacote = {
                id: codigo,
                ciclo: ciclo,
                status: 'Processado',
                hora: horaFormatada
            };

            historicoPacotes.unshift(novoPacote);

            // Atualiza os dados na tela (Aba Bipagem)
            document.getElementById('info-id').innerText = novoPacote.id;
            document.getElementById('info-ciclo').innerText = novoPacote.ciclo;
            document.getElementById('info-status').innerText = novoPacote.status;
            document.getElementById('info-hora').innerText = novoPacote.hora;

            // Se a aba do gráfico estiver ativa, atualiza o gráfico em tempo real
            const abaCicloAtiva = document.getElementById('aba-ciclo-am-pm').classList.contains('active');
            if (abaCicloAtiva) {
                renderizarGraficoCiclo();
            }
        }

        // Troca de Abas sem destruir o leitor de código de barras
        function trocarAba(event, idAba) {
            document.querySelectorAll('.tab-content').forEach(aba => aba.classList.remove('active'));
            document.querySelectorAll('.tab-btn').forEach(btn => btn.classList.remove('active'));

            document.getElementById(idAba).classList.add('active');
            event.currentTarget.classList.add('active');

            // Renderiza o gráfico com garantia de visibilidade do DOM
            if (idAba === 'aba-ciclo-am-pm') {
                setTimeout(() => {
                    renderizarGraficoCiclo();
                }, 50);
            }
        }

        // Renderização corrigida do Chart.js
        function renderizarGraficoCiclo() {
            const canvas = document.getElementById('canvasCicloAMPM');
            if (!canvas) return;

            const totalAM = historicoPacotes.filter(p => p.ciclo === 'AM').length;
            const totalPM = historicoPacotes.filter(p => p.ciclo === 'PM').length;

            // Destrói a instância anterior para evitar erros de renderização
            if (instanciaGraficoCiclo instanceof Chart) {
                instanciaGraficoCiclo.destroy();
            }

            const ctx = canvas.getContext('2d');
            instanciaGraficoCiclo = new Chart(ctx, {
                type: 'bar',
                data: {
                    labels: ['Ciclo AM', 'Ciclo PM'],
                    datasets: [{
                        label: 'Volume de Pacotes Bipados',
                        data: [totalAM, totalPM],
                        backgroundColor: ['#2563eb', '#f59e0b'],
                        borderColor: ['#1d4ed8', '#d97706'],
                        borderWidth: 1,
                        borderRadius: 4
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: true,
                            ticks: { stepSize: 1, precision: 0 }
                        }
                    },
                    plugins: {
                        legend: { display: true, position: 'top' },
                        title: { display: true, text: 'Total Processado por Turno (AM / PM)' }
                    }
                }
            });
        }
    </script>
</body>
</html>
