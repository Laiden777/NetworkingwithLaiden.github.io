<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NetLearn - Virtual Networking Classroom</title>
    <style>
        /* [Previous CSS styles remain exactly the same] */
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
                <a href="#" data-tab="learn">Learn</a>
                <a href="#" data-tab="quiz">Tests & Quizzes</a>
                <a href="#" data-tab="notes">My Notes</a>
                <a href="#" data-tab="chat">AI Assistant</a>
            </div>
        </nav>
    </header>
    
    <div class="container">
        <!-- [All previous content sections remain exactly the same] -->
    </div>
    
    <footer>
        <!-- [Footer content remains the same] -->
    </footer>
    
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Get all tab buttons and content sections
            const tabButtons = document.querySelectorAll('.tab-btn, .nav-links a');
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
                
                // Show the selected tab content
                const activeTab = document.getElementById(tabId);
                if (activeTab) {
                    activeTab.classList.add('active');
                }
                
                // Activate the corresponding tab button
                const activeButton = document.querySelector(`[data-tab="${tabId}"]`);
                if (activeButton) {
                    activeButton.classList.add('active');
                }
                
                // Update URL hash without scrolling
                history.replaceState(null, null, `#${tabId}`);
            }
            
            // Add click event listeners to all tab buttons
            tabButtons.forEach(button => {
                button.addEventListener('click', function(e) {
                    e.preventDefault();
                    const tabId = this.getAttribute('data-tab');
                    switchTab(tabId);
                });
            });
            
            // Check URL hash on page load
            function checkHash() {
                const hash = window.location.hash.substring(1);
                if (hash && document.getElementById(hash)) {
                    switchTab(hash);
                } else {
                    // Default to first tab if no valid hash
                    switchTab('learn');
                }
            }
            
            // Also check hash when navigating back/forward
            window.addEventListener('popstate', checkHash);
            
            // Initialize the page
            checkHash();
            
            // Note Item Selection (keep existing functionality)
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
                        // [Other note contents remain the same]
                    };
                    
                    if (noteContents[item.textContent]) {
                        document.querySelector('.note-content').value = noteContents[item.textContent];
                    }
                });
            });
        });
    </script>
</body>
</html>
