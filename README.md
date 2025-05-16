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
        }
        
        .btn:hover {
            background-color: #e67e22;
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
        }
        
        .message {
            margin-bottom: 1rem;
            display: flex;
        }
        
        .message.user {
            justify-content: flex-end;
        }
        
        .message-content {
            max-width: 70%;
            padding: 0.8rem;
            border-radius: 8px;
            box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
        }
        
        .message.ai .message-content {
            background-color: #f1f0f0;
        }
        
        .message.user .message-content {
            background-color: var(--primary);
            color: white;
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
            
            .footer-content {
                flex-direction: column;
            }
            
            .footer-links {
                margin-top: 1rem;
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
                <a href="#" class="btn start-learning-btn">Start Learning Now</a>
            </div>
            <div class="hero-image">
                <img src="/api/placeholder/500/300" alt="Network Classroom" />
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
                <div class="module-card">
                    <div class="module-image" style="background-color: #3498db;">
                        Network Fundamentals
                    </div>
                    <div class="module-content">
                        <h3>Network Fundamentals</h3>
                        <p>Learn the core concepts of computer networking including OSI model, TCP/IP, and basic network topologies.</p>
                        <a href="#" class="btn">Start Learning</a>
                    </div>
                </div>
                <div class="module-card">
                    <div class="module-image" style="background-color: #e74c3c;">
                        Routing & Switching
                    </div>
                    <div class="module-content">
                        <h3>Routing & Switching</h3>
                        <p>Understand how data is routed across networks and how switches manage local network traffic.</p>
                        <a href="#" class="btn">Start Learning</a>
                    </div>
                </div>
                <div class="module-card">
                    <div class="module-image" style="background-color: #2ecc71;">
                        Network Security
                    </div>
                    <div class="module-content">
                        <h3>Network Security</h3>
                        <p>Explore essential security concepts including firewalls, encryption, VPNs, and threat detection systems.</p>
                        <a href="#" class="btn">Start Learning</a>
                    </div>
                </div>
                <div class="module-card">
                    <div class="module-image" style="background-color: #9b59b6;">
                        Wireless Networking
                    </div>
                    <div class="module-content">
                        <h3>Wireless Networking</h3>
                        <p>Master wireless protocols, standards, and security measures for modern wireless networks.</p>
                        <a href="#" class="btn">Start Learning</a>
                    </div>
                </div>
                <div class="module-card">
                    <div class="module-image" style="background-color: #f39c12;">
                        Cloud Networking
                    </div>
                    <div class="module-content">
                        <h3>Cloud Networking</h3>
                        <p>Discover how networking works in cloud environments and best practices for cloud infrastructure.</p>
                        <a href="#" class="btn">Start Learning</a>
                    </div>
                </div>
                <div class="module-card">
                    <div class="module-image" style="background-color: #1abc9c;">
                        Network Automation
                    </div>
                    <div class="module-content">
                        <h3>Network Automation</h3>
                        <p>Learn how to automate network tasks using scripting, APIs, and infrastructure as code.</p>
                        <a href="#" class="btn">Start Learning</a>
                    </div>
                </div>
            </div>
        </div>
        
        <div id="quiz" class="tab-content">
            <h2 class="section-title">Tests & Quizzes</h2>
            <div class="quiz-list">
                <div class="quiz-card">
                    <h3>Network Fundamentals Quiz</h3>
                    <div class="quiz-meta">
                        <span>10 questions</span>
                        <span>15 minutes</span>
                    </div>
                    <p>Test your understanding of basic networking concepts, protocols, and the OSI model.</p>
                    <a href="#" class="btn">Start Quiz</a>
                </div>
                <div class="quiz-card">
                    <h3>IP Addressing & Subnetting</h3>
                    <div class="quiz-meta">
                        <span>15 questions</span>
                        <span>20 minutes</span>
                    </div>
                    <p>Challenge yourself with questions on IP addressing, subnetting, and CIDR notation.</p>
                    <a href="#" class="btn">Start Quiz</a>
                </div>
                <div class="quiz-card">
                    <h3>Routing Protocols Test</h3>
                    <div class="quiz-meta">
                        <span>12 questions</span>
                        <span>18 minutes</span>
                    </div>
                    <p>Evaluate your knowledge of various routing protocols like OSPF, EIGRP, and BGP.</p>
                    <a href="#" class="btn">Start Quiz</a>
                </div>
                <div class="quiz-card">
                    <h3>Network Security Assessment</h3>
                    <div class="quiz-meta">
                        <span>20 questions</span>
                        <span>30 minutes</span>
                    </div>
                    <p>Test your understanding of network security principles, tools, and best practices.</p>
                    <a href="#" class="btn">Start Quiz</a>
                </div>
                <div class="quiz-card">
                    <h3>Wireless Networking Quiz</h3>
                    <div class="quiz-meta">
                        <span>15 questions</span>
                        <span>20 minutes</span>
                    </div>
                    <p>Demonstrate your knowledge of wireless standards, protocols, and security measures.</p>
                    <a href="#" class="btn">Start Quiz</a>
                </div>
                <div class="quiz-card">
                    <h3>Final Certification Exam</h3>
                    <div class="quiz-meta">
                        <span>50 questions</span>
                        <span>90 minutes</span>
                    </div>
                    <p>Comprehensive exam covering all aspects of networking to earn your NetLearn certification.</p>
                    <a href="#" class="btn">Start Exam</a>
                </div>
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
                    <div class="message user">
                        <div class="message-content">
                            What's the difference between TCP and UDP?
                        </div>
                    </div>
                    <div class="message ai">
                        <div class="message-content">
                            Great question! TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are both transport layer protocols, but they work differently:
                            <br><br>
                            <strong>TCP:</strong>
                            <br>- Connection-oriented protocol
                            <br>- Guarantees delivery of data packets
                            <br>- Performs error checking and recovery
                            <br>- Maintains packet sequence
                            <br>- Examples: Web browsing (HTTP), email (SMTP), file transfers (FTP)
                            <br><br>
                            <strong>UDP:</strong>
                            <br>- Connectionless protocol
                            <br>- No guarantee of delivery
                            <br>- No error recovery
                            <br>- Faster than TCP due to less overhead
                            <br>- Examples: Video streaming, online gaming, DNS lookups
                            <br><br>
                            Would you like me to explain more about when to use each protocol?
                        </div>
                    </div>
                </div>
                <div class="chat-input-container">
                    <input type="text" class="chat-input" placeholder="Type your networking question here...">
                    <button class="chat-send-btn">Send</button>
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
        document.addEventListener('DOMContentLoaded', function() {
            // Tab functionality
            const tabButtons = document.querySelectorAll('.tab-btn');
            const navLinks = document.querySelectorAll('.nav-link');
            const tabContents = document.querySelectorAll('.tab-content');
            
            // Function to switch tabs
            function switchTab(tabId) {
                // Hide all tab contents
                tabContents.forEach(content => {
                    content.classList.remove('active');
                });
                
                // Deactivate all tab buttons
                tabButtons.forEach(button => {
                    button.classList.remove('active');
                });
                
                // Deactivate all nav links
                navLinks.forEach(link => {
                    link.classList.remove('active');
                });
                
                // Show the selected tab content
                document.getElementById(tabId).classList.add('active');
                
                // Activate the corresponding tab button
                document.querySelector(`.tab-btn[data-tab="${tabId}"]`).classList.add('active');
                
                // Activate the corresponding nav link
                document.querySelector(`.nav-link[data-tab="${tabId}"]`).classList.add('active');
            }
            
            // Add click event to tab buttons
            tabButtons.forEach(button => {
                button.addEventListener('click', function() {
                    const tabId = this.getAttribute('data-tab');
                    switchTab(tabId);
                });
            });
            
            // Add click event to nav links
            navLinks.forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    const tabId = this.getAttribute('data-tab');
                    switchTab(tabId);
                });
            });
            
            // Add click event to "Start Learning Now" button
            document.querySelector('.start-learning-btn').addEventListener('click', function(e) {
                e.preventDefault();
                switchTab('learn');
            });
            
            // Note item selection
            const noteItems = document.querySelectorAll('.note-item');
            const noteTitle = document.querySelector('.note-title');
            const noteContent = document.querySelector('.note-content');
            
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
- Last usable host: Broadcast address - 1`,
                "Routing Protocol Comparison": `# Routing Protocol Comparison

