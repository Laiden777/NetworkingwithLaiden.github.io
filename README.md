<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Networking Academy - Virtual Classroom</title>
    <style>
        :root {
            --primary: #4a6fa5;
            --secondary: #166088;
            --accent: #4fc3f7;
            --light: #f5f9ff;
            --dark: #172b4d;
            --success: #66bb6a;
            --warning: #ffa726;
            --danger: #ef5350;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f0f2f5;
            color: var(--dark);
        }
        
        .container {
            display: flex;
            min-height: 100vh;
        }
        
        /* Sidebar styles */
        .sidebar {
            width: 250px;
            background-color: var(--dark);
            color: white;
            padding: 20px 0;
            display: flex;
            flex-direction: column;
            transition: all 0.3s;
        }
        
        .logo {
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 10px 20px;
            margin-bottom: 20px;
            border-bottom: 1px solid rgba(255,255,255,0.1);
        }
        
        .logo h2 {
            font-size: 1.2rem;
            margin-left: 10px;
        }
        
        .nav-item {
            padding: 12px 20px;
            display: flex;
            align-items: center;
            cursor: pointer;
            transition: background 0.3s;
        }
        
        .nav-item:hover, .nav-item.active {
            background-color: rgba(255,255,255,0.1);
        }
        
        .nav-item i {
            margin-right: 10px;
            font-size: 1.2rem;
        }
        
        /* Main content styles */
        .main-content {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
        }
        
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 1px solid #ddd;
        }
        
        .header h1 {
            font-size: 1.8rem;
            color: var(--dark);
        }
        
        .user-profile {
            display: flex;
            align-items: center;
            cursor: pointer;
        }
        
        .user-profile img {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            margin-right: 10px;
        }
        
        /* Section styles */
        .section {
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }
        
        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .section-header h2 {
            font-size: 1.4rem;
            color: var(--secondary);
        }
        
        .section-content {
            line-height: 1.6;
        }
        
        /* Card styles */
        .cards {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            grid-gap: 20px;
        }
        
        .card {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            overflow: hidden;
            transition: transform 0.3s, box-shadow 0.3s;
            cursor: pointer;
        }
        
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.12);
        }
        
        .card-img {
            height: 160px;
            background-color: var(--primary);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 3rem;
        }
        
        .card-body {
            padding: 20px;
        }
        
        .card-title {
            font-size: 1.2rem;
            margin-bottom: 10px;
            color: var(--dark);
        }
        
        .card-text {
            color: #666;
            margin-bottom: 15px;
            font-size: 0.9rem;
        }
        
        .progress-bar {
            height: 6px;
            background-color: #e0e0e0;
            border-radius: 3px;
            overflow: hidden;
            margin-bottom: 10px;
        }
        
        .progress {
            height: 100%;
            background-color: var(--accent);
        }
        
        .progress-text {
            font-size: 0.85rem;
            color: #888;
            display: flex;
            justify-content: space-between;
        }
        
        .btn {
            display: inline-block;
            padding: 8px 16px;
            background-color: var(--accent);
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 0.9rem;
            transition: background 0.3s;
            text-decoration: none;
        }
        
        .btn:hover {
            background-color: var(--primary);
        }
        
        .btn-outline {
            background-color: transparent;
            border: 1px solid var(--accent);
            color: var(--accent);
        }
        
        .btn-outline:hover {
            background-color: var(--accent);
            color: white;
        }
        
        /* Chat interface */
        .chat-container {
            display: flex;
            flex-direction: column;
            height: 500px;
            border: 1px solid #ddd;
            border-radius: 8px;
            overflow: hidden;
        }
        
        .chat-header {
            background-color: var(--primary);
            color: white;
            padding: 15px;
            display: flex;
            align-items: center;
        }
        
        .chat-header img {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            margin-right: 10px;
        }
        
        .chat-messages {
            flex: 1;
            padding: 15px;
            overflow-y: auto;
            background-color: #f9f9f9;
        }
        
        .message {
            margin-bottom: 15px;
            max-width: 80%;
        }
        
        .message-content {
            padding: 10px 15px;
            border-radius: 18px;
            display: inline-block;
        }
        
        .user-message {
            margin-left: auto;
        }
        
        .user-message .message-content {
            background-color: var(--accent);
            color: white;
            border-radius: 18px 18px 0 18px;
        }
        
        .bot-message .message-content {
            background-color: #e0e0e0;
            border-radius: 18px 18px 18px 0;
        }
        
        .message-time {
            font-size: 0.75rem;
            color: #888;
            margin-top: 5px;
        }
        
        .chat-input {
            display: flex;
            padding: 10px;
            background-color: white;
            border-top: 1px solid #ddd;
        }
        
        .chat-input input {
            flex: 1;
            padding: 10px 15px;
            border: 1px solid #ddd;
            border-radius: 20px;
            outline: none;
        }
        
        .chat-input button {
            background-color: var(--accent);
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            margin-left: 10px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        /* Notes section */
        .notes-container {
            height: 300px;
        }
        
        .notes-container textarea {
            width: 100%;
            height: 100%;
            padding: 15px;
            border: 1px solid #ddd;
            border-radius: 8px;
            resize: none;
            outline: none;
            font-size: 0.95rem;
            line-height: 1.5;
        }
        
        /* Quiz styles */
        .quiz-container {
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }
        
        .question {
            margin-bottom: 20px;
        }
        
        .question p {
            font-weight: 500;
            margin-bottom: 10px;
        }
        
        .options {
            list-style-type: none;
        }
        
        .option {
            padding: 10px 15px;
            border: 1px solid #ddd;
            border-radius: 4px;
            margin-bottom: 8px;
            cursor: pointer;
            transition: background 0.3s;
        }
        
        .option:hover {
            background-color: #f9f9f9;
        }
        
        .option.selected {
            background-color: var(--accent);
            color: white;
            border-color: var(--accent);
        }
        
        .option.correct {
            background-color: var(--success);
            color: white;
            border-color: var(--success);
        }
        
        .option.incorrect {
            background-color: var(--danger);
            color: white;
            border-color: var(--danger);
        }
        
        .quiz-controls {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
        }
        
        /* Tab system */
        .tabs {
            display: flex;
            border-bottom: 1px solid #ddd;
            margin-bottom: 20px;
        }
        
        .tab {
            padding: 10px 20px;
            cursor: pointer;
            border-bottom: 2px solid transparent;
            transition: all 0.3s;
        }
        
        .tab:hover {
            background-color: #f5f5f5;
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
        }
        
        /* Status indicators */
        .status {
            display: inline-block;
            padding: 3px 8px;
            border-radius: 10px;
            font-size: 0.75rem;
            margin-left: 10px;
        }
        
        .status-completed {
            background-color: var(--success);
            color: white;
        }
        
        .status-in-progress {
            background-color: var(--warning);
            color: white;
        }
        
        .status-not-started {
            background-color: #e0e0e0;
            color: #666;
        }
        
        /* Hide all pages initially */
        #lessons-page, #quiz-page, #notes-page, #chat-page {
            display: none;
        }
        
        /* Show home page initially */
        #home-page {
            display: block;
        }
        
        /* Font awesome mock */
        .icon {
            width: 16px;
            height: 16px;
            display: inline-block;
            margin-right: 8px;
            background-color: currentColor;
            mask-size: cover;
        }
        
        .icon-home {
            mask: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 576 512'%3E%3Cpath d='M575.8 255.5c0 18-15 32.1-32 32.1h-32l.7 160.2c0 2.7-.2 5.4-.5 8.1V472c0 22.1-17.9 40-40 40H456c-1.1 0-2.2 0-3.3-.1c-1.4 .1-2.8 .1-4.2 .1H416 392c-22.1 0-40-17.9-40-40V448 384c0-17.7-14.3-32-32-32H256c-17.7 0-32 14.3-32 32v64 24c0 22.1-17.9 40-40 40H160 128.1c-1.5 0-3-.1-4.5-.2c-1.2 .1-2.4 .2-3.6 .2H104c-22.1 0-40-17.9-40-40V360c0-.9 0-1.9 .1-2.8V287.6H32c-18 0-32-14-32-32.1c0-9 3-17 10-24L266.4 8c7-7 15-8 22-8s15 2 21 7L564.8 231.5c8 7 12 15 11 24z'/%3E%3C/svg%3E");
        }
        
        .icon-book {
            mask: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 448 512'%3E%3Cpath d='M96 0C43 0 0 43 0 96V416c0 53 43 96 96 96H384h32c17.7 0 32-14.3 32-32s-14.3-32-32-32V384c17.7 0 32-14.3 32-32V32c0-17.7-14.3-32-32-32H384 96zm0 384H352v64H96c-17.7 0-32-14.3-32-32s14.3-32 32-32zm32-240c0-8.8 7.2-16 16-16H336c8.8 0 16 7.2 16 16s-7.2 16-16 16H144c-8.8 0-16-7.2-16-16zm16 48H336c8.8 0 16 7.2 16 16s-7.2 16-16 16H144c-8.8 0-16-7.2-16-16s7.2-16 16-16z'/%3E%3C/svg%3E");
        }
        
        .icon-quiz {
            mask: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 512 512'%3E%3Cpath d='M495.9 166.6c3.2 8.7 .5 18.4-6.4 24.6l-43.3 39.4c1.1 8.3 1.7 16.8 1.7 25.4s-.6 17.1-1.7 25.4l43.3 39.4c6.9 6.2 9.6 15.9 6.4 24.6c-4.4 11.9-9.7 23.3-15.8 34.3l-4.7 8.1c-6.6 11-14 21.4-22.1 31.2c-5.9 7.2-15.7 9.6-24.5 6.8l-55.7-17.7c-13.4 10.3-28.2 18.9-44 25.4l-12.5 57.1c-2 9.1-9 16.3-18.2 17.8c-13.8 2.3-28 3.5-42.5 3.5s-28.7-1.2-42.5-3.5c-9.2-1.5-16.2-8.7-18.2-17.8l-12.5-57.1c-15.8-6.5-30.6-15.1-44-25.4L83.1 425.9c-8.8 2.8-18.6 .3-24.5-6.8c-8.1-9.8-15.5-20.2-22.1-31.2l-4.7-8.1c-6.1-11-11.4-22.4-15.8-34.3c-3.2-8.7-.5-18.4 6.4-24.6l43.3-39.4C64.6 273.1 64 264.6 64 256s.6-17.1 1.7-25.4L22.4 191.2c-6.9-6.2-9.6-15.9-6.4-24.6c4.4-11.9 9.7-23.3 15.8-34.3l4.7-8.1c6.6-11 14-21.4 22.1-31.2c5.9-7.2 15.7-9.6 24.5-6.8l55.7 17.7c13.4-10.3 28.2-18.9 44-25.4l12.5-57.1c2-9.1 9-16.3 18.2-17.8C227.3 1.2 241.5 0 256 0s28.7 1.2 42.5 3.5c9.2 1.5 16.2 8.7 18.2 17.8l12.5 57.1c15.8 6.5 30.6 15.1 44 25.4l55.7-17.7c8.8-2.8 18.6-.3 24.5 6.8c8.1 9.8 15.5 20.2 22.1 31.2l4.7 8.1c6.1 11 11.4 22.4 15.8 34.3zM256 336a80 80 0 1 0 0-160 80 80 0 1 0 0 160z'/%3E%3C/svg%3E");
        }
        
        .icon-notes {
            mask: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 384 512'%3E%3Cpath d='M280 64h40c35.3 0 64 28.7 64 64V448c0 35.3-28.7 64-64 64H64c-35.3 0-64-28.7-64-64V128C0 92.7 28.7 64 64 64h40 9.6C121 27.5 153.3 0 192 0s71 27.5 78.4 64H280zM64 112c-8.8 0-16 7.2-16 16V448c0 8.8 7.2 16 16 16H320c8.8 0 16-7.2 16-16V128c0-8.8-7.2-16-16-16H304v24c0 13.3-10.7 24-24 24H192 104c-13.3 0-24-10.7-24-24V112H64zm128-8a24 24 0 1 0 0-48 24 24 0 1 0 0 48z'/%3E%3C/svg%3E");
        }
        
        .icon-chat {
            mask: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 512 512'%3E%3Cpath d='M512 240c0 114.9-114.6 208-256 208c-37.1 0-72.3-6.4-104.1-17.9c-11.9 8.7-31.3 20.6-54.3 30.6C73.6 471.1 44.7 480 16 480c-6.5 0-12.3-3.9-14.8-9.9c-2.5-6-1.1-12.8 3.4-17.4l0 0 0 0 0 0 0 0 .3-.3c.3-.3 .7-.7 1.3-1.4c1.1-1.2 2.8-3.1 4.9-5.7c4.1-5 9.6-12.4 15.2-21.6c10-16.6 19.5-38.4 21.4-62.9C17.7 326.8 0 285.1 0 240C0 125.1 114.6 32 256 32s256 93.1 256 208z'/%3E%3C/svg%3E");
        }
        
        .icon-send {
            mask: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 512 512'%3E%3Cpath d='M498.1 5.6c10.1 7 15.4 19.1 13.5 31.2l-64 416c-1.5 9.7-7.4 18.2-16 23s-18.9 5.4-28 1.6L284 427.7l-68.5 74.1c-8.9 9.7-22.9 12.9-35.2 8.1S160 493.2 160 480V396.4c0-4 1.5-7.8 4.2-10.7L331.8 202.8c5.8-6.3 5.6-16-.4-22s-15.7-6.4-22-.7L106 360.8 17.7 316.6C7.1 311.3 .3 300.7 0 288.9s5.9-22.8 16.1-28.7l448-256c10.7-6.1 23.9-5.5 34 1.4z'/%3E%3C/svg%3E");
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Sidebar -->
        <div class="sidebar">
            <div class="logo">
                <span class="icon icon-book"></span>
                <h2>Networking Academy</h2>
            </div>
            <nav>
                <div class="nav-item active" id="nav-home" onclick="changePage('home')">
                    <span class="icon icon-home"></span>
                    Dashboard
                </div>
                <div class="nav-item" id="nav-lessons" onclick="changePage('lessons')">
                    <span class="icon icon-book"></span>
                    Lessons
                </div>
                <div class="nav-item" id="nav-quiz" onclick="changePage('quiz')">
                    <span class="icon icon-quiz"></span>
                    Tests & Quizzes
                </div>
                <div class="nav-item" id="nav-notes" onclick="changePage('notes')">
                    <span class="icon icon-notes"></span>
                    My Notes
                </div>
                <div class="nav-item" id="nav-chat" onclick="changePage('chat')">
                    <span class="icon icon-chat"></span>
                    AI Assistant
                </div>
            </nav>
        </div>
        
        <!-- Main Content -->
        <div class="main-content">
            <div class="header">
                <h1>Computer System Networking</h1>
                <div class="user-profile">
                    <img src="/api/placeholder/40/40" alt="User Profile">
                    <span>Student</span>
                </div>
            </div>
            
            <!-- Home Page -->
            <div id="home-page">
                <div class="section">
                    <div class="section-header">
                        <h2>Welcome to Networking Academy</h2>
                    </div>
                    <div class="section-content">
                        <p>Welcome to your virtual classroom for Computer Systems Networking. Our AI teachers will guide you through comprehensive lessons about networking concepts, protocols, security, and practical applications.</p>
                        <p>Use the sidebar navigation to access lessons, take quizzes, write notes, or chat with our AI assistant.</p>
                    </div>
                </div>
                
                <div class="section">
                    <div class="section-header">
                        <h2>Continue Learning</h2>
                    </div>
                    <div class="cards">
                        <div class="card" onclick="goToLessons()">
                            <div class="card-img">
                                <span class="icon icon-book"></span>
                            </div>
                            <div class="card-body">
                                <h3 class="card-title">Network Fundamentals</h3>
                                <p class="card-text">Learn the basic concepts of networking, including OSI model and TCP/IP suite.</p>
                                <div class="progress-bar">
                                    <div class="progress" style="width: 30%"></div>
                                </div>
                                <div class="progress-text">
                                    <span>Progress: 30%</span>
                                    <span>3/10 lessons</span>
                                </div>
                            </div>
                        </div>
                        
                        <div class="card" onclick="goToQuiz()">
                            <div class="card-img">
                                <span class="icon icon-quiz"></span>
                            </div>
                            <div class="card-body">
                                <h3 class="card-title">Practice Quizzes</h3>
                                <p class="card-text">Test your knowledge with interactive quizzes on networking concepts.</p>
                                <button class="btn">Start Quiz</button>
                            </div>
                        </div>
                        
                        <div class="card" onclick="goToChat()">
                            <div class="card-img">
                                <span class="icon icon-chat"></span>
                            </div>
                            <div class="card-body">
                                <h3 class="card-title">AI Assistant</h3>
                                <p class="card-text">Have questions? Chat with our AI assistant for immediate help.</p>
                                <button class="btn">Ask Question</button>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="section">
                    <div class="section-header">
                        <h2>Learning Path</h2>
                    </div>
                    <div class="section-content">
                        <div class="tabs">
                            <div class="tab active">Beginner</div>
                            <div class="tab">Intermediate</div>
                            <div class="tab">Advanced</div>
                        </div>
                        
                        <div class="tab-content active">
                            <div class="card" style="margin-bottom: 15px;">
                                <div class="card-body">
                                    <h3 class="card-title">1. Networking Basics <span class="status status-in-progress">In Progress</span></h3>
                                    <p class="card-text">Introduction to computer networks, types of networks, and basic terminology.</p>
                                </div>
                            </div>
                            
                            <div class="card" style="margin-bottom: 15px;">
                                <div class="card-body">
                                    <h3 class="card-title">2. OSI Model <span class="status status-not-started">Not Started</span></h3>
                                    <p class="card-text">Understanding the 7 layers of the OSI model and their functions.</p>
                                </div>
                            </div>
                            
                            <div class="card" style="margin-bottom: 15px;">
                                <div class="card-body">
                                    <h3 class="card-title">3. TCP/IP Protocol Suite <span class="status status-not-started">Not Started</span></h3>
                                    <p class="card-text">Learn about the TCP/IP protocol stack and its importance.</p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Lessons Page -->
            <div id="lessons-page">
                <div class="section">
                    <div class="section-header">
                        <h2>Network Fundamentals</h2>
                    </div>
                    <div class="section-content">
                        <h3>Introduction to Computer Networks</h3>
                        <p>A computer network is a group of computers linked to each other that enables the computer to communicate with another computer and share their resources, data, and applications.</p>
                        
                        <h4>Types of Networks</h4>
                        <ul>
                            <li><strong>LAN (Local Area Network)</strong>: A network confined to a relatively small area. It is generally limited to a geographic area such as a writing lab, school, or building.</li>
                            <li><strong>WAN (Wide Area Network)</strong>: A network that covers a broad area (i.e., any telecommunications network that links across metropolitan, regional, or national boundaries).</li>
                            <li><strong>MAN (Metropolitan Area Network)</strong>: A network spanning a physical area larger than a LAN but smaller than a WAN, such as a city.</li>
                            <li><strong>PAN (Personal Area Network)</strong>: A network arranged within an individual person, typically within a range of 10 meters.</li>
                            <li><strong>CAN (Campus Area Network)</strong>: A network spanning multiple LANs but smaller than a MAN, such as university or corporate campuses.</li>
                        </ul>
                        
                        <h4>Network Topologies</h4>
                        <p>Network topology refers to the arrangement of elements in a network. Common topologies include:</p>
                        <ul>
                            <li><strong>Bus Topology</strong>: All devices are connected to a central cable.</li>
                            <li><strong>Star Topology</strong>: All devices are connected to a central hub or switch.</li>
                            <li><strong>Ring Topology</strong>: Each device is connected to exactly two other devices, forming a ring.</li>
                            <li><strong>Mesh Topology</strong>: Every device is connected to every other device in the network.</li>
                            <li><strong>Tree Topology</strong>: A hierarchy of nodes arranged like a tree.</li>
                        </ul>
                        
                        <h4>Network Protocols</h4>
                        <p>Protocols are sets of rules that determine how data is transmitted between different devices in a network. Examples include:</p>
                        <ul>
                            <li><strong>TCP/IP</strong>: The fundamental suite of protocols for internet communications.</li>
                            <li><strong>HTTP/HTTPS</strong>: Protocol used for transferring web pages.</li>
                            <li><strong>FTP</strong>: Protocol for transferring files.</li>
                            <li><strong>SMTP</strong>: Protocol for email transmission.</li>
                            <li><strong>DNS</strong>: Protocol that translates domain names to IP addresses.</li>
                        </ul>
                        
                        <div class="section-footer" style="margin-top: 20px;">
                            <button class="btn" onclick="loadNextLesson()">Next Lesson: OSI Model</button>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Quiz Page -->
            <div id="quiz-page">
                <div class="section">
                    <div class="section-header">
                        <h2>Network Fundamentals Quiz</h2>
                    </div>
                    <div class="quiz-container">
                        <div id="quiz-content">
                            <div class="question">
                                <p>1. What type of network is limited to a relatively small area like a school or building?</p>
                                <ul class="options">
                                    <li class="option" onclick="selectOption(this)">Wide Area Network (WAN)</li>
                                    <li class="option" onclick="selectOption(this)">Local Area Network (LAN)</li>
                                    <li class="option" onclick="selectOption(this)">Metropolitan Area Network (MAN)</li>
                                    <li class="option" onclick="selectOption(this)">Personal Area Network (PAN)</li>
                                </ul>
                            </div>
                            
                            <div class="question">
                                <p>2. Which of the following is NOT a network topology?</p>
                                <ul class="options">
                                    <li class="option" onclick="selectOption(this)">Star Topology</li>
                                    <li class="option" onclick="selectOption(this)">Circle Topology</li>
                                    <li class="option" onclick="selectOption(this)">Bus Topology</li>
                                    <li class="option" onclick="selectOption(this)">Mesh Topology</li>
                                </ul>
                            </div>
                            
                            <div class="question">
                                <p>3. Which protocol is primarily used for transferring web pages?</p>
                                <ul class="options">
                                    <li class="option" onclick="selectOption(this)">FTP</li>
                                    <li class="option" onclick="selectOption(this)">SMTP</li>
                                    <li class="option" onclick="selectOption(this)">HTTP</li>
                                    <li class="option" onclick="selectOption(this)">DNS</li>
                                </ul>
                            </div>
                            
                            <div class="question">
                                <p>4. In which topology is every device connected to every other device in the network?</p>
                                <ul class="options">
                                    <li class="option" onclick="selectOption(this)">Bus Topology</li>
                                    <li class="option" onclick="selectOption(this)">Star Topology</li>
                                    <li class="option" onclick="selectOption(this)">Ring Topology</li>
                                    <li class="option" onclick="selectOption(this)">Mesh Topology</li>
                                </ul>
                            </div>
                            
                            <div class="question">
                                <p>5. What does DNS stand for?</p>
                                <ul class="options">
                                    <li class="option" onclick="selectOption(this)">Domain Name System</li>
                                    <li class="option" onclick="selectOption(this)">Digital Network Service</li>
                                    <li class="option" onclick="selectOption(this)">Dynamic Network System</li>
                                    <li class="option" onclick="selectOption(this)">Data Network Standard</li>
                                </ul>
                            </div>
                        </div>
                        
                        <div class="quiz-controls">
                            <button class="btn btn-outline" onclick="resetQuiz()">Reset</button>
                            <button class="btn" onclick="submitQuiz()">Submit Quiz</button>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Notes Page -->
            <div id="notes-page">
                <div class="section">
                    <div class="section-header">
                        <h2>My Notes</h2>
                    </div>
                    <div class="section-content">
                        <p>Use this space to write down important concepts, definitions, and insights from your lessons.</p>
                        <div class="notes-container">
                            <textarea id="notes-area" placeholder="Start typing your notes here...">
# Network Fundamentals Notes

## Types of Networks
- LAN: Local Area Network (small area like building)
- WAN: Wide Area Network (large geographical area)
- MAN: Metropolitan Area Network (city-sized)
- PAN: Personal Area Network (within reach of a person)
- CAN: Campus Area Network (university/corporate campus)

## Common Network Protocols
- TCP/IP: Foundation of internet communications
- HTTP/HTTPS: Web page transfer
- FTP: File transfer
- SMTP: Email transmission
- DNS: Domain name to IP address translation
                            </textarea>
                        </div>
                        <div style="display: flex; justify-content: flex-end; margin-top: 15px;">
                            <button class="btn" onclick="saveNotes()">Save Notes</button>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Chat Page -->
            <div id="chat-page">
                <div class="section">
                    <div class="section-header">
                        <h2>AI Networking Assistant</h2>
                    </div>
                    <div class="section-content">
                        <p>Ask our AI assistant any questions about computer networking concepts.</p>
                        
                        <div class="chat-container">
                            <div class="chat-header">
                                <img src="/api/placeholder/40/40" alt="AI Assistant">
                                <h3>Networking AI Assistant</h3>
                            </div>
                            
                            <div class="chat-messages" id="chat-messages">
                                <div class="message bot-message">
                                    <div class="message-content">
                                        Hello! I'm your Networking AI Assistant. How can I help you with computer networking today?
                                    </div>
                                    <div class="message-time">Just now</div>
                                </div>
                            </div>
                            
                            <div class="chat-input">
                                <input type="text" id="user-input" placeholder="Type your question here..." onkeypress="handleKeyPress(event)">
                                <button onclick="sendMessage()">
                                    <span class="icon icon-send"></span>
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Page navigation
        function changePage(page) {
            // Hide all pages
            document.getElementById('home-page').style.display = 'none';
            document.getElementById('lessons-page').style.display = 'none';
            document.getElementById('quiz-page').style.display = 'none';
            document.getElementById('notes-page').style.display = 'none';
            document.getElementById('chat-page').style.display = 'none';
            
            // Show selected page
            document.getElementById(page + '-page').style.display = 'block';
            
            // Update active nav item
            const navItems = document.querySelectorAll('.nav-item');
            navItems.forEach(item => item.classList.remove('active'));
            
            // Find the nav item that triggered this and make it active
            const activeItems = document.querySelectorAll('.nav-item');
            activeItems.forEach(item => {
                if (item.textContent.trim().toLowerCase().includes(page)) {
                    item.classList.add('active');
                }
            });
            
            // Special case for dashboard
            if (page === 'home') {
                activeItems[0].classList.add('active');
            }
        }
        
        // Quiz functionality
        function selectOption(option) {
            // First, remove 'selected' class from any siblings
            const siblings = option.parentElement.children;
            for (let i = 0; i < siblings.length; i++) {
                siblings[i].classList.remove('selected');
            }
            
            // Then add 'selected' class to the clicked option
            option.classList.add('selected');
        }
        
        function submitQuiz() {
            const questions = document.querySelectorAll('.question');
            let score = 0;
            
            // Correct answers (indices)
            const correctAnswers = [1, 1, 2, 3, 0]; // 0-based index
            
            questions.forEach((question, qIndex) => {
                const options = question.querySelectorAll('.option');
                
                options.forEach((option, oIndex) => {
                    if (option.classList.contains('selected')) {
                        if (oIndex === correctAnswers[qIndex]) {
                            option.classList.add('correct');
                            score++;
                        } else {
                            option.classList.add('incorrect');
                            // Highlight the correct answer
                            options[correctAnswers[qIndex]].classList.add('correct');
                        }
                    }
                });
            });
            
            // Display score
            alert(`You scored ${score} out of ${correctAnswers.length}!`);
        }
        
        function resetQuiz() {
            const options = document.querySelectorAll('.option');
            options.forEach(option => {
                option.classList.remove('selected', 'correct', 'incorrect');
            });
        }
        
        // Notes functionality
        function saveNotes() {
            const notes = document.getElementById('notes-area').value;
            localStorage.setItem('networkingNotes', notes);
            alert('Notes saved successfully!');
        }
        
        // Load saved notes on page load
        window.addEventListener('load', () => {
            const savedNotes = localStorage.getItem('networkingNotes');
            if (savedNotes) {
                document.getElementById('notes-area').value = savedNotes;
            }
        });
        
        // Chat functionality
        let chatResponses = {
            "hello": "Hello! How can I help you with computer networking today?",
            "hi": "Hi there! Do you have any networking questions I can help with?",
            "what is networking": "Computer networking is the practice of connecting computers and devices to share resources and communicate with each other. This includes everything from small home networks to the global internet.",
            "what is lan": "LAN (Local Area Network) is a network that connects computers and devices within a limited area such as a home, school, or office building. LANs typically use Ethernet or Wi-Fi technology.",
            "what is wan": "WAN (Wide Area Network) is a network that spans a large geographical area, often connecting multiple LANs together. The Internet is the largest example of a WAN.",
            "what is the osi model": "The OSI (Open Systems Interconnection) model is a conceptual framework that standardizes the functions of a telecommunication or computing system into seven abstraction layers: Physical, Data Link, Network, Transport, Session, Presentation, and Application.",
            "explain tcp/ip": "TCP/IP (Transmission Control Protocol/Internet Protocol) is the suite of communication protocols used to connect hosts on the Internet. It consists of four layers: Link Layer, Internet Layer, Transport Layer, and Application Layer.",
            "what is a router": "A router is a networking device that forwards data packets between computer networks. It performs the traffic directing functions on the Internet and is located at gateways where two or more networks connect.",
            "what is an ip address": "An IP (Internet Protocol) address is a numerical label assigned to each device connected to a computer network that uses the Internet Protocol for communication. IPv4 addresses are typically displayed in dot-decimal notation (e.g., 192.168.1.1).",
            "what is dns": "DNS (Domain Name System) is like the phone book of the internet. It translates human-readable domain names (like www.example.com) into IP addresses that computers use to identify each other.",
            "what is http": "HTTP (Hypertext Transfer Protocol) is the foundation of data communication on the World Wide Web. It defines how messages are formatted and transmitted, and what actions web servers and browsers should take in response to various commands.",
            "what is a subnet": "A subnet, or subnetwork, is a logical subdivision of an IP network. Subnetting allows organizations to divide a network into smaller, more manageable segments for efficiency and security purposes.",
            "what is a firewall": "A firewall is a network security device or software that monitors and filters incoming and outgoing network traffic based on predefined security rules, acting as a barrier between a trusted internal network and untrusted external networks.",
            "help": "I can answer questions about networking concepts, protocols, topologies, hardware, security, and more. Just ask me anything related to computer networking!"
        };
        
        function getAIResponse(userMessage) {
            // Convert to lowercase for case-insensitive matching
            const messageLower = userMessage.toLowerCase();
            
            // Check for direct matches
            for (const [key, value] of Object.entries(chatResponses)) {
                if (messageLower.includes(key)) {
                    return value;
                }
            }
            
            // If no direct match, look for keywords
            if (messageLower.includes("protocol")) {
                return "Protocols are standardized rules that allow devices to communicate. Common networking protocols include TCP/IP, HTTP, FTP, SMTP, and DNS. Which specific protocol would you like to learn more about?";
            } else if (messageLower.includes("topology")) {
                return "Network topology refers to the arrangement of elements in a network. Common topologies include Bus, Star, Ring, Mesh, and Tree. Each has its own advantages and use cases.";
            } else if (messageLower.includes("security") || messageLower.includes("secure")) {
                return "Network security involves protecting the integrity, confidentiality, and accessibility of computer networks and data. This includes firewalls, encryption, authentication, and intrusion detection systems.";
            } else if (messageLower.includes("layer") || messageLower.includes("osi")) {
                return "The OSI model consists of 7 layers: Physical, Data Link, Network, Transport, Session, Presentation, and Application. Each layer has specific functions and protocols that work together to enable network communication.";
            }
            
            // Default response if no matches found
            return "I'm not sure I understand your question about networking. Could you please rephrase or ask about a specific networking concept like protocols, topologies, or the OSI model?";
        }
        
        function sendMessage() {
            const userInput = document.getElementById('user-input');
            const userMessage = userInput.value.trim();
            
            if (userMessage === '') return;
            
            // Clear input field
            userInput.value = '';
            
            // Add user message to chat
            addMessage(userMessage, 'user');
            
            // Get AI response
            setTimeout(() => {
                const aiResponse = getAIResponse(userMessage);
                addMessage(aiResponse, 'bot');
            }, 500); // Small delay to simulate processing
        }
        
        function addMessage(message, sender) {
            const chatMessages = document.getElementById('chat-messages');
            const messageDiv = document.createElement('div');
            messageDiv.className = `message ${sender}-message`;
            
            const currentTime = new Date();
            const timeString = currentTime.getHours() + ':' + 
                               (currentTime.getMinutes() < 10 ? '0' : '') + currentTime.getMinutes();
            
            messageDiv.innerHTML = `
                <div class="message-content">${message}</div>
                <div class="message-time">${timeString}</div>
            `;
            
            chatMessages.appendChild(messageDiv);
            
            // Scroll to bottom
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }
        
        function handleKeyPress(event) {
            if (event.key === 'Enter') {
                sendMessage();
            }
        }
        
        // Function to load next lesson (placeholder)
        function loadNextLesson() {
            alert("Next lesson content would load here. This would be the 'OSI Model' lesson.");
        }
        
        // Fixed navigation functions
        function changePage(page) {
            // Hide all pages
            document.getElementById('home-page').style.display = 'none';
            document.getElementById('lessons-page').style.display = 'none';
            document.getElementById('quiz-page').style.display = 'none';
            document.getElementById('notes-page').style.display = 'none';
            document.getElementById('chat-page').style.display = 'none';
            
            // Show selected page
            document.getElementById(page + '-page').style.display = 'block';
            
            // Update active nav item
            const navItems = document.querySelectorAll('.nav-item');
            navItems.forEach(item => item.classList.remove('active'));
            
            // Add active class to the correct nav item
            document.getElementById('nav-' + page).classList.add('active');
        }
        
        // Convenience functions for card navigation
        function goToLessons() {
            changePage('lessons');
        }
        
        function goToQuiz() {
            changePage('quiz');
        }
        
        function goToChat() {
            changePage('chat');
        }
        
        // Initialize the app
        document.addEventListener('DOMContentLoaded', function() {
            // Set up any initial state here
            console.log("Networking classroom app initialized");
        });
    </script>
</body>
</html>
