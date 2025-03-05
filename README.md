<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BetMaster - Online Betting Platform</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f0f2f5;
            color: #333;
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        header {
            background-color: #1a2a3a;
            color: white;
            padding: 15px 0;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: #4CAF50;
        }

        .nav-links {
            display: flex;
            gap: 20px;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            padding: 5px 10px;
            border-radius: 4px;
            transition: background-color 0.3s;
        }

        .nav-links a:hover {
            background-color: rgba(255,255,255,0.1);
        }

        .user-actions {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .user-profile {
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
        }

        .profile-img {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background-color: #ddd;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .profile-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 4px;
            cursor: pointer;
            font-weight: bold;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: #3e8e41;
        }

        .main-content {
            display: flex;
            margin-top: 30px;
            gap: 30px;
        }

        .sidebar {
            flex: 1;
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .betting-area {
            flex: 3;
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .bet-card {
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 15px;
            transition: transform 0.3s;
        }

        .bet-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .bet-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
        }

        .bet-teams {
            font-weight: bold;
            font-size: 1.2rem;
        }

        .bet-time {
            color: #666;
        }

        .bet-options {
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }

        .bet-option {
            flex: 1;
            text-align: center;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .bet-option:hover {
            background-color: #f0f2f5;
        }

        .bet-option.selected {
            background-color: #4CAF50;
            color: white;
            border-color: #4CAF50;
        }

        .bet-option-label {
            font-weight: bold;
        }

        .bet-option-odds {
            color: #4CAF50;
            font-weight: bold;
        }

        .bet-option.selected .bet-option-odds {
            color: white;
        }

        .bet-slip {
            margin-top: 20px;
        }

        .balance {
            font-size: 1.5rem;
            margin-bottom: 20px;
            color: #4CAF50;
        }

        .bet-input {
            display: flex;
            margin-top: 15px;
            gap: 10px;
        }

        input[type="number"] {
            flex: 1;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .modal-content {
            background-color: white;
            padding: 30px;
            border-radius: 8px;
            width: 90%;
            max-width: 500px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }

        .form-group input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }

        .close {
            float: right;
            font-size: 1.5rem;
            cursor: pointer;
        }

        .bet-slip-items {
            margin-bottom: 20px;
        }

        .bet-slip-item {
            display: flex;
            justify-content: space-between;
            padding: 10px;
            border-bottom: 1px solid #ddd;
        }

        .bet-slip-total {
            display: flex;
            justify-content: space-between;
            font-weight: bold;
            padding: 10px 0;
        }

        .empty-slip {
            text-align: center;
            padding: 20px;
            color: #666;
        }

        .section-title {
            font-size: 1.2rem;
            margin-bottom: 15px;
            padding-bottom: 5px;
            border-bottom: 1px solid #ddd;
        }

        footer {
            margin-top: 50px;
            background-color: #1a2a3a;
            color: white;
            padding: 20px 0;
            text-align: center;
        }

        .deposit-withdraw {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
        }

        .deposit-withdraw button {
            flex: 1;
        }

        .tabs {
            display: flex;
            margin-bottom: 20px;
            border-bottom: 1px solid #ddd;
        }

        .tab {
            padding: 10px 15px;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            transition: all 0.3s;
        }

        .tab.active {
            border-bottom-color: #4CAF50;
            color: #4CAF50;
            font-weight: bold;
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        .live-match {
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 15px;
        }

        .live-match-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
        }

        .live-match-teams {
            font-weight: bold;
            font-size: 1.2rem;
        }

        .live-status {
            color: #ff4444;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .live-dot {
            display: inline-block;
            width: 10px;
            height: 10px;
            background-color: #ff4444;
            border-radius: 50%;
            animation: pulse 1.5s infinite;
        }

        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.5; }
            100% { opacity: 1; }
        }

        .live-stream {
            width: 100%;
            aspect-ratio: 16/9;
            background-color: #000;
            margin-top: 15px;
            position: relative;
            border-radius: 8px;
            overflow: hidden;
        }

        .stream-placeholder {
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background-color: #1a2a3a;
            color: white;
        }

        .play-button {
            width: 60px;
            height: 60px;
            background-color: rgba(255,255,255,0.2);
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            margin-bottom: 15px;
        }

        .play-button:hover {
            background-color: rgba(255,255,255,0.3);
        }

        .play-icon {
            width: 0;
            height: 0;
            border-style: solid;
            border-width: 15px 0 15px 25px;
            border-color: transparent transparent transparent white;
            margin-left: 5px;
        }

        .game-card {
            border: 1px solid #ddd;
            border-radius: 8px;
            overflow: hidden;
            margin-bottom: 20px;
            transition: transform 0.3s;
        }

        .game-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .game-img {
            width: 100%;
            height: 150px;
            background-color: #1a2a3a;
            position: relative;
        }

        .game-content {
            padding: 15px;
        }

        .game-title {
            font-weight: bold;
            font-size: 1.2rem;
            margin-bottom: 10px;
        }

        .game-description {
            color: #666;
            margin-bottom: 15px;
        }

        .payment-methods {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: 20px;
        }

        .payment-method {
            border: 1px solid #ddd;
            border-radius: 4px;
            padding: 10px;
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
            transition: border-color 0.3s;
        }

        .payment-method:hover {
            border-color: #4CAF50;
        }

        .payment-method.selected {
            border-color: #4CAF50;
            background-color: rgba(76, 175, 80, 0.1);
        }

        .payment-method-icon {
            width: 30px;
            height: 30px;
            background-color: #ddd;
            border-radius: 4px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.2rem;
            font-weight: bold;
        }

        .account-section {
            margin-bottom: 30px;
        }

        .profile-header {
            display: flex;
            align-items: center;
            gap: 20px;
            margin-bottom: 30px;
        }

        .profile-picture {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            background-color: #ddd;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
        }

        .profile-picture img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .profile-picture-overlay {
            position: absolute;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            opacity: 0;
            transition: opacity 0.3s;
            cursor: pointer;
        }

        .profile-picture-overlay:hover {
            opacity: 1;
        }

        .profile-info {
            flex: 1;
        }

        .profile-name {
            font-size: 1.5rem;
            font-weight: bold;
            margin-bottom: 5px;
        }

        .profile-email {
            color: #666;
            margin-bottom: 10px;
        }

        .profile-stats {
            display: flex;
            gap: 20px;
        }

        .stat {
            flex: 1;
            text-align: center;
            padding: 15px;
            background-color: #f9f9f9;
            border-radius: 8px;
        }

        .stat-value {
            font-size: 1.5rem;
            font-weight: bold;
            color: #4CAF50;
        }

        .account-details {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .grid-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
        }

        .transaction-history {
            margin-top: 30px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        table th, table td {
            padding: 10px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }

        table th {
            background-color: #f9f9f9;
        }

        .status-pill {
            display: inline-block;
            padding: 3px 10px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: bold;
            text-transform: uppercase;
        }

        .status-pending {
            background-color: #FFC107;
            color: #000;
        }

        .status-won {
            background-color: #4CAF50;
            color: white;
        }

        .status-lost {
            background-color: #F44336;
            color: white;
        }

        .status-completed {
            background-color: #2196F3;
            color: white;
        }

        .crypto-section {
            margin-top: 20px;
        }

        .crypto-coin {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px;
            border-bottom: 1px solid #ddd;
        }

        .crypto-info {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .crypto-icon {
            width: 30px;
            height: 30px;
            background-color: #f9f9f9;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
        }

        .crypto-price {
            font-weight: bold;
        }

        .crypto-change {
            font-weight: bold;
        }

        .crypto-change.positive {
            color: #4CAF50;
        }

        .crypto-change.negative {
            color: #F44336;
        }

        .chat-support {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 100;
        }

        .chat-button {
            width: 60px;
            height: 60px;
            background-color: #4CAF50;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-size: 1.5rem;
            box-shadow: 0 2px 10px rgba(0,0,0,0.2);
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .chat-button:hover {
            background-color: #3e8e41;
        }

        .chat-window {
            position: fixed;
            bottom: 90px;
            right: 20px;
            width: 300px;
            height: 400px;
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.2);
            display: none;
            flex-direction: column;
            overflow: hidden;
            z-index: 100;
        }

        .chat-header {
            background-color: #4CAF50;
            color: white;
            padding: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .chat-close {
            cursor: pointer;
        }

        .chat-messages {
            flex: 1;
            padding: 15px;
            overflow-y: auto;
        }

        .chat-input {
            display: flex;
            border-top: 1px solid #ddd;
        }

        .chat-input input {
            flex: 1;
            padding: 10px;
            border: none;
            outline: none;
        }

        .chat-input button {
            border-radius: 0;
        }

        .message {
            margin-bottom: 10px;
            max-width: 70%;
        }

        .message-content {
            padding: 10px;
            border-radius: 8px;
        }

        .message-user {
            align-self: flex-end;
            margin-left: auto;
        }

        .message-user .message-content {
            background-color: #4CAF50;
            color: white;
        }

        .message-support {
            align-self: flex-start;
        }

        .message-support .message-content {
            background-color: #f0f2f5;
        }

        .notification-badge {
            position: absolute;
            top: -5px;
            right: -5px;
            width: 20px;
            height: 20px;
            background-color: #F44336;
            color: white;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 0.7rem;
            font-weight: bold;
        }

        .casino-game {
            position: relative;
            width: 100%;
            height: 500px;
            background-color: #1a2a3a;
            color: white;
            border-radius: 8px;
            overflow: hidden;
            margin-top: 20px;
        }

        .slots-container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100%;
            gap: 10px;
        }

        .slot-reel {
            width: 100px;
            height: 300px;
            border: 5px solid #4CAF50;
            border-radius: 8px;
            overflow: hidden;
            position: relative;
        }

        .slot-item {
            width: 100%;
            height: 100px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 2rem;
            background-color: #2a3a4a;
        }

        .slot-controls {
            position: absolute;
            bottom: 30px;
            left: 0;
            width: 100%;
            display: flex;
            justify-content: center;
            gap: 20px;
        }

        .slot-bet {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .slot-bet input {
            width: 100px;
        }

        .spin-button {
            padding: 10px 30px;
            font-size: 1.2rem;
        }

        .slot-result {
            position: absolute;
            top: 30px;
            left: 0;
            width: 100%;
            text-align: center;
            font-size: 1.5rem;
            font-weight: bold;
        }

        @media (max-width: 768px) {
            .main-content {
                flex-direction: column;
            }

            .nav-links {
                display: none;
            }

            .mobile-menu {
                display: block;
                font-size: 1.5rem;
                cursor: pointer;
            }

            .bet-options {
                flex-direction: column;
            }

            .grid-container {
                grid-template-columns: 1fr;
            }

            .profile-header {
                flex-direction: column;
                text-align: center;
            }

            .profile-stats {
                flex-direction: column;
                gap: 10px;
            }

            .account-details {
                grid-template-columns: 1fr;
            }

            .slots-container {
                flex-direction: column;
                gap: 20px;
            }

            .slot-reel {
                width: 80px;
                height: 200px;
            }

            .slot-item {
                height: 66.67px;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <nav>
                <div class="logo">BetMaster</div>
                <div class="nav-links">
                    <a href="#" onclick="showSection('sports')">Sports</a>
                    <a href="#" onclick="showSection('live')">Live</a>
                    <a href="#" onclick="showSection('casino')">Casino</a>
                    <a href="#" onclick="showSection('games')">Games</a>
                    <a href="#" onclick="showSection('crypto')">Crypto</a>
                </div>
                <div class="user-actions">
                    <div id="user-profile" class="user-profile" style="display: none;" onclick="showSection('account')">
                        <div class="profile-img" id="nav-profile-img">
                            <img id="nav-profile-picture" src="data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='40' height='40' viewBox='0 0 24 24' fill='none' stroke='%23888' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'><path d='M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2'></path><circle cx='12' cy='7' r='4'></circle></svg>" alt="Profile">
                        </div>
                        <span id="nav-username">Username</span>
                    </div>
                    <div id="user-balance" style="display: none;">Balance: $<span id="balance-amount">1000</span></div>
                    <button id="login-btn" onclick="openLoginModal()">Login</button>
                    <button id="register-btn" onclick="openRegisterModal()">Register</button>
                    <button id="logout-btn" style="display: none;" onclick="logout()">Logout</button>
                </div>
            </nav>
        </div>
    </header>

    <div class="container">
        <div class="main-content">
            <div class="sidebar">
                <h3 class="section-title">Bet Slip</h3>
                <div id="bet-slip">
                    <div class="empty-slip" id="empty-slip">
                        Your bet slip is empty
                    </div>
                    <div id="bet-slip-items" class="bet-slip-items"></div>
                    <div id="bet-slip-total" class="bet-slip-total" style="display: none;">
                        <span>Total Potential Win:</span>
                        <span id="potential-win">$0.00</span>
                    </div>
                    <div class="bet-input" id="bet-input" style="display: none;">
                        <input type="number" id="bet-amount" placeholder="Enter stake amount" min="1">
                        <button onclick="placeBet()">Place Bet</button>
                    </div>
                </div>

                <div id="user-account" style="display: none;">
                    <h3 class="section-title">Account</h3>
                    <div class="balance">Balance: $<span id="account-balance">1000</span></div>
                    <div class="deposit-withdraw">
                        <button onclick="openDepositModal()">Deposit</button>
                        <button onclick="openWithdrawModal()">Withdraw</button>
                    </div>
                </div>

                <div class="live-now">
                    <h3 class="section-title">Live Now</h3>
                    <div id="live-matches-sidebar">
                        <!-- Live matches will be populated here -->
                    </div>
                </div>

                <div class="promotions">
                    <h3 class="section-title">Promotions</h3>
                    <div class="promotion">
                        <div style="background-color: #4CAF50; color: white; padding: 10px; border-radius: 4px; margin-bottom: 10px;">
                            <p>Welcome Bonus</p>
                            <p style="font-size: 1.5rem; font-weight: bold;">100% up to $200</p>
                        </div>
                        <div style="background-color: #2196F3; color: white; padding: 10px; border-radius: 4px;">
                            <p>Free Bet</p>
                            <p style="font-size: 1.5rem; font-weight: bold;">$20 Risk Free</p>
                        </div>
                    </div>
                </div>
            </div>

            <div class="betting-area" id="content-area">
                <!-- Content will be dynamically loaded here -->
            </div>
        </div>
    </div>

    <!-- Login Modal -->
    <div class="modal" id="login-modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('login-modal')">&times;</span>
            <h2>Login</h2>
            <div class="form-group">
                <label for="login-email">Email</label>
                <input type="email" id="login-email" placeholder="Enter your email">
            </div>
            <div class="form-group">
                <label for="login-password">Password</label>
                <input type="password" id="login-password" placeholder="Enter your password">
            </div>
            <button onclick="login()">Login</button>
            <p style="margin-top: 15px; text-align: center;">
                Don't have an account? <a href="#" onclick="closeModal('login-modal'); openRegisterModal();">Register</a>
            </p>
        </div>
    </div>

    <!-- Register Modal -->
    <div class="modal" id="register-modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('register-modal')">&times;</span>
            <h2>Register</h2>
            <div class="form-group">
                <label for="register-name">Full Name</label>
                <input type="text" id="register-name" placeholder="Enter your full name">
            </div>
            <div class="form-group">
                <label for="register-email">Email</label>
                <input type="email" id="register-email" placeholder="Enter your email">
            </div>
            <div class="form-group">
                <label for="register-password">Password</label>
                <input type="password" id="register-password" placeholder="Create a password">
            </div>
            <div class="form-group">
                <label for="register-confirm-password">Confirm Password</label>
                <input type="password" id="register-confirm-password" placeholder="Confirm your password">
            </div>
            <button onclick="register()">Register</button>
            <p style="margin-top: 15px; text-align: center;">
                Already have an account? <a href="#" onclick="closeModal('register-modal'); openLoginModal();">Login</a>
            </p>
        </div>
    </div>

    <!-- Deposit Modal -->
    <div class="modal" id="deposit-modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('deposit-modal')">&times;</span>
            <h2>Deposit Funds</h2>
            <div class="form-group">
                <label for="deposit-amount">Amount</label>
                <input type="number" id="deposit-amount" placeholder="Enter amount to deposit" min="10">
            </div>
            <div class="form-group">
                <label>Payment Method</label>
                <div class="payment-methods">
                    <div class="payment-method" onclick="selectPaymentMethod(this, 'card')">
                        <div class="payment-method-icon">💳</div>
                        <div>Credit Card</div>
                    </div>
                    <div class="payment-method" onclick="selectPaymentMethod(this, 'paypal')">
                        <div class="payment-method-icon">P</div>
                        <div>PayPal</div>
                    </div>
                    <div class="payment-method" onclick="selectPaymentMethod(this, 'crypto')">
                        <div class="payment-method-icon">₿</div>
                        <div>Crypto</div>
                    </div>
                    <div class="payment-method" onclick="selectPaymentMethod(this, 'bank')">
                        <div class="payment-method-icon">🏦</div>
                        <div>Bank Transfer</div>
                    </div>
                </div>
            </div>
            <div id="payment-details-card" class="payment-details">
                <div class="form-group">
                    <label for="card-number">Card Number</label>
                    <input type="text" id="card-number" placeholder="XXXX XXXX XXXX XXXX">
                </div>
                <div class="form-group">
                    <label for="card-expiry">Expiry Date</label>
                    <input type="text" id="card-expiry" placeholder="MM/YY">
                </div>
                <div class="form-group">
                    <label for="card-cvv">CVV</label>
                    <input type="text" id="card-cvv" placeholder="XXX">
                </div>
            </div>
            <div id="payment-details-paypal" class="payment-details" style="display: none;">
                <div class="form-group">
                    <label for="paypal-email">PayPal Email</label>
                    <input type="email" id="paypal-email" placeholder="Enter your PayPal email">
                </div>
            </div>
            <div id="payment-details-crypto" class="payment-details" style="display: none;">
                <div class="form-group">
                    <label>Cryptocurrency</label>
                    <select id="crypto-type">
                        <option value="btc">Bitcoin</option>
                        <option value="eth">Ethereum</option>
                        <option value="ltc">Litecoin</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Wallet Address</label>
                    <input type="text" id="crypto-address" value="0x742d35Cc6634C0532925a3b844Bc454e4438f44e" readonly>
                    <p style="font-size: 0.8rem; color: #666;">Please send the cryptocurrency to this address. Your account will be credited once the transaction is confirmed.</p>
                </div>
            </div>
            <div id="payment-details-bank" class="payment-details" style="display: none;">
                <div class="form-group">
                    <label>Bank Details</label>
                    <p>Bank: National Bank</p>
                    <p>Account Name: BetMaster Ltd</p>
                    <p>Account Number: 1234567890</p>
                    <p>SWIFT/BIC: NTBNK123</p>
                    <p>Reference: Please use your account email as reference</p>
                </div>
            </div>
            <button onclick="depositFunds()">Deposit</button>
        </div>
    </div>

    <!-- Withdraw Modal -->
    <div class="modal" id="withdraw-modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('withdraw-modal')">&times;</span>
            <h2>Withdraw Funds</h2>
            <div class="form-group">
                <label for="withdraw-amount">Amount</label>
                <input type="number" id="withdraw-amount" placeholder="Enter amount to withdraw" min="10">
            </div>
            <div class="form-group">
                <label>Withdrawal Method</label>
                <div class="payment-methods">
                    <div class="payment-method" onclick="selectWithdrawalMethod(this, 'card')">
                        <div class="payment-method-icon">💳</div>
                        <div>Credit Card</div>
                    </div>
                    <div class="payment-method" onclick="selectWithdrawalMethod(this, 'paypal')">
                        <div class="payment-method-icon">P</div>
                        <div>PayPal</div>
                    </div>
                    <div class="payment-method" onclick="selectWithdrawalMethod(this, 'crypto')">
                        <div class="payment-method-icon">₿</div>
                        <div>Crypto</div>
                    </div>
                    <div class="payment-method" onclick="selectWithdrawalMethod(this, 'bank')">
                        <div class="payment-method-icon">🏦</div>
                        <div>Bank Transfer</div>
                    </div>
                </div>
            </div>
            <div id="withdrawal-details-card" class="payment-details">
                <div class="form-group">
                    <label for="withdrawal-card-number">Card Number</label>
                    <input type="text" id="withdrawal-card-number" placeholder="XXXX XXXX XXXX XXXX">
                </div>
                <div class="form-group">
                    <label for="withdrawal-card-name">Cardholder Name</label>
                    <input type="text" id="withdrawal-card-name" placeholder="Enter cardholder name">
                </div>
            </div>
            <div id="withdrawal-details-paypal" class="payment-details" style="display: none;">
                <div class="form-group">
                    <label for="withdrawal-paypal-email">PayPal Email</label>
                    <input type="email" id="withdrawal-paypal-email" placeholder="Enter your PayPal email">
                </div>
            </div>
            <div id="withdrawal-details-crypto" class="payment-details" style="display: none;">
                <div class="form-group">
                    <label>Cryptocurrency</label>
                    <select id="withdrawal-crypto-type">
                        <option value="btc">Bitcoin</option>
                        <option value="eth">Ethereum</option>
                        <option value="ltc">Litecoin</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Your Wallet Address</label>
                    <input type="text" id="withdrawal-crypto-address" placeholder="Enter your wallet address">
                </div>
            </div>
            <div id="withdrawal-details-bank" class="payment-details" style="display: none;">
                <div class="form-group">
                    <label for="bank-name">Bank Name</label>
                    <input type="text" id="bank-name" placeholder="Enter bank name">
                </div>
                <div class="form-group">
                    <label for="account-name">Account Holder Name</label>
                    <input type="text" id="account-name" placeholder="Enter account holder name">
                </div>
                <div class="form-group">
                    <label for="account-number">Account Number</label>
                    <input type="text" id="account-number" placeholder="Enter account number">
                </div>
                <div class="form-group">
                    <label for="bank-swift">SWIFT/BIC Code</label>
                    <input type="text" id="bank-swift" placeholder="Enter SWIFT/BIC code">
                </div>
            </div>
            <button onclick="withdrawFunds()">Withdraw</button>
        </div>
    </div>

    <!-- Profile Picture Modal -->
    <div class="modal" id="profile-picture-modal">
        <div class="modal-content">
            <span class="close" onclick="closeModal('profile-picture-modal')">&times;</span>
            <h2>Update Profile Picture</h2>
            <div class="form-group">
                <label for="profile-picture-input">Upload Picture</label>
                <input type="file" id="profile-picture-input" accept="image/*">
            </div>
            <div class="form-group">
                <div style="width: 200px; height: 200px; margin: 0 auto; border-radius: 50%; overflow: hidden; background-color: #ddd;">
                    <img id="profile-picture-preview" src="data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='200' height='200' viewBox='0 0 24 24' fill='none' stroke='%23888' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'><path d='M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2'></path><circle cx='12' cy='7' r='4'></circle></svg>" style="width: 100%; height: 100%; object-fit: cover;">
                </div>
            </div>
            <button onclick="updateProfilePicture()">Update</button>
        </div>
    </div>

    <!-- Chat Support -->
    <div class="chat-support">
        <div class="chat-button" onclick="toggleChat()">
            💬
            <div class="notification-badge" id="chat-notification" style="display: none;">1</div>
        </div>
        <div class="chat-window" id="chat-window">
            <div class="chat-header">
                <div>Support Chat</div>
                <div class="chat-close" onclick="toggleChat()">✖</div>
            </div>
            <div class="chat-messages" id="chat-messages">
                <div class="message message-support">
                    <div class="message-content">
                        Hi there! How can I help you today?
                    </div>
                </div>
            </div>
            <div class="chat-input">
                <input type="text" id="chat-input-field" placeholder="Type your message..." onkeypress="if(event.keyCode === 13) sendChatMessage()">
                <button onclick="sendChatMessage()">Send</button>
            </div>
        </div>
    </div>

    <footer>
        <div class="container">
            <p>&copy; 2025 BetMaster. All rights reserved.</p>
            <p>Gambling can be addictive. Please gamble responsibly.</p>
            <div style="margin-top: 20px; display: flex; justify-content: center; gap: 20px;">
                <a href="#" style="color: white;">Terms & Conditions</a>
                <a href="#" style="color: white;">Privacy Policy</a>
                <a href="#" style="color: white;">Responsible Gambling</a>
                <a href="#" style="color: white;">Contact Us</a>
            </div>
        </div>
    </footer>

    <script>
        // Sample data for bets
        const bets = [
            {
                id: 1,
                sport: 'football',
                league: 'Premier League',
                teams: 'Manchester United vs Liverpool',
                time: '2025-03-06 20:00',
                live: true,
                options: [
                    { id: 1, name: 'Home', odds: 2.1 },
                    { id: 2, name: 'Draw', odds: 3.4 },
                    { id: 3, name: 'Away', odds: 2.8 }
                ]
            },
            {
                id: 2,
                sport: 'football',
                league: 'La Liga',
                teams: 'Barcelona vs Real Madrid',
                time: '2025-03-07 21:00',
                live: true,
                options: [
                    { id: 4, name: 'Home', odds: 1.9 },
                    { id: 5, name: 'Draw', odds: 3.5 },
                    { id: 6, name: 'Away', odds: 3.0 }
                ]
            },
            {
                id: 3,
                sport: 'basketball',
                league: 'NBA',
                teams: 'LA Lakers vs Chicago Bulls',
                time: '2025-03-06 18:30',
                live: true,
                score: '78-82',
                period: '3rd Quarter',
                options: [
                    { id: 7, name: 'Home', odds: 1.7 },
                    { id: 8, name: 'Away', odds: 2.2 }
                ]
            },
            {
                id: 4,
                sport: 'tennis',
                league: 'ATP Masters',
                teams: 'Rafael Nadal vs Novak Djokovic',
                time: '2025-03-08 15:00',
                live: true,
                options: [
                    { id: 9, name: 'Nadal', odds: 2.0 },
                    { id: 10, name: 'Djokovic', odds: 1.8 }
                ]
            },
            {
                id: 5,
                sport: 'esports',
                league: 'League of Legends World Championship',
                teams: 'T1 vs G2 Esports',
                time: '2025-03-09 16:00',
                live: true,
                score: '1-0',
                period: 'Game 2',
                options: [
                    { id: 11, name: 'T1', odds: 1.6 },
                    { id: 12, name: 'G2', odds: 2.3 }
                ]
            },
            {
                id: 6,
                sport: 'football',
                league: 'Champions League',
                teams: 'Bayern Munich vs PSG',
                time: '2025-03-10 20:00',
                live: false,
                options: [
                    { id: 13, name: 'Home', odds: 1.8 },
                    { id: 14, name: 'Draw', odds: 3.6 },
                    { id: 15, name: 'Away', odds: 3.2 }
                ]
            },
            {
                id: 7,
                sport: 'football',
                league: 'Serie A',
                teams: 'Juventus vs Inter Milan',
                time: '2025-03-09 19:45',
                live: true,
                score: '1-1',
                period: '67\'',
                options: [
                    { id: 16, name: 'Home', odds: 2.5 },
                    { id: 17, name: 'Draw', odds: 2.0 },
                    { id: 18, name: 'Away', odds: 3.5 }
                ]
            }
        ];

        // Sample data for games
        const games = [
            {
                id: 1,
                name: 'Slots Bonanza',
                type: 'slots',
                description: 'Spin the reels and win big with 50+ paylines!'
            },
            {
                id: 2,
                name: 'Blackjack Pro',
                type: 'cards',
                description: 'Classic blackjack with 99.5% RTP and multiple side bets'
            },
            {
                id: 3,
                name: 'Roulette Master',
                type: 'table',
                description: 'European roulette with immersive 3D graphics'
            },
            {
                id: 4,
                name: 'Poker Challenge',
                type: 'cards',
                description: 'Texas Hold\'em with tournaments and cash tables'
            },
            {
                id: 5,
                name: 'Crash Game',
                type: 'arcade',
                description: 'Watch the multiplier grow and cash out before it crashes!'
            },
            {
                id: 6,
                name: 'Bingo Blast',
                type: 'lottery',
                description: 'Multiple bingo rooms with progressive jackpots'
            }
        ];

        // Sample data for transactions
        const sampleTransactions = [
            {
                id: 1,
                type: 'Deposit',
                amount: 200.00,
                method: 'Credit Card',
                date: '2025-03-01',
                status: 'Completed'
            },
            {
                id: 2,
                type: 'Bet',
                amount: -50.00,
                event: 'Manchester United vs Liverpool',
                date: '2025-03-02',
                status: 'Lost'
            },
            {
                id: 3,
                type: 'Bet',
                amount: 120.00,
                event: 'LA Lakers vs Chicago Bulls',
                date: '2025-03-03',
                status: 'Won'
            },
            {
                id: 4,
                type: 'Withdrawal',
                amount: -100.00,
                method: 'Bank Transfer',
                date: '2025-03-04',
                status: 'Pending'
            }
        ];

        // Sample data for crypto prices
        const cryptoPrices = [
            {
                symbol: 'BTC',
                name: 'Bitcoin',
                price: 58423.45,
                change: 2.3
            },
            {
                symbol: 'ETH',
                name: 'Ethereum',
                price: 3521.87,
                change: 1.5
            },
            {
                symbol: 'LTC',
                name: 'Litecoin',
                price: 187.26,
                change: -0.8
            },
            {
                symbol: 'DOGE',
                name: 'Dogecoin',
                price: 0.12,
                change: 5.4
            }
        ];

        // Application state
        let currentUser = null;
        let selectedBets = {};
        let betAmount = 0;
        let currentSection = 'sports';
        let currentPaymentMethod = 'card';
        let currentWithdrawalMethod = 'card';
        let slotMachine = null;

        // Initialize the application
        function init() {
            loadUser();
            renderLiveSidebar();
            showSection('sports');

            // Set up automatic chat notification
            setTimeout(() => {
                document.getElementById('chat-notification').style.display = 'flex';
            }, 30000);
        }

        // Load user from local storage
        function loadUser() {
            const savedUser = localStorage.getItem('betmaster_user');
            if (savedUser) {
                currentUser = JSON.parse(savedUser);
                showLoggedInUI();
            }
        }

        // Show UI for logged in users
        function showLoggedInUI() {
            document.getElementById('login-btn').style.display = 'none';
            document.getElementById('register-btn').style.display = 'none';
            document.getElementById('logout-btn').style.display = 'block';
            document.getElementById('user-balance').style.display = 'block';
            document.getElementById('user-account').style.display = 'block';
            document.getElementById('user-profile').style.display = 'flex';
            document.getElementById('balance-amount').textContent = currentUser.balance.toFixed(2);
            document.getElementById('account-balance').textContent = currentUser.balance.toFixed(2);
            document.getElementById('nav-username').textContent = currentUser.name.split(' ')[0];

            if (currentUser.profilePicture) {
                document.getElementById('nav-profile-picture').src = currentUser.profilePicture;
            }
        }

        // Show UI for logged out users
        function showLoggedOutUI() {
            document.getElementById('login-btn').style.display = 'block';
            document.getElementById('register-btn').style.display = 'block';
            document.getElementById('logout-btn').style.display = 'none';
            document.getElementById('user-balance').style.display = 'none';
            document.getElementById('user-account').style.display = 'none';
            document.getElementById('user-profile').style.display = 'none';
            document.getElementById('bet-input').style.display = 'none';
        }

        // Render live matches in sidebar
        function renderLiveSidebar() {
            const liveMatchesSidebar = document.getElementById('live-matches-sidebar');
            liveMatchesSidebar.innerHTML = '';

            const liveMatches = bets.filter(bet => bet.live);

            if (liveMatches.length === 0) {
                liveMatchesSidebar.innerHTML = '<p>No live matches at the moment</p>';
                return;
            }

            liveMatches.forEach(match => {
                const matchElement = document.createElement('div');
                matchElement.style.padding = '10px';
                matchElement.style.borderBottom = '1px solid #ddd';
                matchElement.style.cursor = 'pointer';
                matchElement.onclick = () => showLiveMatch(match.id);

                matchElement.innerHTML = `
                    <div style="display: flex; align-items: center; gap: 5px;">
                        <div class="live-dot"></div>
                        <div style="color: #ff4444">LIVE</div>
                    </div>
                    <div><strong>${match.teams}</strong></div>
                    <div>${match.score} | ${match.period}</div>
                `;

                liveMatchesSidebar.appendChild(matchElement);
            });
        }

        // Show specific section of the site
        function showSection(section) {
            currentSection = section;
            const contentArea = document.getElementById('content-area');

            switch (section) {
                case 'sports':
                    renderSportsSection();
                    break;
                case 'live':
                    renderLiveSection();
                    break;
                case 'casino':
                    renderCasinoSection();
                    break;
                case 'games':
                    renderGamesSection();
                    break;
                case 'crypto':
                    renderCryptoSection();
                    break;
                case 'account':
                    if (currentUser) {
                        renderAccountSection();
                    } else {
                        openLoginModal();
                        showSection('sports');
                    }
                    break;
                default:
                    renderSportsSection();
            }
        }

        // Render the sports betting section
        function renderSportsSection() {
            const contentArea = document.getElementById('content-area');
            contentArea.innerHTML = `
                <h2>Sports Betting</h2>
                <div class="tabs">
                    <div class="tab active" onclick="filterSports('all')">All Sports</div>
                    <div class="tab" onclick="filterSports('football')">Football</div>
                    <div class="tab" onclick="filterSports('basketball')">Basketball</div>
                    <div class="tab" onclick="filterSports('tennis')">Tennis</div>
                    <div class="tab" onclick="filterSports('esports')">Esports</div>
                </div>
                <div id="bets-container"></div>
            `;

            renderBets();
        }

        // Render the live betting section
        function renderLiveSection() {
            const contentArea = document.getElementById('content-area');
            contentArea.innerHTML = `
                <h2>Live Betting</h2>
                <div id="live-matches-container"></div>
            `;

            renderLiveMatches();
        }

        // Render the casino section
        function renderCasinoSection() {
            const contentArea = document.getElementById('content-area');
            contentArea.innerHTML = `
                <h2>Casino Games</h2>
                <div class="tabs">
                    <div class="tab active" onclick="filterCasino('all')">All Games</div>
                    <div class="tab" onclick="filterCasino('slots')">Slots</div>
                    <div class="tab" onclick="filterCasino('cards')">Card Games</div>
                    <div class="tab" onclick="filterCasino('table')">Table Games</div>
                </div>
                <div class="grid-container" id="casino-container">
                    <!-- Casino games will be populated here -->
                </div>
            `;

            renderCasinoGames();
        }

        // Render the games section
        function renderGamesSection() {
            const contentArea = document.getElementById('content-area');
            contentArea.innerHTML = `
                <h2>Instant Win Games</h2>
                <div class="casino-game" id="slots-game">
                    <div class="slot-result" id="slot-result"></div>
                    <div class="slots-container">
                        <div class="slot-reel" id="reel1">
                            <div class="slot-item">🍒</div>
                            <div class="slot-item">🍋</div>
                            <div class="slot-item">🍊</div>
                        </div>
                        <div class="slot-reel" id="reel2">
                            <div class="slot-item">💎</div>
                            <div class="slot-item">🍒</div>
                            <div class="slot-item">7️⃣</div>
                        </div>
                        <div class="slot-reel" id="reel3">
                            <div class="slot-item">🍊</div>
                            <div class="slot-item">💎</div>
                            <div class="slot-item">🍋</div>
                        </div>
                    </div>
                    <div class="slot-controls">
                        <div class="slot-bet">
                            <label>Bet:</label>
                            <input type="number" id="slot-bet-amount" value="10" min="1">
                        </div>
                        <button class="spin-button" onclick="spinSlots()">Spin</button>
                    </div>
                </div>

                <h2 style="margin-top: 30px;">More Games</h2>
                <div class="grid-container" id="games-container">
                    <!-- Games will be populated here -->
                </div>
            `;

            renderInstantGames();
            setupSlotMachine();
        }

        // Render the crypto betting section
        function renderCryptoSection() {
            const contentArea = document.getElementById('content-area');
            contentArea.innerHTML = `
                <h2>Crypto Betting</h2>
                <p>Bet on cryptocurrency price movements and earn rewards! Track live prices and place your bets.</p>

                <div class="crypto-section">
                    <h3 class="section-title">Live Cryptocurrency Prices</h3>
                    <div id="crypto-prices">
                        <!-- Crypto prices will be populated here -->
                    </div>
                </div>

                <h3 class="section-title" style="margin-top: 30px;">Crypto Price Bets</h3>
                <div id="crypto-bets">
                    <div class="bet-card">
                        <div class="bet-header">
                            <div class="bet-teams">Bitcoin Price Direction</div>
                            <div class="bet-time">Expires in 24h</div>
                        </div>
                        <div class="bet-league">Will BTC be higher or lower than $58,000 in 24 hours?</div>
                        <div class="bet-options">
                            <div class="bet-option" onclick="selectCryptoBet('btc-up')">
                                <div class="bet-option-label">Higher</div>
                                <div class="bet-option-odds">1.95</div>
                            </div>
                            <div class="bet-option" onclick="selectCryptoBet('btc-down')">
                                <div class="bet-option-label">Lower</div>
                                <div class="bet-option-odds">1.95</div>
                            </div>
                        </div>
                    </div>

                    <div class="bet-card">
                        <div class="bet-header">
                            <div class="bet-teams">Ethereum Next Hour</div>
                            <div class="bet-time">Expires in 1h</div>
                        </div>
                        <div class="bet-league">Will ETH move by more than 2% in the next hour?</div>
                        <div class="bet-options">
                            <div class="bet-option" onclick="selectCryptoBet('eth-yes')">
                                <div class="bet-option-label">Yes</div>
                                <div class="bet-option-odds">2.50</div>
                            </div>
                            <div class="bet-option" onclick="selectCryptoBet('eth-no')">
                                <div class="bet-option-label">No</div>
                                <div class="bet-option-odds">1.45</div>
                            </div>
                        </div>
                    </div>
                </div>
            `;

            renderCryptoPrices();
        }

        // Render the account section
        function renderAccountSection() {
            if (!currentUser) return;

            const transactions = JSON.parse(localStorage.getItem('betmaster_transactions_' + currentUser.id) || JSON.stringify(sampleTransactions));
            const betHistory = JSON.parse(localStorage.getItem('betmaster_bet_history') || '[]');

            const contentArea = document.getElementById('content-area');
            contentArea.innerHTML = `
                <h2>My Account</h2>

                <div class="profile-header">
                    <div class="profile-picture">
                        <img id="profile-picture" src="${currentUser.profilePicture || 'data:image/svg+xml;utf8,<svg xmlns=\'http://www.w3.org/2000/svg\' width=\'100\' height=\'100\' viewBox=\'0 0 24 24\' fill=\'none\' stroke=\'%23888\' stroke-width=\'2\' stroke-linecap=\'round\' stroke-linejoin=\'round\'><path d=\'M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2\'></path><circle cx=\'12\' cy=\'7\' r=\'4\'></circle></svg>'}" alt="Profile Picture">
                        <div class="profile-picture-overlay" onclick="openProfilePictureModal()">
                            <span>Change</span>
                        </div>
                    </div>
                    <div class="profile-info">
                        <div class="profile-name">${currentUser.name}</div>
                        <div class="profile-email">${currentUser.email}</div>
                        <div class="profile-stats">
                            <div class="stat">
                                <div class="stat-value">$${currentUser.balance.toFixed(2)}</div>
                                <div>Balance</div>
                            </div>
                            <div class="stat">
                                <div class="stat-value">${betHistory.length}</div>
                                <div>Bets Placed</div>
                            </div>
                            <div class="stat">
                                <div class="stat-value">${betHistory.filter(bet => bet.status === 'Won').length}</div>
                                <div>Bets Won</div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="account-section">
                    <h3 class="section-title">Quick Actions</h3>
                    <div class="account-details">
                        <div class="stat">
                            <div style="font-size: 1.2rem; font-weight: bold; margin-bottom: 10px;">Deposit</div>
                            <button onclick="openDepositModal()">Deposit Funds</button>
                        </div>
                        <div class="stat">
                            <div style="font-size: 1.2rem; font-weight: bold; margin-bottom: 10px;">Withdraw</div>
                            <button onclick="openWithdrawModal()">Withdraw Funds</button>
                        </div>
                        <div class="stat">
                            <div style="font-size: 1.2rem; font-weight: bold; margin-bottom: 10px;">Bonuses</div>
                            <button onclick="checkBonuses()">Check Bonuses</button>
                        </div>
                        <div class="stat">
                            <div style="font-size: 1.2rem; font-weight: bold; margin-bottom: 10px;">Support</div>
                            <button onclick="toggleChat()">Contact Support</button>
                        </div>
                    </div>
                </div>

                <div class="transaction-history">
                    <h3 class="section-title">Transaction History</h3>
                    <table>
                        <thead>
                            <tr>
                                <th>Date</th>
                                <th>Type</th>
                                <th>Details</th>
                                <th>Amount</th>
                                <th>Status</th>
                            </tr>
                        </thead>
                        <tbody>
                            ${transactions.map(transaction => `
                                <tr>
                                    <td>${transaction.date}</td>
                                    <td>${transaction.type}</td>
                                    <td>${transaction.event || transaction.method || '-'}</td>
                                    <td style="color: ${transaction.amount > 0 ? '#4CAF50' : '#F44336'}">$${Math.abs(transaction.amount).toFixed(2)}</td>
                                    <td><span class="status-pill status-${transaction.status.toLowerCase()}">${transaction.status}</span></td>
                                </tr>
                            `).join('')}
                        </tbody>
                    </table>
                </div>

                <div class="bet-history" style="margin-top: 30px;">
                    <h3 class="section-title">Bet History</h3>
                    <table>
                        <thead>
                            <tr>
                                <th>Date</th>
                                <th>Selections</th>
                                <th>Stake</th>
                                <th>Potential Win</th>
                                <th>Status</th>
                            </tr>
                        </thead>
                        <tbody>
                            ${betHistory.map(bet => `
                                <tr>
                                    <td>${new Date(bet.date).toLocaleDateString()}</td>
                                    <td>${bet.selections.map(s => `${s.teams} - ${s.option}`).join('<br>')}</td>
                                    <td>$${bet.amount.toFixed(2)}</td>
                                    <td>$${bet.potentialWin.toFixed(2)}</td>
                                    <td><span class="status-pill status-${bet.status.toLowerCase()}">${bet.status}</span></td>
                                </tr>
                            `).join('')}
                        </tbody>
                    </table>
                </div>

                <div class="account-settings" style="margin-top: 30px;">
                    <h3 class="section-title">Account Settings</h3>
                    <div class="account-details">
                        <div class="form-group">
                            <label>Change Password</label>
                            <input type="password" id="current-password" placeholder="Current Password">
                        </div>
                        <div class="form-group">
                            <input type="password" id="new-password" placeholder="New Password">
                        </div>
                        <div class="form-group">
                            <input type="password" id="confirm-new-password" placeholder="Confirm New Password">
                        </div>
                        <div class="form-group">
                            <button onclick="changePassword()">Update Password</button>
                        </div>
                    </div>
                </div>
            `;
        }

        // Render all available bets
        function renderBets(sport = null) {
            const betsContainer = document.getElementById('bets-container');
            if (!betsContainer) return;

            betsContainer.innerHTML = '';

            const filteredBets = sport && sport !== 'all' ? bets.filter(bet => bet.sport === sport) : bets;

            filteredBets.forEach(bet => {
                const betCard = document.createElement('div');
                betCard.className = 'bet-card';

                // Add live indicator if it's a live match
                const liveIndicator = bet.live ? `
                    <div style="display: flex; align-items: center; gap: 5px; margin-bottom: 5px;">
                        <div class="live-dot"></div>
                        <div style="color: #ff4444">LIVE</div>
                        <div>${bet.score} | ${bet.period}</div>
                    </div>
                ` : '';

                betCard.innerHTML = `
                    ${liveIndicator}
                    <div class="bet-header">
                        <div class="bet-teams">${bet.teams}</div>
                        <div class="bet-time">${formatDate(bet.time)}</div>
                    </div>
                    <div class="bet-league">${bet.league}</div>
                    <div class="bet-options">
                        ${bet.options.map(option => `
                            <div class="bet-option" id="option-${option.id}" onclick="selectBet(${bet.id}, ${option.id})">
                                <div class="bet-option-label">${option.name}</div>
                                <div class="bet-option-odds">${option.odds.toFixed(2)}</div>
                            </div>
                        `).join('')}
                    </div>
                    ${bet.live ? `<div style="margin-top: 10px; text-align: center;">
                        <button onclick="showLiveMatch(${bet.id})">Watch Live</button>
                    </div>` : ''}
                `;
                betsContainer.appendChild(betCard);
            });
        }

        // Filter sports by category
        function filterSports(sport) {
            // Update active tab
            const tabs = document.querySelectorAll('.tab');
            tabs.forEach(tab => tab.classList.remove('active'));
            event.target.classList.add('active');

            renderBets(sport);
        }

        // Filter casino games by type
        function filterCasino(type) {
            // Update active tab
            const tabs = document.querySelectorAll('.tab');
            tabs.forEach(tab => tab.classList.remove('active'));
            event.target.classList.add('active');

            renderCasinoGames(type);
        }

        // Render live matches with streaming option
        function renderLiveMatches() {
            const liveMatchesContainer = document.getElementById('live-matches-container');
            if (!liveMatchesContainer) return;

            const liveMatches = bets.filter(bet => bet.live);

            if (liveMatches.length === 0) {
                liveMatchesContainer.innerHTML = '<p>No live matches at the moment. Check back later!</p>';
                return;
            }

            liveMatches.forEach(match => {
                const matchElement = document.createElement('div');
                matchElement.className = 'live-match';
                matchElement.innerHTML = `
                    <div class="live-match-header">
                        <div class="live-match-teams">${match.teams}</div>
                        <div class="live-status">
                            <div class="live-dot"></div>
                            LIVE
                        </div>
                    </div>
                    <div>${match.league} | ${match.score} | ${match.period}</div>
                    <div class="bet-options">
                        ${match.options.map(option => `
                            <div class="bet-option" id="live-option-${option.id}" onclick="selectBet(${match.id}, ${option.id})">
                                <div class="bet-option-label">${option.name}</div>
                                <div class="bet-option-odds">${option.odds.toFixed(2)}</div>
                            </div>
                        `).join('')}
                    </div>
                    <div class="live-stream">
                        <div class="stream-placeholder">
                            <div class="play-button" onclick="startStream(${match.id})">
                                <div class="play-icon"></div>
                            </div>
                            <div>Click to watch live stream</div>
                        </div>
                    </div>
                `;
                liveMatchesContainer.appendChild(matchElement);
            });
        }

        // Show a specific live match
        function showLiveMatch(matchId) {
            showSection('live');

            // Scroll to the specific match after rendering
            setTimeout(() => {
                const matchElements = document.querySelectorAll('.live-match');
                matchElements.forEach(element => {
                    if (element.innerHTML.includes(`selectBet(${matchId},`)) {
                        element.scrollIntoView({ behavior: 'smooth' });
                    }
                });
            }, 100);
        }

        // Start stream for a match
        function startStream(matchId) {
            if (!currentUser) {
                openLoginModal();
                return;
            }

            const match = bets.find(b => b.id === matchId);
            if (!match) return;

            // Replace the placeholder with a "live" stream
            const streamPlaceholders = document.querySelectorAll('.stream-placeholder');
            streamPlaceholders.forEach(placeholder => {
                if (placeholder.parentElement.parentElement.innerHTML.includes(`selectBet(${matchId},`)) {
                    placeholder.innerHTML = `
                        <div style="width: 100%; height: 100%; background-color: #000; display: flex; flex-direction: column; justify-content: center; align-items: center; color: white;">
                            <div style="font-size: 1.5rem; font-weight: bold; margin-bottom: 10px;">${match.teams}</div>
                            <div style="font-size: 2rem; margin-bottom: 20px;">${match.score}</div>
                            <div style="display: flex; align-items: center; gap: 5px;">
                                <div class="live-dot"></div>
                                <div>LIVE: ${match.period}</div>
                            </div>
                        </div>
                    `;
                }
            });
        }

        // Render casino games
        function renderCasinoGames(type = 'all') {
            const casinoContainer = document.getElementById('casino-container');
            if (!casinoContainer) return;

            casinoContainer.innerHTML = '';

            const filteredGames = type && type !== 'all' ? games.filter(game => game.type === type) : games;

            filteredGames.forEach(game => {
                const gameCard = document.createElement('div');
                gameCard.className = 'game-card';
                gameCard.innerHTML = `
                    <div class="game-img" style="background-color: ${getRandomColor()}; display: flex; justify-content: center; align-items: center; color: white; font-size: 2rem;">
                        ${getGameIcon(game.type)}
                    </div>
                    <div class="game-content">
                        <div class="game-title">${game.name}</div>
                        <div class="game-description">${game.description}</div>
                        <button onclick="playGame(${game.id})">Play Now</button>
                    </div>
                `;
                casinoContainer.appendChild(gameCard);
            });
        }

        // Render instant win games
        function renderInstantGames() {
            const gamesContainer = document.getElementById('games-container');
            if (!gamesContainer) return;

            gamesContainer.innerHTML = '';

            // Lottery game
            const lotteryGame = document.createElement('div');
            lotteryGame.className = 'game-card';
            lotteryGame.innerHTML = `
                <div class="game-img" style="background-color: #2196F3; display: flex; justify-content: center; align-items: center; color: white; font-size: 2rem;">
                    🎲
                </div>
                <div class="game-content">
                    <div class="game-title">Lucky Draw</div>
                    <div class="game-description">Pick your numbers and win the jackpot! Draws every hour.</div>
                    <button onclick="playLottery()">Play Now</button>
                </div>
            `;
            gamesContainer.appendChild(lotteryGame);

            // Scratch card game
            const scratchGame = document.createElement('div');
            scratchGame.className = 'game-card';
            scratchGame.innerHTML = `
                <div class="game-img" style="background-color: #FF9800; display: flex; justify-content: center; align-items: center; color: white; font-size: 2rem;">
                    🎫
                </div>
                <div class="game-content">
                    <div class="game-title">Scratch & Win</div>
                    <div class="game-description">Scratch the card and reveal instant cash prizes!</div>
                    <button onclick="playScratchCard()">Play Now</button>
                </div>
            `;
            gamesContainer.appendChild(scratchGame);

            // Dice game
            const diceGame = document.createElement('div');
            diceGame.className = 'game-card';
            diceGame.innerHTML = `
                <div class="game-img" style="background-color: #9C27B0; display: flex; justify-content: center; align-items: center; color: white; font-size: 2rem;">
                    🎲
                </div>
                <div class="game-content">
                    <div class="game-title">Dice Roll</div>
                    <div class="game-description">Predict the roll and multiply your stake!</div>
                    <button onclick="playDice()">Play Now</button>
                </div>
            `;
            gamesContainer.appendChild(diceGame);

            // Crash game
            const crashGame = document.createElement('div');
            crashGame.className = 'game-card';
            crashGame.innerHTML = `
                <div class="game-img" style="background-color: #F44336; display: flex; justify-content: center; align-items: center; color: white; font-size: 2rem;">
                    📈
                </div>
                <div class="game-content">
                    <div class="game-title">Crash Game</div>
                    <div class="game-description">Watch the multiplier grow and cash out before it crashes!</div>
                    <button onclick="playCrash()">Play Now</button>
                </div>
            `;
            gamesContainer.appendChild(crashGame);
        }

        // Setup slot machine
        function setupSlotMachine() {
            // Define slot symbols
            const symbols = ['🍒', '🍋', '🍊', '🍇', '🍉', '💎', '7️⃣', '🔔'];

            // Initialize slot reels
            const reel1 = document.getElementById('reel1');
            const reel2 = document.getElementById('reel2');
            const reel3 = document.getElementById('reel3');

            if (!reel1 || !reel2 || !reel3) return;

            // Fill reels with random symbols
            fillReel(reel1, symbols);
            fillReel(reel2, symbols);
            fillReel(reel3, symbols);
        }

        // Fill a reel with random symbols
        function fillReel(reel, symbols) {
            reel.innerHTML = '';
            for (let i = 0; i < 3; i++) {
                const slotItem = document.createElement('div');
                slotItem.className = 'slot-item';
                slotItem.textContent = symbols[Math.floor(Math.random() * symbols.length)];
                reel.appendChild(slotItem);
            }
        }

        // Spin the slot machine
        function spinSlots() {
            if (!currentUser) {
                openLoginModal();
                return;
            }

            const betAmount = parseFloat(document.getElementById('slot-bet-amount').value);

            if (isNaN(betAmount) || betAmount <= 0) {
                alert('Please enter a valid bet amount');
                return;
            }

            if (betAmount > currentUser.balance) {
                alert('Insufficient balance');
                return;
            }

            // Clear previous result
            document.getElementById('slot-result').textContent = '';

            // Deduct bet amount
            currentUser.balance -= betAmount;
            updateUserBalance();

            // Define slot symbols with their respective values
            const symbols = [
                { symbol: '🍒', value: 2 },
                { symbol: '🍋', value: 2 },
                { symbol: '🍊', value: 3 },
                { symbol: '🍇', value: 4 },
                { symbol: '🍉', value: 5 },
                { symbol: '💎', value: 10 },
                { symbol: '7️⃣', value: 20 },
                { symbol: '🔔', value: 3 }
            ];

            // Get the reels
            const reel1 = document.getElementById('reel1');
            const reel2 = document.getElementById('reel2');
            const reel3 = document.getElementById('reel3');

            // Animation timing for each reel
            const spinTime1 = 1000;
            const spinTime2 = 1500;
            const spinTime3 = 2000;

            // Spin animation
            animateSpin(reel1, symbols, spinTime1);
            animateSpin(reel2, symbols, spinTime2);
            animateSpin(reel3, symbols, spinTime3, () => {
                // Check for win after all reels stop
                const result1 = reel1.children[1].textContent;
                const result2 = reel2.children[1].textContent;
                const result3 = reel3.children[1].textContent;

                // Check if all symbols are the same (jackpot)
                if (result1 === result2 && result2 === result3) {
                    const symbol = symbols.find(s => s.symbol === result1);
                    const winAmount = betAmount * symbol.value;

                    // Update balance
                    currentUser.balance += winAmount;
                    updateUserBalance();

                    // Show result
                    document.getElementById('slot-result').textContent = `JACKPOT! You won $${winAmount.toFixed(2)}`;
                    document.getElementById('slot-result').style.color = '#4CAF50';
                }
                // Check if two symbols are the same
                else if (result1 === result2 || result2 === result3 || result1 === result3) {
                    let matchSymbol;
                    if (result1 === result2) matchSymbol = result1;
                    else if (result2 === result3) matchSymbol = result2;
                    else matchSymbol = result1;

                    const symbol = symbols.find(s => s.symbol === matchSymbol);
                    const winAmount = betAmount * (symbol.value / 2);

                    // Update balance
                    currentUser.balance += winAmount;
                    updateUserBalance();

                    // Show result
                    document.getElementById('slot-result').textContent = `You won $${winAmount.toFixed(2)}`;
                    document.getElementById('slot-result').style.color = '#4CAF50';
                }
                // No match, player loses
                else {
                    document.getElementById('slot-result').textContent = `You lost $${betAmount.toFixed(2)}`;
                    document.getElementById('slot-result').style.color = '#F44336';
                }

                // Add transaction to history
                addTransaction({
                    type: 'Game',
                    amount: currentUser.balance > 0 ? betAmount : -betAmount,
                    event: 'Slots Game',
                    date: new Date().toISOString().split('T')[0],
                    status: currentUser.balance > 0 ? 'Won' : 'Lost'
                });
            });
        }

        // Animate slot reel spinning
        function animateSpin(reel, symbols, duration, callback) {
            let startTime = null;
            const spinSpeed = 50; // ms per frame

            function spin(timestamp) {
                if (!startTime) startTime = timestamp;
                const progress = timestamp - startTime;

                if (progress % spinSpeed < 20) {
                    // Move symbols
                    const firstSymbol = reel.children[0];
                    reel.removeChild(firstSymbol);

                    // Add new random symbol at the end
                    const newSymbol = document.createElement('div');
                    newSymbol.className = 'slot-item';
                    newSymbol.textContent = symbols[Math.floor(Math.random() * symbols.length)].symbol;
                    reel.appendChild(newSymbol);
                }

                if (progress < duration) {
                    requestAnimationFrame(spin);
                } else if (callback) {
                    callback();
                }
            }

            requestAnimationFrame(spin);
        }

        // Render crypto prices
        function renderCryptoPrices() {
            const cryptoPricesContainer = document.getElementById('crypto-prices');
            if (!cryptoPricesContainer) return;

            cryptoPricesContainer.innerHTML = '';

            cryptoPrices.forEach(crypto => {
                const cryptoElement = document.createElement('div');
                cryptoElement.className = 'crypto-coin';
                cryptoElement.innerHTML = `
                    <div class="crypto-info">
                        <div class="crypto-icon">${crypto.symbol[0]}</div>
                        <div>
                            <div><strong>${crypto.name}</strong></div>
                            <div>${crypto.symbol}</div>
                        </div>
                    </div>
                    <div>
                        <div class="crypto-price">$${crypto.price.toFixed(2)}</div>
                        <div class="crypto-change ${crypto.change >= 0 ? 'positive' : 'negative'}">
                            ${crypto.change >= 0 ? '+' : ''}${crypto.change}%
                        </div>
                    </div>
                `;
                cryptoPricesContainer.appendChild(cryptoElement);
            });
        }

        // Select crypto bet
        function selectCryptoBet(betId) {
            if (!currentUser) {
                openLoginModal();
                return;
            }

            // Find the element
            const elements = document.querySelectorAll('.bet-option');
            elements.forEach(element => {
                if (element.innerHTML.includes(betId)) {
                    // Toggle selection
                    if (element.classList.contains('selected')) {
                        element.classList.remove('selected');
                    } else {
                        // Remove selection from other options in the same bet
                        const parentBetCard = element.closest('.bet-card');
                        parentBetCard.querySelectorAll('.bet-option').forEach(option => {
                            option.classList.remove('selected');
                        });

                        // Select this option
                        element.classList.add('selected');
                    }
                }
            });
        }

        // Play casino game
        function playGame(gameId) {
            if (!currentUser) {
                openLoginModal();
                return;
            }

            const game = games.find(g => g.id === gameId);
            if (!game) return;

            alert(`Opening ${game.name}. This feature is coming soon!`);
        }

        // Play lottery game
        function playLottery() {
            if (!currentUser) {
                openLoginModal();
                return;
            }

            alert('Lottery game is coming soon!');
        }

        // Play scratch card game
        function playScratchCard() {
            if (!currentUser) {
                openLoginModal();
                return;
            }

            alert('Scratch card game is coming soon!');
        }

        // Play dice game
        function playDice() {
            if (!currentUser) {
                openLoginModal();
                return;
            }

            alert('Dice game is coming soon!');
        }

        // Play crash game
        function playCrash() {
            if (!currentUser) {
                openLoginModal();
                return;
            }

            alert('Crash game is coming soon!');
        }

        // Format date for display
        function formatDate(dateString) {
            const date = new Date(dateString);
            return date.toLocaleString();
        }

        // Select a bet to add to bet slip
        function selectBet(betId, optionId) {
            if (!currentUser) {
                openLoginModal();
                return;
            }

            const bet = bets.find(b => b.id === betId);
            const option = bet.options.find(o => o.id === optionId);

            // Toggle selection
            if (selectedBets[betId] && selectedBets[betId].optionId === optionId) {
                // Remove the bet if it's already selected
                delete selectedBets[betId];
                document.getElementById(`option-${optionId}`).classList.remove('selected');
            } else {
                // If there was another option selected for this bet, remove its selection
                if (selectedBets[betId]) {
                    document.getElementById(`option-${selectedBets[betId].optionId}`).classList.remove('selected');
                }

                // Add the new selection
                selectedBets[betId] = {
                    betId,
                    optionId,
                    teams: bet.teams,
                    option: option.name,
                    odds: option.odds
                };
                document.getElementById(`option-${optionId}`).classList.add('selected');
            }

            updateBetSlip();
        }

        // Update the bet slip UI
        function updateBetSlip() {
            const betSlipItems = document.getElementById('bet-slip-items');
            const emptySlip = document.getElementById('empty-slip');
            const betSlipTotal = document.getElementById('bet-slip-total');
            const betInput = document.getElementById('bet-input');

            betSlipItems.innerHTML = '';

            const selectedBetsArray = Object.values(selectedBets);

            if (selectedBetsArray.length === 0) {
                emptySlip.style.display = 'block';
                betSlipTotal.style.display = 'none';
                betInput.style.display = 'none';
                return;
            }

            emptySlip.style.display = 'none';
            betSlipTotal.style.display = 'block';
            betInput.style.display = 'block';

            let totalOdds = 1;

            selectedBetsArray.forEach(bet => {
                const betItem = document.createElement('div');
                betItem.className = 'bet-slip-item';
                betItem.innerHTML = `
                    <div>
                        <div>${bet.teams}</div>
                        <div>${bet.option}</div>
                    </div>
                    <div>
                        <div>${bet.odds.toFixed(2)}</div>
                        <button onclick="removeBet(${bet.betId})">Remove</button>
                    </div>
                `;
                betSlipItems.appendChild(betItem);
                totalOdds *= bet.odds;
            });

            const betAmount = parseFloat(document.getElementById('bet-amount').value) || 0;
            const potentialWin = betAmount * totalOdds;

            document.getElementById('potential-win').textContent = `$${potentialWin.toFixed(2)}`;
        }

        // Remove a bet from the bet slip
        function removeBet(betId) {
            if (selectedBets[betId]) {
                const optionElement = document.getElementById(`option-${selectedBets[betId].optionId}`);
                if (optionElement) {
                    optionElement.classList.remove('selected');
                }
                delete selectedBets[betId];
                updateBetSlip();
            }
        }

        // Place a bet
        function placeBet() {
            if (!currentUser) {
                openLoginModal();
                return;
            }

            const selectedBetsArray = Object.values(selectedBets);
            if (selectedBetsArray.length === 0) {
                alert('Please select at least one bet');
                return;
            }

            const betAmount = parseFloat(document.getElementById('bet-amount').value);
            if (isNaN(betAmount) || betAmount <= 0) {
                alert('Please enter a valid bet amount');
                return;
            }

            if (betAmount > currentUser.balance) {
                alert('Insufficient balance');
                return;
            }

            // Calculate potential win
            let totalOdds = 1;
            selectedBetsArray.forEach(bet => {
                totalOdds *= bet.odds;
            });

            const potentialWin = betAmount * totalOdds;

            // Update user balance
            currentUser.balance -= betAmount;
            updateUserBalance();

            // Add bet to user's bet history
            const betHistory = JSON.parse(localStorage.getItem('betmaster_bet_history') || '[]');
            betHistory.push({
                id: Date.now(),
                date: new Date().toISOString(),
                selections: selectedBetsArray,
                amount: betAmount,
                potentialWin: potentialWin,
                status: 'Pending'
            });
            localStorage.setItem('betmaster_bet_history', JSON.stringify(betHistory));

            // Add transaction record
            addTransaction({
                type: 'Bet',
                amount: -betAmount,
                event: selectedBetsArray.map(bet => bet.teams).join(', '),
                date: new Date().toISOString().split('T')[0],
                status: 'Pending'
            });

            // Clear bet slip
            selectedBets = {};
            document.getElementById('bet-amount').value = '';
            selectedBetsArray.forEach(bet => {
                const element = document.getElementById(`option-${bet.optionId}`);
                if (element) {
                    element.classList.remove('selected');
                }
            });
            updateBetSlip();

            alert(`Bet placed successfully! Potential win: $${potentialWin.toFixed(2)}`);
        }

        // Open login modal
        function openLoginModal() {
            document.getElementById('login-modal').style.display = 'flex';
        }

        // Open register modal
        function openRegisterModal() {
            document.getElementById('register-modal').style.display = 'flex';
        }

        // Open deposit modal
        function openDepositModal() {
            document.getElementById('deposit-modal').style.display = 'flex';
        }

        // Open withdraw modal
        function openWithdrawModal() {
            document.getElementById('withdraw-modal').style.display = 'flex';
        }

        // Open profile picture modal
        function openProfilePictureModal() {
            document.getElementById('profile-picture-modal').style.display = 'flex';

            // Set current profile picture to preview
            if (currentUser.profilePicture) {
                document.getElementById('profile-picture-preview').src = currentUser.profilePicture;
            }

            // Set up image preview on file selection
            document.getElementById('profile-picture-input').addEventListener('change', function(event) {
                const file = event.target.files[0];
                if (file) {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        document.getElementById('profile-picture-preview').src = e.target.result;
                    };
                    reader.readAsDataURL(file);
                }
            });
        }

        // Close modal
        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }

        // Toggle chat window
        function toggleChat() {
            const chatWindow = document.getElementById('chat-window');
            const chatNotification = document.getElementById('chat-notification');

            if (chatWindow.style.display === 'flex') {
                chatWindow.style.display = 'none';
            } else {
                chatWindow.style.display = 'flex';
                chatNotification.style.display = 'none';
            }
        }

        // Send chat message
        function sendChatMessage() {
            const inputField = document.getElementById('chat-input-field');
            const message = inputField.value.trim();

            if (message === '') return;

            const chatMessages = document.getElementById('chat-messages');

            // Add user message
            const userMessage = document.createElement('div');
            userMessage.className = 'message message-user';
            userMessage.innerHTML = `<div class="message-content">${message}</div>`;
            chatMessages.appendChild(userMessage);

            // Clear input field
            inputField.value = '';

            // Scroll to bottom
            chatMessages.scrollTop = chatMessages.scrollHeight;

            // Simulate support response after a delay
            setTimeout(() => {
                const supportMessage = document.createElement('div');
                supportMessage.className = 'message message-support';
                supportMessage.innerHTML = `<div class="message-content">${getAutoResponse(message)}</div>`;
                chatMessages.appendChild(supportMessage);

                // Scroll to bottom
                chatMessages.scrollTop = chatMessages.scrollHeight;
            }, 1000);
        }

        // Get automated response based on user message
        function getAutoResponse(message) {
            message = message.toLowerCase();

            if (message.includes('deposit') || message.includes('payment')) {
                return 'To make a deposit, please go to your account and click on "Deposit Funds". We accept credit cards, PayPal, and cryptocurrency.';
            } else if (message.includes('withdraw') || message.includes('cash out')) {
                return 'Withdrawals are processed within 24-48 hours. Please go to your account and click on "Withdraw Funds" to request a withdrawal.';
            } else if (message.includes('bonus') || message.includes('promotion')) {
                return 'We offer a welcome bonus of 100% up to $200 for new users. We also have regular promotions for existing users. Check the Promotions section for details.';
            } else if (message.includes('bet') || message.includes('odds')) {
                return 'You can place bets by selecting odds on any available event. Your selections will be added to your bet slip where you can enter your stake amount.';
            } else if (message.includes('account') || message.includes('register') || message.includes('login')) {
                return 'You can create an account by clicking "Register" or sign in to your existing account by clicking "Login" at the top right of the page.';
            } else if (message.includes('help') || message.includes('support')) {
                return 'Our support team is available 24/7. You can contact us through this chat, email us at support@betmaster.com, or call us at +1-800-BET-HELP.';
            } else {
                return 'Thank you for your message. How else can I assist you today?';
            }
        }

        // Login functionality
        function login() {
            const email = document.getElementById('login-email').value;
            const password = document.getElementById('login-password').value;

            if (!email || !password) {
                alert('Please fill in all fields');
                return;
            }

            // In a real app, this would check credentials against a server
            // For demo purposes, we'll check if the user exists in localStorage
            const users = JSON.parse(localStorage.getItem('betmaster_users') || '[]');
            const user = users.find(u => u.email === email && u.password === password);

            if (user) {
                currentUser = user;
                localStorage.setItem('betmaster_user', JSON.stringify(user));
                showLoggedInUI();
                closeModal('login-modal');
            } else {
                alert('Invalid email or password');
            }
        }

        // Register functionality
        function register() {
            const name = document.getElementById('register-name').value;
            const email = document.getElementById('register-email').value;
            const password = document.getElementById('register-password').value;
            const confirmPassword = document.getElementById('register-confirm-password').value;

            if (!name || !email || !password || !confirmPassword) {
                alert('Please fill in all fields');
                return;
            }

            if (password !== confirmPassword) {
                alert('Passwords do not match');
                return;
            }

            // In a real app, this would send data to a server
            // For demo purposes, we'll store in localStorage
            const users = JSON.parse(localStorage.getItem('betmaster_users') || '[]');

            if (users.some(u => u.email === email)) {
                alert('Email already in use');
                return;
            }

            const newUser = {
                id: Date.now(),
                name,
                email,
                password,
                balance: 1000, // Starting balance for new users
                created: new Date().toISOString()
            };

            users.push(newUser);
            localStorage.setItem('betmaster_users', JSON.stringify(users));

            // Log in the new user
            currentUser = newUser;
            localStorage.setItem('betmaster_user', JSON.stringify(newUser));
            showLoggedInUI();

            closeModal('register-modal');
            alert('Registration successful! Welcome to BetMaster.');
        }

        // Logout functionality
        function logout() {
            localStorage.removeItem('betmaster_user');
            currentUser = null;
            selectedBets = {};
            updateBetSlip();
            showLoggedOutUI();
            showSection('sports');
        }

        // Update profile picture
        function updateProfilePicture() {
            const profilePictureInput = document.getElementById('profile-picture-input');

            if (profilePictureInput.files.length > 0) {
                const file = profilePictureInput.files[0];
                const reader = new FileReader();

                reader.onload = function(e) {
                    const imageDataUrl = e.target.result;

                    // Update current user profile picture
                    currentUser.profilePicture = imageDataUrl;

                    // Update in localStorage
                    localStorage.setItem('betmaster_user', JSON.stringify(currentUser));

                    // Update UI
                    document.getElementById('nav-profile-picture').src = imageDataUrl;
                    if (document.getElementById('profile-picture')) {
                        document.getElementById('profile-picture').src = imageDataUrl;
                    }

                    closeModal('profile-picture-modal');
                };

                reader.readAsDataURL(file);
            } else {
                alert('Please select an image file');
            }
        }

        // Change password
        function changePassword() {
            const currentPassword = document.getElementById('current-password').value;
            const newPassword = document.getElementById('new-password').value;
            const confirmNewPassword = document.getElementById('confirm-new-password').value;

            if (!currentPassword || !newPassword || !confirmNewPassword) {
                alert('Please fill in all password fields');
                return;
            }

            if (currentPassword !== currentUser.password) {
                alert('Current password is incorrect');
                return;
            }

            if (newPassword !== confirmNewPassword) {
                alert('New passwords do not match');
                return;
            }

            // Update password
            currentUser.password = newPassword;

            // Update in localStorage
            localStorage.setItem('betmaster_user', JSON.stringify(currentUser));

            // Update in users list
            const users = JSON.parse(localStorage.getItem('betmaster_users') || '[]');
            const userIndex = users.findIndex(u => u.id === currentUser.id);
            if (userIndex !== -1) {
                users[userIndex] = currentUser;
                localStorage.setItem('betmaster_users', JSON.stringify(users));
            }

            // Clear password fields
            document.getElementById('current-password').value = '';
            document.getElementById('new-password').value = '';
            document.getElementById('confirm-new-password').value = '';

            alert('Password changed successfully');
        }

        // Deposit funds
        function depositFunds() {
            const amount = parseFloat(document.getElementById('deposit-amount').value);

            if (isNaN(amount) || amount <= 0) {
                alert('Please enter a valid amount');
                return;
            }

            // Validate payment details based on method
            if (currentPaymentMethod === 'card') {
                const cardNumber = document.getElementById('card-number').value;
                const cardExpiry = document.getElementById('card-expiry').value;
                const cardCvv = document.getElementById('card-cvv').value;

                if (!cardNumber || !cardExpiry || !cardCvv) {
                    alert('Please fill in all card details');
                    return;
                }
            } else if (currentPaymentMethod === 'paypal') {
                const paypalEmail = document.getElementById('paypal-email').value;

                if (!paypalEmail) {
                    alert('Please enter your PayPal email');
                    return;
                }
            } else if (currentPaymentMethod === 'crypto') {
                // No validation needed for crypto deposits as they're handled differently
            } else if (currentPaymentMethod === 'bank') {
                // No additional validation needed for bank transfers
            }

            // In a real app, this would process payment via a payment gateway
            // For demo purposes, we'll just update the user's balance
            currentUser.balance += amount;
            updateUserBalance();

            // Add transaction record
            addTransaction({
                type: 'Deposit',
                amount: amount,
                method: getPaymentMethodName(currentPaymentMethod),
                date: new Date().toISOString().split('T')[0],
                status: 'Completed'
            });

            closeModal('deposit-modal');
            alert(`Successfully deposited $${amount.toFixed(2)}`);
        }

        // Withdraw funds
        function withdrawFunds() {
            const amount = parseFloat(document.getElementById('withdraw-amount').value);

            if (isNaN(amount) || amount <= 0) {
                alert('Please enter a valid amount');
                return;
            }

            if (amount > currentUser.balance) {
                alert('Insufficient balance');
                return;
            }

            // Validate withdrawal details based on method
            if (currentWithdrawalMethod === 'card') {
                const cardNumber = document.getElementById('withdrawal-card-number').value;
                const cardName = document.getElementById('withdrawal-card-name').value;

                if (!cardNumber || !cardName) {
                    alert('Please fill in all card details');
                    return;
                }
            } else if (currentWithdrawalMethod === 'paypal') {
                const paypalEmail = document.getElementById('withdrawal-paypal-email').value;

                if (!paypalEmail) {
                    alert('Please enter your PayPal email');
                    return;
                }
            } else if (currentWithdrawalMethod === 'crypto') {
                const cryptoAddress = document.getElementById('withdrawal-crypto-address').value;

                if (!cryptoAddress) {
                    alert('Please enter your wallet address');
                    return;
                }
            } else if (currentWithdrawalMethod === 'bank') {
                const bankName = document.getElementById('bank-name').value;
                const accountName = document.getElementById('account-name').value;
                const accountNumber = document.getElementById('account-number').value;
                const bankSwift = document.getElementById('bank-swift').value;

                if (!bankName || !accountName || !accountNumber || !bankSwift) {
                    alert('Please fill in all bank details');
                    return;
                }
            }

            // In a real app, this would process the withdrawal via a payment processor
            // For demo purposes, we'll just update the user's balance
            currentUser.balance -= amount;
            updateUserBalance();

            // Add transaction record
            addTransaction({
                type: 'Withdrawal',
                amount: -amount,
                method: getPaymentMethodName(currentWithdrawalMethod),
                date: new Date().toISOString().split('T')[0],
                status: 'Pending'
            });

            closeModal('withdraw-modal');
            alert(`Withdrawal of $${amount.toFixed(2)} initiated. It will be processed within 1-3 business days.`);
        }

        // Update user balance in UI and storage
        function updateUserBalance() {
            document.getElementById('balance-amount').textContent = currentUser.balance.toFixed(2);
            document.getElementById('account-balance').textContent = currentUser.balance.toFixed(2);
            localStorage.setItem('betmaster_user', JSON.stringify(currentUser));
        }

        // Add transaction to history
        function addTransaction(transaction) {
            const transactions = JSON.parse(localStorage.getItem('betmaster_transactions_' + currentUser.id) || '[]');
            transaction.id = Date.now();
            transactions.unshift(transaction); // Add to beginning of array
            localStorage.setItem('betmaster_transactions_' + currentUser.id, JSON.stringify(transactions));
        }

        // Select payment method for deposit
        function selectPaymentMethod(element, method) {
            // Remove selection from all methods
            const methods = document.querySelectorAll('.payment-method');
            methods.forEach(m => m.classList.remove('selected'));

            // Add selection to this method
            element.classList.add('selected');

            // Hide all payment details
            document.getElementById('payment-details-card').style.display = 'none';
            document.getElementById('payment-details-paypal').style.display = 'none';
            document.getElementById('payment-details-crypto').style.display = 'none';
            document.getElementById('payment-details-bank').style.display = 'none';

            // Show details for selected method
            document.getElementById('payment-details-' + method).style.display = 'block';

            // Update current method
            currentPaymentMethod = method;
        }

        // Select withdrawal method
        function selectWithdrawalMethod(element, method) {
            // Remove selection from all methods
            const methods = document.querySelectorAll('.payment-method');
            methods.forEach(m => m.classList.remove('selected'));

            // Add selection to this method
            element.classList.add('selected');

            // Hide all withdrawal details
            document.getElementById('withdrawal-details-card').style.display = 'none';
            document.getElementById('withdrawal-details-paypal').style.display = 'none';
            document.getElementById('withdrawal-details-crypto').style.display = 'none';
            document.getElementById('withdrawal-details-bank').style.display = 'none';

            // Show details for selected method
            document.getElementById('withdrawal-details-' + method).style.display = 'block';

            // Update current method
            currentWithdrawalMethod = method;
        }

        // Get payment method display name
        function getPaymentMethodName(method) {
            switch (method) {
                case 'card': return 'Credit Card';
                case 'paypal': return 'PayPal';
                case 'crypto': return 'Cryptocurrency';
                case 'bank': return 'Bank Transfer';
                default: return 'Unknown';
            }
        }

        // Check for available bonuses
        function checkBonuses() {
            alert('You have a Welcome Bonus available: 100% up to $200 on your first deposit!');
        }

        // Get random color for game cards
        function getRandomColor() {
            const colors = ['#4CAF50', '#2196F3', '#9C27B0', '#FF9800', '#F44336', '#009688'];
            return colors[Math.floor(Math.random() * colors.length)];
        }

        // Get icon for game type
        function getGameIcon(type) {
            switch (type) {
                case 'slots': return '🎰';
                case 'cards': return '🃏';
                case 'table': return '🎲';
                case 'arcade': return '🎮';
                case 'lottery': return '🎫';
                default: return '🎲';
            }
        }

        // Listen for changes to bet amount
        document.addEventListener('input', function(e) {
            if (e.target.id === 'bet-amount') {
                updateBetSlip();
            }
        });

        // Initialize the application when the page loads
        window.onload = init;
    </script>
</body>
</html>
