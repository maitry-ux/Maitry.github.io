# Maitry.github.io
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Chemistry Lab</title>
    <style>
        :root {
            --primary: #6a11cb;
            --secondary: #2575fc;
            --accent: #00ff88;
            --dark: #121f2b;
            --light: #f8f9fa;
            --danger: #ff3860;
            --warning: #ffdd57;
            --success: #00d1b2;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, var(--dark), #1a2a3a);
            color: var(--light);
            min-height: 100vh;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        /* Login Page Styles */
        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(135deg, rgba(106, 17, 203, 0.8), rgba(37, 117, 252, 0.8));
            background-size: cover;
        }
        
        .login-box {
            background: rgba(20, 30, 40, 0.9);
            padding: 40px;
            border-radius: 15px;
            width: 100%;
            max-width: 500px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            transform: translateY(0);
            transition: transform 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .login-box:hover {
            transform: translateY(-5px);
        }
        
        .login-box h1 {
            text-align: center;
            margin-bottom: 30px;
            color: var(--accent);
            font-size: 2.5rem;
            text-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: var(--light);
            font-weight: 500;
        }
        
        .form-group input, .form-group select {
            width: 100%;
            padding: 12px 15px;
            border-radius: 8px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            background: rgba(0, 0, 0, 0.3);
            color: var(--light);
            font-size: 16px;
            transition: all 0.3s;
        }
        
        .form-group input:focus, .form-group select:focus {
            outline: none;
            border-color: var(--accent);
            box-shadow: 0 0 0 3px rgba(0, 255, 136, 0.2);
        }
        
        .btn {
            display: inline-block;
            padding: 12px 24px;
            background: linear-gradient(to right, var(--primary), var(--secondary));
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            text-align: center;
            text-decoration: none;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(106, 17, 203, 0.4);
        }
        
        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(106, 17, 203, 0.6);
        }
        
        .btn:active {
            transform: translateY(0);
        }
        
        .btn-block {
            display: block;
            width: 100%;
        }
        
        /* Main App Styles */
        .app-container {
            display: none;
        }
        
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 0;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            margin-bottom: 30px;
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--accent);
            display: flex;
            align-items: center;
        }
        
        .logo i {
            margin-right: 10px;
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .user-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: linear-gradient(to right, var(--primary), var(--secondary));
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: white;
        }
        
        .user-details {
            text-align: right;
        }
        
        .user-name {
            font-weight: 600;
        }
        
        .user-class {
            font-size: 0.8rem;
            opacity: 0.8;
        }
        
        .stats {
            display: flex;
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .stat-card {
            flex: 1;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            padding: 20px;
            display: flex;
            align-items: center;
            gap: 15px;
            transition: transform 0.3s ease;
            border-left: 4px solid var(--accent);
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.08);
        }
        
        .stat-icon {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: rgba(0, 255, 136, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            color: var(--accent);
        }
        
        .stat-info h3 {
            font-size: 1.2rem;
            margin-bottom: 5px;
        }
        
        .stat-info p {
            font-size: 0.9rem;
            opacity: 0.8;
        }
        
        .tabs {
            display: flex;
            margin-bottom: 20px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .tab {
            padding: 12px 20px;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            transition: all 0.3s;
            font-weight: 600;
        }
        
        .tab:hover {
            background: rgba(255, 255, 255, 0.05);
        }
        
        .tab.active {
            border-bottom-color: var(--accent);
            color: var(--accent);
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* Experiments Tab */
        .experiment-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 20px;
        }
        
        .experiment-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            overflow: hidden;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .experiment-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.3);
            border-color: rgba(0, 255, 136, 0.3);
        }
        
        .experiment-card.completed {
            border-left: 4px solid var(--accent);
        }
        
        .experiment-header {
            padding: 15px;
            background: rgba(0, 0, 0, 0.2);
            display: flex;
            justify-content: space-between;
            align-items: center;
            cursor: pointer;
        }
        
        .experiment-title {
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .experiment-number {
            background: var(--accent);
            color: var(--dark);
            width: 25px;
            height: 25px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.8rem;
            font-weight: bold;
        }
        
        .experiment-status {
            font-size: 0.8rem;
            padding: 3px 8px;
            border-radius: 20px;
            background: rgba(0, 255, 136, 0.2);
            color: var(--accent);
        }
        
        .experiment-details {
            padding: 0 15px;
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.3s ease, padding 0.3s ease;
        }
        
        .experiment-card.active .experiment-details {
            padding: 15px;
            max-height: 1000px;
        }
        
        .experiment-objective {
            margin-bottom: 10px;
            font-size: 0.9rem;
            opacity: 0.9;
        }
        
        /* Experiment Choices */
        .experiment-choices {
            margin-top: 15px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 10px;
        }
        
        .choice-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 8px;
            padding: 15px;
            cursor: pointer;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .choice-card:hover {
            background: rgba(0, 255, 136, 0.1);
            border-color: var(--accent);
            transform: translateY(-3px);
        }
        
        .choice-card.selected {
            background: rgba(0, 255, 136, 0.2);
            border-color: var(--accent);
            box-shadow: 0 0 0 2px var(--accent);
        }
        
        .choice-title {
            font-weight: 600;
            margin-bottom: 8px;
            color: var(--accent);
        }
        
        .choice-desc {
            font-size: 0.9rem;
            opacity: 0.9;
        }
        
        .chemical-used {
            font-size: 0.8rem;
            color: var(--accent);
            margin-top: 5px;
        }
        
        /* Procedure Display */
        .procedure-display {
            margin-top: 20px;
            padding: 15px;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 8px;
            display: none;
        }
        
        .procedure-step {
            margin-bottom: 10px;
            display: none;
        }
        
        .procedure-step.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        .step-actions {
            display: flex;
            justify-content: space-between;
            margin-top: 15px;
        }
        
        /* Experiment Visual */
        .experiment-visual {
            height: 150px;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 5px;
            display: flex;
            justify-content: center;
            align-items: center;
            position: relative;
            overflow: hidden;
            margin: 15px 0;
        }
        
        .chemical {
            position: absolute;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-weight: bold;
            transition: all 0.5s;
        }
        
        .beaker {
            width: 100px;
            height: 120px;
            border: 3px solid rgba(255, 255, 255, 0.5);
            border-bottom: 15px solid rgba(255, 255, 255, 0.5);
            border-radius: 0 0 20px 20px;
            position: relative;
            background: linear-gradient(to bottom, rgba(200, 200, 255, 0.1), rgba(100, 100, 255, 0.05));
        }
        
        .liquid {
            position: absolute;
            bottom: 0;
            width: 100%;
            border-radius: 0 0 15px 15px;
            transition: all 1s;
        }
        
        .flame {
            position: absolute;
            width: 30px;
            height: 50px;
            background: linear-gradient(to top, orange, yellow);
            border-radius: 50% 50% 20% 20%;
            filter: blur(5px);
            bottom: -15px;
            opacity: 0;
        }
        
        .bubbles {
            position: absolute;
            width: 100%;
            height: 100%;
        }
        
        .bubble {
            position: absolute;
            background-color: rgba(255, 255, 255, 0.6);
            border-radius: 50%;
            animation: bubbleRise linear infinite;
        }
        
        @keyframes bubbleRise {
            0% { transform: translateY(0); opacity: 0; }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { transform: translateY(-100px); opacity: 0; }
        }
        
        /* Result Display */
        .result-display {
            margin-top: 15px;
            padding: 15px;
            background: rgba(0, 50, 0, 0.2);
            border-radius: 5px;
            border-left: 4px solid var(--accent);
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        /* Inventory Tab */
        .inventory-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
            gap: 15px;
        }
        
        .chemical-item {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 8px;
            padding: 15px;
            text-align: center;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .chemical-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }
        
        .chemical-icon {
            width: 60px;
            height: 60px;
            margin: 0 auto 10px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            font-weight: bold;
            background: rgba(0, 255, 136, 0.1);
            color: var(--accent);
        }
        
        .chemical-name {
            font-weight: 600;
            font-size: 0.9rem;
            margin-bottom: 5px;
        }
        
        .chemical-quantity {
            font-size: 0.8rem;
            opacity: 0.8;
        }
        
        /* Achievements Tab */
        .achievements-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
        }
        
        .achievement-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 10px;
            padding: 20px;
            display: flex;
            gap: 15px;
            align-items: center;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .achievement-card.locked {
            opacity: 0.6;
            filter: grayscale(0.8);
        }
        
        .achievement-card:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.08);
        }
        
        .achievement-icon {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: rgba(106, 17, 203, 0.2);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            color: var(--primary);
            flex-shrink: 0;
        }
        
        .achievement-info h3 {
            font-size: 1rem;
            margin-bottom: 5px;
        }
        
        .achievement-info p {
            font-size: 0.8rem;
            opacity: 0.8;
        }
        
        /* Console Tab */
        .console-container {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 10px;
            padding: 20px;
            height: 400px;
            overflow-y: auto;
            font-family: 'Courier New', monospace;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .console-line {
            margin-bottom: 10px;
            line-height: 1.5;
            animation: fadeIn 0.3s ease;
        }
        
        .console-line:last-child {
            margin-bottom: 0;
        }
        
        .console-input {
            display: flex;
            margin-top: 15px;
        }
        
        .console-input input {
            flex: 1;
            padding: 10px 15px;
            background: rgba(0, 0, 0, 0.5);
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 5px 0 0 5px;
            color: white;
            font-family: 'Courier New', monospace;
        }
        
        .console-input button {
            padding: 10px 15px;
            background: var(--accent);
            color: var(--dark);
            border: none;
            border-radius: 0 5px 5px 0;
            font-weight: bold;
            cursor: pointer;
        }
        
        /* Animations */
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        
        .pulse {
            animation: pulse 1.5s infinite;
        }
        
        /* Rating Stars */
        .rating {
            display: flex;
            gap: 5px;
        }
        
        .star {
            color: #ccc;
            font-size: 1.2rem;
        }
        
        .star.filled {
            color: gold;
        }
        
        /* Celebration Effects */
        .confetti {
            position: fixed;
            width: 10px;
            height: 10px;
            background-color: #f00;
            opacity: 0;
            z-index: 1000;
            animation: confettiFall 5s ease-in-out;
        }
        
        @keyframes confettiFall {
            0% { transform: translateY(-100px) rotate(0deg); opacity: 1; }
            100% { transform: translateY(100vh) rotate(360deg); opacity: 0; }
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .stats {
                flex-direction: column;
            }
            
            .experiment-list {
                grid-template-columns: 1fr;
            }
            
            .login-box {
                padding: 30px 20px;
                margin: 20px;
            }
            
            .experiment-choices {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Login Page -->
    <div class="login-container" id="login-page">
        <div class="login-box">
            <h1>🧪 Chemistry Lab Simulator</h1>
            <div class="form-group">
                <label for="student-name">Your Name</label>
                <input type="text" id="student-name" placeholder="Enter your name">
            </div>
            <div class="form-group">
                <label for="student-class">Class/Grade</label>
                <input type="text" id="student-class" placeholder="Enter your class/grade">
            </div>
            <div class="form-group">
                <label for="avatar-color">Choose Avatar Color</label>
                <select id="avatar-color">
                    <option value="#6a11cb">Purple</option>
                    <option value="#2575fc">Blue</option>
                    <option value="#00ff88">Green</option>
                    <option value="#ff3860">Red</option>
                    <option value="#ffdd57">Yellow</option>
                </select>
            </div>
            <button class="btn btn-block" id="login-btn">Enter Lab</button>
        </div>
    </div>
    
    <!-- Main App -->
    <div class="app-container" id="app">
        <div class="container">
            <header>
                <div class="logo">
                    <i class="fas fa-flask"></i> ChemLab Pro
                </div>
                <div class="user-info">
                    <div class="user-details">
                        <div class="user-name" id="display-name">User</div>
                        <div class="user-class" id="display-class">Class 10</div>
                    </div>
                    <div class="user-avatar" id="user-avatar">U</div>
                </div>
            </header>
            
            <div class="stats">
                <div class="stat-card">
                    <div class="stat-icon">
                        <i class="fas fa-star"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="xp-display">0 XP</h3>
                        <p>Experience Points</p>
                    </div>
                </div>
                <div class="stat-card">
                    <div class="stat-icon">
                        <i class="fas fa-trophy"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="rating-display">Novice</h3>
                        <p>Current Rating</p>
                    </div>
                </div>
                <div class="stat-card">
                    <div class="stat-icon">
                        <i class="fas fa-check-circle"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="completed-display">0</h3>
                        <p>Experiments Completed</p>
                    </div>
                </div>
            </div>
            
            <div class="tabs">
                <div class="tab active" data-tab="experiments">Experiments</div>
                <div class="tab" data-tab="inventory">Inventory</div>
                <div class="tab" data-tab="achievements">Achievements</div>
                <div class="tab" data-tab="console">Lab Console</div>
            </div>
            
            <div class="tab-content active" id="experiments-tab">
                <h3>🔬 Available Experiments:</h3>
                <div class="experiment-list" id="experiment-list">
                    <!-- Experiments will be added here dynamically -->
                </div>
            </div>
            
            <div class="tab-content" id="inventory-tab">
                <h3>🧪 Chemical Inventory:</h3>
                <div class="inventory-grid" id="inventory-grid">
                    <!-- Inventory items will be added here dynamically -->
                </div>
            </div>
            
            <div class="tab-content" id="achievements-tab">
                <h3>🏆 Achievements:</h3>
                <div class="achievements-list" id="achievements-list">
                    <!-- Achievements will be added here dynamically -->
                </div>
            </div>
            
            <div class="tab-content" id="console-tab">
                <h3>📟 Lab Console:</h3>
                <div class="console-container" id="console-output">
                    <div class="console-line">> Welcome to Chemistry Lab Simulator v2.0</div>
                    <div class="console-line">> System initialized...</div>
                    <div class="console-line">> Type 'help' for available commands</div>
                </div>
                <div class="console-input">
                    <input type="text" id="console-input" placeholder="Enter command...">
                    <button id="console-submit">Execute</button>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Audio Elements -->
    <audio id="success-sound" src="https://assets.mixkit.co/sfx/preview/mixkit-achievement-bell-600.mp3" preload="auto"></audio>
    <audio id="click-sound" src="https://assets.mixkit.co/sfx/preview/mixkit-select-click-1109.mp3" preload="auto"></audio>
    <audio id="bubble-sound" src="https://assets.mixkit.co/sfx/preview/mixkit-bubbles-in-water-1171.mp3" preload="auto"></audio>
    <audio id="flame-sound" src="https://assets.mixkit.co/sfx/preview/mixkit-fire-large-1740.mp3" preload="auto"></audio>
    <audio id="pour-sound" src="https://assets.mixkit.co/sfx/preview/mixkit-water-pouring-into-glass-1180.mp3" preload="auto"></audio>
    <audio id="beep-sound" src="https://assets.mixkit.co/sfx/preview/mixkit-retro-arcade-game-beep-209.mp3" preload="auto"></audio>
    
    <!-- Font Awesome for icons -->
    <script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
    
    <script>
        // Game State
        const gameState = {
            studentName: '',
            studentClass: '',
            avatarColor: '#6a11cb',
            xp: 0,
            completedExperiments: [],
            unlockedAchievements: [],
            inventory: {
                'NaOH': 500,
                'HCl': 500,
                'H₂SO₄': 300,
                'Phenolphthalein': 50,
                'Na₂SO₄': 200,
                'CuSO₄': 150,
                'Vegetable Oil': 200,
                'Salt': 300,
                'pH Paper': 20,
                'pH Meter': 1
            },
            rating: 'Novice',
            consoleHistory: [],
            historyIndex: -1
        };
        
        // Experiments Data with Multiple Methods
        const experiments = [
            {
                id: 1,
                title: 'Acid-Base Titration',
                objective: 'Determine the concentration of an unknown acid solution.',
                methods: [
                    {
                        id: 'standard',
                        name: 'Standard Titration',
                        description: 'Use a burette and indicator for precise measurement',
                        chemicals: ['NaOH', 'HCl', 'Phenolphthalein'],
                        steps: [
                            'Fill the burette with 0.1M NaOH solution',
                            'Measure exactly 25ml of unknown HCl solution into an Erlenmeyer flask',
                            'Add 2-3 drops of phenolphthalein indicator to the flask',
                            'Slowly titrate the NaOH solution into the HCl while swirling',
                            'Stop when the solution turns pale pink and remains for 30 seconds',
                            'Record the volume of NaOH used to reach the endpoint'
                        ],
                        visual: 'burette',
                        xpRange: [80, 120]
                    },
                    {
                        id: 'quick',
                        name: 'Quick Test',
                        description: 'Approximate concentration using pH paper',
                        chemicals: ['pH Paper', 'HCl'],
                        steps: [
                            'Dip a strip of pH paper into the unknown acid solution',
                            'Compare the color change to the pH scale',
                            'Estimate the concentration based on the pH value',
                            'Record your approximate concentration value'
                        ],
                        visual: 'ph_paper',
                        xpRange: [30, 50]
                    },
                    {
                        id: 'advanced',
                        name: 'Advanced pH Meter',
                        description: 'Use digital pH meter for accurate measurement',
                        chemicals: ['pH Meter', 'HCl'],
                        steps: [
                            'Calibrate the pH meter with standard buffer solutions',
                            'Rinse the electrode with distilled water',
                            'Immerse the electrode in the unknown acid solution',
                            'Wait for the reading to stabilize and record the pH',
                            'Calculate the concentration from the pH value'
                        ],
                        visual: 'ph_meter',
                        xpRange: [60, 90]
                    }
                ]
            },
            {
                id: 2,
                title: 'Electrolysis of Water',
                objective: 'Decompose water into hydrogen and oxygen gas.',
                methods: [
                    {
                        id: 'basic',
                        name: 'Basic Electrolysis',
                        description: 'Simple setup with battery and electrodes',
                        chemicals: ['H₂O', 'Na₂SO₄'],
                        steps: [
                            'Fill the electrolysis apparatus with distilled water',
                            'Add a small amount of Na₂SO₄ as electrolyte',
                            'Connect graphite electrodes to a 6V battery',
                            'Observe gas bubbles forming at both electrodes',
                            'Test the gases with a glowing splint (oxygen) and flame (hydrogen)'
                        ],
                        visual: 'electrolysis',
                        xpRange: [50, 80]
                    },
                    {
                        id: 'quantitative',
                        name: 'Quantitative Analysis',
                        description: 'Measure gas volumes to verify stoichiometry',
                        chemicals: ['H₂O', 'H₂SO₄'],
                        steps: [
                            'Set up Hoffman apparatus with 0.1M H₂SO₄ solution',
                            'Connect to a DC power supply at 12V',
                            'Allow electrolysis to proceed for 10 minutes',
                            'Measure the volumes of gases collected in each tube',
                            'Calculate the ratio of hydrogen to oxygen produced'
                        ],
                        visual: 'hoffman',
                        xpRange: [90, 130]
                    }
                ]
            },
            {
                id: 3,
                title: 'Flame Tests',
                objective: 'Identify metal ions based on flame color.',
                methods: [
                    {
                        id: 'traditional',
                        name: 'Traditional Method',
                        description: 'Use nichrome wire and Bunsen burner',
                        chemicals: ['HCl', 'NaCl', 'CuSO₄'],
                        steps: [
                            'Clean nichrome wire by dipping in HCl and heating',
                            'Dip the wire into the unknown salt solution',
                            'Hold the wire in the hottest part of the Bunsen flame',
                            'Observe and record the characteristic flame color',
                            'Compare to known samples to identify the metal ion'
                        ],
                        visual: 'flame_test',
                        xpRange: [40, 70]
                    },
                    {
                        id: 'spectroscope',
                        name: 'Spectroscope Analysis',
                        description: 'Use spectroscope for precise wavelength measurement',
                        chemicals: ['HCl', 'Various Salts'],
                        steps: [
                            'Prepare samples of various metal salts',
                            'Perform flame test with each sample',
                            'View the flame through a spectroscope',
                            'Record the emission line wavelengths',
                            'Identify the metal ions based on their spectra'
                        ],
                        visual: 'spectroscope',
                        xpRange: [80, 110]
                    }
                ]
            },
            {
                id: 4,
                title: 'Making Soap',
                objective: 'Demonstrate saponification by making soap.',
                methods: [
                    {
                        id: 'cold',
                        name: 'Cold Process',
                        description: 'Traditional soap making at room temperature',
                        chemicals: ['Vegetable Oil', 'NaOH'],
                        steps: [
                            'Measure 100ml of vegetable oil into a beaker',
                            'Slowly add NaOH solution while stirring constantly',
                            'Continue stirring until trace (mixture thickens)',
                            'Pour into molds and allow to cure for 4-6 weeks',
                            'Test the soap for pH and cleaning ability'
                        ],
                        visual: 'soap',
                        xpRange: [60, 90]
                    },
                    {
                        id: 'hot',
                        name: 'Hot Process',
                        description: 'Faster method using heat to accelerate saponification',
                        chemicals: ['Vegetable Oil', 'NaOH'],
                        steps: [
                            'Heat vegetable oil to 50°C in a double boiler',
                            'Slowly add warmed NaOH solution while stirring',
                            'Continue heating and stirring until saponification is complete',
                            'Add fragrance or colorants if desired',
                            'Pour into molds and allow to cool for 24 hours'
                        ],
                        visual: 'soap_hot',
                        xpRange: [70, 100]
                    }
                ]
            },
            {
                id: 5,
                title: 'Crystal Growing',
                objective: 'Grow crystals from a supersaturated solution.',
                methods: [
                    {
                        id: 'slow',
                        name: 'Slow Evaporation',
                        description: 'Grow large crystals over several days',
                        chemicals: ['CuSO₄', 'H₂O'],
                        steps: [
                            'Dissolve CuSO₄ in hot water until saturated',
                            'Filter the solution into a clean beaker',
                            'Suspend a seed crystal in the solution',
                            'Cover with filter paper to allow slow evaporation',
                            'Observe crystal growth over 3-5 days'
                        ],
                        visual: 'crystals_slow',
                        xpRange: [50, 80]
                    },
                    {
                        id: 'fast',
                        name: 'Fast Cooling',
                        description: 'Grow smaller crystals quickly',
                        chemicals: ['CuSO₄', 'H₂O'],
                        steps: [
                            'Prepare a saturated CuSO₄ solution at 80°C',
                            'Pour into a shallow dish to maximize surface area',
                            'Allow to cool rapidly at room temperature',
                            'Observe crystal formation within hours',
                            'Examine crystal shapes under magnification'
                        ],
                        visual: 'crystals_fast',
                        xpRange: [40, 60]
                    }
                ]
            }
        ];
        
        // Achievements Data
        const achievements = [
            {
                id: 'first-experiment',
                title: 'First Experiment',
                description: 'Complete your first chemistry experiment',
                icon: 'fas fa-flask',
                xpReward: 50
            },
            {
                id: 'junior-chemist',
                title: 'Junior Chemist',
                description: 'Complete 3 experiments',
                icon: 'fas fa-atom',
                xpReward: 100
            },
            {
                id: 'lab-expert',
                title: 'Lab Expert',
                description: 'Complete all basic experiments',
                icon: 'fas fa-microscope',
                xpReward: 200
            },
            {
                id: 'perfect-score',
                title: 'Perfect Score',
                description: 'Get maximum XP from an experiment',
                icon: 'fas fa-star',
                xpReward: 50
            },
            {
                id: 'quick-learner',
                title: 'Quick Learner',
                description: 'Complete 2 experiments in one session',
                icon: 'fas fa-bolt',
                xpReward: 75
            },
            {
                id: 'inventory-master',
                title: 'Inventory Master',
                description: 'Use all available chemicals at least once',
                icon: 'fas fa-vial',
                xpReward: 150
            }
        ];
        
        // DOM Elements
        const loginPage = document.getElementById('login-page');
        const appContainer = document.getElementById('app');
        const loginBtn = document.getElementById('login-btn');
        const studentNameInput = document.getElementById('student-name');
        const studentClassInput = document.getElementById('student-class');
        const avatarColorInput = document.getElementById('avatar-color');
        const displayName = document.getElementById('display-name');
        const displayClass = document.getElementById('display-class');
        const userAvatar = document.getElementById('user-avatar');
        const xpDisplay = document.getElementById('xp-display');
        const ratingDisplay = document.getElementById('rating-display');
        const completedDisplay = document.getElementById('completed-display');
        const experimentList = document.getElementById('experiment-list');
        const inventoryGrid = document.getElementById('inventory-grid');
        const achievementsList = document.getElementById('achievements-list');
        const consoleOutput = document.getElementById('console-output');
        const consoleInput = document.getElementById('console-input');
        const consoleSubmit = document.getElementById('console-submit');
        const tabs = document.querySelectorAll('.tab');
        const tabContents = document.querySelectorAll('.tab-content');
        
        // Audio Elements
        const successSound = document.getElementById('success-sound');
        const clickSound = document.getElementById('click-sound');
        const bubbleSound = document.getElementById('bubble-sound');
        const flameSound = document.getElementById('flame-sound');
        const pourSound = document.getElementById('pour-sound');
        const beepSound = document.getElementById('beep-sound');
        
        // Initialize the app
        function init() {
            // Check for saved data
            loadSavedData();
            
            // Set up event listeners
            loginBtn.addEventListener('click', handleLogin);
            consoleInput.addEventListener('keydown', handleConsoleInput);
            consoleSubmit.addEventListener('click', executeConsoleCommand);
            
            // Tab switching
            tabs.forEach(tab => {
                tab.addEventListener('click', () => {
                    switchTab(tab.dataset.tab);
                    playSound(clickSound);
                });
            });
        }
        // Handle login
        function handleLogin() {
            const name = studentNameInput.value.trim();
            const className = studentClassInput.value.trim();
            
            if (name === '' || className === '') {
                alert('Please enter your name and class');
                return;
            }
            
            gameState.studentName = name;
            gameState.studentClass = className;
            gameState.avatarColor = avatarColorInput.value;
            
            // Update UI
            displayName.textContent = name;
            displayClass.textContent = className;
            userAvatar.textContent = name.charAt(0).toUpperCase();
            userAvatar.style.background = `linear-gradient(to right, ${gameState.avatarColor}, ${lightenColor(gameState.avatarColor, 20)})`;
            
            // Switch to app view
            loginPage.style.display = 'none';
            appContainer.style.display = 'block';
            
            // Initialize app components
            updateXP();
            updateRating();
            updateCompletedExperiments();
            renderExperiments();
            renderInventory();
            renderAchievements();
            
            // Play success sound
            playSound(successSound);
            
            // Add welcome message
            addToConsole(`> Welcome, ${name}! Ready to start experimenting?`);
            addToConsole(`> Type 'help' for available commands`);
        }
        
        // Load saved data
        function loadSavedData() {
            const savedData = localStorage.getItem(`chemLab_${studentNameInput.value.trim()}_${studentClassInput.value.trim()}`);
            if (savedData) {
                const parsedData = JSON.parse(savedData);
                Object.assign(gameState, parsedData);
                
                // Show welcome back message
                addToConsole(`> Welcome back, ${parsedData.studentName}! Loading your saved progress...`);
                
                // Update UI if data exists
                if (parsedData.studentName) {
                    studentNameInput.value = parsedData.studentName;
                    studentClassInput.value = parsedData.studentClass;
                    avatarColorInput.value = parsedData.avatarColor || '#6a11cb';
                }
            }
        }
        
        // Save game state
        function saveGameState() {
            localStorage.setItem(
                `chemLab_${gameState.studentName}_${gameState.studentClass}`,
                JSON.stringify(gameState)
            );
        }
        
        // Update XP display
        function updateXP() {
            xpDisplay.textContent = `${gameState.xp} XP`;
        }
        
        // Update rating display
        function updateRating() {
            let rating = 'Novice';
            let starCount = 1;
            
            if (gameState.xp >= 500) {
                rating = 'Advanced';
                starCount = 3;
            } else if (gameState.xp >= 200) {
                rating = 'Intermediate';
                starCount = 2;
            } else if (gameState.xp >= 50) {
                rating = 'Beginner';
                starCount = 1;
            }
            
            if (gameState.xp >= 1000) {
                rating = 'Expert';
                starCount = 5;
            } else if (gameState.xp >= 750) {
                rating = 'Proficient';
                starCount = 4;
            }
            
            gameState.rating = rating;
            ratingDisplay.textContent = rating;
            
            // Update stars in rating display
            const statCard = ratingDisplay.closest('.stat-info');
            let starsHtml = '<div class="rating">';
            for (let i = 0; i < 5; i++) {
                starsHtml += `<span class="star ${i < starCount ? 'filled' : ''}">★</span>`;
            }
            starsHtml += '</div>';
            
            // Add stars if not already there
            if (!statCard.querySelector('.rating')) {
                statCard.querySelector('p').insertAdjacentHTML('afterend', starsHtml);
            } else {
                statCard.querySelector('.rating').innerHTML = starsHtml;
            }
        }
        
        // Update completed experiments display
        function updateCompletedExperiments() {
            completedDisplay.textContent = gameState.completedExperiments.length;
        }
        
        // Render experiments
        function renderExperiments() {
            experimentList.innerHTML = '';
            
            experiments.forEach(exp => {
                const isCompleted = gameState.completedExperiments.includes(exp.id);
                
                const experimentCard = document.createElement('div');
                experimentCard.className = `experiment-card ${isCompleted ? 'completed' : ''}`;
                experimentCard.innerHTML = `
                    <div class="experiment-header">
                        <div class="experiment-title">
                            <span class="experiment-number">${exp.id}</span>
                            ${exp.title}
                        </div>
                        <div class="experiment-status">${isCompleted ? 'Completed' : 'New'}</div>
                    </div>
                    <div class="experiment-details">
                        <p class="experiment-objective"><strong>Objective:</strong> ${exp.objective}</p>
                        <div class="experiment-choices" id="exp-${exp.id}-choices"></div>
                        <div class="procedure-display" id="exp-${exp.id}-procedure"></div>
                        <div class="experiment-visual" id="exp-${exp.id}-visual"></div>
                        <div class="result-display" id="exp-${exp.id}-result"></div>
                    </div>
                `;
                
                // Render methods for this experiment
                const choicesContainer = experimentCard.querySelector(`#exp-${exp.id}-choices`);
                exp.methods.forEach(method => {
                    const choiceCard = document.createElement('div');
                    choiceCard.className = 'choice-card';
                    choiceCard.dataset.choice = method.id;
                    choiceCard.dataset.expId = exp.id;
                    choiceCard.innerHTML = `
                        <div class="choice-title">${method.name}</div>
                        <div class="choice-desc">${method.description}</div>
                        <div class="chemical-used">Uses: ${method.chemicals.join(', ')}</div>
                    `;
                    
                    choiceCard.addEventListener('click', () => selectExperimentMethod(exp.id, method.id));
                    choicesContainer.appendChild(choiceCard);
                });
                
                experimentList.appendChild(experimentCard);
                
                // Add click handler for header
                experimentCard.querySelector('.experiment-header').addEventListener('click', () => {
                    experimentCard.classList.toggle('active');
                    playSound(clickSound);
                });
            });
        }
        // Select experiment method
        function selectExperimentMethod(expId, methodId) {
            const exp = experiments.find(e => e.id === expId);
            const method = exp.methods.find(m => m.id === methodId);
            
            // Clear previous selections
            document.querySelectorAll(`#exp-${expId}-choices .choice-card`).forEach(card => {
                card.classList.remove('selected');
            });
            
            // Select current method
            const selectedCard = document.querySelector(`#exp-${expId}-choices .choice-card[data-choice="${methodId}"]`);
            selectedCard.classList.add('selected');
            
            // Show procedure
            const procedureDisplay = document.getElementById(`exp-${expId}-procedure`);
            procedureDisplay.style.display = 'block';
            procedureDisplay.innerHTML = `
                <h4>${method.name} Procedure:</h4>
                <ol class="experiment-steps" id="exp-${expId}-steps"></ol>
                <div class="step-actions">
                    <button class="btn btn-sm" onclick="startExperimentProcedure(${expId})">Start Procedure</button>
                </div>
            `;
            
            // Add steps
            const stepsList = document.getElementById(`exp-${expId}-steps`);
            method.steps.forEach((step, index) => {
                const li = document.createElement('li');
                li.textContent = step;
                li.style.display = 'none';
                li.id = `exp-${expId}-step-${index}`;
                stepsList.appendChild(li);
            });
            
            // Render visual
            renderExperimentVisual(expId, method.visual);
            
            playSound(clickSound);
        }
        
        // Render experiment visual
        function renderExperimentVisual(expId, visualType) {
            const visualContainer = document.getElementById(`exp-${expId}-visual`);
            visualContainer.innerHTML = '';
            
            switch(visualType) {
                case 'burette':
                    visualContainer.innerHTML = `
                        <div class="beaker">
                            <div class="liquid" id="acid-solution" style="height: 80%; background-color: rgba(255, 100, 100, 0.5);"></div>
                        </div>
                        <div style="position: absolute; right: 20px; bottom: 0; width: 30px; height: 200px; background: linear-gradient(to right, #888, #aaa, #888); border-radius: 5px;"></div>
                    `;
                    break;
                    
                case 'ph_paper':
                    visualContainer.innerHTML = `
                        <div style="display: flex; flex-direction: column; align-items: center;">
                            <div style="width: 100px; height: 20px; background: linear-gradient(to right, red, orange, yellow, green, blue, indigo, violet); margin-bottom: 10px;"></div>
                            <div style="width: 50px; height: 100px; background: rgba(255, 100, 100, 0.5);"></div>
                        </div>
                    `;
                    break;
                    
                case 'ph_meter':
                    visualContainer.innerHTML = `
                        <div style="display: flex; flex-direction: column; align-items: center;">
                            <div style="width: 80px; height: 120px; background: #333; border-radius: 5px; display: flex; justify-content: center; align-items: center; color: var(--accent); font-weight: bold;">
                                pH: 7.0
                            </div>
                            <div style="width: 5px; height: 50px; background: #555; margin-top: 10px;"></div>
                        </div>
                    `;
                    break;
                    
                case 'electrolysis':
                    visualContainer.innerHTML = `
                        <div class="beaker">
                            <div class="liquid" style="height: 90%; background-color: rgba(100, 100, 255, 0.3);"></div>
                            <div class="bubbles" id="electrolysis-bubbles"></div>
                        </div>
                    `;
                    break;
                    
                case 'hoffman':
                    visualContainer.innerHTML = `
                        <div style="position: relative; width: 200px; height: 100%; display: flex; justify-content: center;">
                            <div style="width: 80px; height: 150px; background: rgba(100, 100, 255, 0.3); position: relative;">
                                <div style="position: absolute; top: 0; width: 100%; height: 50%; background: rgba(255, 255, 255, 0.3);"></div>
                                <div style="position: absolute; top: 50%; width: 100%; height: 50%; background: rgba(255, 255, 255, 0.6);"></div>
                            </div>
                        </div>
                    `;
                    break;
                    
                case 'flame_test':
                    visualContainer.innerHTML = `
                        <div class="flame" id="bunsen-flame"></div>
                        <div style="position: relative; height: 100%; display: flex; justify-content: center;">
                            <div style="width: 30px; height: 80px; background: linear-gradient(to right, #444, #888, #444); border-radius: 5px;"></div>
                        </div>
                    `;
                    break;
                    
                case 'spectroscope':
                    visualContainer.innerHTML = `
                        <div style="display: flex; flex-direction: column; align-items: center;">
                            <div style="width: 100px; height: 20px; background: linear-gradient(to right, red, orange, yellow, green, blue, indigo, violet); margin-bottom: 10px;"></div>
                            <div style="width: 80px; height: 80px; background: #333; border-radius: 5px; position: relative;">
                                <div style="position: absolute; top: 10px; left: 10px; width: 60px; height: 60px; background: #111; border-radius: 3px;"></div>
                            </div>
                        </div>
                    `;
                    break;
                    
                case 'soap':
                case 'soap_hot':
                    visualContainer.innerHTML = `
                        <div class="beaker">
                            <div class="liquid" style="height: 60%; background-color: rgba(200, 150, 100, 0.6);"></div>
                        </div>
                    `;
                    break;
                    
                case 'crystals_slow':
                case 'crystals_fast':
                    visualContainer.innerHTML = `
                        <div class="beaker">
                            <div class="liquid" style="height: 70%; background-color: rgba(100, 200, 255, 0.5);"></div>
                            <div id="crystal-seed" style="position: absolute; bottom: 30px; left: 50%; transform: translateX(-50%); width: 10px; height: 10px; background-color: rgba(255, 255, 255, 0.8); display: none;"></div>
                        </div>
                    `;
                    break;
            }
        }
        
        // Start experiment procedure
        function startExperimentProcedure(expId) {
            const exp = experiments.find(e => e.id === expId);
            const selectedCard = document.querySelector(`#exp-${expId}-choices .choice-card.selected`);
            if (!selectedCard) return;
            
            const methodId = selectedCard.dataset.choice;
            const method = exp.methods.find(m => m.id === methodId);
            
            // Check if already completed
            const isFirstTime = !gameState.completedExperiments.includes(expId);
            
            // Clear previous result
            const resultDisplay = document.getElementById(`exp-${expId}-result`);
            resultDisplay.style.display = 'none';
            resultDisplay.innerHTML = '';
            
            // Start procedure
            let currentStep = 0;
            const totalSteps = method.steps.length;
            
            addToConsole(`> Starting experiment #${expId}: ${exp.title} (${method.name})`);
            
            function showNextStep() {
                // Hide all steps
                for (let i = 0; i < totalSteps; i++) {
                    document.getElementById(`exp-${expId}-step-${i}`).style.display = 'none';
                }
                
                // Show current step
                document.getElementById(`exp-${expId}-step-${currentStep}`).style.display = 'block';
                
                // Play sound for this step
                playSound(beepSound);
                
                // Update visual for this step
                updateExperimentVisual(expId, method.visual, currentStep);
                
                currentStep++;
                
                if (currentStep < totalSteps) {
                    setTimeout(showNextStep, 3000);
                } else {
                    // Experiment complete
                    completeExperiment(expId, method);
                }
            }
            
            showNextStep();
        }
        
        // Update experiment visual for current step
        function updateExperimentVisual(expId, visualType, stepIndex) {
            const visualContainer = document.getElementById(`exp-${expId}-visual`);
            
            switch(visualType) {
                case 'burette':
                    if (stepIndex >= 3) { // When titration starts
                        const acidSolution = visualContainer.querySelector('.liquid');
                        acidSolution.style.height = `${80 - (stepIndex * 10)}%`;
                        
                        if (stepIndex >= 4) { // Endpoint reached
                            acidSolution.style.backgroundColor = 'rgba(255, 100, 255, 0.5)';
                            playSound(successSound);
                        }
                    }
                    break;
                    
                case 'ph_paper':
                    if (stepIndex >= 1) {
                        const paper = visualContainer.querySelector('div > div:last-child');
                        paper.style.backgroundColor = `rgba(255, ${100 - (stepIndex * 30)}, 100, 0.5)`;
                    }
                    break;
                    
                case 'ph_meter':
                    if (stepIndex >= 3) {
                        const meter = visualContainer.querySelector('div > div:first-child');
                        meter.textContent = `pH: ${(4 - (stepIndex - 3)).toFixed(1)}`;
                    }
                    break;
                    
                case 'electrolysis':
                    if (stepIndex >= 3) {
                        playSound(bubbleSound);
                        const bubblesContainer = document.getElementById('electrolysis-bubbles');
                        bubblesContainer.innerHTML = ";
                        // Create bubbles at both electrodes
                        for (let i = 0; i < 20; i++) {
                            // Hydrogen bubbles (left electrode)
                            setTimeout(() => {
                                const bubble = document.createElement('div');
                                bubble.className = 'bubble';
                                bubble.style.width = `${Math.random() * 8 + 4}px`;
                                bubble.style.height = bubble.style.width;
                                bubble.style.left = '30%';
                                bubble.style.bottom = '10px';
                                bubble.style.animationDuration = `${Math.random() * 2 + 1}s`;
                                bubblesContainer.appendChild(bubble);
                                
                                setTimeout(() => bubble.remove(), 2000);
                            }, i * 200);
                            
                            // Oxygen bubbles (right electrode)
                            setTimeout(() => {
                                const bubble = document.createElement('div');
                                bubble.className = 'bubble';
                                bubble.style.width = `${Math.random() * 5 + 3}px`;
                                bubble.style.height = bubble.style.width;
                                bubble.style.left = '70%';
                                bubble.style.bottom = '10px';
                                bubble.style.animationDuration = `${Math.random() * 2 + 1.5}s`;
                                bubblesContainer.appendChild(bubble);
                                
                                setTimeout(() => bubble.remove(), 2000);
                            }, i * 300);
                        }
                    }
                    break;
                    
                case 'flame_test':
                    if (stepIndex >= 2) {
                        playSound(flameSound);
                        const flame = document.getElementById('bunsen-flame');
                        flame.style.opacity = '1';
                        
                        // Random flame color based on possible metal ions
                        const colors = [
                            { color: 'crimson', name: 'crimson (Lithium)' },
                            { color: 'gold', name: 'gold (Sodium)' },
                            { color: 'red', name: 'red (Calcium)' },
                            { color: 'green', name: 'green (Barium)' },
                            { color: 'blue', name: 'blue (Copper)' },
                            { color: 'purple', name: 'purple (Potassium)' }
                        ];
                        const randomColor = colors[Math.floor(Math.random() * colors.length)];
                        flame.style.background = `linear-gradient(to top, ${randomColor.color}, yellow)`;
                        
                        setTimeout(() => {
                            flame.style.opacity = '0';
                        }, 2000);
                    }
                    break;
                    
                case 'soap':
                case 'soap_hot':
                    if (stepIndex >= 2) {
                        const soapMixture = visualContainer.querySelector('.liquid');
                        soapMixture.style.height = `${60 - (stepIndex * 5)}%`;
                        
                        if (stepIndex >= 3) {
                            soapMixture.style.backgroundColor = 'rgba(240, 240, 240, 0.8)';
                        }
                    }
                    break;
                    
                case 'crystals_slow':
                case 'crystals_fast':
                    if (stepIndex >= 2) {
                        const solution = visualContainer.querySelector('.liquid');
                        solution.style.height = `${70 - (stepIndex * 5)}%`;
                        
                        if (stepIndex >= 3) {
                            const seed = visualContainer.querySelector('#crystal-seed');
                            seed.style.display = 'block';
                            
                            // Create crystal shapes
                            const crystals = [
                                { size: '15px', left: '45%', bottom: '30px' },
                                { size: '10px', left: '50%', bottom: '35px' },
                                { size: '8px', left: '55%', bottom: '32px' }
                            ];
                            
                            crystals.forEach(crystal => {
                                const c = document.createElement('div');
                                c.style.position = 'absolute';
                                c.style.width = crystal.size;
                                c.style.height = crystal.size;
                                c.style.left = crystal.left;
                                c.style.bottom = crystal.bottom;
                                c.style.backgroundColor = 'rgba(100, 200, 255, 0.8)';
                                c.style.borderRadius = '2px';
                                c.style.transform = 'rotate(45deg)';
                                visualContainer.querySelector('.beaker').appendChild(c);
                            });
                        }
                    }
                    break;
            }
        }
        
        // Complete experiment
        function completeExperiment(expId, method) {
            const exp = experiments.find(e => e.id === expId);
            const isFirstTime = !gameState.completedExperiments.includes(expId);
            
            // Calculate earned XP
            const earnedXP = Math.floor(Math.random() * (method.xpRange[1] - method.xpRange[0] + 1)) + method.xpRange[0];
            gameState.xp += earnedXP;
            
            if (isFirstTime) {
                gameState.completedExperiments.push(expId);
            }
            
            // Update inventory (reduce used chemicals)
            method.chemicals.forEach(chem => {
                if (gameState.inventory[chem] > 0) {
                    gameState.inventory[chem] -= 10; // Deduct 10 units per use
                    if (gameState.inventory[chem] < 0) gameState.inventory[chem] = 0;
                }
            });
            
            // Check for achievements
            checkAchievements();
            
            // Update UI
            updateXP();
            updateRating();
            updateCompletedExperiments();
            renderExperiments();
            renderInventory();
            
            // Show result
            const resultDisplay = document.getElementById(`exp-${expId}-result`);
            resultDisplay.style.display = 'block';
            resultDisplay.innerHTML = `
                <p>Experiment completed successfully!</p>
                <p>Method: <strong>${method.name}</strong></p>
                <p>+${earnedXP} XP earned!</p>
            `;
            
            // Show celebration if reached new rating
            checkForRatingCelebration();
            
            // Save progress
            saveGameState();
            
            // Add to console
            addToConsole(`> Experiment #${expId} completed! +${earnedXP} XP`);
            playSound(successSound);
        }
        
        // Check for achievements
        function checkAchievements() {
            const newAchievements = [];
            
            // First Experiment
            if (gameState.completedExperiments.length === 1 && !gameState.unlockedAchievements.includes('first-experiment')) {
                newAchievements.push(achievements.find(a => a.id === 'first-experiment'));
                gameState.unlockedAchievements.push('first-experiment');
            }
            
            // Junior Chemist
            if (gameState.completedExperiments.length >= 3 && !gameState.unlockedAchievements.includes('junior-chemist')) {
                newAchievements.push(achievements.find(a => a.id === 'junior-chemist'));
                gameState.unlockedAchievements.push('junior-chemist');
            }
            
            // Lab Expert
            if (gameState.completedExperiments.length >= experiments.length && !gameState.unlockedAchievements.includes('lab-expert')) {
                newAchievements.push(achievements.find(a => a.id === 'lab-expert'));
                gameState.unlockedAchievements.push('lab-expert');
            }
            
            // Inventory Master
            const allChemicalsUsed = Object.keys(gameState.inventory).every(chem => {
                return gameState.inventory[chem] < 500; // Assuming we started with 500 of each
            });
            if (allChemicalsUsed && !gameState.unlockedAchievements.includes('inventory-master')) {
                newAchievements.push(achievements.find(a => a.id === 'inventory-master'));
                gameState.unlockedAchievements.push('inventory-master');
            }
            
            // Process new achievements
            if (newAchievements.length > 0) {
                newAchievements.forEach(ach => {
                    gameState.xp += ach.xpReward;
                    addToConsole(`> Achievement Unlocked: ${ach.title}! +${ach.xpReward} XP`);
                    showAchievementPopup(ach);
                });
                
                updateXP();
                updateRating();
                renderAchievements();
                saveGameState();
            }
        }
        
        // Show achievement popup
        function showAchievementPopup(achievement) {
            playSound(successSound);
            createConfetti();
            
            const popup = document.createElement('div');
            popup.className = 'achievement-popup';
            popup.style.position = 'fixed';
            popup.style.top = '20px';
            popup.style.left = '50%';
            popup.style.transform = 'translateX(-50%)';
            popup.style.background = 'rgba(20, 30, 40, 0.95)';
            popup.style.padding = '20px';
            popup.style.borderRadius = '10px';
            popup.style.border = '2px solid var(--accent)';
            popup.style.boxShadow = '0 5px 20px rgba(0, 0, 0, 0.5)';
            popup.style.zIndex = '1000';
            popup.style.animation = 'fadeIn 0.5s ease';
            popup.style.display = 'flex';
            popup.style.alignItems = 'center';
            popup.style.gap = '15px';
            
            popup.innerHTML = `
                <div style="font-size: 2rem; color: gold;">
                    <i class="${achievement.icon}"></i>
                </div>
                <div>
                    <h3 style="margin-bottom: 5px; color: var(--accent);">Achievement Unlocked!</h3>
                    <h4 style="margin-bottom: 5px;">${achievement.title}</h4>
                    <p style="margin-bottom: 0; font-size: 0.9rem;">${achievement.description}</p>
                    <p style="margin-top: 5px; color: var(--accent); font-weight: bold;">+${achievement.xpReward} XP</p>
                </div>
            `;
            
            document.body.appendChild(popup);
            
            // Remove after 5 seconds
            setTimeout(() => {
                popup.style.animation = 'fadeIn 0.5s ease reverse';
                setTimeout(() => popup.remove(), 500);
            }, 5000);
        }
        
        // Check for rating celebration
        function checkForRatingCelebration() {
            const prevRating = gameState.rating;
            updateRating();
            
            if (gameState.rating !== prevRating) {
                addToConsole(`> Congratulations! You've been promoted to ${gameState.rating}!`);
                createConfetti();
                playSound(successSound);
            }
        }
        
        // Create confetti effect
        function createConfetti() {
            const colors = ['#f00', '#0f0', '#00f', '#ff0', '#f0f', '#0ff'];
            
            for (let i = 0; i < 50; i++) {
                const confetti = document.createElement('div');
                confetti.className = 'confetti';
                confetti.style.left = `${Math.random() * 100}vw`;
                confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                confetti.style.width = `${Math.random() * 10 + 5}px`;
                confetti.style.height = `${Math.random() * 10 + 5}px`;
                confetti.style.animationDuration = `${Math.random() * 3 + 2}s`;
                document.body.appendChild(confetti);
                
                // Remove after animation
                setTimeout(() => {
                    confetti.remove();
                }, 5000);
            }
        }
        
        // Render inventory
        function renderInventory() {
            inventoryGrid.innerHTML = '';
            
            for (const [chemical, quantity] of Object.entries(gameState.inventory)) {
                const chemicalItem = document.createElement('div');
                chemicalItem.className = 'chemical-item';
                chemicalItem.innerHTML = `
                    <div class="chemical-icon">${getChemicalSymbol(chemical)}</div>
                    <div class="chemical-name">${chemical}</div>
                    <div class="chemical-quantity">${quantity} ml/g</div>
                `;
                
                inventoryGrid.appendChild(chemicalItem);
            }
        }
        
        // Get chemical symbol
        function getChemicalSymbol(chemical) {
            if (chemical.includes('H₂SO₄')) return 'H₂SO₄';
            if (chemical.includes('NaOH')) return 'NaOH';
            if (chemical.includes('Na₂SO₄')) return 'Na₂SO₄';
            if (chemical.includes('CuSO₄')) return 'CuSO₄';
            if (chemical.includes('HCl')) return 'HCl';
            return chemical.charAt(0);
        }
        // Render achievements
        function renderAchievements() {
            achievementsList.innerHTML = '';
            
            achievements.forEach(ach => {
                const isUnlocked = gameState.unlockedAchievements.includes(ach.id);
                
                const achievementCard = document.createElement('div');
                achievementCard.className = `achievement-card ${isUnlocked ? '' : 'locked'}`;
                achievementCard.innerHTML = `
                    <div class="achievement-icon">
                        <i class="${ach.icon}"></i>
                    </div>
                    <div class="achievement-info">
                        <h3>${ach.title}</h3>
                        <p>${ach.description}</p>
                        ${isUnlocked ? `<p style="color: var(--accent); font-weight: bold;">+${ach.xpReward} XP</p>` : '<p style="opacity: 0.7;">Locked</p>'}
                    </div>
                `;
                
                achievementsList.appendChild(achievementCard);
            });
        }
        
        // Play sound
        function playSound(audioElement) {
            audioElement.currentTime = 0;
            audioElement.play().catch(e => console.log('Audio play prevented:', e));
        }
        
        // Add to console
        function addToConsole(message) {
            const line = document.createElement('div');
            line.className = 'console-line';
            line.textContent = message;
            consoleOutput.appendChild(line);
            consoleOutput.scrollTop = consoleOutput.scrollHeight;
            
            // Add to history
            gameState.consoleHistory.push(message);
            gameState.historyIndex = gameState.consoleHistory.length;
        }
        
        // Handle console input
        function handleConsoleInput(e) {
            if (e.key === 'Enter') {
                executeConsoleCommand();
            } else if (e.key === 'ArrowUp') {
                e.preventDefault();
                if (gameState.historyIndex > 0) {
                    gameState.historyIndex--;
                    consoleInput.value = gameState.consoleHistory[gameState.historyIndex].replace('> ', '');
                }
            } else if (e.key === 'ArrowDown') {
                e.preventDefault();
                if (gameState.historyIndex < gameState.consoleHistory.length - 1) {
                    gameState.historyIndex++;
                    consoleInput.value = gameState.consoleHistory[gameState.historyIndex].replace('> ', '');
                } else {
                    gameState.historyIndex = gameState.consoleHistory.length;
                    consoleInput.value = '';
                }
            }
        }
        
        // Execute console command
        function executeConsoleCommand() {
            const command = consoleInput.value.trim().toLowerCase();
            if (!command) return;
            
            addToConsole(`> ${command}`);
            consoleInput.value = '';
            
            switch(command) {
                case 'help':
                    addToConsole('Available commands:');
                    addToConsole('help - Show this help message');
                    addToConsole('clear - Clear the console');
                    addToConsole('xp - Show your current XP');
                    addToConsole('rating - Show your current rating');
                    addToConsole('experiments - List available experiments');
                    addToConsole('inventory - Show your chemical inventory');
                    addToConsole('achievements - List your achievements');
                    break;
                    
                case 'clear':
                    consoleOutput.innerHTML = '';
                    break;
                    
                case 'xp':
                    addToConsole(`Current XP: ${gameState.xp}`);
                    break;
                    
                case 'rating':
                    addToConsole(`Current Rating: ${gameState.rating}`);
                    break;
                    
                case 'experiments':
                    addToConsole('Available Experiments:');
                    experiments.forEach(exp => {
                        const isCompleted = gameState.completedExperiments.includes(exp.id);
                        addToConsole(`#${exp.id} ${exp.title} - ${isCompleted ? 'Completed' : 'Available'}`);
                    });
                    break;
                    
                case 'inventory':
                    addToConsole('Chemical Inventory:');
                    for (const [chemical, quantity] of Object.entries(gameState.inventory)) {
                        addToConsole(`${chemical}: ${quantity} ml/g`);
                    }
                    break;
                    
                case 'achievements':
                    addToConsole('Achievements:');
                    achievements.forEach(ach => {
                        const isUnlocked = gameState.unlockedAchievements.includes(ach.id);
                        addToConsole(`${isUnlocked ? '✓' : '✗'} ${ach.title} - ${ach.description} ${isUnlocked ? `(+${ach.xpReward} XP)` : ''}`);
                    });
                    break;
                    
                default:
                    addToConsole(`Unknown command: "${command}". Type "help" for available commands.`);
            }
            
            gameState.consoleHistory.push(command);
            gameState.historyIndex = gameState.consoleHistory.length;
        }
        
        // Switch tabs
        function switchTab(tabId) {
            // Update active tab
            tabs.forEach(tab => {
                tab.classList.toggle('active', tab.dataset.tab === tabId);
            });
            
            // Update active content
            tabContents.forEach(content => {
                content.classList.toggle('active', content.id === `${tabId}-tab`);
            });
        }
        // Update active content
            tabContents.forEach(content => {
                content.classList.toggle('active', content.id === `${tabId}-tab`);
            });
        }
        
        // Lighten color
        function lightenColor(color, percent) {
            const num = parseInt(color.replace('#', ''), 16);
            const amt = Math.round(2.55 * percent);
            const R = (num >> 16) + amt;
            const G = (num >> 8 & 0x00FF) + amt;
            const B = (num & 0x0000FF) + amt;
            
            return `#${(
                0x1000000 +
                (R < 255 ? (R < 1 ? 0 : R) : 255) * 0x10000 +
                (G < 255 ? (G < 1 ? 0 : G) : 255) * 0x100 +
                (B < 255 ? (B < 1 ? 0 : B) : 255)
            ).toString(16).slice(1)}`;
        }
        
        // Initialize the app when DOM is loaded
        document.addEventListener('DOMContentLoaded', init);
    </script>
</body>
</html>
             
