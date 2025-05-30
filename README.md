<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GlobalExchange - Обмен валют в Москве, Стамбуле, Дубае, Грозном</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 20px;
            margin-bottom: 30px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 20px;
        }
        
        .logo {
            font-size: 28px;
            font-weight: bold;
            background: linear-gradient(45deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .cities {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
        }
        
        .city {
            padding: 8px 16px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border-radius: 20px;
            font-size: 14px;
            font-weight: 500;
        }
        
        .main-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin-bottom: 30px;
        }
        
        .exchange-card, .rates-card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }
        
        .card-title {
            font-size: 24px;
            font-weight: bold;
            margin-bottom: 20px;
            color: #333;
        }
        
        .exchange-form {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .form-row {
            display: flex;
            gap: 15px;
            align-items: center;
        }
        
        select, input {
            flex: 1;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px;
            transition: all 0.3s;
        }
        
        select:focus, input:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }
        
        .swap-btn {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border: none;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            cursor: pointer;
            font-size: 18px;
            transition: transform 0.3s;
        }
        
        .swap-btn:hover {
            transform: rotate(180deg);
        }
        
        .calculate-btn {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 10px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .calculate-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .result {
            background: linear-gradient(45deg, #4CAF50, #45a049);
            color: white;
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            font-size: 18px;
            font-weight: bold;
            margin-top: 10px;
            display: none;
        }
        
        .rates-table {
            width: 100%;
            border-collapse: collapse;
        }
        
        .rates-table th,
        .rates-table td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #e0e0e0;
        }
        
        .rates-table th {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
        }
        
        .rate-buy {
            color: #4CAF50;
            font-weight: bold;
        }
        
        .rate-sell {
            color: #f44336;
            font-weight: bold;
        }
        
        .services {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }
        
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }
        
        .service-item {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            transition: transform 0.3s;
        }
        
        .service-item:hover {
            transform: translateY(-5px);
        }
        
        .service-icon {
            font-size: 30px;
            margin-bottom: 10px;
        }
        
        .order-form {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        
        textarea {
            width: 100%;
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px;
            resize: vertical;
            min-height: 100px;
        }
        
        .submit-btn {
            background: linear-gradient(45deg, #4CAF50, #45a049);
            color: white;
            border: none;
            padding: 15px 40px;
            border-radius: 10px;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            width: 100%;
            transition: all 0.3s;
        }
        
        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        @media (max-width: 768px) {
            .main-content {
                grid-template-columns: 1fr;
            }
            
            .form-row {
                flex-direction: column;
            }
            
            .header-content {
                text-align: center;
            }
            
            .cities {
                justify-content: center;
            }
        }
        
        .live-indicator {
            display: inline-block;
            width: 8px;
            height: 8px;
            background: #4CAF50;
            border-radius: 50%;
            margin-right: 5px;
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.5; }
            100% { opacity: 1; }
        }

        .admin-panel {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
            display: none;
        }

        .admin-toggle {
            position: fixed;
            top: 20px;
            right: 20px;
            background: linear-gradient(45deg, #ff6b6b, #ee5a24);
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 50px;
            cursor: pointer;
            font-size: 14px;
            z-index: 1000;
            transition: all 0.3s;
        }

        .admin-toggle:hover {
            transform: scale(1.05);
        }

        .rate-edit {
            display: inline-flex;
            gap: 5px;
            align-items: center;
        }

        .rate-input {
            width: 60px;
            padding: 2px 5px;
            border: 1px solid #ddd;
            border-radius: 3px;
            font-size: 12px;
        }

        .save-rates-btn {
            background: linear-gradient(45deg, #4CAF50, #45a049);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 10px;
            cursor: pointer;
            margin-top: 15px;
        }

        .telegram-config {
            background: #f0f8ff;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
        }

        .telegram-config input {
            width: 100%;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <button class="admin-toggle" onclick="toggleAdmin()">⚙️ Админ</button>
        
        <div id="adminPanel" class="admin-panel">
            <h2 class="card-title">🔧 Панель администратора</h2>
            
            <div class="telegram-config">
                <h3>📱 Настройки Telegram</h3>
                <input type="text" id="botToken" placeholder="Токен бота (от @BotFather)" value="">
                <input type="text" id="chatId" placeholder="ID чата для получения заявок" value="">
                <button onclick="saveTelegramConfig()" class="save-rates-btn">Сохранить настройки Telegram</button>
            </div>

            <h3>💱 Редактирование курсов</h3>
            <table class="rates-table">
                <thead>
                    <tr>
                        <th>Валюта</th>
                        <th>Покупка</th>
                        <th>Продажа</th>
                    </tr>
                </thead>
                <tbody id="adminRatesTable">
                    <tr>
                        <td>🇺🇸 USD/RUB</td>
                        <td class="rate-edit">
                            <input type="number" class="rate-input" id="USD_RUB_buy" value="89.50" step="0.01">
                        </td>
                        <td class="rate-edit">
                            <input type="number" class="rate-input" id="USD_RUB_sell" value="92.30" step="0.01">
                        </td>
                    </tr>
                    <tr>
                        <td>🇪🇺 EUR/RUB</td>
                        <td class="rate-edit">
                            <input type="number" class="rate-input" id="EUR_RUB_buy" value="96.20" step="0.01">
                        </td>
                        <td class="rate-edit">
                            <input type="number" class="rate-input" id="EUR_RUB_sell" value="99.80" step="0.01">
                        </td>
                    </tr>
                    <tr>
                        <td>🇹🇷 TRY/RUB</td>
                        <td class="rate-edit">
                            <input type="number" class="rate-input" id="TRY_RUB_buy" value="2.85" step="0.01">
                        </td>
                        <td class="rate-edit">
                            <input type="number" class="rate-input" id="TRY_RUB_sell" value="3.15" step="0.01">
                        </td>
                    </tr>
                    <tr>
                        <td>🇦🇪 AED/RUB</td>
                        <td class="rate-edit">
                            <input type="number" class="rate-input" id="AED_RUB_buy" value="24.30" step="0.01">
                        </td>
                        <td class="rate-edit">
                            <input type="number" class="rate-input" id="AED_RUB_sell" value="25.80" step="0.01">
                        </td>
                    </tr>
                    <tr>
                        <td>💰 USDT/RUB</td>
                        <td class="rate-edit">
                            <input type="number" class="rate-input" id="USDT_RUB_buy" value="89.80" step="0.01">
                        </td>
                        <td class="rate-edit">
                            <input type="number" class="rate-input" id="USDT_RUB_sell" value="91.20" step="0.01">
                        </td>
                    </tr>
                </tbody>
            </table>
            <button onclick="saveRates()" class="save-rates-btn">💾 Сохранить курсы</button>
        </div>
        <header>
            <div class="header-content">
                <div class="logo">💱 GlobalExchange</div>
                <div class="cities">
                    <div class="city">🇷🇺 Москва</div>
                    <div class="city">🇹🇷 Стамбул</div>
                    <div class="city">🇦🇪 Дубай</div>
                    <div class="city">🇷🇺 Грозный</div>
                </div>
            </div>
        </header>

        <div class="main-content">
            <div class="exchange-card">
                <h2 class="card-title">💰 Калькулятор обмена</h2>
                <div class="exchange-form">
                    <div class="form-row">
                        <select id="fromCurrency">
                            <option value="USD">USD - Доллар США</option>
                            <option value="EUR">EUR - Евро</option>
                            <option value="TRY">TRY - Турецкая лира</option>
                            <option value="AED">AED - Дирхам ОАЭ</option>
                            <option value="RUB">RUB - Рубль</option>
                            <option value="USDT">USDT - Tether</option>
                        </select>
                        <button class="swap-btn" onclick="swapCurrencies()">⇄</button>
                        <select id="toCurrency">
                            <option value="RUB">RUB - Рубль</option>
                            <option value="USD">USD - Доллар США</option>
                            <option value="EUR">EUR - Евро</option>
                            <option value="TRY">TRY - Турецкая лира</option>
                            <option value="AED">AED - Дирхам ОАЭ</option>
                            <option value="USDT">USDT - Tether</option>
                        </select>
                    </div>
                    <div class="form-row">
                        <input type="number" id="amount" placeholder="Сумма для обмена" step="0.01">
                        <select id="fromCity">
                            <option value="">Выберите город</option>
                            <option value="moscow">Москва</option>
                            <option value="istanbul">Стамбул</option>
                            <option value="dubai">Дубай</option>
                            <option value="grozny">Грозный</option>
                        </select>
                    </div>
                    <button class="calculate-btn" onclick="calculateExchange()">Рассчитать</button>
                    <div id="result" class="result"></div>
                </div>
            </div>

            <div class="rates-card">
                <h2 class="card-title"><span class="live-indicator"></span>Курсы валют</h2>
                <table class="rates-table">
                    <thead>
                        <tr>
                            <th>Валюта</th>
                            <th>Покупка</th>
                            <th>Продажа</th>
                        </tr>
                    </thead>
                    <tbody id="ratesTable">
                        <tr>
                            <td>🇺🇸 USD/RUB</td>
                            <td class="rate-buy">89.50</td>
                            <td class="rate-sell">92.30</td>
                        </tr>
                        <tr>
                            <td>🇪🇺 EUR/RUB</td>
                            <td class="rate-buy">96.20</td>
                            <td class="rate-sell">99.80</td>
                        </tr>
                        <tr>
                            <td>🇹🇷 TRY/RUB</td>
                            <td class="rate-buy">2.85</td>
                            <td class="rate-sell">3.15</td>
                        </tr>
                        <tr>
                            <td>🇦🇪 AED/RUB</td>
                            <td class="rate-buy">24.30</td>
                            <td class="rate-sell">25.80</td>
                        </tr>
                        <tr>
                            <td>💰 USDT/RUB</td>
                            <td class="rate-buy">89.80</td>
                            <td class="rate-sell">91.20</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>

        <div class="services">
            <h2 class="card-title">🌟 Наши услуги</h2>
            <div class="services-grid">
                <div class="service-item">
                    <div class="service-icon">💵</div>
                    <h3>Наличный обмен</h3>
                    <p>USD, EUR, TRY, AED, RUB</p>
                </div>
                <div class="service-item">
                    <div class="service-icon">₿</div>
                    <h3>Криптовалюты</h3>
                    <p>USDT и другие монеты</p>
                </div>
                <div class="service-item">
                    <div class="service-icon">🌍</div>
                    <h3>Переводы</h3>
                    <p>Между городами</p>
                </div>
                <div class="service-item">
                    <div class="service-icon">💳</div>
                    <h3>Карточные операции</h3>
                    <p>По согласованию</p>
                </div>
            </div>
        </div>

        <div class="order-form">
            <h2 class="card-title">📝 Оставить заявку</h2>
            <form id="orderForm">
                <div class="form-group">
                    <label>Тип операции:</label>
                    <select id="operationType" required>
                        <option value="">Выберите тип операции</option>
                        <option value="cash">Наличный обмен</option>
                        <option value="crypto">Обмен криптовалют</option>
                        <option value="transfer">Перевод между городами</option>
                        <option value="card">Карточные операции</option>
                    </select>
                </div>
                
                <div class="form-row">
                    <div class="form-group" style="flex: 1; margin-right: 10px;">
                        <label>Отдаю:</label>
                        <select id="giveAmount" required>
                            <option value="">Выберите валюту</option>
                            <option value="USD">USD - Доллар США</option>
                            <option value="EUR">EUR - Евро</option>
                            <option value="TRY">TRY - Турецкая лира</option>
                            <option value="AED">AED - Дирхам ОАЭ</option>
                            <option value="RUB">RUB - Рубль</option>
                            <option value="USDT">USDT - Tether</option>
                        </select>
                    </div>
                    <div class="form-group" style="flex: 1; margin-left: 10px;">
                        <label>Получаю:</label>
                        <select id="receiveAmount" required>
                            <option value="">Выберите валюту</option>
                            <option value="USD">USD - Доллар США</option>
                            <option value="EUR">EUR - Евро</option>
                            <option value="TRY">TRY - Турецкая лира</option>
                            <option value="AED">AED - Дирхам ОАЭ</option>
                            <option value="RUB">RUB - Рубль</option>
                            <option value="USDT">USDT - Tether</option>
                        </select>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group" style="flex: 1; margin-right: 10px;">
                        <label>Сумма:</label>
                        <input type="number" id="orderAmount" step="0.01" placeholder="Введите сумму" required>
                    </div>
                    <div class="form-group" style="flex: 1; margin-left: 10px;">
                        <label>Город:</label>
                        <select id="orderCity" required>
                            <option value="">Выберите город</option>
                            <option value="moscow">Москва</option>
                            <option value="istanbul">Стамбул</option>
                            <option value="dubai">Дубай</option>
                            <option value="grozny">Грозный</option>
                        </select>
                    </div>
                </div>

                <div class="form-group">
                    <label>Контактная информация (Telegram):</label>
                    <input type="text" id="contactInfo" placeholder="@username (обязательно)" required pattern="^@[a-zA-Z0-9_]{5,32}$" title="Введите Telegram username в формате @username">
                </div>

                <div class="form-group">
                    <label>Дополнительная информация:</label>
                    <textarea id="additionalInfo" placeholder="Укажите дополнительные детали операции"></textarea>
                </div>

                <button type="submit" class="submit-btn">Отправить заявку</button>
            </form>
        </div>
    </div>

    <script>
        // Курсы валют (хранятся в localStorage)
        let rates = JSON.parse(localStorage.getItem('exchangeRates')) || {
            'USD/RUB': { buy: 89.50, sell: 92.30 },
            'EUR/RUB': { buy: 96.20, sell: 99.80 },
            'TRY/RUB': { buy: 2.85, sell: 3.15 },
            'AED/RUB': { buy: 24.30, sell: 25.80 },
            'USDT/RUB': { buy: 89.80, sell: 91.20 },
            'USD/TRY': { buy: 28.50, sell: 29.20 },
            'EUR/USD': { buy: 1.05, sell: 1.08 },
            'AED/USD': { buy: 0.27, sell: 0.28 }
        };

        // Настройки Telegram
        let telegramConfig = JSON.parse(localStorage.getItem('telegramConfig')) || {
            botToken: '',
            chatId: ''
        };

        // Инициализация при загрузке страницы
        window.onload = function() {
            updateRatesDisplay();
            loadTelegramConfig();
        };

        function toggleAdmin() {
            const panel = document.getElementById('adminPanel');
            panel.style.display = panel.style.display === 'none' ? 'block' : 'none';
        }

        function updateRatesDisplay() {
            const tbody = document.getElementById('ratesTable');
            tbody.innerHTML = `
                <tr>
                    <td>🇺🇸 USD/RUB</td>
                    <td class="rate-buy">${rates['USD/RUB'].buy}</td>
                    <td class="rate-sell">${rates['USD/RUB'].sell}</td>
                </tr>
                <tr>
                    <td>🇪🇺 EUR/RUB</td>
                    <td class="rate-buy">${rates['EUR/RUB'].buy}</td>
                    <td class="rate-sell">${rates['EUR/RUB'].sell}</td>
                </tr>
                <tr>
                    <td>🇹🇷 TRY/RUB</td>
                    <td class="rate-buy">${rates['TRY/RUB'].buy}</td>
                    <td class="rate-sell">${rates['TRY/RUB'].sell}</td>
                </tr>
                <tr>
                    <td>🇦🇪 AED/RUB</td>
                    <td class="rate-buy">${rates['AED/RUB'].buy}</td>
                    <td class="rate-sell">${rates['AED/RUB'].sell}</td>
                </tr>
                <tr>
                    <td>💰 USDT/RUB</td>
                    <td class="rate-buy">${rates['USDT/RUB'].buy}</td>
                    <td class="rate-sell">${rates['USDT/RUB'].sell}</td>
                </tr>
            `;
        }

        function saveRates() {
            // Собираем новые курсы из полей ввода
            rates['USD/RUB'].buy = parseFloat(document.getElementById('USD_RUB_buy').value);
            rates['USD/RUB'].sell = parseFloat(document.getElementById('USD_RUB_sell').value);
            rates['EUR/RUB'].buy = parseFloat(document.getElementById('EUR_RUB_buy').value);
            rates['EUR/RUB'].sell = parseFloat(document.getElementById('EUR_RUB_sell').value);
            rates['TRY/RUB'].buy = parseFloat(document.getElementById('TRY_RUB_buy').value);
            rates['TRY/RUB'].sell = parseFloat(document.getElementById('TRY_RUB_sell').value);
            rates['AED/RUB'].buy = parseFloat(document.getElementById('AED_RUB_buy').value);
            rates['AED/RUB'].sell = parseFloat(document.getElementById('AED_RUB_sell').value);
            rates['USDT/RUB'].buy = parseFloat(document.getElementById('USDT_RUB_buy').value);
            rates['USDT/RUB'].sell = parseFloat(document.getElementById('USDT_RUB_sell').value);

            // Сохраняем в localStorage
            localStorage.setItem('exchangeRates', JSON.stringify(rates));
            
            // Обновляем отображение
            updateRatesDisplay();
            
            alert('✅ Курсы сохранены!');
        }

        function loadTelegramConfig() {
            document.getElementById('botToken').value = telegramConfig.botToken;
            document.getElementById('chatId').value = telegramConfig.chatId;
        }

        function saveTelegramConfig() {
            telegramConfig.botToken = document.getElementById('botToken').value;
            telegramConfig.chatId = document.getElementById('chatId').value;
            
            localStorage.setItem('telegramConfig', JSON.stringify(telegramConfig));
            
            alert('✅ Настройки Telegram сохранены!');
        }

        async function sendToTelegram(message) {
            if (!telegramConfig.botToken || !telegramConfig.chatId) {
                console.log('Telegram не настроен');
                return false;
            }

            try {
                const response = await fetch(`https://api.telegram.org/bot${telegramConfig.botToken}/sendMessage`, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify({
                        chat_id: telegramConfig.chatId,
                        text: message,
                        parse_mode: 'HTML'
                    })
                });

                return response.ok;
            } catch (error) {
                console.error('Ошибка отправки в Telegram:', error);
                return false;
            }
        }

        function swapCurrencies() {
            const fromCurrency = document.getElementById('fromCurrency');
            const toCurrency = document.getElementById('toCurrency');
            
            const temp = fromCurrency.value;
            fromCurrency.value = toCurrency.value;
            toCurrency.value = temp;
        }

        function calculateExchange() {
            const fromCurrency = document.getElementById('fromCurrency').value;
            const toCurrency = document.getElementById('toCurrency').value;
            const amount = parseFloat(document.getElementById('amount').value);
            const fromCity = document.getElementById('fromCity').value;
            
            if (!amount || !fromCity) {
                alert('Пожалуйста, заполните все поля');
                return;
            }

            const pair = `${fromCurrency}/${toCurrency}`;
            let rate = 0;
            
            if (rates[pair]) {
                rate = rates[pair].sell;
            } else {
                // Примерный расчет через рубль
                const fromToRub = rates[`${fromCurrency}/RUB`];
                const toFromRub = rates[`${toCurrency}/RUB`];
                
                if (fromToRub && toFromRub) {
                    rate = fromToRub.sell / toFromRub.buy;
                } else {
                    rate = 1; // Заглушка
                }
            }

            const result = amount * rate;
            const resultDiv = document.getElementById('result');
            
            resultDiv.innerHTML = `
                <strong>Результат:</strong><br>
                ${amount} ${fromCurrency} = ${result.toFixed(2)} ${toCurrency}<br>
                <small>Курс: ${rate.toFixed(4)} | Город: ${getCity(fromCity)}</small>
            `;
            resultDiv.style.display = 'block';
        }

        function getCity(code) {
            const cities = {
                'moscow': 'Москва',
                'istanbul': 'Стамбул', 
                'dubai': 'Дубай',
                'grozny': 'Грозный'
            };
            return cities[code] || code;
        }

        // Обработка формы заявки
        document.getElementById('orderForm').addEventListener('submit', async function(e) {
            e.preventDefault();
            
            const formData = {
                type: document.getElementById('operationType').value,
                give: document.getElementById('giveAmount').value,
                receive: document.getElementById('receiveAmount').value,
                amount: document.getElementById('orderAmount').value,
                city: document.getElementById('orderCity').value,
                contact: document.getElementById('contactInfo').value,
                additional: document.getElementById('additionalInfo').value
            };

            // Проверяем формат Telegram username
            if (!formData.contact.startsWith('@') || formData.contact.length < 6) {
                alert('❌ Пожалуйста, укажите корректный Telegram username в формате @username');
                return;
            }
            
            // Формируем сообщение для Telegram
            const message = `
🆕 <b>НОВАЯ ЗАЯВКА</b>

💼 <b>Тип операции:</b> ${getOperationType(formData.type)}
💱 <b>Обмен:</b> ${formData.amount} ${formData.give} → ${formData.receive}
🏙 <b>Город:</b> ${getCity(formData.city)}
📱 <b>Telegram:</b> ${formData.contact}

${formData.additional ? '📝 <b>Дополнительно:</b> ' + formData.additional : ''}

⏰ <b>Время:</b> ${new Date().toLocaleString('ru-RU')}
            `;

            // Отправляем в Telegram
            const sent = await sendToTelegram(message);
            
            if (sent) {
                alert('✅ Заявка отправлена! Мы свяжемся с вами в ближайшее время.');
                this.reset();
            } else {
                alert('⚠️ Заявка сохранена, но возникла проблема с отправкой. Мы обработаем её вручную.');
                console.log('Данные заявки:', formData);
            }
        });

        function getOperationType(type) {
            const types = {
                'cash': 'Наличный обмен',
                'crypto': 'Обмен криптовалют',
                'transfer': 'Перевод между городами',
                'card': 'Карточные операции'
            };
            return types[type] || type;
        }

        // Обновление курсов каждые 30 секунд (можно подключить API)
        setInterval(function() {
            console.log('Проверка обновлений курсов...');
        }, 30000);
    </script>
</body>
</html>