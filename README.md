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
        
        /* [Rest of your CSS remains exactly the same] */
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
                <a href="#learn" class="nav-link">Learn</a>
                <a href="#quiz" class="nav-link">Tests & Quizzes</a>
                <a href="#notes" class="nav-link">My Notes</a>
                <a href="#chat" class="nav-link">AI Assistant</a>
            </div>
        </nav>
    </header>
    
    <div class="container">
        <!-- Your existing content sections remain exactly the same -->
        <!-- Just ensure each section has the correct ID: -->
        <!-- learn, quiz, notes, chat -->
    </div>
    
    <footer>
        <!-- Your footer content remains the same -->
    </footer>
    
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Get all navigation links
            const navLinks = document.querySelectorAll('.nav-link');
            
            // Get all tab buttons and content sections
            const tabButtons = document.querySelectorAll('.tab-btn');
            const tabContents = document.querySelectorAll('.tab-content');
            
            // Function to show a specific tab
            function showTab(tabId) {
                // Hide all tab contents
                tabContents.forEach(content => {
                    content.classList.remove('active');
                });
                
                // Deactivate all tab buttons
                tabButtons.forEach(button => {
                    button.classList.remove('active');
                });
                
                // Show the selected tab content
                const activeTab = document.getElementById(tabId);
                if (activeTab) {
                    activeTab.classList.add('active');
                }
                
                // Activate the corresponding tab button if it exists
                const activeButton = document.querySelector(`.tab-btn[data-tab="${tabId}"]`);
                if (activeButton) {
                    activeButton.classList.add('active');
                }
            }
            
            // Handle navigation link clicks
            navLinks.forEach(link => {
                link.addEventListener('click', function(e) {
                    e.preventDefault();
                    const targetId = this.getAttribute('href').substring(1);
                    showTab(targetId);
                    
                    // Update URL without page jump
                    history.pushState(null, null, `#${targetId}`);
                });
            });
            
            // Handle tab button clicks
            tabButtons.forEach(button => {
                button.addEventListener('click', function() {
                    const tabId = this.getAttribute('data-tab');
                    showTab(tabId);
                    
                    // Update URL without page jump
                    history.pushState(null, null, `#${tabId}`);
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
            
            // Also handle back/forward navigation
            window.addEventListener('popstate', function() {
                const hash = window.location.hash.substring(1);
                if (hash && document.getElementById(hash)) {
                    showTab(hash);
                }
            });
            
            // Initialize the page
            checkInitialTab();
            
            // Your existing note item selection code can remain the same
            document.querySelectorAll('.note-item').forEach(item => {
                item.addEventListener('click', () => {
                    document.querySelectorAll('.note-item').forEach(note => {
                        note.classList.remove('active');
                    });
                    item.classList.add('active');
                    
                    // Note content loading logic here...
                });
            });
        });
    </script>
</body>
</html>
