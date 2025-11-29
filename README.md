<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistema de Rifas Online</title>
    <style>
        :root {
            --primary: #3498db;
            --secondary: #2ecc71;
            --danger: #e74c3c;
            --dark: #2c3e50;
            --light: #ecf0f1;
            --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: var(--dark);
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        header {
            background-color: var(--dark);
            color: white;
            padding: 1rem 0;
            box-shadow: var(--shadow);
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: var(--light);
        }
        
        nav ul {
            display: flex;
            list-style: none;
        }
        
        nav ul li {
            margin-left: 1.5rem;
        }
        
        nav ul li a {
            color: white;
            text-decoration: none;
            transition: color 0.3s;
        }
        
        nav ul li a:hover {
            color: var(--primary);
        }
        
        .hero {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 3rem 0;
            text-align: center;
            margin-bottom: 2rem;
        }
        
        .hero h1 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }
        
        .hero p {
            font-size: 1.2rem;
            max-width: 700px;
            margin: 0 auto;
        }
        
        .section-title {
            text-align: center;
            margin: 2rem 0;
            color: var(--dark);
        }
        
        .rifas-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 2rem;
            margin-bottom: 3rem;
        }
        
        .rifa-card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: transform 0.3s;
        }
        
        .rifa-card:hover {
            transform: translateY(-5px);
        }
        
        .rifa-image {
            height: 200px;
            background-color: #ddd;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            color: #777;
        }
        
        .rifa-info {
            padding: 1.5rem;
        }
        
        .rifa-title {
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
        }
        
        .rifa-description {
            color: #666;
            margin-bottom: 1rem;
        }
        
        .rifa-meta {
            display: flex;
            justify-content: space-between;
            margin-bottom: 1rem;
            font-size: 0.9rem;
        }
        
        .progress-bar {
            height: 8px;
            background-color: #eee;
            border-radius: 4px;
            margin-bottom: 1rem;
            overflow: hidden;
        }
        
        .progress {
            height: 100%;
            background-color: var(--secondary);
            border-radius: 4px;
        }
        
        .btn {
            display: inline-block;
            background-color: var(--primary);
            color: white;
            padding: 0.7rem 1.5rem;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            text-decoration: none;
            font-weight: bold;
            transition: background-color 0.3s;
        }
        
        .btn:hover {
            background-color: #2980b9;
        }
        
        .btn-success {
            background-color: var(--secondary);
        }
        
        .btn-success:hover {
            background-color: #27ae60;
        }
        
        .btn-danger {
            background-color: var(--danger);
        }
        
        .btn-danger:hover {
            background-color: #c0392b;
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }
        
        .modal-content {
            background-color: white;
            padding: 2rem;
            border-radius: 10px;
            width: 90%;
            max-width: 500px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }
        
        .close-modal {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: #777;
        }
        
        .form-group {
            margin-bottom: 1rem;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: bold;
        }
        
        .form-control {
            width: 100%;
            padding: 0.7rem;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 1rem;
        }
        
        footer {
            background-color: var(--dark);
            color: white;
            text-align: center;
            padding: 2rem 0;
            margin-top: 3rem;
        }
        
        .numbers-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(50px, 1fr));
            gap: 0.5rem;
            margin: 1.5rem 0;
            max-height: 300px;
            overflow-y: auto;
        }
        
        .number {
            background-color: #eee;
            border-radius: 5px;
            padding: 0.7rem;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .number:hover {
            background-color: #ddd;
        }
        
        .number.selected {
            background-color: var(--primary);
            color: white;
        }
        
        .number.sold {
            background-color: #ccc;
            cursor: not-allowed;
        }
        
        .admin-panel {
            background-color: white;
            padding: 2rem;
            border-radius: 10px;
            box-shadow: var(--shadow);
            margin-bottom: 2rem;
        }
        
        .admin-section {
            margin-bottom: 2rem;
            padding-bottom: 1.5rem;
            border-bottom: 1px solid #eee;
        }
        
        .winner-announcement {
            background-color: var(--secondary);
            color: white;
            padding: 1.5rem;
            border-radius: 10px;
            margin: 1.5rem 0;
            text-align: center;
        }
        
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                text-align: center;
            }
            
            nav ul {
                margin-top: 1rem;
            }
            
            .hero h1 {
                font-size: 2rem;
            }
            
            .rifas-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">RifasOnline</div>
                <nav>
                    <ul>
                        <li><a href="#" class="active">Início</a></li>
                        <li><a href="#" id="admin-link">Administração</a></li>
                        <li><a href="#" id="create-rifa-link">Criar Rifa</a></li>
                    </ul>
                </nav>
            </div>
        </div>
    </header>

    <section class="hero">
        <div class="container">
            <h1>Participe de Rifas Incríveis</h1>
            <p>Compre números para concorrer a prêmios exclusivos. Quando todas as rifas forem vendidas, o sorteio é realizado automaticamente!</p>
        </div>
    </section>

    <div class="container">
        <h2 class="section-title">Rifas Disponíveis</h2>
        
        <div class="rifas-grid" id="rifas-container">
            <!-- As rifas serão carregadas dinamicamente aqui -->
        </div>

        <div class="admin-panel" id="admin-panel" style="display: none;">
            <h2 class="section-title">Painel de Administração</h2>
            
            <div class="admin-section">
                <h3>Rifas Ativas</h3>
                <div id="admin-rifas-list">
                    <!-- Lista de rifas para administração -->
                </div>
            </div>
            
            <div class="admin-section">
                <h3>Sorteios Realizados</h3>
                <div id="sorteios-list">
                    <!-- Lista de sorteios realizados -->
                </div>
            </div>
        </div>
    </div>

    <!-- Modal para criar rifa -->
    <div class="modal" id="create-rifa-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Criar Nova Rifa</h2>
                <button class="close-modal">&times;</button>
            </div>
            <form id="create-rifa-form">
                <div class="form-group">
                    <label for="rifa-name">Nome do Prêmio</label>
                    <input type="text" id="rifa-name" class="form-control" required>
                </div>
                <div class="form-group">
                    <label for="rifa-description">Descrição</label>
                    <textarea id="rifa-description" class="form-control" rows="3" required></textarea>
                </div>
                <div class="form-group">
                    <label for="rifa-value">Valor Total (R$)</label>
                    <input type="number" id="rifa-value" class="form-control" min="1" required>
                </div>
                <div class="form-group">
                    <label for="rifa-ticket-price">Valor por Número (R$)</label>
                    <input type="number" id="rifa-ticket-price" class="form-control" min="1" required>
                </div>
                <div class="form-group">
                    <label for="rifa-image">URL da Imagem</label>
                    <input type="text" id="rifa-image" class="form-control">
                </div>
                <button type="submit" class="btn btn-success">Criar Rifa</button>
            </form>
        </div>
    </div>

    <!-- Modal para comprar números -->
    <div class="modal" id="buy-tickets-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 id="modal-rifa-title">Comprar Números</h2>
                <button class="close-modal">&times;</button>
            </div>
            <div id="rifa-details">
                <!-- Detalhes da rifa serão carregados aqui -->
            </div>
            <div class="numbers-grid" id="numbers-container">
                <!-- Os números serão carregados aqui -->
            </div>
            <div class="form-group">
                <label for="customer-email">Seu E-mail</label>
                <input type="email" id="customer-email" class="form-control" required>
            </div>
            <div class="form-group">
                <p id="selected-count">Nenhum número selecionado</p>
                <p id="total-price">Total: R$ 0,00</p>
            </div>
            <button id="confirm-purchase" class="btn btn-success" disabled>Confirmar Compra</button>
        </div>
    </div>

    <!-- Modal para resultado do sorteio -->
    <div class="modal" id="result-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h2>Resultado do Sorteio</h2>
                <button class="close-modal">&times;</button>
            </div>
            <div id="result-content">
                <!-- Conteúdo do resultado será carregado aqui -->
            </div>
        </div>
    </div>

    <footer>
        <div class="container">
            <p>&copy; 2023 RifasOnline - Todos os direitos reservados</p>
        </div>
    </footer>

    <script>
        // Dados de exemplo
        let rifas = JSON.parse(localStorage.getItem('rifas')) || [
            {
                id: 1,
                name: "Smartphone XYZ",
                description: "Um smartphone de última geração com câmera de 108MP",
                totalValue: 2000,
                ticketPrice: 10,
                soldTickets: 75,
                totalTickets: 200,
                image: "",
                status: "active", // active, completed
                tickets: [],
                winner: null
            },
            {
                id: 2,
                name: "TV 55 Polegadas",
                description: "TV LED 4K Ultra HD com Smart TV integrado",
                totalValue: 2500,
                ticketPrice: 25,
                soldTickets: 40,
                totalTickets: 100,
                image: "",
                status: "active",
                tickets: [],
                winner: null
            }
        ];

        // Elementos DOM
        const rifasContainer = document.getElementById('rifas-container');
        const adminPanel = document.getElementById('admin-panel');
        const adminRifasList = document.getElementById('admin-rifas-list');
        const sorteiosList = document.getElementById('sorteios-list');
        const createRifaModal = document.getElementById('create-rifa-modal');
        const buyTicketsModal = document.getElementById('buy-tickets-modal');
        const resultModal = document.getElementById('result-modal');
        const createRifaForm = document.getElementById('create-rifa-form');
        const numbersContainer = document.getElementById('numbers-container');
        const rifaDetails = document.getElementById('rifa-details');
        const confirmPurchase = document.getElementById('confirm-purchase');
        const customerEmail = document.getElementById('customer-email');
        const selectedCount = document.getElementById('selected-count');
        const totalPrice = document.getElementById('total-price');
        const resultContent = document.getElementById('result-content');

        // Variáveis globais
        let currentRifa = null;
        let selectedNumbers = [];

        // Inicialização
        document.addEventListener('DOMContentLoaded', function() {
            renderRifas();
            setupEventListeners();
        });

        // Configurar event listeners
        function setupEventListeners() {
            // Links de navegação
            document.getElementById('admin-link').addEventListener('click', function(e) {
                e.preventDefault();
                adminPanel.style.display = adminPanel.style.display === 'none' ? 'block' : 'none';
                renderAdminPanel();
            });

            document.getElementById('create-rifa-link').addEventListener('click', function(e) {
                e.preventDefault();
                createRifaModal.style.display = 'flex';
            });

            // Fechar modais
            document.querySelectorAll('.close-modal').forEach(button => {
                button.addEventListener('click', function() {
                    this.closest('.modal').style.display = 'none';
                });
            });

            // Criar rifa
            createRifaForm.addEventListener('submit', function(e) {
                e.preventDefault();
                createRifa();
            });

            // Comprar números
            confirmPurchase.addEventListener('click', function() {
                purchaseTickets();
            });

            // Validar e-mail para habilitar compra
            customerEmail.addEventListener('input', function() {
                validatePurchase();
            });
        }

        // Renderizar rifas na página principal
        function renderRifas() {
            rifasContainer.innerHTML = '';
            
            rifas.forEach(rifa => {
                if (rifa.status === 'active') {
                    const progress = (rifa.soldTickets / rifa.totalTickets) * 100;
                    
                    const rifaCard = document.createElement('div');
                    rifaCard.className = 'rifa-card';
                    rifaCard.innerHTML = `
                        <div class="rifa-image">
                            ${rifa.image ? `<img src="${rifa.image}" alt="${rifa.name}" style="width:100%;height:100%;object-fit:cover;">` : 'Imagem do Prêmio'}
                        </div>
                        <div class="rifa-info">
                            <h3 class="rifa-title">${rifa.name}</h3>
                            <p class="rifa-description">${rifa.description}</p>
                            <div class="rifa-meta">
                                <span>Valor: R$ ${rifa.totalValue.toFixed(2)}</span>
                                <span>Números: ${rifa.soldTickets}/${rifa.totalTickets}</span>
                            </div>
                            <div class="progress-bar">
                                <div class="progress" style="width: ${progress}%"></div>
                            </div>
                            <p>Valor por número: R$ ${rifa.ticketPrice.toFixed(2)}</p>
                            <button class="btn buy-ticket-btn" data-id="${rifa.id}">Comprar Números</button>
                        </div>
                    `;
                    
                    rifasContainer.appendChild(rifaCard);
                }
            });

            // Adicionar event listeners aos botões de compra
            document.querySelectorAll('.buy-ticket-btn').forEach(button => {
                button.addEventListener('click', function() {
                    const rifaId = parseInt(this.getAttribute('data-id'));
                    openBuyTicketsModal(rifaId);
                });
            });
        }

        // Abrir modal para comprar números
        function openBuyTicketsModal(rifaId) {
            currentRifa = rifas.find(r => r.id === rifaId);
            
            if (!currentRifa) return;
            
            // Atualizar título
            document.getElementById('modal-rifa-title').textContent = `Comprar Números - ${currentRifa.name}`;
            
            // Atualizar detalhes da rifa
            rifaDetails.innerHTML = `
                <p><strong>${currentRifa.name}</strong></p>
                <p>${currentRifa.description}</p>
                <p>Valor por número: R$ ${currentRifa.ticketPrice.toFixed(2)}</p>
                <p>Números disponíveis: ${currentRifa.totalTickets - currentRifa.soldTickets}</p>
            `;
            
            // Renderizar números
            renderNumbers();
            
            // Resetar seleção
            selectedNumbers = [];
            customerEmail.value = '';
            updateSelectionInfo();
            
            // Mostrar modal
            buyTicketsModal.style.display = 'flex';
        }

        // Renderizar números disponíveis
        function renderNumbers() {
            numbersContainer.innerHTML = '';
            
            for (let i = 1; i <= currentRifa.totalTickets; i++) {
                const numberElement = document.createElement('div');
                numberElement.className = 'number';
                numberElement.textContent = i;
                
                // Verificar se o número já foi vendido
                const isSold = currentRifa.tickets.some(ticket => ticket.number === i);
                
                if (isSold) {
                    numberElement.classList.add('sold');
                } else {
                    numberElement.addEventListener('click', function() {
                        toggleNumberSelection(i);
                    });
                }
                
                numbersContainer.appendChild(numberElement);
            }
        }

        // Alternar seleção de número
        function toggleNumberSelection(number) {
            const index = selectedNumbers.indexOf(number);
            
            if (index === -1) {
                selectedNumbers.push(number);
            } else {
                selectedNumbers.splice(index, 1);
            }
            
            updateSelectionInfo();
            highlightSelectedNumbers();
        }

        // Atualizar informações de seleção
        function updateSelectionInfo() {
            const count = selectedNumbers.length;
            const total = count * currentRifa.ticketPrice;
            
            selectedCount.textContent = count === 0 ? 'Nenhum número selecionado' : 
                                      count === 1 ? '1 número selecionado' : 
                                      `${count} números selecionados`;
            
            totalPrice.textContent = `Total: R$ ${total.toFixed(2)}`;
            
            validatePurchase();
        }

        // Destacar números selecionados
        function highlightSelectedNumbers() {
            const numberElements = numbersContainer.querySelectorAll('.number:not(.sold)');
            
            numberElements.forEach(element => {
                const number = parseInt(element.textContent);
                
                if (selectedNumbers.includes(number)) {
                    element.classList.add('selected');
                } else {
                    element.classList.remove('selected');
                }
            });
        }

        // Validar se a compra pode ser realizada
        function validatePurchase() {
            const hasSelectedNumbers = selectedNumbers.length > 0;
            const hasValidEmail = customerEmail.value && /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(customerEmail.value);
            
            confirmPurchase.disabled = !(hasSelectedNumbers && hasValidEmail);
        }

        // Realizar compra de números
        function purchaseTickets() {
            if (!currentRifa || selectedNumbers.length === 0 || !customerEmail.value) return;
            
            // Adicionar tickets vendidos
            selectedNumbers.forEach(number => {
                currentRifa.tickets.push({
                    number: number,
                    email: customerEmail.value,
                    purchaseDate: new Date().toISOString()
                });
            });
            
            // Atualizar contagem de tickets vendidos
            currentRifa.soldTickets += selectedNumbers.length;
            
            // Verificar se a rifa foi totalmente vendida
            if (currentRifa.soldTickets >= currentRifa.totalTickets) {
                completeRifa();
            }
            
            // Salvar no localStorage
            localStorage.setItem('rifas', JSON.stringify(rifas));
            
            // Fechar modal e atualizar interface
            buyTicketsModal.style.display = 'none';
            renderRifas();
            
            // Mostrar confirmação
            alert(`Compra realizada com sucesso! Você adquiriu os números: ${selectedNumbers.join(', ')}`);
        }

        // Finalizar rifa e realizar sorteio
        function completeRifa() {
            // Selecionar um ganhador aleatório
            const randomIndex = Math.floor(Math.random() * currentRifa.tickets.length);
            const winnerTicket = currentRifa.tickets[randomIndex];
            
            // Atualizar rifa
            currentRifa.status = 'completed';
            currentRifa.winner = {
                number: winnerTicket.number,
                email: winnerTicket.email,
                drawDate: new Date().toISOString()
            };
            
            // Simular envio de e-mail
            sendWinnerEmail(currentRifa);
            
            // Mostrar resultado
            showResult(currentRifa);
        }

        // Simular envio de e-mail para o ganhador
        function sendWinnerEmail(rifa) {
            // Em um sistema real, aqui seria feita uma chamada para um servidor
            console.log(`E-mail enviado para: ${rifa.winner.email}`);
            console.log(`Assunto: Parabéns! Você ganhou a rifa: ${rifa.name}`);
            console.log(`Conteúdo: 
                Olá!
                
                Parabéns! O número ${rifa.winner.number} foi sorteado na rifa "${rifa.name}".
                
                Para retirar seu prêmio, entre em contato conosco através do e-mail contato@rifasonline.com 
                ou pelo telefone (11) 99999-9999 dentro de 30 dias.
                
                Atenciosamente,
                Equipe RifasOnline
            `);
        }

        // Mostrar resultado do sorteio
        function showResult(rifa) {
            resultContent.innerHTML = `
                <div class="winner-announcement">
                    <h3>Parabéns ao Ganhador!</h3>
                    <p>Rifa: <strong>${rifa.name}</strong></p>
                    <p>Número Sorteado: <strong>${rifa.winner.number}</strong></p>
                    <p>Ganhador: <strong>${rifa.winner.email}</strong></p>
                    <p>Data do Sorteio: ${new Date(rifa.winner.drawDate).toLocaleDateString('pt-BR')}</p>
                </div>
                <p>Um e-mail foi enviado para o ganhador com instruções para retirar o prêmio.</p>
            `;
            
            resultModal.style.display = 'flex';
        }

        // Criar nova rifa
        function createRifa() {
            const name = document.getElementById('rifa-name').value;
            const description = document.getElementById('rifa-description').value;
            const totalValue = parseFloat(document.getElementById('rifa-value').value);
            const ticketPrice = parseFloat(document.getElementById('rifa-ticket-price').value);
            const image = document.getElementById('rifa-image').value;
            
            // Calcular número total de tickets
            const totalTickets = Math.ceil(totalValue / ticketPrice);
            
            // Criar nova rifa
            const newRifa = {
                id: rifas.length > 0 ? Math.max(...rifas.map(r => r.id)) + 1 : 1,
                name,
                description,
                totalValue,
                ticketPrice,
                totalTickets,
                soldTickets: 0,
                image,
                status: 'active',
                tickets: [],
                winner: null
            };
            
            // Adicionar à lista
            rifas.push(newRifa);
            
            // Salvar no localStorage
            localStorage.setItem('rifas', JSON.stringify(rifas));
            
            // Fechar modal e atualizar interface
            createRifaModal.style.display = 'none';
            createRifaForm.reset();
            renderRifas();
        }

        // Renderizar painel de administração
        function renderAdminPanel() {
            // Lista de rifas ativas
            adminRifasList.innerHTML = '';
            
            rifas.forEach(rifa => {
                if (rifa.status === 'active') {
                    const rifaElement = document.createElement('div');
                    rifaElement.className = 'rifa-card';
                    rifaElement.innerHTML = `
                        <div class="rifa-info">
                            <h3 class="rifa-title">${rifa.name}</h3>
                            <p>Valor total: R$ ${rifa.totalValue.toFixed(2)}</p>
                            <p>Números vendidos: ${rifa.soldTickets}/${rifa.totalTickets}</p>
                            <p>Arrecadado: R$ ${(rifa.soldTickets * rifa.ticketPrice).toFixed(2)}</p>
                            <button class="btn btn-danger force-draw-btn" data-id="${rifa.id}">Forçar Sorteio</button>
                        </div>
                    `;
                    
                    adminRifasList.appendChild(rifaElement);
                }
            });
            
            // Lista de sorteios realizados
            sorteiosList.innerHTML = '';
            
            const completedRifas = rifas.filter(rifa => rifa.status === 'completed');
            
            if (completedRifas.length === 0) {
                sorteiosList.innerHTML = '<p>Nenhum sorteio realizado ainda.</p>';
            } else {
                completedRifas.forEach(rifa => {
                    const sorteioElement = document.createElement('div');
                    sorteioElement.className = 'rifa-card';
                    sorteioElement.innerHTML = `
                        <div class="rifa-info">
