<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NetLearn - Virtual Networking Classroom</title>
    <style>
        :root {
            --primary: #3498db;
            --secondary: #2980b9;
            --accent: #f39c12;
            --light: #ecf0f1;
            --dark: #2c3e50;
            --success: #27ae60;
            --danger: #e74c3c;
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
        }
        
        header {
            background-color: var(--primary);
            color: white;
            padding: 1rem;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            display: flex;
            align-items: center;
        }
        
        .logo-icon {
            margin-right: 0.5rem;
        }
        
        .nav-links {
            display: flex;
        }
        
        .nav-links a {
            color: white;
            text-decoration: none;
            margin-left: 1.5rem;
            padding: 0.5rem;
            border-radius: 4px;
            transition: background-color 0.3s;
        }
        
        .nav-links a:hover {
            background-color: var(--secondary);
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }
        
        .hero {
            display: flex;
            align-items: center;
            justify-content: space-between;
            margin-bottom: 3rem;
        }
        
        .hero-content {
            flex: 1;
            padding-right: 2rem;
        }
        
        .hero-image {
            flex: 1;
            text-align: center;
        }
        
        .hero h1 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            color: var(--dark);
        }
        
        .hero p {
            font-size: 1.1rem;
            color: #666;
            margin-bottom: 1.5rem;
            line-height: 1.6;
        }
        
        .btn {
            display: inline-block;
            padding: 0.8rem 1.5rem;
            background-color: var(--accent);
            color: white;
            text-decoration: none;
            border-radius: 4px;
            font-weight: bold;
            transition: background-color 0.3s;
            cursor: pointer;
            border: none;
        }
        
        .btn:hover {
            background-color: #e67e22;
        }
        
        .btn-secondary {
            background-color: var(--secondary);
        }
        
        .btn-secondary:hover {
            background-color: var(--primary);
        }
        
        .section-title {
            margin: 2rem 0 1rem;
            padding-bottom: 0.5rem;
            border-bottom: 2px solid var(--primary);
        }
        
        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin: 3rem 0;
        }
        
        .feature-card {
            background-color: white;
            border-radius: 8px;
            padding: 1.5rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .feature-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
        }
        
        .feature-icon {
            font-size: 2rem;
            color: var(--primary);
            margin-bottom: 1rem;
        }
        
        .feature-card h3 {
            margin-bottom: 0.5rem;
        }
        
        .feature-card p {
            color: #666;
            line-height: 1.6;
        }
        
        .tabs {
            display: flex;
            border-bottom: 1px solid #ddd;
            margin-bottom: 2rem;
            overflow-x: auto;
        }
        
        .tab-btn {
            padding: 0.8rem 1.5rem;
            background: none;
            border: none;
            cursor: pointer;
            font-size: 1rem;
            font-weight: bold;
            color: #666;
            border-bottom: 3px solid transparent;
            transition: all 0.3s;
            white-space: nowrap;
        }
        
        .tab-btn.active {
            color: var(--primary);
            border-bottom: 3px solid var(--primary);
        }
        
        .tab-content {
            display: none;
            animation: fadeIn 0.5s;
        }
        
        .tab-content.active {
            display: block;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .learning-modules {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }
        
        .module-card {
            background-color: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s;
        }
        
        .module-card:hover {
            transform: translateY(-5px);
        }
        
        .module-image {
            height: 150px;
            background-color: #ccc;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.2rem;
        }
        
        .module-content {
            padding: 1.5rem;
        }
        
        .module-card h3 {
            margin-bottom: 0.5rem;
        }
        
        .module-card p {
            color: #666;
            margin-bottom: 1rem;
            line-height: 1.6;
        }
        
        .quiz-list {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }
        
        .quiz-card {
            background-color: white;
            border-radius: 8px;
            padding: 1.5rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        .quiz-card h3 {
            margin-bottom: 0.5rem;
        }
        
        .quiz-card p {
            color: #666;
            margin-bottom: 1rem;
            line-height: 1.6;
        }
        
        .quiz-meta {
            display: flex;
            justify-content: space-between;
            font-size: 0.9rem;
            color: #888;
            margin-bottom: 1rem;
        }
        
        .quiz-container {
            background-color: white;
            border-radius: 8px;
            padding: 1.5rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            display: none;
        }
        
        .quiz-question {
            font-size: 1.2rem;
            margin-bottom: 1.5rem;
            font-weight: 500;
        }
        
        .quiz-options {
            margin-bottom: 2rem;
        }
        
        .quiz-option {
            display: block;
            padding: 0.8rem;
            margin-bottom: 0.8rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .quiz-option:hover {
            background-color: #f5f5f5;
        }
        
        .quiz-option.selected {
            background-color: #e3f2fd;
            border-color: var(--primary);
        }
        
        .quiz-option.correct {
            background-color: #e8f5e9;
            border-color: var(--success);
        }
        
        .quiz-option.incorrect {
            background-color: #ffebee;
            border-color: var(--danger);
        }
        
        .quiz-navigation {
            display: flex;
            justify-content: space-between;
            margin-top: 2rem;
        }
        
        .quiz-progress {
            margin-top: 1rem;
            font-size: 0.9rem;
            color: #666;
        }
        
        .quiz-result {
            text-align: center;
            padding: 2rem;
            display: none;
        }
        
        .quiz-result h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
        }
        
        .quiz-score {
            font-size: 2rem;
            font-weight: bold;
            color: var(--primary);
            margin: 1rem 0;
        }
        
        .quiz-feedback {
            margin-bottom: 2rem;
        }
        
        .notes-container {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 2rem;
        }
        
        .notes-list {
            background-color: white;
            border-radius: 8px;
            padding: 1rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            height: 500px;
            overflow-y: auto;
        }
        
        .note-item {
            padding: 0.8rem;
            border-bottom: 1px solid #eee;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .note-item:hover {
            background-color: #f9f9f9;
        }
        
        .note-item.active {
            background-color: #e3f2fd;
            border-left: 3px solid var(--primary);
        }
        
        .note-editor {
            background-color: white;
            border-radius: 8px;
            padding: 1.5rem;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        .note-title {
            width: 100%;
            padding: 0.8rem;
            font-size: 1.2rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            margin-bottom: 1rem;
        }
        
        .note-content {
            width: 100%;
            height: 400px;
            padding: 0.8rem;
            font-size: 1rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            resize: none;
            font-family: inherit;
        }
        
        .chat-container {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            display: flex;
            flex-direction: column;
            height: 600px;
        }
        
        .chat-header {
            background-color: var(--primary);
            color: white;
            padding: 1rem;
            font-weight: bold;
            display: flex;
            align-items: center;
        }
        
        .chat-header-icon {
            margin-right: 0.5rem;
        }
        
        .chat-messages {
            flex: 1;
            padding: 1rem;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }
        
        .message {
            display: flex;
            max-width: 80%;
        }
        
        .message.user {
            align-self: flex-end;
            justify-content: flex-end;
        }
        
        .message.ai {
            align-self: flex-start;
            justify-content: flex-start;
        }
        
        .message-content {
            padding: 0.8rem 1rem;
            border-radius: 8px;
            box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
            word-wrap: break-word;
        }
        
        .message.ai .message-content {
            background-color: #f1f0f0;
            border-radius: 0 8px 8px 8px;
        }
        
        .message.user .message-content {
            background-color: var(--primary);
            color: white;
            border-radius: 8px 0 8px 8px;
        }
        
        .chat-input-container {
            display: flex;
            padding: 1rem;
            border-top: 1px solid #eee;
        }
        
        .chat-input {
            flex: 1;
            padding: 0.8rem;
            border: 1px solid #ddd;
            border-radius: 4px 0 0 4px;
            font-size: 1rem;
            outline: none;
        }
        
        .chat-send-btn {
            padding: 0.8rem 1.5rem;
            background-color: var(--primary);
            color: white;
            border: none;
            border-radius: 0 4px 4px 0;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        .chat-send-btn:hover {
            background-color: var(--secondary);
        }
        
        .typing-indicator {
            display: none;
            padding: 0.5rem 1rem;
            background-color: #f1f0f0;
            border-radius: 8px;
            align-self: flex-start;
            margin-bottom: 0.5rem;
        }
        
        .typing-indicator span {
            display: inline-block;
            width: 8px;
            height: 8px;
            background-color: #666;
            border-radius: 50%;
            margin: 0 2px;
            animation: typing 1s infinite ease-in-out;
        }
        
        .typing-indicator span:nth-child(2) {
            animation-delay: 0.2s;
        }
        
        .typing-indicator span:nth-child(3) {
            animation-delay: 0.4s;
        }
        
        @keyframes typing {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
        }
        
        footer {
            background-color: var(--dark);
            color: white;
            text-align: center;
            padding: 2rem;
            margin-top: 3rem;
        }
        
        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .footer-links {
            display: flex;
        }
        
        .footer-links a {
            color: white;
            text-decoration: none;
            margin-left: 1.5rem;
        }
        
        .footer-links a:hover {
            text-decoration: underline;
        }
        
        @media (max-width: 768px) {
            .hero {
                flex-direction: column;
            }
            
            .hero-content {
                padding-right: 0;
                margin-bottom: 2rem;
            }
            
            .notes-container {
                grid-template-columns: 1fr;
            }
            
            .quiz-container {
                padding: 1rem;
            }
            
            .footer-content {
                flex-direction: column;
            }
            
            .footer-links {
                margin-top: 1rem;
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .footer-links a {
                margin: 0.5rem;
            }
            
            .nav-links {
                display: none;
            }
            
            .message {
                max-width: 90%;
            }
        }
    </style>
</head>
<body>
    <header>
        <nav>
            <div class="logo">
                <span class="logo-icon">🌐</span>
                NetLearn
            </div>
            <div class="nav-links">
                <a href="#" class="nav-link" data-tab="learn">Learn</a>
                <a href="#" class="nav-link" data-tab="quiz">Tests & Quizzes</a>
                <a href="#" class="nav-link" data-tab="notes">My Notes</a>
                <a href="#" class="nav-link" data-tab="chat">AI Assistant</a>
            </div>
        </nav>
    </header>
    
    <div class="container">
        <section class="hero">
            <div class="hero-content">
                <h1>Master Computer Networking with AI Teachers</h1>
                <p>Welcome to NetLearn, your interactive virtual classroom for learning computer system networking. Our AI teachers provide personalized education, instant feedback, and expert guidance on networking concepts.</p>
                <a href="#" class="btn" data-tab="learn">Start Learning Now</a>
            </div>
            <div class="hero-image">
                <img src="https://via.placeholder.com/500x300?text=Network+Classroom" alt="Network Classroom" />
            </div>
        </section>
        
        <section class="features">
            <div class="feature-card">
                <div class="feature-icon">👩‍🏫</div>
                <h3>AI Teachers</h3>
                <p>Learn from our advanced AI teachers who provide personalized instruction and answer your networking questions 24/7.</p>
            </div>
            <div class="feature-card">
                <div class="feature-icon">📝</div>
                <h3>Interactive Quizzes</h3>
                <p>Test your knowledge with adaptive quizzes that focus on your weak areas and help reinforce your learning.</p>
            </div>
            <div class="feature-card">
                <div class="feature-icon">📚</div>
                <h3>Smart Notes</h3>
                <p>Organize your thoughts with our intelligent note-taking system that links concepts and helps you build your knowledge base.</p>
            </div>
            <div class="feature-card">
                <div class="feature-icon">💬</div>
                <h3>Networking Assistant</h3>
                <p>Chat with our specialized networking assistant to get instant help on any networking topic or troubleshooting guidance.</p>
            </div>
        </section>
        
        <div class="tabs">
            <button class="tab-btn active" data-tab="learn">Learning Modules</button>
            <button class="tab-btn" data-tab="quiz">Tests & Quizzes</button>
            <button class="tab-btn" data-tab="notes">My Notes</button>
            <button class="tab-btn" data-tab="chat">AI Assistant</button>
        </div>
        
        <div id="learn" class="tab-content active">
            <h2 class="section-title">Learning Modules</h2>
            <div class="learning-modules">
                <div class="module-card" data-topic="network fundamentals">
                    <div class="module-image" style="background-color: #3498db;">
                        Network Fundamentals
                    </div>
                    <div class="module-content">
                        <h3>Network Fundamentals</h3>
                        <p>Learn the core concepts of computer networking including OSI model, TCP/IP, and basic network topologies.</p>
                        <button class="btn learn-btn">Start Learning</button>
                    </div>
                </div>
                <div class="module-card" data-topic="routing and switching">
                    <div class="module-image" style="background-color: #e74c3c;">
                        Routing & Switching
                    </div>
                    <div class="module-content">
                        <h3>Routing & Switching</h3>
                        <p>Understand how data is routed across networks and how switches manage local network traffic.</p>
                        <button class="btn learn-btn">Start Learning</button>
                    </div>
                </div>
                <div class="module-card" data-topic="network security">
                    <div class="module-image" style="background-color: #2ecc71;">
                        Network Security
                    </div>
                    <div class="module-content">
                        <h3>Network Security</h3>
                        <p>Explore essential security concepts including firewalls, encryption, VPNs, and threat detection systems.</p>
                        <button class="btn learn-btn">Start Learning</button>
                    </div>
                </div>
                <div class="module-card" data-topic="wireless networking">
                    <div class="module-image" style="background-color: #9b59b6;">
                        Wireless Networking
                    </div>
                    <div class="module-content">
                        <h3>Wireless Networking</h3>
                        <p>Master wireless protocols, standards, and security measures for modern wireless networks.</p>
                        <button class="btn learn-btn">Start Learning</button>
                    </div>
                </div>
                <div class="module-card" data-topic="cloud networking">
                    <div class="module-image" style="background-color: #f39c12;">
                        Cloud Networking
                    </div>
                    <div class="module-content">
                        <h3>Cloud Networking</h3>
                        <p>Discover how networking works in cloud environments and best practices for cloud infrastructure.</p>
                        <button class="btn learn-btn">Start Learning</button>
                    </div>
                </div>
                <div class="module-card" data-topic="network automation">
                    <div class="module-image" style="background-color: #1abc9c;">
                        Network Automation
                    </div>
                    <div class="module-content">
                        <h3>Network Automation</h3>
                        <p>Learn how to automate network tasks using scripting, APIs, and infrastructure as code.</p>
                        <button class="btn learn-btn">Start Learning</button>
                    </div>
                </div>
            </div>
        </div>
        
        <div id="quiz" class="tab-content">
            <h2 class="section-title">Tests & Quizzes</h2>
            <div class="quiz-list" id="quizList">
                <!-- Quizzes will be loaded here by JavaScript -->
            </div>
            
            <div class="quiz-container" id="quizContainer">
                <h2 id="quizTitle"></h2>
                <p id="quizDescription"></p>
                <div class="quiz-progress" id="quizProgress"></div>
                
                <div id="quizContent">
                    <!-- Questions will be loaded here -->
                </div>
                
                <div class="quiz-navigation">
                    <button class="btn btn-secondary" id="prevQuestion">Previous</button>
                    <button class="btn" id="nextQuestion">Next</button>
                </div>
            </div>
            
            <div class="quiz-result" id="quizResult">
                <h3>Quiz Completed!</h3>
                <div class="quiz-score" id="quizScore"></div>
                <div class="quiz-feedback" id="quizFeedback"></div>
                <button class="btn" id="retakeQuiz">Retake Quiz</button>
                <button class="btn btn-secondary" id="backToQuizzes">Back to Quizzes</button>
            </div>
        </div>
        
        <div id="notes" class="tab-content">
            <h2 class="section-title">My Notes</h2>
            <div class="notes-container">
                <div class="notes-list">
                    <div class="note-item active">OSI Model Notes</div>
                    <div class="note-item">TCP/IP Protocol Suite</div>
                    <div class="note-item">Subnetting Cheat Sheet</div>
                    <div class="note-item">Routing Protocol Comparison</div>
                    <div class="note-item">Network Security Best Practices</div>
                    <div class="note-item">Wireless Standards Overview</div>
                </div>
                <div class="note-editor">
                    <input type="text" class="note-title" value="OSI Model Notes">
                    <textarea class="note-content"># OSI Model Layers

## Layer 1: Physical
- Deals with the physical connection between devices
- Transmits raw bit stream over physical medium
- Examples: Cables, switches, network adapters

## Layer 2: Data Link
- Provides node-to-node data transfer
- Detects and possibly corrects errors from physical layer
- Examples: Ethernet, PPP, Switch, Bridge

## Layer 3: Network
- Routes data packets between networks
- Handles addressing and path determination
- Examples: IP, ICMP, Routers

## Layer 4: Transport
- Provides end-to-end communication control
- Examples: TCP, UDP

## Layer 5: Session
- Manages sessions between applications
- Examples: NetBIOS, RPC

## Layer 6: Presentation
- Translates data between networking service and application
- Examples: JPEG, MPEG, SSL

## Layer 7: Application
- Interface for user applications
- Examples: HTTP, SMTP, FTP, DNS

Important to remember: "Please Do Not Throw Sausage Pizza Away" (Physical, Data Link, Network, Transport, Session, Presentation, Application)</textarea>
                </div>
            </div>
        </div>
        
        <div id="chat" class="tab-content">
            <h2 class="section-title">AI Networking Assistant</h2>
            <div class="chat-container">
                <div class="chat-header">
                    <span class="chat-header-icon">🤖</span>
                    NetLearn Assistant
                </div>
                <div class="chat-messages">
                    <div class="message ai">
                        <div class="message-content">
                            Hello! I'm your NetLearn AI assistant. I'm here to help with any networking questions you have. What would you like to learn about today?
                        </div>
                    </div>
                </div>
                <div class="typing-indicator" id="typingIndicator">
                    <span></span>
                    <span></span>
                    <span></span>
                </div>
                <div class="chat-input-container">
                    <input type="text" class="chat-input" id="chatInput" placeholder="Type your networking question here...">
                    <button class="chat-send-btn" id="sendBtn">Send</button>
                </div>
            </div>
        </div>
    </div>
    
    <footer>
        <div class="footer-content">
            <div>
                <p>&copy; 2025 NetLearn Virtual Classroom. All rights reserved.</p>
            </div>
            <div class="footer-links">
                <a href="#">Terms of Service</a>
                <a href="#">Privacy Policy</a>
                <a href="#">Contact Us</a>
            </div>
        </div>
    </footer>
    
    <script>
        // Tab Functionality
        function switchTab(tabId) {
            // Deactivate all tabs
            document.querySelectorAll('.tab-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            document.querySelectorAll('.tab-content').forEach(content => {
                content.classList.remove('active');
            });
            
            // Activate selected tab
            document.querySelector(`.tab-btn[data-tab="${tabId}"]`).classList.add('active');
            document.getElementById(tabId).classList.add('active');
            
            // Scroll to the top of the tab content
            document.getElementById(tabId).scrollIntoView({ behavior: 'smooth' });
        }
        
        // Set up tab buttons
        document.querySelectorAll('.tab-btn').forEach(button => {
            button.addEventListener('click', () => {
                const tabId = button.getAttribute('data-tab');
                switchTab(tabId);
            });
        });
        
        // Set up navigation links
        document.querySelectorAll('.nav-link, .btn[data-tab]').forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                const tabId = link.getAttribute('data-tab');
                if (tabId) {
                    switchTab(tabId);
                }
            });
        });
        
        // Note Item Selection
        document.querySelectorAll('.note-item').forEach(item => {
            item.addEventListener('click', () => {
                document.querySelectorAll('.note-item').forEach(note => {
                    note.classList.remove('active');
                });
                item.classList.add('active');
                
                // In a real application, we would load the note content here
                // This is a simplified demo
                document.querySelector('.note-title').value = item.textContent;
                
                // Sample notes content based on selection
                const noteContents = {
                    "OSI Model Notes": `# OSI Model Layers

## Layer 1: Physical
- Deals with the physical connection between devices
- Transmits raw bit stream over physical medium
- Examples: Cables, switches, network adapters

## Layer 2: Data Link
- Provides node-to-node data transfer
- Detects and possibly corrects errors from physical layer
- Examples: Ethernet, PPP, Switch, Bridge

## Layer 3: Network
- Routes data packets between networks
- Handles addressing and path determination
- Examples: IP, ICMP, Routers

## Layer 4: Transport
- Provides end-to-end communication control
- Examples: TCP, UDP

## Layer 5: Session
- Manages sessions between applications
- Examples: NetBIOS, RPC

## Layer 6: Presentation
- Translates data between networking service and application
- Examples: JPEG, MPEG, SSL

## Layer 7: Application
- Interface for user applications
- Examples: HTTP, SMTP, FTP, DNS

Important to remember: "Please Do Not Throw Sausage Pizza Away" (Physical, Data Link, Network, Transport, Session, Presentation, Application)`,
                    "TCP/IP Protocol Suite": `# TCP/IP Protocol Stack

## Application Layer
- Corresponds to OSI layers 5-7
- Protocols: HTTP, FTP, SMTP, DNS, DHCP, Telnet

## Transport Layer
- Corresponds to OSI layer 4
- Protocols: TCP, UDP
- TCP provides reliable, connection-oriented service
- UDP provides unreliable, connectionless service

## Internet Layer
- Corresponds to OSI layer 3
- Protocols: IP, ICMP, ARP
- Handles logical addressing and routing

## Network Interface Layer
- Corresponds to OSI layers 1-2
- Examples: Ethernet, Wi-Fi, PPP
- Handles physical addressing and media access

## Key Differences from OSI Model
- TCP/IP is simpler with 4 layers instead of 7
- TCP/IP is more practical and widely implemented
- OSI is more theoretical but useful for understanding network concepts`,
                    "Subnetting Cheat Sheet": `# Subnetting Quick Reference

## CIDR Notation
- /24 = 255.255.255.0 (Class C) - 256 addresses, 254 hosts
- /25 = 255.255.255.128 - 128 addresses, 126 hosts
- /26 = 255.255.255.192 - 64 addresses, 62 hosts
- /27 = 255.255.255.224 - 32 addresses, 30 hosts
- /28 = 255.255.255.240 - 16 addresses, 14 hosts
- /29 = 255.255.255.248 - 8 addresses, 6 hosts
- /30 = 255.255.255.252 - 4 addresses, 2 hosts

## Subnet Mask Calculations
- 2^n (where n is number of host bits) = number of addresses
- Number of hosts = 2^n - 2 (subtract network and broadcast addresses)

## Subnet Mask Increments
- /24 (256): 0, 256, 512...
- /25 (128): 0, 128, 256...
- /26 (64): 0, 64, 128, 192...
- /27 (32): 0, 32, 64, 96...
- /28 (16): 0, 16, 32, 48...

## Formula for Subnets
- Number of subnets = 2^s (where s is subnet bits)
- Block size = 2^h (where h is host bits)

## Quick Tips
- Network address: First address in subnet range
- Broadcast address: Last address in subnet range
- First usable host: Network address + 1
- Last usable host: Broadcast address - 1`
                };
                
                document.querySelector('.note-content').value = noteContents[item.textContent] || '';
            });
        });
        
        // Chatbot Functionality
        const chatInput = document.getElementById('chatInput');
        const sendBtn = document.getElementById('sendBtn');
        const chatMessages = document.querySelector('.chat-messages');
        const typingIndicator = document.getElementById('typingIndicator');
        
        // Enhanced knowledge base with comprehensive networking information
        const knowledgeBase = {
            "network fundamentals": {
                response: `Network fundamentals form the foundation of all networking concepts. Here's a detailed breakdown:

1. OSI Model (7 Layers):
   • Layer 7 - Application: HTTP, FTP, SMTP (user interfaces)
   • Layer 6 - Presentation: Encryption, compression (data translation)
   • Layer 5 - Session: Establishes and manages connections
   • Layer 4 - Transport: TCP (reliable) and UDP (fast)
   • Layer 3 - Network: IP addressing and routing
   • Layer 2 - Data Link: MAC addresses, switches
   • Layer 1 - Physical: Cables, signals, hubs

2. TCP/IP Protocol Suite:
   • Application Layer: Combines OSI App/Pres/Session
   • Transport Layer: TCP/UDP with ports
   • Internet Layer: IP (IPv4/IPv6), ICMP, ARP
   • Network Interface: Ethernet, Wi-Fi

3. Common Network Topologies:
   • Star: Central switch with connected devices
   • Bus: Single cable with terminators
   • Ring: Circular connection
   • Mesh: Fully or partially connected
   • Hybrid: Combination of above

4. Network Devices:
   • Hubs: Layer 1 repeaters (obsolete)
   • Switches: Layer 2, use MAC addresses
   • Routers: Layer 3, connect networks
   • Firewalls: Security filtering

Would you like me to elaborate on any specific aspect of network fundamentals?`,
                followUp: ["Explain TCP vs UDP in detail", "How does IP addressing work?", "What's the difference between switches and routers?"]
            },
            "routing and switching": {
                response: `Routing and switching are core functions in networking:

1. Switching (Layer 2):
   • Uses MAC addresses to forward frames
   • Learns MAC addresses from incoming traffic
   • Maintains MAC address tables
   • VLANs create logical networks
   • STP prevents switching loops

2. Routing (Layer 3):
   • Uses IP addresses to route packets
   • Routing tables determine best paths
   • Static vs dynamic routing
   • Common protocols:
     - OSPF: Link-state, fast convergence
     - EIGRP: Cisco's advanced distance vector
     - BGP: Path vector for internet routing

3. Key Differences:
   • Switches: Faster, work within same network
   • Routers: Connect different networks
   • Switches use hardware (ASICs) for forwarding
   • Routers use software for path determination

Would you like to dive deeper into any routing protocol or switching concept?`,
                followUp: ["How does OSPF calculate routes?", "Explain VLAN trunking", "What are the advantages of EIGRP?"]
            },
            "network security": {
                response: `Network security is crucial for protecting infrastructure:

1. Firewalls:
   • Packet filtering: Basic ACLs
   • Stateful inspection: Tracks connections
   • Next-gen: Application awareness
   • Web application firewalls

2. Encryption:
   • Symmetric: AES (fast, same key)
   • Asymmetric: RSA (key pairs)
   • SSL/TLS for secure communications

3. VPN Technologies:
   • IPsec: Secure site-to-site tunnels
   • SSL VPN: Clientless remote access
   • DMVPN: Dynamic multipoint VPNs

4. Authentication:
   • 802.1X: Port-based NAC
   • RADIUS/TACACS+: AAA services
   • Multi-factor authentication

5. Common Threats:
   • DDoS: Overwhelm resources
   • MITM: Eavesdropping attacks
   • Phishing: Social engineering
   • Zero-day exploits

Which security area would you like to explore further?`,
                followUp: ["How does SSL/TLS handshake work?", "What's the difference between IDS and IPS?", "Explain DMZ in network security"]
            },
            "wireless networking": {
                response: `Wireless networking enables mobile connectivity:

1. IEEE 802.11 Standards:
   • 802.11a: 5GHz, 54Mbps
   • 802.11b: 2.4GHz, 11Mbps
   • 802.11g: 2.4GHz, 54Mbps
   • 802.11n (WiFi 4): MIMO, 600Mbps
   • 802.11ac (WiFi 5): 5GHz, 1.3Gbps
   • 802.11ax (WiFi 6): OFDMA, 10Gbps

2. Wireless Security:
   • WEP: Broken, avoid
   • WPA: TKIP encryption
   • WPA2: AES-CCMP (current standard)
   • WPA3: SAE, 192-bit encryption

3. Components:
   • Access Points (APs)
   • Wireless Controllers
   • SSIDs for network identification
   • BSSIDs (MAC of AP)

4. Design Considerations:
   • Channel planning (1,6,11 for 2.4GHz)
   • Power settings
   • Roaming between APs
   • Interference from other devices

What specific wireless topic would you like to discuss?`,
                followUp: ["How does MIMO improve performance?", "Explain WPA3 security features", "What's the difference between 2.4GHz and 5GHz?"]
            },
            "cloud networking": {
                response: `Cloud networking transforms traditional infrastructure:

1. Key Concepts:
   • Virtual Networks (VPC/VNet)
   • Software Defined Networking (SDN)
   • Network Function Virtualization (NFV)
   • Hybrid cloud connectivity

2. Major Providers:
   • AWS: VPC, Direct Connect
   • Azure: VNet, ExpressRoute
   • GCP: VPC, Cloud Interconnect

3. Services:
   • Load Balancers (ALB/NLB)
   • Content Delivery Networks (CDN)
   • Auto-scaling groups
   • Serverless networking

4. Security:
   • Security Groups (stateful)
   • Network ACLs (stateless)
   • Web Application Firewalls
   • DDoS protection services

Which cloud networking concept would you like to explore?`,
                followUp: ["How does AWS VPC peering work?", "Explain Azure ExpressRoute", "What are the benefits of SDN?"]
            },
            "network automation": {
                response: `Network automation revolutionizes operations:

1. Tools and Technologies:
   • Ansible: Agentless automation
   • Puppet/Chef: Configuration management
   • Terraform: Infrastructure as Code
   • Python scripting (Netmiko, NAPALM)

2. Protocols and APIs:
   • NETCONF/YANG: Standardized config
   • REST APIs: Modern device interfaces
   • gRPC: High-performance telemetry

3. Use Cases:
   • Configuration management
   • Device provisioning
   • Change management
   • Compliance enforcement
   • Monitoring and remediation

4. CI/CD Pipelines:
   • Version control (Git)
   • Automated testing
   • Continuous deployment
   • Rollback procedures

What automation topic interests you most?`,
                followUp: ["How to use Ansible for network automation?", "Explain NETCONF/YANG models", "Python scripts for network tasks"]
            },
            "subnetting": {
                response: `Subnetting is essential for efficient IP addressing:

1. Key Concepts:
   • CIDR Notation (e.g., /24)
   • Subnet Masks (e.g., 255.255.255.0)
   • Network vs Host portions
   • VLSM (Variable Length Subnet Masking)

2. Calculation Steps:
   1. Determine needed subnets/hosts
   2. Borrow bits from host portion
   3. Calculate subnet mask
   4. Determine subnet ranges
   5. Identify network/broadcast addresses

3. Example: 192.168.1.0/24 divided into /26:
   • 4 subnets (2^2)
   • 62 hosts per subnet (2^6-2)
   • Subnet ranges:
     - 192.168.1.0-63
     - 192.168.1.64-127
     - 192.168.1.128-191
     - 192.168.1.192-255

Would you like practice problems or more examples?`,
                followUp: ["Show more subnetting examples", "How to calculate VLSM?", "IPv6 subnetting basics"]
            },
            "tcp vs udp": {
                response: `TCP and UDP are transport layer protocols:

TCP (Transmission Control Protocol):
• Connection-oriented (3-way handshake)
• Reliable delivery (acknowledgments)
• Ordered packet delivery
• Flow control (window sizing)
• Error checking and recovery
• Higher overhead (20-60 byte headers)
• Used by: HTTP, FTP, SMTP, SSH

UDP (User Datagram Protocol):
• Connectionless (no handshake)
• No delivery guarantees
• No ordering of packets
• No flow control
• Minimal error checking
• Lower overhead (8 byte headers)
• Used by: DNS, VoIP, video streaming, gaming

When to use each:
• TCP: When reliability is critical (web, email, file transfer)
• UDP: When speed is priority (real-time media, gaming)

Would you like examples of applications using each?`,
                followUp: ["Why does DNS use UDP?", "Explain TCP 3-way handshake", "How does VoIP handle UDP packet loss?"]
            },
            "default": {
                response: "I'm sorry, I don't have information about that specific networking topic. Could you rephrase your question or ask about something else? I can help with topics like TCP/IP, routing, switching, network security, wireless networking, subnetting, and more!",
                followUp: []
            }
        };

        // Quiz database
        const quizDatabase = {
            "network fundamentals": {
                title: "Network Fundamentals Quiz",
                description: "Test your understanding of basic networking concepts, protocols, and the OSI model.",
                timeLimit: 15,
                questions: [
                    {
                        question: "Which layer of the OSI model is responsible for logical addressing and routing?",
                        options: [
                            "Physical",
                            "Data Link",
                            "Network",
                            "Transport"
                        ],
                        answer: 2,
                        explanation: "The Network layer (Layer 3) handles logical addressing (IP addresses) and routing between networks."
                    },
                    {
                        question: "What is the purpose of the TCP three-way handshake?",
                        options: [
                            "To encrypt data",
                            "To establish a connection",
                            "To compress data",
                            "To route packets"
                        ],
                        answer: 1,
                        explanation: "The three-way handshake (SYN, SYN-ACK, ACK) establishes a reliable TCP connection before data transfer."
                    },
                    {
                        question: "Which protocol operates at the Transport layer and provides connectionless communication?",
                        options: [
                            "TCP",
                            "HTTP",
                            "UDP",
                            "IP"
                        ],
                        answer: 2,
                        explanation: "UDP (User Datagram Protocol) is connectionless and operates at the Transport layer, unlike TCP which is connection-oriented."
                    }
                ]
            },
            "ip addressing & subnetting": {
                title: "IP Addressing & Subnetting",
                description: "Challenge yourself with questions on IP addressing, subnetting, and CIDR notation.",
                timeLimit: 20,
                questions: [
                    {
                        question: "What is the network address for host 192.168.1.150/24?",
                        options: [
                            "192.168.1.0",
                            "192.168.1.1",
                            "192.168.0.0",
                            "192.168.1.255"
                        ],
                        answer: 0,
                        explanation: "With a /24 subnet mask, the network address is x.x.x.0 and the broadcast is x.x.x.255."
                    },
                    {
                        question: "How many usable host addresses are in a /28 subnet?",
                        options: [
                            "14",
                            "16",
                            "30",
                            "254"
                        ],
                        answer: 0,
                        explanation: "A /28 has 4 host bits (2^4=16 addresses). Subtract 2 for network and broadcast = 14 usable hosts."
                    },
                    {
                        question: "Which of these is a private IP address range?",
                        options: [
                            "10.0.0.0 - 10.255.255.255",
                            "172.15.0.0 - 172.31.255.255",
                            "192.168.0.0 - 192.169.255.255",
                            "169.254.0.0 - 169.254.255.255"
                        ],
                        answer: 0,
                        explanation: "The private ranges are 10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16."
                    }
                ]
            },
            "routing protocols": {
                title: "Routing Protocols Test",
                description: "Evaluate your knowledge of various routing protocols like OSPF, EIGRP, and BGP.",
                timeLimit: 18,
                questions: [
                    {
                        question: "Which routing protocol uses the Dijkstra algorithm to calculate the shortest path?",
                        options: [
                            "RIP",
                            "OSPF",
                            "EIGRP",
                            "BGP"
                        ],
                        answer: 1,
                        explanation: "OSPF is a link-state protocol that uses Dijkstra's algorithm to build its shortest path first tree."
                    },
                    {
                        question: "What is the administrative distance of EIGRP?",
                        options: [
                            "90",
                            "100",
                            "110",
                            "120"
                        ],
                        answer: 0,
                        explanation: "EIGRP has an AD of 90 for internal routes and 170 for external routes."
                    },
                    {
                        question: "Which protocol is considered the 'protocol of the Internet'?",
                        options: [
                            "OSPF",
                            "EIGRP",
                            "BGP",
                            "RIP"
                        ],
                        answer: 2,
                        explanation: "BGP (Border Gateway Protocol) is the path-vector protocol used to exchange routing information between autonomous systems on the Internet."
                    }
                ]
            }
        };

        // Quiz functionality
        const quizList = document.getElementById('quizList');
        const quizContainer = document.getElementById('quizContainer');
        const quizTitle = document.getElementById('quizTitle');
        const quizDescription = document.getElementById('quizDescription');
        const quizProgress = document.getElementById('quizProgress');
        const quizContent = document.getElementById('quizContent');
        const prevQuestionBtn = document.getElementById('prevQuestion');
        const nextQuestionBtn = document.getElementById('nextQuestion');
        const quizResult = document.getElementById('quizResult');
        const quizScore = document.getElementById('quizScore');
        const quizFeedback = document.getElementById('quizFeedback');
        const retakeQuizBtn = document.getElementById('retakeQuiz');
        const backToQuizzesBtn = document.getElementById('backToQuizzes');

        let currentQuiz = null;
        let currentQuestionIndex = 0;
        let userAnswers = [];
        let quizScoreValue = 0;

        // Load quizzes into the quiz list
        function loadQuizzes() {
            quizList.innerHTML = '';
            for (const [quizId, quizData] of Object.entries(quizDatabase)) {
                const quizCard = document.createElement('div');
                quizCard.className = 'quiz-card';
                quizCard.innerHTML = `
                    <h3>${quizData.title}</h3>
                    <div class="quiz-meta">
                        <span>${quizData.questions.length} questions</span>
                        <span>${quizData.timeLimit} minutes</span>
                    </div>
                    <p>${quizData.description}</p>
                    <button class="btn start-quiz" data-quiz="${quizId}">Start Quiz</button>
                `;
                quizList.appendChild(quizCard);
            }

            // Add event listeners to start quiz buttons
            document.querySelectorAll('.start-quiz').forEach(btn => {
                btn.addEventListener('click', function() {
                    const quizId = this.getAttribute('data-quiz');
                    startQuiz(quizId);
                });
            });
        }

        // Start a quiz
        function startQuiz(quizId) {
            currentQuiz = quizDatabase[quizId];
            currentQuestionIndex = 0;
            userAnswers = [];
            quizScoreValue = 0;

            quizTitle.textContent = currentQuiz.title;
            quizDescription.textContent = currentQuiz.description;

            // Hide quiz list and show quiz container
            quizList.style.display = 'none';
            quizContainer.style.display = 'block';
            quizResult.style.display = 'none';

            showQuestion();
        }

        // Show current question
        function showQuestion() {
            const question = currentQuiz.questions[currentQuestionIndex];
            
            quizProgress.textContent = `Question ${currentQuestionIndex + 1} of ${currentQuiz.questions.length}`;
            
            quizContent.innerHTML = `
                <div class="quiz-question">${question.question}</div>
                <div class="quiz-options">
                    ${question.options.map((option, index) => `
                        <div class="quiz-option" data-index="${index}">${option}</div>
                    `).join('')}
                </div>
            `;

            // Highlight selected answer if exists
            if (userAnswers[currentQuestionIndex] !== undefined) {
                const selectedOption = document.querySelector(`.quiz-option[data-index="${userAnswers[currentQuestionIndex]}"]`);
                if (selectedOption) {
                    selectedOption.classList.add('selected');
                }
            }

            // Update navigation buttons
            prevQuestionBtn.disabled = currentQuestionIndex === 0;
            nextQuestionBtn.textContent = currentQuestionIndex === currentQuiz.questions.length - 1 ? 'Submit Quiz' : 'Next';
        }

        // Event delegation for quiz options
        quizContent.addEventListener('click', function(e) {
            if (e.target.classList.contains('quiz-option')) {
                // Remove selected class from all options
                document.querySelectorAll('.quiz-option').forEach(opt => {
                    opt.classList.remove('selected');
                });

                // Add selected class to clicked option
                e.target.classList.add('selected');
                
                // Save user's answer
                const selectedIndex = parseInt(e.target.getAttribute('data-index'));
                userAnswers[currentQuestionIndex] = selectedIndex;
            }
        });

        // Navigation between questions
        prevQuestionBtn.addEventListener('click', function() {
            if (currentQuestionIndex > 0) {
                currentQuestionIndex--;
                showQuestion();
            }
        });

        nextQuestionBtn.addEventListener('click', function() {
            if (userAnswers[currentQuestionIndex] === undefined) {
                alert('Please select an answer before proceeding.');
                return;
            }

            if (currentQuestionIndex < currentQuiz.questions.length - 1) {
                currentQuestionIndex++;
                showQuestion();
            } else {
                submitQuiz();
            }
        });

        // Submit quiz and show results
        function submitQuiz() {
            // Calculate score
            quizScoreValue = 0;
            currentQuiz.questions.forEach((question, index) => {
                if (userAnswers[index] === question.answer) {
                    quizScoreValue++;
                }
            });

            // Show results
            quizContainer.style.display = 'none';
            quizResult.style.display = 'block';

            const percentage = Math.round((quizScoreValue / currentQuiz.questions.length) * 100);
            quizScore.textContent = `${quizScoreValue}/${currentQuiz.questions.length} (${percentage}%)`;

            if (percentage >= 80) {
                quizFeedback.textContent = 'Excellent work! You have a strong understanding of this topic.';
            } else if (percentage >= 60) {
                quizFeedback.textContent = 'Good job! You have a decent understanding but could review some areas.';
            } else {
                quizFeedback.textContent = 'Keep practicing! Review the material and try again.';
            }
        }

        // Retake quiz
        retakeQuizBtn.addEventListener('click', function() {
            startQuiz(Object.keys(quizDatabase).find(key => quizDatabase[key] === currentQuiz));
        });

        // Back to quizzes list
        backToQuizzesBtn.addEventListener('click', function() {
            quizList.style.display = 'grid';
            quizContainer.style.display = 'none';
            quizResult.style.display = 'none';
        });

        // Set up learning module buttons
        document.querySelectorAll('.learn-btn').forEach(button => {
            button.addEventListener('click', function() {
                const moduleCard = this.closest('.module-card');
                const topic = moduleCard.getAttribute('data-topic');
                
                // Switch to AI Assistant tab
                switchTab('chat');
                
                // After a short delay to allow tab switch, ask about the topic
                setTimeout(() => {
                    askAboutTopic(topic);
                }, 300);
            });
        });

        // Function to ask the AI about a specific topic
        function askAboutTopic(topic) {
            const knowledge = knowledgeBase[topic] || knowledgeBase['default'];
            
            // Clear previous messages except the first welcome message
            const messages = document.querySelectorAll('.chat-messages .message');
            for (let i = 1; i < messages.length; i++) {
                messages[i].remove();
            }
            
            // Add the topic question
            addMessage(`Tell me about ${topic}`, 'user');
            
            // Show typing indicator
            typingIndicator.style.display = 'flex';
            
            // Simulate AI thinking
            setTimeout(() => {
                typingIndicator.style.display = 'none';
                
                // Add AI response
                addMessage(knowledge.response, 'ai');
                
                // Add follow-up questions as buttons
                if (knowledge.followUp && knowledge.followUp.length > 0) {
                    const followUpDiv = document.createElement('div');
                    followUpDiv.className = 'follow-up-questions';
                    followUpDiv.style.marginTop = '10px';
                    followUpDiv.style.display = 'flex';
                    followUpDiv.style.flexWrap = 'wrap';
                    followUpDiv.style.gap = '5px';
                    
                    knowledge.followUp.forEach(question => {
                        const btn = document.createElement('button');
                        btn.textContent = question;
                        btn.className = 'follow-up-btn';
                        btn.style.padding = '5px 10px';
                        btn.style.backgroundColor = '#f1f0f0';
                        btn.style.border = 'none';
                        btn.style.borderRadius = '4px';
                        btn.style.cursor = 'pointer';
                        btn.style.fontSize = '0.9rem';
                        
                        btn.addEventListener('click', () => {
                            chatInput.value = question;
                            sendMessage();
                        });
                        
                        followUpDiv.appendChild(btn);
                    });
                    
                    document.querySelector('.chat-messages').appendChild(followUpDiv);
                    chatMessages.scrollTop = chatMessages.scrollHeight;
                }
            }, 1500);
        }

        // Send message function
        function sendMessage() {
            const message = chatInput.value.trim();
            if (!message) return;
            
            // Add user message to chat
            addMessage(message, 'user');
            chatInput.value = '';
            
            // Show typing indicator
            typingIndicator.style.display = 'flex';
            
            // Simulate AI thinking
            setTimeout(() => {
                typingIndicator.style.display = 'none';
                
                // Find the best response
                const lowerMessage = message.toLowerCase();
                let response = knowledgeBase['default'].response;
                let followUp = [];
                
                for (const [key, value] of Object.entries(knowledgeBase)) {
                    if (lowerMessage.includes(key.toLowerCase())) {
                        response = value.response;
                        followUp = value.followUp || [];
                        break;
                    }
                }
                
                // Add AI response
                addMessage(response, 'ai');
                
                // Add follow-up questions if available
                if (followUp.length > 0) {
                    const followUpDiv = document.createElement('div');
                    followUpDiv.className = 'follow-up-questions';
                    followUpDiv.style.marginTop = '10px';
                    followUpDiv.style.display = 'flex';
                    followUpDiv.style.flexWrap = 'wrap';
                    followUpDiv.style.gap = '5px';
                    
                    followUp.forEach(question => {
                        const btn = document.createElement('button');
                        btn.textContent = question;
                        btn.className = 'follow-up-btn';
                        btn.style.padding = '5px 10px';
                        btn.style.backgroundColor = '#f1f0f0';
                        btn.style.border = 'none';
                        btn.style.borderRadius = '4px';
                        btn.style.cursor = 'pointer';
                        btn.style.fontSize = '0.9rem';
                        
                        btn.addEventListener('click', () => {
                            chatInput.value = question;
                            sendMessage();
                        });
                        
                        followUpDiv.appendChild(btn);
                    });
                    
                    document.querySelector('.chat-messages').appendChild(followUpDiv);
                }
                
                // Scroll to bottom
                chatMessages.scrollTop = chatMessages.scrollHeight;
            }, 1500);
        }
        
        // Add message to chat
        function addMessage(content, sender) {
            const messageDiv = document.createElement('div');
            messageDiv.className = `message ${sender}`;
            
            const contentDiv = document.createElement('div');
            contentDiv.className = 'message-content';
            contentDiv.textContent = content;
            
            messageDiv.appendChild(contentDiv);
            chatMessages.appendChild(messageDiv);
            
            // Scroll to bottom
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }
        
        // Event listeners for chat
        sendBtn.addEventListener('click', sendMessage);
        chatInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                sendMessage();
            }
        });
        
        // Initialize
        loadQuizzes();
        switchTab('learn');
    </script>
</body>
</html>
