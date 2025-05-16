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
        
        /* [All your existing CSS styles remain exactly the same] */
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
        <!-- Your existing content sections -->
        <div id="learn" class="tab-content">
            <!-- Learn content -->
        </div>
        <div id="quiz" class="tab-content" style="display:none;">
            <!-- Quiz content -->
        </div>
        <div id="notes" class="tab-content" style="display:none;">
            <!-- Notes content -->
        </div>
        <div id="chat" class="tab-content" style="display:none;">
            <!-- Chat content -->
        </div>
    </div>
    
    <footer>
        <!-- Your footer content -->
    </footer>
    
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Get all navigation links and tab buttons
            const navLinks = document.querySelectorAll('.nav-link');
            const tabButtons = document.querySelectorAll('.tab-btn');
            
            // Function to show a specific tab
            function showTab(tabId) {
                // Hide all tab contents
                document.querySelectorAll('.tab-content').forEach(content => {
                    content.style.display = 'none';
                });
                
                // Show the selected tab content
                const activeTab = document.getElementById(tabId);
                if (activeTab) {
                    activeTab.style.display = 'block';
                }
                
                // Update active state for navigation links
                navLinks.forEach(link => {
                    link.style.fontWeight = link.dataset.tab === tabId ? 'bold' : 'normal';
                });
                
                // Update active state for tab buttons
                tabButtons.forEach(button => {
                    if (button.dataset.tab === tabId) {
                        button.classList.add('active');
                    } else {
                        button.classList.remove('active');
                    }
                });
            }
            
            // Handle navigation link clicks
            navLinks.forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    const tabId = this.dataset.tab;
                    showTab(tabId);
                    window.location.hash = tabId;
                });
            });
            
            // Handle tab button clicks
            tabButtons.forEach(button => {
                button.addEventListener('click', function() {
                    const tabId = this.dataset.tab;
                    showTab(tabId);
                    window.location.hash = tabId;
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
            
            // Handle browser back/forward navigation
            window.addEventListener('popstate', function() {
                const hash = window.location.hash.substring(1);
                if (hash && document.getElementById(hash)) {
                    showTab(hash);
                }
            });
        });
    </script>
</body>
</html>
