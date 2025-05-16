<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NetLearn - Virtual Networking Classroom</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            background-color: #f5f7fa;
            color: #333;
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        header {
            background-color: #2c3e50;
            color: white;
            padding: 20px 0;
            text-align: center;
            border-radius: 5px;
            margin-bottom: 30px;
        }
        .chat-container {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            padding: 20px;
            margin-bottom: 20px;
            height: 500px;
            overflow-y: auto;
        }
        .input-area {
            display: flex;
            gap: 10px;
        }
        input[type="text"] {
            flex: 1;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 16px;
        }
        button {
            background-color: #3498db;
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #2980b9;
        }
        .message {
            margin-bottom: 15px;
            padding: 10px 15px;
            border-radius: 18px;
            max-width: 80%;
        }
        .user-message {
            background-color: #e3f2fd;
            margin-left: auto;
            border-bottom-right-radius: 0;
        }
        .bot-message {
            background-color: #f1f1f1;
            margin-right: auto;
            border-bottom-left-radius: 0;
        }
        .follow-up-questions {
            margin-top: 15px;
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }
        .follow-up-btn {
            background-color: #e0e0e0;
            color: #333;
            border: none;
            padding: 8px 12px;
            border-radius: 16px;
            cursor: pointer;
            font-size: 14px;
            transition: all 0.3s;
        }
        .follow-up-btn:hover {
            background-color: #d0d0d0;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>NetLearn</h1>
            <p>Virtual Networking Classroom</p>
        </header>
        
        <div class="chat-container" id="chatContainer">
            <!-- Chat messages will appear here -->
        </div>
        
        <div class="input-area">
            <input type="text" id="userInput" placeholder="Ask me anything about networking..." autocomplete="off">
            <button id="sendBtn">Send</button>
        </div>
    </div>

    <script>
        // ==================== KNOWLEDGE DATABASES ==================== //
        
        // General Knowledge Base
        const generalKnowledge = {
            "greetings": {
                response: "Hello! I'm NetLearn, your virtual networking assistant. How can I help you today?",
                followUp: []
            },
            "what is your name": {
                response: "I'm NetLearn, your virtual networking classroom assistant.",
                followUp: []
            },
            "who created you": {
                response: "I was created by computer tech wizard Laiden to help students master networking concepts.",
                followUp: ["What can you teach me about networking?", "Tell me about Laiden's other projects"]
            },
            "current time": {
                response: `The current time is ${new Date().toLocaleTimeString()}.`,
                followUp: []
            },
            "today's date": {
                response: `Today's date is ${new Date().toLocaleDateString()}.`,
                followUp: []
            },
            "thank you": {
                response: "You're welcome! Is there anything else you'd like to know about networking?",
                followUp: []
            },
            "default": {
                response: "I'm primarily focused on networking topics, but I can try to help. Could you rephrase your question?",
                followUp: []
            }
        };

        // Networking Knowledge Base
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
   • Firewalls: Security filtering`,
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
   • Routers use software for path determination`,
                followUp: ["How does OSPF calculate routes?", "Explain VLAN trunking", "What are the advantages of EIGRP?"]
            }
        };

        // Quiz Database
        const quizDatabase = {
            "network fundamentals": {
                title: "Network Fundamentals Quiz",
                description: "Test your understanding of basic networking concepts, protocols, and the OSI model.",
                timeLimit: 15,
                questions: [
                    {
                        question: "Which layer of the OSI model is responsible for logical addressing and routing?",
                        options: ["Physical", "Data Link", "Network", "Transport"],
                        answer: 2,
                        explanation: "The Network layer (Layer 3) handles logical addressing (IP addresses) and routing between networks."
                    },
                    {
                        question: "What is the purpose of the TCP three-way handshake?",
                        options: ["To encrypt data", "To establish a connection", "To compress data", "To route packets"],
                        answer: 1,
                        explanation: "The three-way handshake (SYN, SYN-ACK, ACK) establishes a reliable TCP connection before data transfer."
                    }
                ]
            }
        };

        // ==================== CHAT FUNCTIONALITY ==================== //
        const chatContainer = document.getElementById('chatContainer');
        const userInput = document.getElementById('userInput');
        const sendBtn = document.getElementById('sendBtn');

        // Display initial greeting
        displayMessage('bot', generalKnowledge.greetings.response);

        // Send button click handler
        sendBtn.addEventListener('click', sendMessage);

        // Enter key handler
        userInput.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                sendMessage();
            }
        });

        function sendMessage() {
            const message = userInput.value.trim();
            if (message) {
                displayMessage('user', message);
                userInput.value = '';
                
                // Process the message and get response
                setTimeout(() => {
                    const response = getResponse(message);
                    displayMessage('bot', response.response);
                    
                    // Display follow-up questions if any
                    if (response.followUp && response.followUp.length > 0) {
                        displayFollowUpQuestions(response.followUp);
                    }
                }, 500);
            }
        }

        function displayMessage(sender, message) {
            const messageDiv = document.createElement('div');
            messageDiv.classList.add('message');
            messageDiv.classList.add(sender === 'user' ? 'user-message' : 'bot-message');
            messageDiv.textContent = message;
            chatContainer.appendChild(messageDiv);
            chatContainer.scrollTop = chatContainer.scrollHeight;
        }

        function displayFollowUpQuestions(questions) {
            const container = document.createElement('div');
            container.classList.add('follow-up-questions');
            
            questions.forEach(question => {
                const btn = document.createElement('button');
                btn.classList.add('follow-up-btn');
                btn.textContent = question;
                btn.addEventListener('click', () => {
                    userInput.value = question;
                    sendMessage();
                });
                container.appendChild(btn);
            });
            
            chatContainer.appendChild(container);
            chatContainer.scrollTop = chatContainer.scrollHeight;
        }

        function getResponse(userInput) {
            const input = userInput.toLowerCase().trim();
            
            // Check for creator-related questions
            if (/who (made|created|built) you|your creator/.test(input)) {
                return generalKnowledge["who created you"];
            }
            
            // Check general knowledge first
            for (const [key, value] of Object.entries(generalKnowledge)) {
                if (input.includes(key)) {
                    return value;
                }
            }
            
            // Then check networking knowledge
            for (const [key, value] of Object.entries(knowledgeBase)) {
                if (input.includes(key)) {
                    return value;
                }
            }
            
            return generalKnowledge.default;
        }
    </script>
</body>
</html>
