<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AdEarn - Earn by Watching Ads</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        :root {
            --primary: #4361ee;
            --secondary: #3a0ca3;
            --accent: #f72585;
            --light: #f8f9fa;
            --dark: #212529;
            --success: #4cc9f0;
            --warning: #ffd166;
            --danger: #ef476f;
            --gray: #6c757d;
        }
        
        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .container {
            width: 100%;
            max-width: 1200px;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
            overflow: hidden;
            display: flex;
            min-height: 90vh;
        }
        
        .welcome-section {
            flex: 1;
            background: linear-gradient(to right bottom, var(--primary), var(--secondary));
            color: white;
            padding: 40px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
        }
        
        .welcome-section h1 {
            font-size: 2.5rem;
            margin-bottom: 20px;
        }
        
        .welcome-section p {
            font-size: 1.2rem;
            margin-bottom: 30px;
            max-width: 400px;
        }
        
        .app-icon {
            font-size: 5rem;
            margin-bottom: 30px;
            color: var(--warning);
        }
        
        .features {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
        }
        
        .feature {
            background: rgba(255, 255, 255, 0.2);
            padding: 15px;
            border-radius: 10px;
            width: 150px;
            text-align: center;
        }
        
        .feature i {
            font-size: 2rem;
            margin-bottom: 10px;
        }
        
        .form-section {
            flex: 1;
            padding: 40px;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
        
        .form-container {
            width: 100%;
            max-width: 400px;
            margin: 0 auto;
        }
        
        .tab-container {
            display: flex;
            margin-bottom: 30px;
        }
        
        .tab {
            flex: 1;
            text-align: center;
            padding: 15px;
            cursor: pointer;
            font-weight: 600;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            border-bottom: 3px solid transparent;
        }
        
        .tab.active {
            border-bottom: 3px solid var(--primary);
            color: var(--primary);
        }
        
        .form {
            display: none;
        }
        
        .form.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: var(--dark);
        }
        
        .form-group input {
            width: 100%;
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
            transition: border 0.3s ease;
        }
        
        .form-group input:focus {
            border-color: var(--primary);
            outline: none;
        }
        
        .btn {
            width: 100%;
            padding: 15px;
            border: none;
            border-radius: 8px;
            background: var(--primary);
            color: white;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: background 0.3s ease;
        }
        
        .btn:hover {
            background: var(--secondary);
        }
        
        .dashboard {
            display: none;
            width: 100%;
            padding: 20px;
        }
        
        .dashboard-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding-bottom: 15px;
            border-bottom: 1px solid #eee;
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .user-avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: var(--primary);
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-size: 1.5rem;
        }
        
        .balance-card {
            background: linear-gradient(to right, var(--primary), var(--secondary));
            color: white;
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 30px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .balance-label {
            font-size: 1rem;
            margin-bottom: 10px;
            opacity: 0.9;
        }
        
        .balance-amount {
            font-size: 2.5rem;
            font-weight: 700;
        }
        
        .nav-tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 30px;
            border-bottom: 1px solid #eee;
            padding-bottom: 15px;
        }
        
        .nav-tab {
            padding: 12px 25px;
            border-radius: 30px;
            background: #f1f3f9;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        
        .nav-tab.active {
            background: var(--primary);
            color: white;
        }
        
        .content-section {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .content-section.active {
            display: block;
        }
        
        .withdrawal-option {
            background: white;
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 15px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.08);
            display: flex;
            align-items: center;
            gap: 15px;
            cursor: pointer;
            transition: transform 0.3s ease;
        }
        
        .withdrawal-option:hover {
            transform: translateY(-3px);
        }
        
        .option-icon {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: #f1f3f9;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 1.5rem;
            color: var(--primary);
        }
        
        .option-details h3 {
            margin-bottom: 5px;
            color: var(--dark);
        }
        
        .option-details p {
            color: #777;
            font-size: 0.9rem;
        }
        
        .ad-container {
            background: white;
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            margin-bottom: 30px;
        }
        
        .ad-placeholder {
            width: 100%;
            height: 250px;
            background: #f1f3f9;
            border-radius: 10px;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            margin-bottom: 20px;
        }
        
        .ad-icon {
            font-size: 3rem;
            color: var(--primary);
            margin-bottom: 15px;
        }
        
        .watch-btn {
            padding: 15px 40px;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 30px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: background 0.3s ease;
        }
        
        .watch-btn:hover {
            background: var(--secondary);
        }
        
        .earnings-history {
            background: white;
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .history-title {
            margin-bottom: 20px;
            color: var(--dark);
        }
        
        .history-item {
            display: flex;
            justify-content: space-between;
            padding: 15px 0;
            border-bottom: 1px solid #eee;
        }
        
        .history-item:last-child {
            border-bottom: none;
        }
        
        .logout-btn {
            background: var(--danger);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 30px;
            cursor: pointer;
            font-weight: 600;
            transition: background 0.3s ease;
        }
        
        .logout-btn:hover {
            background: #d32f2f;
        }
        
        .withdrawal-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }
        
        .modal-content {
            background: white;
            padding: 30px;
            border-radius: 15px;
            width: 90%;
            max-width: 500px;
            box-shadow: 0 5px 25px rgba(0, 0, 0, 0.2);
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .close-btn {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--gray);
        }
        
        .modal-form {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .modal-form input {
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
        }
        
        .modal-form button {
            padding: 12px;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            margin-top: 10px;
        }
        
        @media (max-width: 900px) {
            .container {
                flex-direction: column;
                min-height: auto;
            }
            
            .welcome-section {
                padding: 30px 20px;
            }
            
            .form-section {
                padding: 30px 20px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Welcome Section -->
        <div class="welcome-section">
            <div class="app-icon">
                <i class="fas fa-ad"></i>
            </div>
            <h1>AdEarn</h1>
            <p>Watch ads, earn money, and withdraw your earnings via multiple options</p>
            
            <div class="features">
                <div class="feature">
                    <i class="fas fa-wallet"></i>
                    <p>Easy Withdrawal</p>
                </div>
                <div class="feature">
                    <i class="fas fa-rupee-sign"></i>
                    <p>Instant Earnings</p>
                </div>
                <div class="feature">
                    <i class="fas fa-user-shield"></i>
                    <p>Secure</p>
                </div>
            </div>
        </div>
        
        <!-- Form Section -->
        <div class="form-section">
            <div class="form-container">
                <div class="tab-container">
                    <div class="tab active" onclick="switchTab('login')">Login</div>
                    <div class="tab" onclick="switchTab('signup')">Sign Up</div>
                </div>
                
                <form class="form active" id="loginForm">
                    <div class="form-group">
                        <label for="loginEmail">Email</label>
                        <input type="email" id="loginEmail" placeholder="Enter your email" required>
                    </div>
                    <div class="form-group">
                        <label for="loginPassword">Password</label>
                        <input type="password" id="loginPassword" placeholder="Enter your password" required>
                    </div>
                    <button type="button" class="btn" onclick="login()">Login</button>
                </form>
                
                <form class="form" id="signupForm">
                    <div class="form-group">
                        <label for="signupName">Full Name</label>
                        <input type="text" id="signupName" placeholder="Enter your full name" required>
                    </div>
                    <div class="form-group">
                        <label for="signupEmail">Email</label>
                        <input type="email" id="signupEmail" placeholder="Enter your email" required>
                    </div>
                    <div class="form-group">
                        <label for="signupPassword">Password</label>
                        <input type="password" id="signupPassword" placeholder="Create a password" required>
                    </div>
                    <button type="button" class="btn" onclick="signup()">Sign Up</button>
                </form>
            </div>
        </div>
        
        <!-- Dashboard -->
        <div class="dashboard" id="dashboard">
            <div class="dashboard-header">
                <div class="user-info">
                    <div class="user-avatar">
                        <i class="fas fa-user"></i>
                    </div>
                    <div>
                        <h2 id="userName">User Name</h2>
                        <p id="userEmail">user@example.com</p>
                    </div>
                </div>
                <button class="logout-btn" onclick="logout()">Logout</button>
            </div>
            
            <div class="balance-card">
                <div class="balance-label">Your Balance</div>
                <div class="balance-amount">₹<span id="userBalance">50.25</span></div>
            </div>
            
            <div class="nav-tabs">
                <div class="nav-tab active" onclick="switchContent('withdraw')">Withdraw</div>
                <div class="nav-tab" onclick="switchContent('tasks')">Earn</div>
            </div>
            
            <!-- Withdrawal Section -->
            <div class="content-section active" id="withdrawSection">
                <h2 class="section-title">Withdrawal Options</h2>
                <p style="margin-bottom: 20px; color: #777;">Choose your preferred withdrawal method</p>
                
                <div class="withdrawal-option" onclick="openWithdrawalModal('amazon')">
                    <div class="option-icon">
                        <i class="fab fa-amazon"></i>
                    </div>
                    <div class="option-details">
                        <h3>Amazon Voucher</h3>
                        <p>Minimum withdrawal: ₹100</p>
                    </div>
                </div>
                
                <div class="withdrawal-option" onclick="openWithdrawalModal('google')">
                    <div class="option-icon">
                        <i class="fab fa-google-play"></i>
                    </div>
                    <div class="option-details">
                        <h3>Google Play Code</h3>
                        <p>Minimum withdrawal: ₹50</p>
                    </div>
                </div>
                
                <div class="withdrawal-option" onclick="openWithdrawalModal('upi')">
                    <div class="option-icon">
                        <i class="fas fa-mobile-alt"></i>
                    </div>
                    <div class="option-details">
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AdEarn - Earn by Watching Ads</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        :root {
            --primary: #4361ee;
            --secondary: #3a0ca3;
            --accent: #f72585;
            --light: #f8f9fa;
            --dark: #212529;
            --success: #4cc9f0;
            --warning: #ffd166;
            --danger: #ef476f;
            --gray: #6c757d;
        }
        
        body {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .container {
            width: 100%;
            max-width: 1200px;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
            overflow: hidden;
            display: flex;
            min-height: 90vh;
        }
        
        .welcome-section {
            flex: 1;
            background: linear-gradient(to right bottom, var(--primary), var(--secondary));
            color: white;
            padding: 40px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
        }
        
        .welcome-section h1 {
            font-size: 2.5rem;
            margin-bottom: 20px;
        }
        
        .welcome-section p {
            font-size: 1.2rem;
            margin-bottom: 30px;
            max-width: 400px;
        }
        
        .app-icon {
            font-size: 5rem;
            margin-bottom: 30px;
            color: var(--warning);
        }
        
        .features {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
        }
        
        .feature {
            background: rgba(255, 255, 255, 0.2);
            padding: 15px;
            border-radius: 10px;
            width: 150px;
            text-align: center;
        }
        
        .feature i {
            font-size: 2rem;
            margin-bottom: 10px;
        }
        
        .form-section {
            flex: 1;
            padding: 40px;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
        
        .form-container {
            width: 100%;
            max-width: 400px;
            margin: 0 auto;
        }
        
        .tab-container {
            display: flex;
            margin-bottom: 30px;
        }
        
        .tab {
            flex: 1;
            text-align: center;
            padding: 15px;
            cursor: pointer;
            font-weight: 600;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            border-bottom: 3px solid transparent;
        }
        
        .tab.active {
            border-bottom: 3px solid var(--primary);
            color: var(--primary);
        }
        
        .form {
            display: none;
        }
        
        .form.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: var(--dark);
        }
        
        .form-group input {
            width: 100%;
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
            transition: border 0.3s ease;
        }
        
        .form-group input:focus {
            border-color: var(--primary);
            outline: none;
        }
        
        .btn {
            width: 100%;
            padding: 15px;
            border: none;
            border-radius: 8px;
            background: var(--primary);
            color: white;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: background 0.3s ease;
        }
        
        .btn:hover {
            background: var(--secondary);
        }
        
        .dashboard {
            display: none;
            width: 100%;
            padding: 20px;
        }
        
        .dashboard-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding-bottom: 15px;
            border-bottom: 1px solid #eee;
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .user-avatar {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: var(--primary);
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-size: 1.5rem;
        }
        
        .balance-card {
            background: linear-gradient(to right, var(--primary), var(--secondary));
            color: white;
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 30px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .balance-label {
            font-size: 1rem;
            margin-bottom: 10px;
            opacity: 0.9;
        }
        
        .balance-amount {
            font-size: 2.5rem;
            font-weight: 700;
        }
        
        .nav-tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 30px;
            border-bottom: 1px solid #eee;
            padding-bottom: 15px;
        }
        
        .nav-tab {
            padding: 12px 25px;
            border-radius: 30px;
            background: #f1f3f9;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        
        .nav-tab.active {
            background: var(--primary);
            color: white;
        }
        
        .content-section {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .content-section.active {
            display: block;
        }
        
        .withdrawal-option {
            background: white;
            border-radius: 12px;
            padding: 20px;
            margin-bottom: 15px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.08);
            display: flex;
            align-items: center;
            gap: 15px;
            cursor: pointer;
            transition: transform 0.3s ease;
        }
        
        .withdrawal-option:hover {
            transform: translateY(-3px);
        }
        
        .option-icon {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: #f1f3f9;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 1.5rem;
            color: var(--primary);
        }
        
        .option-details h3 {
            margin-bottom: 5px;
            color: var(--dark);
        }
        
        .option-details p {
            color: #777;
            font-size: 0.9rem;
        }
        
        .ad-container {
            background: white;
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            margin-bottom: 30px;
        }
        
        .ad-placeholder {
            width: 100%;
            height: 250px;
            background: #f1f3f9;
            border-radius: 10px;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            margin-bottom: 20px;
        }
        
        .ad-icon {
            font-size: 3rem;
            color: var(--primary);
            margin-bottom: 15px;
        }
        
        .watch-btn {
            padding: 15px 40px;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 30px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: background 0.3s ease;
        }
        
        .watch-btn:hover {
            background: var(--secondary);
        }
        
        .earnings-history {
            background: white;
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .history-title {
            margin-bottom: 20px;
            color: var(--dark);
        }
        
        .history-item {
            display: flex;
            justify-content: space-between;
            padding: 15px 0;
            border-bottom: 1px solid #eee;
        }
        
        .history-item:last-child {
            border-bottom: none;
        }
        
        .logout-btn {
            background: var(--danger);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 30px;
            cursor: pointer;
            font-weight: 600;
            transition: background 0.3s ease;
        }
        
        .logout-btn:hover {
            background: #d32f2f;
        }
        
        .withdrawal-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }
        
        .modal-content {
            background: white;
            padding: 30px;
            border-radius: 15px;
            width: 90%;
            max-width: 500px;
            box-shadow: 0 5px 25px rgba(0, 0, 0, 0.2);
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .close-btn {
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--gray);
        }
        
        .modal-form {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .modal-form input {
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 1rem;
        }
        
        .modal-form button {
            padding: 12px;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            margin-top: 10px;
        }
        
        @media (max-width: 900px) {
            .container {
                flex-direction: column;
                min-height: auto;
            }
            
            .welcome-section {
                padding: 30px 20px;
            }
            
            .form-section {
                padding: 30px 20px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Welcome Section -->
        <div class="welcome-section">
            <div class="app-icon">
                <i class="fas fa-ad"></i>
            </div>
            <h1>AdEarn</h1>
            <p>Watch ads, earn money, and withdraw your earnings via multiple options</p>
            
            <div class="features">
                <div class="feature">
                    <i class="fas fa-wallet"></i>
                    <p>Easy Withdrawal</p>
                </div>
                <div class="feature">
                    <i class="fas fa-rupee-sign"></i>
                    <p>Instant Earnings</p>
                </div>
                <div class="feature">
                    <i class="fas fa-user-shield"></i>
                    <p>Secure</p>
                </div>
            </div>
        </div>
        
        <!-- Form Section -->
        <div class="form-section">
            <div class="form-container">
                <div class="tab-container">
                    <div class="tab active" onclick="switchTab('login')">Login</div>
                    <div class="tab" onclick="switchTab('signup')">Sign Up</div>
                </div>
                
                <form class="form active" id="loginForm">
                    <div class="form-group">
                        <label for="loginEmail">Email</label>
                        <input type="email" id="loginEmail" placeholder="Enter your email" required>
                    </div>
                    <div class="form-group">
                        <label for="loginPassword">Password</label>
                        <input type="password" id="loginPassword" placeholder="Enter your password" required>
                    </div>
                    <button type="button" class="btn" onclick="login()">Login</button>
                </form>
                
                <form class="form" id="signupForm">
                    <div class="form-group">
                        <label for="signupName">Full Name</label>
                        <input type="text" id="signupName" placeholder="Enter your full name" required>
                    </div>
                    <div class="form-group">
                        <label for="signupEmail">Email</label>
                        <input type="email" id="signupEmail" placeholder="Enter your email" required>
                    </div>
                    <div class="form-group">
                        <label for="signupPassword">Password</label>
                        <input type="password" id="signupPassword" placeholder="Create a password" required>
                    </div>
                    <button type="button" class="btn" onclick="signup()">Sign Up</button>
                </form>
            </div>
        </div>
        
        <!-- Dashboard -->
        <div class="dashboard" id="dashboard">
            <div class="dashboard-header">
                <div class="user-info">
                    <div class="user-avatar">
                        <i class="fas fa-user"></i>
                    </div>
                    <div>
                        <h2 id="userName">User Name</h2>
                        <p id="userEmail">user@example.com</p>
                    </div>
                </div>
                <button class="logout-btn" onclick="logout()">Logout</button>
            </div>
            
            <div class="balance-card">
                <div class="balance-label">Your Balance</div>
                <div class="balance-amount">₹<span id="userBalance">50.25</span></div>
            </div>
            
            <div class="nav-tabs">
                <div class="nav-tab active" onclick="switchContent('withdraw')">Withdraw</div>
                <div class="nav-tab" onclick="switchContent('tasks')">Earn</div>
            </div>
            
            <!-- Withdrawal Section -->
            <div class="content-section active" id="withdrawSection">
                <h2 class="section-title">Withdrawal Options</h2>
                <p style="margin-bottom: 20px; color: #777;">Choose your preferred withdrawal method</p>
                
                <div class="withdrawal-option" onclick="openWithdrawalModal('amazon')">
                    <div class="option-icon">
                        <i class="fab fa-amazon"></i>
                    </div>
                    <div class="option-details">
                        <h3>Amazon Voucher</h3>
                        <p>Minimum withdrawal: ₹100</p>
                    </div>
                </div>
                
                <div class="withdrawal-option" onclick="openWithdrawalModal('google')">
                    <div class="option-icon">
                        <i class="fab fa-google-play"></i>
                    </div>
                    <div class="option-details">
                        <h3>Google Play Code</h3>
                        <p>Minimum withdrawal: ₹50</p>
                    </div>
                </div>
                
                <div class="withdrawal-option" onclick="openWithdrawalModal('upi')">
                    <div class="option-icon">
                        <i class="fas fa-mobile-alt"></i>
                    </div>
                    <div class="option-details">
                        <h3>UPI Transfer</h3>
                        <p>Minimum withdrawal: ₹20</p>
                    </div>
                </div>
            </div>
            
            <!-- Tasks Section -->
            <div class="content-section" id="tasksSection">
                <h2 class="section-title">Earn by Watching Ads</h2>
                <p style="margin-bottom: 20px; color: #777;">Watch ads and earn ₹0.10 per ad</p>
                
                <div class="ad-container">
                    <div class="ad-placeholder">
                        <div class="ad-icon">
                            <i class="fas fa-ad"></i>
                        </div>
                        <p>Advertisement will be shown here</p>
                    </div>
                    <button class="watch-btn" onclick="watchAd()">Watch Ad & Earn ₹0.10</button>
                </div>
                
                <div class="earnings-history">
                    <h3 class="history-title">Your Earnings History</h3>
                    <div id="earningsList">
                        <div class="history-item">
                            <div>Ad Watch - 10:30 AM</div>
                            <div>+ ₹0.10</div>
                        </div>
                        <div class="history-item">
                            <div>Ad Watch - 09:45 AM</div>
                            <div>+ ₹0.10</div>
                        </div>
                        <div class="history-item">
                            <div>Ad Watch - Yesterday</div>
                            <div>+ ₹0.10</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Withdrawal Modal -->
    <div class="withdrawal-modal" id="withdrawalModal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 id="modalTitle">Withdraw Funds</h2>
                <button class="close-btn" onclick="closeModal()">&times;</button>
            </div>
            <div class="modal-form">
                <input type="number" id="withdrawAmount" placeholder="Enter amount">
                <div id="additionalFields"></div>
                <button type="button" onclick="processWithdrawal()">Withdraw</button>
            </div>
        </div>
    </div>

    <script>
        // Current user data (in a real app, this would come from a server)
        let currentUser = null;
        let currentWithdrawalMethod = '';
        
        // Demo users data
        const users = [
            {
                name: "John Doe",
                email: "john@example.com",
                password: "password123",
                balance: 50.25,
                earnings: [
                    { date: "10:30 AM", amount: 0.10 },
                    { date: "09:45 AM", amount: 0.10 },
                    { date: "Yesterday", amount: 0.10 }
                ]
            },
            {
                name: "Jane Smith",
                email: "jane@example.com",
                password: "password123",
                balance: 125.75,
                earnings: [
                    { date: "11:15 AM", amount: 0.10 },
                    { date: "10:20 AM", amount: 0.10 },
                    { date: "Yesterday", amount: 0.10 }
                ]
            }
        ];
        
        // Switch between login and signup tabs
        function switchTab(tab) {
            document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.form').forEach(f => f.classList.remove('active'));
            
            if (tab === 'login') {
                document.querySelector('.tab:nth-child(1)').classList.add('active');
                document.getElementById('loginForm').classList.add('active');
            } else {
                document.querySelector('.tab:nth-child(2)').classList.add('active');
                document.getElementById('signupForm').classList.add('active');
            }
        }
        
        // Switch between dashboard content
        function switchContent(content) {
            document.querySelectorAll('.nav-tab').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.content-section').forEach(s => s.classList.remove('active'));
            
            if (content === 'withdraw') {
                document.querySelector('.nav-tab:nth-child(1)').classList.add('active');
                document.getElementById('withdrawSection').classList.add('active');
            } else {
                document.querySelector('.nav-tab:nth-child(2)').classList.add('active');
                document.getElementById('tasksSection').classList.add('active');
            }
        }
        
        // Login function
        function login() {
            const email = document.getElementById('loginEmail').value;
            const password = document.getElementById('loginPassword').value;
            
            // Find user in demo data
            const user = users.find(u => u.email === email && u.password === password);
            
            if (user) {
                currentUser = user;
                showDashboard();
            } else {
                alert('Invalid email or password. Try with john@example.com/password123 or jane@example.com/password123');
            }
        }
        
        // Signup function
        function signup() {
            const name = document.getElementById('signupName').value;
            const email = document.getElementById('signupEmail').value;
            const password = document.getElementById('signupPassword').value;
            
            // Check if user already exists
            if (users.some(u => u.email === email)) {
                alert('User with this email already exists');
                return;
            }
            
            // Create new user
            const newUser = {
                name,
                email,
                password,
                balance: 0,
                earnings: []
            };
            
            users.push(newUser);
            currentUser = newUser;
            
            alert('Account created successfully!');
            showDashboard();
        }
        
        // Show dashboard
        function showDashboard() {
            document.querySelector('.form-section').style.display = 'none';
            document.querySelector('.welcome-section').style.display = 'none';
            document.getElementById('dashboard').style.display = 'block';
            
            // Update user info
            document.getElementById('userName').textContent = currentUser.name;
            document.getElementById('userEmail').textContent = currentUser.email;
            document.getElementById('userBalance').textContent = currentUser.balance.toFixed(2);
            
            // Update earnings history
            updateEarningsHistory();
        }
        
        // Update earnings history
        function updateEarningsHistory() {
            const earningsList = document.getElementById('earningsList');
            earningsList.innerHTML = '';
            
            currentUser.earnings.forEach(earning => {
                const item = document.createElement('div');
                item.className = 'history-item';
                item.innerHTML = `
                    <div>Ad Watch - ${earning.date}</div>
                    <div>+ ₹${earning.amount.toFixed(2)}</div>
                `;
                earningsList.appendChild(item);
            });
        }
        
        // Logout function
        function logout() {
            currentUser = null;
            document.getElementById('dashboard').style.display = 'none';
            document.querySelector('.form-section').style.display = 'flex';
            document.querySelector('.welcome-section').style.display = 'flex';
            
            // Clear form fields
            document.getElementById('loginEmail').value = '';
            document.getElementById('loginPassword').value = '';
            document.getElementById('signupName').value = '';
            document.getElementById('signupEmail').value = '';
            document.getElementById('signupPassword').value = '';
            
            // Switch to login tab
            switchTab('login');
        }
        
        // Open withdrawal modal
        function openWithdrawalModal(method) {
            currentWithdrawalMethod = method;
            const modal = document.getElementById('withdrawalModal');
            const modalTitle = document.getElementById('modalTitle');
            const additionalFields = document.getElementById('additionalFields');
            
            // Set modal title based on method
            switch(method) {
                case 'amazon':
                    modalTitle.textContent = 'Amazon Voucher Withdrawal';
                    additionalFields.innerHTML = `
                        <input type="email" placeholder="Amazon account email">
                    `;
                    break;
                case 'google':
                    modalTitle.textContent = 'Google Play Code Withdrawal';
                    additionalFields.innerHTML = `
                        <input type="email" placeholder="Google account email">
                    `;
                    break;
                case 'upi':
                    modalTitle.textContent = 'UPI Transfer Withdrawal';
                    additionalFields.innerHTML = `
                        <input type="text" placeholder="UPI ID">
                    `;
                    break;
            }
            
            modal.style.display = 'flex';
        }
        
        // Close modal
        function closeModal() {
            document.getElementById('withdrawalModal').style.display = 'none';
        }
        
        // Process withdrawal
        function processWithdrawal() {
            const amount = parseFloat(document.getElementById('withdrawAmount').value);
            let minAmount = 0;
            
            // Set minimum amount based on method
            switch(currentWithdrawalMethod) {
                case 'amazon':
                    minAmount = 100;
                    break;
                case 'google':
                    minAmount = 50;
                    break;
                case 'upi':
                    minAmount = 20;
                    break;
            }
            
            // Validate amount
            if (isNaN(amount) || amount < minAmount) {
                alert(`Minimum withdrawal amount for ${currentWithdrawalMethod} is ₹${minAmount}`);
                return;
            }
            
            if (amount > currentUser.balance) {
                alert('Insufficient balance');
                return;
            }
            
            // Process withdrawal (in a real app, this would call a backend API)
            currentUser.balance -= amount;
            document.getElementById('userBalance').textContent = currentUser.balance.toFixed(2);
            
            alert(`Withdrawal request of ₹${amount} for ${currentWithdrawalMethod} processed successfully!`);
            closeModal();
        }
        
        // Watch ad function
        function watchAd() {
            if (!currentUser) return;
            
            // Simulate ad watching with a delay
            const btn = document.querySelector('.watch-btn');
            btn.disabled = true;
            btn.textContent = 'Watching ad...';
            
            setTimeout(() => {
                // Add earnings
                const earnings = 0.10;
                currentUser.balance += earnings;
                
                // Add to earnings history
                const now = new Date();
                const time = now.toLocaleTimeString([], { hour: '2-digit', minute: '2-digit' });
                currentUser.earnings.unshift({ date: time, amount: earnings });
                
                // Update UI
                document.getElementById('userBalance').textContent = currentUser.balance.toFixed(2);
                updateEarningsHistory();
                
                btn.disabled = false;
                btn.textContent = 'Watch Ad & Earn ₹0.10';
                
                alert(`You earned ₹${earnings.toFixed(2)} for watching the ad!`);
            }, 3000);
        }
        
        // Initialize with demo account suggestion
        setTimeout(() => {
            alert('Demo Accounts:\nEmail: john@example.com\nPassword: password123\n\nEmail: jane@example.com\nPassword: password123');
        }, 1000);
        
        // Close modal if clicked outside
        window.onclick = function(event) {
            const modal = document.getElementById('withdrawalModal');
            if (event.target == modal) {
                closeModal();
            }
        }
    </script>
</body>
</html>￼Enter                        <h3>UPI Transfer</h3>
                        <p>Minimum withdrawal: ₹20</p>
                    </div>
                </div>
            </div>
            
            <!-- Tasks Section -->
            <div class="content-section" id="tasksSection">
                <h2 class="section-title">Earn by Watching Ads</h2>
                <p style="margin-bottom: 20px; color: #777;">Watch ads and earn ₹0.10 per ad</p>
                
                <div class="ad-container">
                    <div class="ad-placeholder">
                        <div class="ad-icon">
                            <i class="fas fa-ad"></i>
                        </div>
                        <p>Advertisement will be shown here</p>
                    </div>
                    <button class="watch-btn" onclick="watchAd()">Watch Ad & Earn ₹0.10</button>
                </div>
                
                <div class="earnings-history">
                    <h3 class="history-title">Your Earnings History</h3>
                    <div id="earningsList">
                        <div class="history-item">
                            <div>Ad Watch - 10:30 AM</div>
                            <div>+ ₹0.10</div>
                        </div>
                        <div class="history-item">
                            <div>Ad Watch - 09:45 AM</div>
                            <div>+ ₹0.10</div>
                        </div>
                        <div class="history-item">
                            <div>Ad Watch - Yesterday</div>
                            <div>+ ₹0.10</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Withdrawal Modal -->
    <div class="withdrawal-modal" id="withdrawalModal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 id="modalTitle">Withdraw Funds</h2>
                <button class="close-btn" onclick="closeModal()">&times;</button>
            </div>
            <div class="modal-form">
                <input type="number" id="withdrawAmount" placeholder="Enter amount">
                <div id="additionalFields"></div>
                <button type="button" onclick="processWithdrawal()">Withdraw</button>
            </div>
        </div>
    </div>

    <script>
        // Current user data (in a real app, this would come from a server)
        let currentUser = null;
        let currentWithdrawalMethod = '';
        
        // Demo users data
        const users = [
            {
                name: "John Doe",
                email: "john@example.com",
                password: "password123",
                balance: 50.25,
                earnings: [
                    { date: "10:30 AM", amount: 0.10 },
                    { date: "09:45 AM", amount: 0.10 },
                    { date: "Yesterday", amount: 0.10 }
                ]
            },
            {
                name: "Jane Smith",
                email: "jane@example.com",
                password: "password123",
                balance: 125.75,
                earnings: [
                    { date: "11:15 AM", amount: 0.10 },
                    { date: "10:20 AM", amount: 0.10 },
                    { date: "Yesterday", amount: 0.10 }
                ]
            }
        ];
        
        // Switch between login and signup tabs
        function switchTab(tab) {
            document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.form').forEach(f => f.classList.remove('active'));
            
            if (tab === 'login') {
                document.querySelector('.tab:nth-child(1)').classList.add('active');
                document.getElementById('loginForm').classList.add('active');
            } else {
                document.querySelector('.tab:nth-child(2)').classList.add('active');
                document.getElementById('signupForm').classList.add('active');
            }
        }
        
        // Switch between dashboard content
        function switchContent(content) {
            document.querySelectorAll('.nav-tab').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.content-section').forEach(s => s.classList.remove('active'));
            
            if (content === 'withdraw') {
                document.querySelector('.nav-tab:nth-child(1)').classList.add('active');
          document.getElementById('withdrawSection').classList.add('active');
            } else {
                document.querySelector('.nav-tab:nth-child(2)').classList.add('active');
                document.getElementById('tasksSection').classList.add('active');
            }
        }
        
        // Login function
        function login() {
            const email = document.getElementById('loginEmail').value;
            const password = document.getElementById('loginPassword').value;
            
            // Find user in demo data
            const user = users.find(u => u.email === email && u.password === password);
            
            if (user) {
                currentUser = user;
                showDashboard();
            } else {
                alert('Invalid email or password. Try with john@example.com/password123 or jane@example.com/password123');
            }
        }
        
        // Signup function
        function signup() {
            const name = document.getElementById('signupName').value;
            const email = document.getElementById('signupEmail').value;
            const password = document.getElementById('signupPassword').value;
            
            // Check if user already exists
            if (users.some(u => u.email === email)) {
                alert('User with this email already exists');
                return;
            }
            
            // Create new user
            const newUser = {
                name,
                email,
                password,
                balance: 0,
                earnings: []
            };
            
            users.push(newUser);
            currentUser = newUser;
            
            alert('Account created successfully!');
            showDashboard();
        }
        
        // Show dashboard
        function showDashboard() {
            document.querySelector('.form-section').style.display = 'none';
            document.querySelector('.welcome-section').style.display = 'none';
            document.getElementById('dashboard').style.display = 'block';
            
            // Update user info
            document.getElementById('userName').textContent = currentUser.name;
            document.getElementById('userEmail').textContent = currentUser.email;
            document.getElementById('userBalance').textContent = currentUser.balance.toFixed(2);
            
            // Update earnings history
            updateEarningsHistory();
        }
        
        // Update earnings history
        function updateEarningsHistory() {
            const earningsList = document.getElementById('earningsList');
            earningsList.innerHTML = '';
            
            currentUser.earnings.forEach(earning => {
                const item = document.createElement('div');
                item.className = 'history-item';
                item.innerHTML = `
                    <div>Ad Watch - ${earning.date}</div>
                    <div>+ ₹${earning.amount.toFixed(2)}</div>
                `;
                earningsList.appendChild(item);
            });
        }
        
        // Logout function
        function logout() {
            currentUser = null;
            document.getElementById('dashboard').style.display = 'none';
            document.querySelector('.form-section').style.display = 'flex';
            document.querySelector('.welcome-section').style.display = 'flex';
            
            // Clear form fields
            document.getElementById('loginEmail').value = '';
            document.getElementById('loginPassword').value = '';
            document.getElementById('signupName').value = '';
            document.getElementById('signupEmail').value = '';
            document.getElementById('signupPassword').value = '';
            
            // Switch to login tab
            switchTab('login');
        }
        
        // Open withdrawal modal
        function openWithdrawalModal(method) {
            currentWithdrawalMethod = method;
            const modal = document.getElementById('withdrawalModal');
            const modalTitle = document.getElementById('modalTitle');
            const additionalFields = document.getElementById('additionalFields');
            
            // Set modal title based on method
            switch(method) {