## Distance Vector Protocols
- RIP (Routing Information Protocol)
  - Uses hop count as metric
  - Maximum 15 hops
  - Slow convergence
  - Simple to configure

- EIGRP (Enhanced Interior Gateway Routing Protocol)
  - Cisco proprietary
  - Uses bandwidth and delay as metrics
  - Fast convergence
  - Supports VLSM

## Link State Protocols
- OSPF (Open Shortest Path First)
  - Uses cost as metric (based on bandwidth)
  - Fast convergence
  - Hierarchical design with areas
  - Supports VLSM

- IS-IS (Intermediate System to Intermediate System)
  - Similar to OSPF but for ISPs
  - Uses cost as metric
  - Supports IPv4 and IPv6

## Path Vector Protocol
- BGP (Border Gateway Protocol)
  - Used between autonomous systems
  - Uses path attributes for routing decisions
  - Very scalable
  - Complex configuration`,
                "Network Security Best Practices": `# Network Security Best Practices

## Access Control
- Implement principle of least privilege
- Use strong authentication (MFA)
- Regularly review user permissions
- Disable unused accounts

## Network Segmentation
- Use VLANs to separate traffic
- Implement DMZ for public-facing services
- Separate sensitive data networks
- Use micro-segmentation where possible

## Monitoring & Logging
- Implement SIEM system
- Monitor for unusual traffic patterns
- Keep logs for at least 90 days
- Set up alerts for security events

