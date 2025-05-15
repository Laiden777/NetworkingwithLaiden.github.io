<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NetworkingwithLaiden - AI Networking Classroom</title>
    <style>
        :root {
            --primary: #3498db;
            --secondary: #2980b9;
            --accent: #e74c3c;
            --light: #ecf0f1;
            --dark: #2c3e50;
            --success: #2ecc71;
            --warning: #f39c12;
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

        h1, h2, h3, h4 {
            margin-bottom: 1rem;
            color: var(--dark);
        }

        header {
            background-color: var(--primary);
            color: white;
            padding: 1rem;
            text-align: center;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        header h1 {
            color: white;
            margin-bottom: 0.5rem;
        }

        nav {
            background-color: var(--secondary);
            padding: 0.5rem;
            display: flex;
            justify-content: center;
        }

        nav button {
            background-color: transparent;
            border: none;
            color: white;
            padding: 0.5rem 1rem;
            margin: 0 0.5rem;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        nav button:hover {
            background-color: rgba(255,255,255,0.1);
        }

        nav button.active {
            background-color: rgba(255,255,255,0.2);
            font-weight: bold;
        }

        main {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 1rem;
        }

        .section {
            display: none;
            background-color: white;
            border-radius: 8px;
            padding: 2rem;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            margin-bottom: 2rem;
        }

        .section.active {
            display: block;
        }

        .topic-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 1.5rem;
        }

        .topic-card {
            background-color: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            transition: transform 0.3s, box-shadow 0.3s;
            cursor: pointer;
        }

        .topic-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .topic-card-header {
            background-color: var(--primary);
            color: white;
            padding: 1rem;
        }

        .topic-card-body {
            padding: 1rem;
        }

        .topic-card-footer {
            padding: 1rem;
            background-color: var(--light);
            text-align: right;
        }

        .lesson-content {
            margin-bottom: 2rem;
        }

        .lesson-navigation {
            display: flex;
            justify-content: space-between;
            margin-top: 2rem;
        }

        button {
            background-color: var(--primary);
            color: white;
            border: none;
            padding: 0.5rem 1rem;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: var(--secondary);
        }

        button.secondary {
            background-color: var(--light);
            color: var(--dark);
        }

        button.secondary:hover {
            background-color: #dfe6e9;
        }

        #chat-container {
            display: flex;
            flex-direction: column;
            height: 500px;
            border: 1px solid #ddd;
            border-radius: 8px;
            overflow: hidden;
        }

        #chat-messages {
            flex-grow: 1;
            padding: 1rem;
            overflow-y: auto;
            background-color: #f9f9f9;
        }

        .message {
            margin-bottom: 1rem;
            padding: 0.8rem;
            border-radius: 8px;
            max-width: 80%;
        }

        .user-message {
            background-color: var(--primary);
            color: white;
            align-self: flex-end;
            margin-left: auto;
        }

        .ai-message {
            background-color: #e9e9e9;
            color: var(--dark);
        }

        #chat-input-container {
            display: flex;
            padding: 1rem;
            background-color: white;
            border-top: 1px solid #ddd;
        }

        #chat-input {
            flex-grow: 1;
            padding: 0.8rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            margin-right: 0.5rem;
        }

        .quiz-container {
            margin-bottom: 2rem;
        }

        .quiz-question {
            margin-bottom: 1.5rem;
            padding: 1rem;
            background-color: var(--light);
            border-radius: 8px;
        }

        .quiz-options {
            list-style-type: none;
        }

        .quiz-option {
            padding: 0.8rem;
            margin-bottom: 0.5rem;
            background-color: white;
            border: 1px solid #ddd;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .quiz-option:hover {
            background-color: #f1f1f1;
        }

        .quiz-option.selected {
            background-color: var(--primary);
            color: white;
        }

        .quiz-option.correct {
            background-color: var(--success);
            color: white;
        }

        .quiz-option.incorrect {
            background-color: var(--accent);
            color: white;
        }

        #notes-container {
            display: flex;
            flex-direction: column;
            height: 100%;
        }

        #notes-list {
            margin-bottom: 1rem;
        }

        .note-card {
            padding: 1rem;
            background-color: var(--light);
            border-radius: 8px;
            margin-bottom: 1rem;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .note-card:hover {
            background-color: #dfe6e9;
        }

        .note-card h3 {
            margin-bottom: 0.5rem;
        }

        .note-card p {
            color: #636e72;
        }

        #note-editor {
            display: flex;
            flex-direction: column;
        }

        #note-title {
            padding: 0.8rem;
            margin-bottom: 1rem;
            border: 1px solid #ddd;
            border-radius: 4px;
        }

        #note-content {
            padding: 0.8rem;
            margin-bottom: 1rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            min-height: 200px;
            resize: vertical;
        }

        .grid-container {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 2rem;
        }

        @media (max-width: 768px) {
            .grid-container {
                grid-template-columns: 1fr;
            }
            
            nav {
                flex-wrap: wrap;
            }
            
            nav button {
                margin-bottom: 0.5rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>NetworkingwithLaiden: AI Networking Classroom</h1>
        <p>Learn computer networking concepts with AI-powered instruction</p>
    </header>
    
    <nav>
        <button id="nav-home" class="active">Home</button>
        <button id="nav-learn">Learn</button>
        <button id="nav-test">Tests & Quizzes</button>
        <button id="nav-notes">My Notes</button>
        <button id="nav-chat">AI Chat</button>
    </nav>
    
    <main>
        <!-- Home Section -->
        <section id="home-section" class="section active">
            <h2>Welcome to NetLearn</h2>
            <p>Your AI-powered classroom for learning computer networking concepts</p>
            
            <div class="topic-list">
                <div class="topic-card" onclick="navigateTo('learn')">
                    <div class="topic-card-header">
                        <h3>Learning Center</h3>
                    </div>
                    <div class="topic-card-body">
                        <p>Access interactive lessons covering all aspects of computer networking.</p>
                    </div>
                    <div class="topic-card-footer">
                        <button>Start Learning</button>
                    </div>
                </div>
                
                <div class="topic-card" onclick="navigateTo('test')">
                    <div class="topic-card-header">
                        <h3>Tests & Quizzes</h3>
                    </div>
                    <div class="topic-card-body">
                        <p>Test your knowledge with interactive quizzes based on what you've learned.</p>
                    </div>
                    <div class="topic-card-footer">
                        <button>Take a Quiz</button>
                    </div>
                </div>
                
                <div class="topic-card" onclick="navigateTo('notes')">
                    <div class="topic-card-header">
                        <h3>My Notes</h3>
                    </div>
                    <div class="topic-card-body">
                        <p>Keep track of what you've learned with a personal note-taking system.</p>
                    </div>
                    <div class="topic-card-footer">
                        <button>Open Notes</button>
                    </div>
                </div>
                
                <div class="topic-card" onclick="navigateTo('chat')">
                    <div class="topic-card-header">
                        <h3>AI Chat Assistant</h3>
                    </div>
                    <div class="topic-card-body">
                        <p>Have questions? Chat with our AI assistant for immediate help with networking concepts.</p>
                    </div>
                    <div class="topic-card-footer">
                        <button>Start Chatting</button>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Learn Section -->
        <section id="learn-section" class="section">
            <h2>Learning Center</h2>
            
            <div id="topic-selection">
                <h3>Select a topic to begin learning</h3>
                
                <div class="topic-list">
                    <div class="topic-card" onclick="loadLesson('intro')">
                        <div class="topic-card-header">
                            <h3>Introduction to Networking</h3>
                        </div>
                        <div class="topic-card-body">
                            <p>Learn the fundamentals of computer networks and why they matter.</p>
                        </div>
                    </div>
                    
                    <div class="topic-card" onclick="loadLesson('osi')">
                        <div class="topic-card-header">
                            <h3>OSI Model</h3>
                        </div>
                        <div class="topic-card-body">
                            <p>Understand the 7-layer OSI model that standardizes network communications.</p>
                        </div>
                    </div>
                    
                    <div class="topic-card" onclick="loadLesson('tcp-ip')">
                        <div class="topic-card-header">
                            <h3>TCP/IP Protocol Suite</h3>
                        </div>
                        <div class="topic-card-body">
                            <p>Explore the protocols that power the internet and modern networks.</p>
                        </div>
                    </div>
                    
                    <div class="topic-card" onclick="loadLesson('routing')">
                        <div class="topic-card-header">
                            <h3>Routing & Switching</h3>
                        </div>
                        <div class="topic-card-body">
                            <p>Learn how data finds its way across networks and between devices.</p>
                        </div>
                    </div>
                    
                    <div class="topic-card" onclick="loadLesson('security')">
                        <div class="topic-card-header">
                            <h3>Network Security</h3>
                        </div>
                        <div class="topic-card-body">
                            <p>Discover essential security concepts for protecting network infrastructure.</p>
                        </div>
                    </div>
                    
                    <div class="topic-card" onclick="loadLesson('wireless')">
                        <div class="topic-card-header">
                            <h3>Wireless Networks</h3>
                        </div>
                        <div class="topic-card-body">
                            <p>Understand Wi-Fi and other wireless networking technologies.</p>
                        </div>
                    </div>
                </div>
            </div>
            
            <div id="lesson-content" style="display: none;">
                <div id="lesson-title">
                    <h3>Lesson Title</h3>
                </div>
                
                <div id="lesson-body" class="lesson-content">
                    <!-- Lesson content will be loaded here -->
                </div>
                
                <div class="lesson-navigation">
                    <button onclick="showTopicSelection()" class="secondary">Back to Topics</button>
                    <button onclick="completeLesson()">Complete & Continue</button>
                </div>
            </div>
        </section>
        
        <!-- Tests & Quizzes Section -->
        <section id="test-section" class="section">
            <h2>Tests & Quizzes</h2>
            
            <div id="quiz-selection">
                <h3>Select a quiz to test your knowledge</h3>
                
                <div class="topic-list">
                    <div class="topic-card" onclick="loadQuiz('intro-quiz')">
                        <div class="topic-card-header">
                            <h3>Introduction to Networking</h3>
                        </div>
                        <div class="topic-card-body">
                            <p>Test your knowledge of network fundamentals.</p>
                        </div>
                    </div>
                    
                    <div class="topic-card" onclick="loadQuiz('osi-quiz')">
                        <div class="topic-card-header">
                            <h3>OSI Model</h3>
                        </div>
                        <div class="topic-card-body">
                            <p>Verify your understanding of the 7-layer model.</p>
                        </div>
                    </div>
                    
                    <div class="topic-card" onclick="loadQuiz('tcp-ip-quiz')">
                        <div class="topic-card-header">
                            <h3>TCP/IP Quiz</h3>
                        </div>
                        <div class="topic-card-body">
                            <p>Test your knowledge of internet protocols.</p>
                        </div>
                    </div>
                    
                    <div class="topic-card" onclick="loadQuiz('routing-quiz')">
                        <div class="topic-card-header">
                            <h3>Routing & Switching</h3>
                        </div>
                        <div class="topic-card-body">
                            <p>Challenge yourself on network routing concepts.</p>
                        </div>
                    </div>
                    
                    <div class="topic-card" onclick="loadQuiz('security-quiz')">
                        <div class="topic-card-header">
                            <h3>Network Security</h3>
                        </div>
                        <div class="topic-card-body">
                            <p>Test your network security knowledge.</p>
                        </div>
                    </div>
                    
                    <div class="topic-card" onclick="loadQuiz('wireless-quiz')">
                        <div class="topic-card-header">
                            <h3>Wireless Networks</h3>
                        </div>
                        <div class="topic-card-body">
                            <p>Evaluate your understanding of wireless technologies.</p>
                        </div>
                    </div>
                </div>
            </div>
            
            <div id="quiz-container" style="display: none;">
                <div id="quiz-title">
                    <h3>Quiz Title</h3>
                </div>
                
                <div id="quiz-progress">
                    Question <span id="current-question">1</span> of <span id="total-questions">10</span>
                </div>
                
                <div id="quiz-content" class="quiz-container">
                    <!-- Quiz content will be loaded here -->
                </div>
                
                <div class="lesson-navigation">
                    <button onclick="showQuizSelection()" class="secondary">Back to Quizzes</button>
                    <button id="next-question" onclick="nextQuestion()">Next Question</button>
                    <button id="finish-quiz" style="display: none;" onclick="finishQuiz()">Finish Quiz</button>
                </div>
            </div>
            
            <div id="quiz-results" style="display: none;">
                <h3>Quiz Results</h3>
                <div id="results-content">
                    <!-- Results will be shown here -->
                </div>
                <div class="lesson-navigation">
                    <button onclick="showQuizSelection()" class="secondary">Back to Quizzes</button>
                </div>
            </div>
        </section>
        
        <!-- Notes Section -->
        <section id="notes-section" class="section">
            <h2>My Notes</h2>
            
            <div class="grid-container">
                <div id="notes-sidebar">
                    <button onclick="createNewNote()" style="width: 100%; margin-bottom: 1rem;">Create New Note</button>
                    
                    <h3>My Saved Notes</h3>
                    <div id="notes-list">
                        <!-- Notes list will be populated here -->
                    </div>
                </div>
                
                <div id="note-editor">
                    <input type="text" id="note-title" placeholder="Note Title">
                    <textarea id="note-content" placeholder="Write your notes here..."></textarea>
                    
                    <div style="display: flex; justify-content: space-between;">
                        <button class="secondary" onclick="cancelNote()">Cancel</button>
                        <button onclick="saveNote()">Save Note</button>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Chat Section -->
        <section id="chat-section" class="section">
            <h2>AI Chat Assistant</h2>
            <p>Ask our AI teacher any questions about computer networking</p>
            
            <div id="chat-container">
                <div id="chat-messages">
                    <div class="message ai-message">
                        Hello! I'm NetLearn's AI assistant. I'm here to help you with any networking questions you might have. What would you like to learn about today?
                    </div>
                </div>
                
                <div id="chat-input-container">
                    <input type="text" id="chat-input" placeholder="Type your question here...">
                    <button onclick="sendMessage()">Send</button>
                </div>
            </div>
        </section>
    </main>

    <script>
        // Navigation
        const navButtons = document.querySelectorAll('nav button');
        const sections = document.querySelectorAll('.section');
        
        function navigateTo(section) {
            // Deactivate all sections and nav buttons
            sections.forEach(s => s.classList.remove('active'));
            navButtons.forEach(b => b.classList.remove('active'));
            
            // Activate the requested section and nav button
            document.getElementById(`${section}-section`).classList.add('active');
            document.getElementById(`nav-${section}`).classList.add('active');
        }
        
        navButtons.forEach(button => {
            button.addEventListener('click', function() {
                const section = this.id.replace('nav-', '');
                navigateTo(section);
            });
        });
        
        // Learning Center
        function showTopicSelection() {
            document.getElementById('topic-selection').style.display = 'block';
            document.getElementById('lesson-content').style.display = 'none';
        }
        
        function loadLesson(lessonId) {
            document.getElementById('topic-selection').style.display = 'none';
            document.getElementById('lesson-content').style.display = 'block';
            
            // Content for each lesson
            const lessons = {
                'intro': {
                    title: 'Introduction to Computer Networks',
                    content: `
                        <h3>What is a Computer Network?</h3>
                        <p>A computer network is a collection of computing devices that are connected together to communicate and share resources. These connections can be physical (like cables) or wireless (like Wi-Fi or Bluetooth).</p>
                        
                        <h3>Why Do We Need Networks?</h3>
                        <p>Networks allow us to:</p>
                        <ul>
                            <li>Share resources like printers and files</li>
                            <li>Communicate through email, messaging, and video calls</li>
                            <li>Access services and information from anywhere in the world</li>
                            <li>Play multiplayer games and collaborate on projects</li>
                        </ul>
                        
                        <h3>Types of Networks</h3>
                        <h4>Based on Scale:</h4>
                        <ul>
                            <li><strong>LAN (Local Area Network)</strong>: Connects devices in a limited area like a home, office, or building</li>
                            <li><strong>WAN (Wide Area Network)</strong>: Spans a large geographical area, often connecting multiple LANs</li>
                            <li><strong>MAN (Metropolitan Area Network)</strong>: Larger than a LAN but smaller than a WAN, typically spanning a city</li>
                            <li><strong>PAN (Personal Area Network)</strong>: Connects personal devices within close proximity</li>
                        </ul>
                        
                        <h4>Based on Architecture:</h4>
                        <ul>
                            <li><strong>Client-Server</strong>: Centralized servers provide services to client computers</li>
                            <li><strong>Peer-to-Peer</strong>: All devices have equal capabilities and responsibilities</li>
                        </ul>
                        
                        <h3>Network Components</h3>
                        <ul>
                            <li><strong>Nodes</strong>: Any device connected to the network (computers, servers, IoT devices)</li>
                            <li><strong>Network Interfaces</strong>: Hardware that connects devices to the network</li>
                            <li><strong>Transmission Media</strong>: The physical connections (cables, wireless signals)</li>
                            <li><strong>Switches & Routers</strong>: Devices that direct traffic within and between networks</li>
                            <li><strong>Protocols</strong>: Rules that govern how data is formatted and transmitted</li>
                        </ul>
                        
                        <h3>The Internet: The Network of Networks</h3>
                        <p>The Internet is a global system of interconnected computer networks that use standardized communication protocols (primarily TCP/IP) to connect devices worldwide. It enables services like the World Wide Web, email, file sharing, and more.</p>
                    `
                },
                'osi': {
                    title: 'The OSI Model',
                    content: `
                        <h3>What is the OSI Model?</h3>
                        <p>The Open Systems Interconnection (OSI) model is a conceptual framework used to understand network interactions. It divides network communication into seven distinct layers, each handling specific functions.</p>
                        
                        <h3>The Seven Layers</h3>
                        
                        <h4>7. Application Layer</h4>
                        <p><strong>Function:</strong> Provides network services directly to user applications</p>
                        <p><strong>Protocols:</strong> HTTP, FTP, SMTP, DNS, Telnet</p>
                        <p><strong>PDU (Protocol Data Unit):</strong> Data</p>
                        <p><strong>Example:</strong> When you use a web browser, the application layer handles the HTTP protocol.</p>
                        
                        <h4>6. Presentation Layer</h4>
                        <p><strong>Function:</strong> Translates data between application format and network format, handles encryption/decryption, compression</p>
                        <p><strong>Protocols:</strong> SSL/TLS, JPEG, MPEG, ASCII, Unicode</p>
                        <p><strong>PDU:</strong> Data</p>
                        <p><strong>Example:</strong> Converting an image into a format suitable for transmission.</p>
                        
                        <h4>5. Session Layer</h4>
                        <p><strong>Function:</strong> Establishes, manages, and terminates connections between applications</p>
                        <p><strong>Protocols:</strong> NetBIOS, RPC, SIP</p>
                        <p><strong>PDU:</strong> Data</p>
                        <p><strong>Example:</strong> Managing the communication session for a video call.</p>
                        
                        <h4>4. Transport Layer</h4>
                        <p><strong>Function:</strong> Provides reliable data transfer, segmentation, flow control, and error correction</p>
                        <p><strong>Protocols:</strong> TCP, UDP</p>
                        <p><strong>PDU:</strong> Segment (TCP) or Datagram (UDP)</p>
                        <p><strong>Example:</strong> Ensuring all parts of an email arrive completely and in order.</p>
                        
                        <h4>3. Network Layer</h4>
                        <p><strong>Function:</strong> Handles logical addressing, routing, and traffic control</p>
                        <p><strong>Protocols:</strong> IP, ICMP, OSPF, BGP</p>
                        <p><strong>PDU:</strong> Packet</p>
                        <p><strong>Example:</strong> Determining the best path for data to travel from your computer to a website's server.</p>
                        
                        <h4>2. Data Link Layer</h4>
                        <p><strong>Function:</strong> Provides node-to-node data transfer, handles physical addressing, error detection, and flow control</p>
                        <p><strong>Protocols:</strong> Ethernet, PPP, Frame Relay, HDLC</p>
                        <p><strong>PDU:</strong> Frame</p>
                        <p><strong>Example:</strong> Wi-Fi transmitting data between your laptop and router.</p>
                        
                        <h4>1. Physical Layer</h4>
                        <p><strong>Function:</strong> Transmits raw bit stream over physical medium, defines hardware specifications</p>
                        <p><strong>Protocols:</strong> USB, Bluetooth, IEEE 802.11, DSL</p>
                        <p><strong>PDU:</strong> Bit</p>
                        <p><strong>Example:</strong> The electrical signals traveling through an Ethernet cable.</p>
                        
                        <h3>Data Encapsulation</h3>
                        <p>As data travels down the OSI layers from sender to network:</p>
                        <ol>
                            <li>Each layer adds its own header (and sometimes trailer) to the data</li>
                            <li>This process is called encapsulation</li>
                            <li>At the receiving end, each layer removes its corresponding header/trailer (decapsulation)</li>
                        </ol>
                        
                        <h3>Why is the OSI Model Important?</h3>
                        <ul>
                            <li>Standardizes components and interfaces for compatibility</li>
                            <li>Simplifies troubleshooting by isolating network problems to specific layers</li>
                            <li>Facilitates modular engineering of network systems</li>
                            <li>Provides a common language for networking professionals</li>
                        </ul>
                    `
                },
                'tcp-ip': {
                    title: 'TCP/IP Protocol Suite',
                    content: `
                        <h3>What is TCP/IP?</h3>
                        <p>The Transmission Control Protocol/Internet Protocol (TCP/IP) is the foundational communication protocol suite of the Internet. Unlike the theoretical OSI model, TCP/IP is a practical implementation used in real-world networking.</p>
                        
                        <h3>The TCP/IP Model Layers</h3>
                        
                        <h4>4. Application Layer</h4>
                        <p><strong>Corresponds to OSI Layers:</strong> 5 (Session), 6 (Presentation), and 7 (Application)</p>
                        <p><strong>Function:</strong> Provides network services to applications</p>
                        <p><strong>Key Protocols:</strong></p>
                        <ul>
                            <li><strong>HTTP/HTTPS:</strong> Web browsing</li>
                            <li><strong>FTP:</strong> File transfer</li>
                            <li><strong>SMTP/POP3/IMAP:</strong> Email</li>
                            <li><strong>DNS:</strong> Domain name resolution</li>
                            <li><strong>SSH:</strong> Secure remote access</li>
                            <li><strong>Telnet:</strong> Remote terminal access</li>
                        </ul>
                        
                        <h4>3. Transport Layer</h4>
                        <p><strong>Corresponds to OSI Layer:</strong> 4 (Transport)</p>
                        <p><strong>Function:</strong> Provides end-to-end communication, reliability, flow control</p>
                        <p><strong>Key Protocols:</strong></p>
