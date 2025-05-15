<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NetLearn - Virtual Networking Classroom</title>
    <style>
        /* [Keep all your existing CSS styles the same] */
        /* ... */
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
    
    <!-- [Keep all your existing HTML content the same until the script section] -->
    <!-- ... -->

    <script>
        // Tab Functionality
        function activateTab(tabId) {
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
        }

        // Set up tab buttons
        document.querySelectorAll('.tab-btn').forEach(button => {
            button.addEventListener('click', () => {
                const tabId = button.getAttribute('data-tab');
                activateTab(tabId);
            });
        });
        
        // Set up navigation links
        document.querySelectorAll('.nav-links a').forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                const tabId = link.getAttribute('data-tab');
                activateTab(tabId);
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
                    - /26 (64): 0, 64, 128