## Patch Management
- Keep all systems updated
- Have a vulnerability management process
- Test patches before deployment
- Maintain an asset inventory

## Encryption
- Use TLS for all web traffic
- Encrypt sensitive data at rest
- Use VPNs for remote access
- Implement IPsec where appropriate`,
                "Wireless Standards Overview": `# Wireless Standards Overview

## 802.11 Standards
- 802.11a: 5 GHz, 54 Mbps
- 802.11b: 2.4 GHz, 11 Mbps
- 802.11g: 2.4 GHz, 54 Mbps
- 802.11n (Wi-Fi 4): 2.4/5 GHz, 600 Mbps
- 802.11ac (Wi-Fi 5): 5 GHz, 6.9 Gbps
- 802.11ax (Wi-Fi 6): 2.4/5 GHz, 9.6 Gbps

## Security Protocols
- WEP (Weak, avoid)
- WPA (TKIP encryption)
- WPA2 (AES encryption, current standard)
- WPA3 (Latest standard, more secure)

## Best Practices
- Use WPA2 or WPA3 encryption
- Disable WPS
- Change default admin credentials
- Use strong passphrases (12+ characters)
- Hide SSID if possible
- Implement MAC filtering for additional security
- Place APs strategically for optimal coverage`
            };
            
            noteItems.forEach(item => {
                item.addEventListener('click', function() {
                    // Remove active class from all notes
                    noteItems.forEach(note => {
                        note.classList.remove('active');
                    });
                    
                    // Add active class to clicked note
                    this.classList.add('active');
                    
                    // Update note content
                    const noteName = this.textContent;
                    noteTitle.value = noteName;
                    noteContent.value = noteContents[noteName] || '';
                });
            });
            
            // Initialize with first tab active
            switchTab('learn');
        });
    </script>
</body>
</html>
