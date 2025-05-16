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
        
        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
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
            list-style: none;
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
        
        .hamburger {
            display: none;
            cursor: pointer;
            flex-direction: column;
            gap: 5px;
            background: transparent;
            border: none;
        }
        
        .hamburger span {
            width: 25px;
            height: 3px;
            background-color: white;
            transition: all 0.3s ease;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }
        
        /* Rest of your existing CSS styles... */
        /* [Previous CSS content remains exactly the same] */
        
        @media (max-width: 768px) {
            .hamburger {
                display: flex;
            }
            
            .nav-links {
                position: fixed;
                top: 70px;
                left: -100%;
                width: 100%;
                height: calc(100vh - 70px);
                background-color: var(--primary);
                flex-direction: column;
                align-items: center;
                justify-content: flex-start;
                padding-top: 2rem;
                transition: all 0.5s ease;
            }
            
            .nav-links.active {
                left: 0;
            }
            
            .nav-links a {
                margin: 0.5rem 0;
                padding: 1rem;
                width: 80%;
                text-align: center;
            }
            
            .hamburger.active span:nth-child(1) {
                transform: translateY(8px) rotate(45deg);
            }
            
            .hamburger.active span:nth-child(2) {
                opacity: 0;
            }
            
            .hamburger.active span:nth-child(3) {
                transform: translateY(-8px) rotate(-45deg);
            }
            
            /* Other mobile styles from your original CSS */
        }
    </style>
</head>
<body>
    <header>
        <nav class="navbar">
            <div class="logo">
                <span class="logo-icon">🌐</span>
                NetLearn
            </div>
            <ul class="nav-links">
                <li><a href="#" data-tab="learn">Learn</a></li>
                <li><a href="#" data-tab="quiz">Tests & Quizzes</a></li>
                <li><a href="#" data-tab="notes">My Notes</a></li>
                <li><a href="#" data-tab="chat">AI Assistant</a></li>
            </ul>
            <button class="hamburger">
                <span></span>
                <span></span>
                <span></span>
            </button>
        </nav>
    </header>
    
    <!-- Rest of your HTML content remains exactly the same -->
    <!-- [Previous HTML content remains unchanged] -->
    
    <script>
        // Mobile Navigation
        const hamburger = document.querySelector('.hamburger');
        const navLinks = document.querySelector('.nav-links');
        
        hamburger.addEventListener('click', () => {
            hamburger.classList.toggle('active');
            navLinks.classList.toggle('active');
        });
        
        // Close mobile menu when clicking a link
        document.querySelectorAll('.nav-links a').forEach(link => {
            link.addEventListener('click', () => {
                hamburger.classList.remove('active');
                navLinks.classList.remove('active');
            });
        });
        
        // Tab Functionality
        document.querySelectorAll('[data-tab]').forEach(button => {
            button.addEventListener('click', (e) => {
                e.preventDefault();
                
                // Deactivate all tabs
                document.querySelectorAll('.tab-btn').forEach(btn => {
                    btn.classList.remove('active');
                });
                document.querySelectorAll('.tab-content').forEach(content => {
                    content.classList.remove('active');
                });
                
                // Activate clicked tab
                const tabId = button.getAttribute('data-tab');
                document.querySelector(`.tab-btn[data-tab="${tabId}"]`).classList.add('active');
                document.getElementById(tabId).classList.add('active');
                
                // Scroll to top of container
                document.querySelector('.container').scrollIntoView({
                    behavior: 'smooth'
                });
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
        
        // Chat functionality
        const chatInput = document.querySelector('.chat-input');
        const chatSendBtn = document.querySelector('.chat-send-btn');
        const chatMessages = document.querySelector('.chat-messages');
        
        chatSendBtn.addEventListener('click', sendMessage);
        chatInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                sendMessage();
            }
        });
        
        function sendMessage() {
            const message = chatInput.value.trim();
            if (message) {
                // Add user message
                addMessage(message, 'user');
                chatInput.value = '';
                
                // Simulate AI response after a delay
                setTimeout(() => {
                    const responses = [
                        "That's a great question about networking! Would you like me to explain in more detail?",
                        "I can help with that networking concept. Here's what you need to know...",
                        "That's an important aspect of computer networking. Let me break it down for you.",
                        "I'd be happy to explain that networking topic. Here are the key points...",
                        "Excellent question! This is fundamental to understanding network communications."
                    ];
                    const randomResponse = responses[Math.floor(Math.random() * responses.length)];
                    addMessage(randomResponse, 'ai');
                }, 1000);
            }
        }
        
        function addMessage(text, sender) {
            const messageDiv = document.createElement('div');
            messageDiv.className = `message ${sender}`;
            messageDiv.innerHTML = `
                <div class="message-content">
                    ${text}
                </div>
            `;
            chatMessages.appendChild(messageDiv);
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }
    </script>
</body>
</html>
