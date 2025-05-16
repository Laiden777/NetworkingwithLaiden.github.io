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
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        /* Add all your other existing CSS styles here */
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
                <a href="#learn" class="nav-link" data-tab="learn">Learn</a>
                <a href="#quiz" class="nav-link" data-tab="quiz">Tests & Quizzes</a>
                <a href="#notes" class="nav-link" data-tab="notes">My Notes</a>
                <a href="#chat" class="nav-link" data-tab="chat">AI Assistant</a>
            </div>
        </nav>
    </header>
    
    <div class="container">
        <!-- Learn Tab Content -->
        <div id="learn" class="tab-content active">
            <h2>Learning Modules</h2>
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
                <!-- Add more module cards here -->
            </div>
        </div>
        
        <!-- Quiz Tab Content -->
        <div id="quiz" class="tab-content">
            <h2>Tests & Quizzes</h2>
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
                <!-- Add more quiz cards here -->
            </div>
        </div>
        
        <!-- Notes Tab Content -->
        <div id="notes" class="tab-content">
            <h2>My Notes</h2>
            <div class="notes-container">
                <div class="notes-list">
                    <div class="note-item active">OSI Model Notes</div>
                    <div class="note-item">TCP/IP Protocol Suite</div>
                    <!-- Add more note items here -->
                </div>
                <div class="note-editor">
                    <input type="text" class="note-title" value="OSI Model Notes">
                    <textarea class="note-content"># OSI Model Layers

## Layer 1: Physical
- Deals with the physical connection between devices
- Transmits raw bit stream over physical medium
- Examples: Cables, switches, network adapters</textarea>
                </div>
            </div>
        </div>
        
        <!-- Chat Tab Content -->
        <div id="chat" class="tab-content">
            <h2>AI Networking Assistant</h2>
            <div class="chat-container">
                <div class="chat-header">
                    <span class="chat-header-icon">🤖</span>
                    NetLearn Assistant
                </div>
                <div class="chat-messages">
                    <div class="message ai">
                        <div class="message-content">
                            Hello! I'm your NetLearn AI assistant. What would you like to learn about today?
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
                <p>&copy; 2023 NetLearn Virtual Classroom. All rights reserved.</p>
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
            // Get all navigation links
            const navLinks = document.querySelectorAll('.nav-link');
            
            // Function to show a specific tab
            function showTab(tabId) {
                // Hide all tab contents
                document.querySelectorAll('.tab-content').forEach(content => {
                    content.classList.remove('active');
                });
                
                // Show the selected tab content
                const activeTab = document.getElementById(tabId);
                if (activeTab) {
                    activeTab.classList.add('active');
                }
                
                // Update URL hash
                window.location.hash = tabId;
            }
            
            // Handle navigation link clicks
            navLinks.forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    const tabId = this.getAttribute('data-tab');
                    showTab(tabId);
                });
            });
            
            // Check URL hash on page load
            function checkInitialTab() {
                const hash = window.location.hash.substring(1);
                if (hash && document.getElementById(hash)) {
                    showTab(hash);
                } else {
                    // Default to first tab
                    showTab('learn');
                }
            }
            
            // Initialize the page
            checkInitialTab();
        });
    </script>
</body>
</html>
