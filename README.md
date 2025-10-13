<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Surpresa Especial para o Amor da Minha Vida ❤️</title>
    <style>
        /* --- TEMA E CONFIGURAÇÃO GERAL --- */
        :root {
            /* Manter o destaque original para botões e corações */
            --cor-destaque: #DC143C; /* Carmesim (Rosa Avermelhado) */
            --cor-destaque-hover: #ff4d6e;

            /* Ajustes para o tema PRETO */
            --cor-fundo-geral: #000000;
            --cor-transparente-fosco: rgba(0, 0, 0, 0.8); /* Fundo escuro transparente/fosco */
            --cor-texto-principal: #FFFFFF; /* Texto branco para contraste no fundo escuro */
            --cor-caixas-fundo: rgba(255, 255, 255, 0.1); /* Fundo sutil para caixas de texto/contador */
        }

        body {
            margin: 0;
            padding: 0;
            font-family: 'Arial', sans-serif;
            background: var(--cor-fundo-geral); /* Fundo Preto */
            color: var(--cor-texto-principal); /* Texto Branco */
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        /* Corações caindo no fundo (Geral) */
        .heart-fall {
            position: fixed;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            overflow: hidden;
            z-index: 1; 
            pointer-events: none;
        }
        .heart {
            position: absolute;
            color: var(--cor-destaque); /* CORAÇÕES EM CARMESIM */
            font-size: 20px;
            animation: fall linear infinite;
        }
        @keyframes fall {
            0% { transform: translateY(-10vh) scale(0.5); opacity: 0.8; }
            100% { transform: translateY(100vh) scale(1.5); opacity: 0; }
        }

        /* --- CONTÊINER PRINCIPAL (Fosco e Transparente) --- */
        .container {
            width: 90%;
            max-width: 800px;
            padding: 30px;
            background: var(--cor-transparente-fosco); /* Fundo Preto Fosco */
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(255, 255, 255, 0.1); /* Sombra clara */
            text-align: center;
            z-index: 10;
            backdrop-filter: blur(5px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: all 0.5s ease-in-out;
            min-height: 400px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .tela {
            display: none;
            width: 100%;
            padding: 10px;
        }
        .tela.ativa {
            display: block;
        }
        
        /* --- ESTILOS DA PRIMEIRA TELA (EDIÇÃO) --- */
        #edicao h2, #edicao label {
            color: var(--cor-texto-principal); /* Garante que os rótulos sejam brancos */
        }

        #edicao input, #edicao textarea {
            width: 90%;
            padding: 10px;
            margin: 10px 0;
            border-radius: 8px;
            border: 1px solid #ccc;
            background: #222; /* Fundo escuro para os campos de input */
            color: var(--cor-texto-principal);
            box-sizing: border-box;
        }
        #edicao button, #btn-surpresa {
            background-color: var(--cor-destaque); /* BOTÕES EM CARMESIM */
            color: white;
            padding: 15px 30px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-size: 1.2em;
            margin-top: 20px;
            transition: background-color 0.3s;
        }
        #edicao button:hover, #btn-surpresa:hover {
            background-color: var(--cor-destaque-hover);
        }

        /* --- ESTILOS DA TELA PRINCIPAL --- */
        #nomes-casal-display {
            font-family: 'Brush Script MT', cursive; 
            color: var(--cor-destaque); /* NOME EM CARMESIM */
            font-size: 3.5em;
            margin-bottom: 25px;
            text-shadow: 2px 2px 5px rgba(255, 255, 255, 0.1);
        }
        .galeria {
            min-height: 50px;
            margin-bottom: 20px;
        }

        #texto-amor-display {
            margin: 25px 0;
            padding: 20px;
            background: var(--cor-caixas-fundo); /* Fundo transparente sutil */
            border-radius: 15px;
            border-left: 5px solid var(--cor-destaque); /* BORDA EM CARMESIM */
            text-align: left;
            font-style: italic;
            line-height: 1.6;
            color: var(--cor-texto-principal);
        }

        /* Estilo para a contagem de tempo */
        #contador-tempo {
            margin-bottom: 30px;
            padding: 15px;
            background: var(--cor-caixas-fundo); /* Fundo transparente sutil */
            border-radius: 15px;
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 15px;
        }
        .tempo-item {
            text-align: center;
            flex: 1 1 10%; 
            min-width: 60px;
        }
        .tempo-valor {
            font-size: 1.8em;
            color: var(--cor-destaque); /* VALORES EM CARMESIM */
            display: block;
            font-weight: bold;
        }
        .tempo-label {
            display: block;
            font-size: 0.7em;
            font-weight: normal;
        }

        /* Botão Final (Clique Aqui) */
        #btn-pedido {
            background-color: var(--cor-destaque); /* BOTÃO EM CARMESIM */
            color: white;
            padding: 25px 50px;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-size: 1.6em;
            font-weight: bold;
            transition: background-color 0.3s, transform 0.2s;
            box-shadow: 0 5px 15px rgba(220, 20, 60, 0.5);
            margin-top: 40px;
            animation: pulse 1.5s infinite;
        }
        #btn-pedido:hover {
            background-color: var(--cor-destaque-hover);
        }
        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(220, 20, 60, 0.7); }
            70% { box-shadow: 0 0 0 10px rgba(220, 20, 60, 0); }
            100% { box-shadow: 0 0 0 0 rgba(220, 20, 60, 0); }
        }

        /* --- POP-UP DE MÚSICA (Audio Player) --- */
        .audio-popup {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            padding: 10px 20px;
            background: rgba(0, 0, 0, 0.9); /* Fundo do player preto opaco */
            color: white;
            border-radius: 15px;
            z-index: 20;
            display: none; 
            align-items: center;
            box-shadow: 0 5px 20px rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(5px);
        }
        .audio-popup span {
            margin-right: 15px;
            font-size: 0.9em;
        }
        .audio-popup audio {
            /* Deixa os controles padrão do áudio */
            filter: invert(100%); /* Inverte as cores dos controles do player para que fiquem brancos */
            width: 200px;
            height: 40px;
        }
        
        /* --- ESTILOS DA TELA DE PEDIDO (FINAL) --- */
        #pedido p {
            font-size: 2.5em;
            margin-bottom: 40px;
            color: var(--cor-destaque); /* PEDIDO EM CARMESIM */
        }
        #pedido h1 {
            color: var(--cor-destaque); /* EU TE AMO! EM CARMESIM */
        }

        /* Corações do Pedido (Chuva de corações) */
        .pedido-heart-fall {
            position: fixed;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            overflow: hidden;
            z-index: 30; 
            pointer-events: none;
            display: none;
        }
        .pedido-heart {
            position: absolute;
            color: var(--cor-destaque); /* CORAÇÕES DE PEDIDO EM CARMESIM */
            font-size: 35px;
            animation: pedido-fall linear infinite;
        }
        @keyframes pedido-fall {
            0% { transform: translateY(-10vh) scale(0.8) rotate(0deg); opacity: 1; }
            100% { transform: translateY(100vh) scale(1.8) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>

    <div class="heart-fall" id="background-hearts"></div>

    <div class="container" id="main-container">

        <div class="tela ativa" id="edicao">
            <h2>✨ Primeiro, vamos editar a surpresa! ✨</h2>
            <form id="form-edicao">
                
                <label for="nome-casal">Nome do Casal (Ex: Ana & Pedro):</label>
                <input type="text" id="nome-casal" placeholder="Insira os nomes..." required><br>

                <label for="data-inicio">Data de Início do Namoro:</label>
                <input type="date" id="data-inicio" required><br>

                <label for="texto-personalizado">Seu Texto de Amor:</label>
                <textarea id="texto-personalizado" rows="5" placeholder="Escreva o texto que você quer que apareça..." required></textarea><br>
                
                <button type="submit">Começar</button>
            </form>
        </div>

        <div class="tela" id="surpresa">
            <h1>Preparado(a) para a Surpresa?</h1>
            <button id="btn-surpresa">Surpresa ❤️</button>
        </div>

        <div class="tela" id="principal">
            <h1 id="nomes-casal-display"></h1>
            
            <div class="galeria" id="galeria-fotos"></div>

            <p id="texto-amor-display"></p>

            <div id="contador-tempo">
                <div class="tempo-item"><span id="anos" class="tempo-valor">0</span><span class="tempo-label">Anos</span></div>
                <div class="tempo-item"><span id="meses" class="tempo-valor">0</span><span class="tempo-label">Meses</span></div>
                <div class="tempo-item"><span id="semanas" class="tempo-valor">0</span><span class="tempo-label">Semanas</span></div>
                <div class="tempo-item"><span id="dias" class="tempo-valor">0</span><span class="tempo-label">Dias</span></div>
                <div class="tempo-item"><span id="horas" class="tempo-valor">0</span><span class="tempo-label">Horas</span></div>
                <div class="tempo-item"><span id="minutos" class="tempo-valor">0</span><span class="tempo-label">Minutos</span></div>
                <div class="tempo-item"><span id="segundos" class="tempo-valor">0</span><span class="tempo-label">Segundos</span></div>
            </div>

            <button id="btn-pedido">Clique aqui ❤️</button>
        </div>

        <div class="tela" id="pedido">
            </div>

    </div>

    <div class="audio-popup" id="audio-player">
        <span>🎵 Música Aliança</span>
        <audio id="musica-alianca" controls loop>
            <source src="link_para_sua_musica_alianca.mp3" type="audio/mp3">
            Seu navegador não suporta o elemento de áudio.
        </audio>
    </div>

    <div class="pedido-heart-fall" id="pedido-hearts"></div>

    <script>
        // --- VARIÁVEIS DE ELEMENTOS ---
        const TELA_EDICAO = document.getElementById('edicao');
        const TELA_SURPRESA = document.getElementById('surpresa');
        const TELA_PRINCIPAL = document.getElementById('principal');
        const TELA_PEDIDO = document.getElementById('pedido');
        const BTN_SURPRESA = document.getElementById('btn-surpresa');
        const BTN_PEDIDO = document.getElementById('btn-pedido');
        const FORM_EDICAO = document.getElementById('form-edicao');
        const AUDIO_PLAYER = document.getElementById('audio-player');
        const MUSICA_ALIANCA = document.getElementById('musica-alianca');
        const PEDIDO_HEARTS_CONTAINER = document.getElementById('pedido-hearts');

        let dataInicioNamoro = null;
        let contadorInterval = null;

        // --- FUNÇÕES DE CONTROLE DE FLUXO ---
        function trocarTela(telaAtivar) {
            document.querySelectorAll('.tela').forEach(tela => tela.classList.remove('ativa'));
            telaAtivar.classList.add('ativa');
            
            // Controle do Áudio
            if (telaAtivar === TELA_PRINCIPAL) {
                AUDIO_PLAYER.style.display = 'flex';
                MUSICA_ALIANCA.play().catch(e => console.log("Música não pôde ser iniciada automaticamente: ", e)); 
            } else {
                AUDIO_PLAYER.style.display = 'none';
                MUSICA_ALIANCA.pause();
                if (contadorInterval) clearInterval(contadorInterval);
            }
            PEDIDO_HEARTS_CONTAINER.style.display = 'none';
        }

        // --- LÓGICA DE EDIÇÃO (TELA 1) ---
        FORM_EDICAO.addEventListener('submit', function(e) {
            e.preventDefault();

            const nomeCasal = document.getElementById('nome-casal').value.trim();
            const textoPersonalizado = document.getElementById('texto-personalizado').value.trim().replace(/\n/g, '<br>');
            const dataInicioStr = document.getElementById('data-inicio').value;

            // Validação
            if (!nomeCasal || !dataInicioStr || !textoPersonalizado) {
                alert("Por favor, preencha todos os campos obrigatórios (Nome, Data e Texto)!");
                return;
            }

            // Processar Dados
            document.getElementById('nomes-casal-display').textContent = nomeCasal;
            document.getElementById('texto-amor-display').innerHTML = textoPersonalizado;
            
            dataInicioNamoro = new Date(dataInicioStr + 'T00:00:00'); 
            
            // Avança para a tela de surpresa
            trocarTela(TELA_SURPRESA);
        });

        // --- LÓGICA DA TELA SURPRESA (TELA 2) ---
        BTN_SURPRESA.addEventListener('click', function() {
            trocarTela(TELA_PRINCIPAL);
            // Inicia o contador de tempo
            if (contadorInterval) clearInterval(contadorInterval);
            contadorInterval = setInterval(atualizarContador, 1000); 
        });

        // --- LÓGICA DO CONTADOR DE TEMPO ---
        function atualizarContador() {
            if (!dataInicioNamoro) return;

            const agora = new Date();
            const diferenca = agora - dataInicioNamoro;

            const msPorDia = 1000 * 60 * 60 * 24;
            
            const diasTotal = Math.floor(diferenca / msPorDia);
            const mesesTotal = Math.floor(diferenca / (msPorDia * 30.4375));
            const anos = Math.floor(diferenca / (msPorDia * 365.25));
            
            const horas = Math.floor((diferenca % msPorDia) / (1000 * 60 * 60));
            const minutos = Math.floor((diferenca % (1000 * 60 * 60)) / (1000 * 60));
            const segundos = Math.floor((diferenca % (1000 * 60)) / 1000);
            
            const semanas = Math.floor(diasTotal / 7);


            document.getElementById('anos').textContent = anos;
            document.getElementById('meses').textContent = mesesTotal;
            document.getElementById('semanas').textContent = semanas;
            document.getElementById('dias').textContent = diasTotal;
            document.getElementById('horas').textContent = horas;
            document.getElementById('minutos').textContent = minutos;
            document.getElementById('segundos').textContent = segundos;
        }


        // --- LÓGICA DO PEDIDO DE NAMORO (TELA 4) ---
        BTN_PEDIDO.addEventListener('click', function() {
            trocarTela(TELA_PEDIDO);
            
            // 1. Mostrar o pedido
            TELA_PEDIDO.innerHTML = `
                <p>Você aceita namorar comigo?</p>
                <div style="display:flex; justify-content: center; gap: 30px;">
                    <button id="btn-sim" style="padding: 15px 35px; font-size: 1.8em; background-color: green; color: white; border: none; border-radius: 10px; cursor: pointer;">SIM! ❤️</button>
                </div>
            `;
            
            // 2. Ativar a chuva de corações do pedido
            PEDIDO_HEARTS_CONTAINER.style.display = 'block';
            for (let i = 0; i < 50; i++) {
                criarCoracao(PEDIDO_HEARTS_CONTAINER, 'pedido-heart');
            }

            // 3. Adicionar evento ao botão SIM
            document.getElementById('btn-sim').addEventListener('click', function() {
                // Mensagem final
                TELA_PEDIDO.innerHTML = `
                    <h1 style="font-size: 3em; color: var(--cor-destaque); margin-bottom: 5px;">EU TE AMO!</h1>
                    <p style="font-size: 1.5em; margin-top: 0; color: var(--cor-texto-principal);">Obrigado &lt;3</p>
                `;
            });
        });

        // --- LÓGICA DOS CORAÇÕES CAINDO (GERAL) ---
        function criarCoracao(container, className) {
            const heart = document.createElement('div');
            heart.classList.add(className);
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 4 + 6 + 's';
            heart.style.animationDelay = Math.random() * 5 + 's';
            container.appendChild(heart);

            setTimeout(() => { heart.remove(); }, 12000); 
        }

        const backgroundHeartsContainer = document.getElementById('background-hearts');
        setInterval(() => {
            if (document.querySelectorAll('.heart-fall .heart').length < 30) {
                criarCoracao(backgroundHeartsContainer, 'heart');
            }
        }, 500);
        
        for (let i = 0; i < 20; i++) {
            criarCoracao(backgroundHeartsContainer, 'heart');
        }

    </script>
</body>
</html>
