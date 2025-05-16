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
            max-width: 900px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f5f5f5;
            color: #333;
        }
        
        header {
            background-color: #2c3e50;
            color: white;
            padding: 20px;
            border-radius: 5px;
            margin-bottom: 20px;
            text-align: center;
        }
        
        #chat-display {
            height: 400px;
            border: 1px solid #ddd;
            margin-bottom: 15px;
            padding: 15px;
            overflow-y: auto;
            background-color: white;
            border-radius: 5px;
        }
        
        .question {
            color: #2980b9;
            margin: 10px 0;
            padding: 8px 12px;
            background-color: #eaf2f8;
            border-radius: 18px;
            display: inline-block;
            max-width: 80%;
        }
        
        .response {
            color: #27ae60;
            margin: 10px 0 20px 0;
            padding: 10px 15px;
            background-color: #e8f8f0;
            border-radius: 18px;
            border-top-left-radius: 0;
        }
        
        .follow-up {
            margin-top: 10px;
            font-style: italic;
            color: #7f8c8d;
        }
        
        .follow-up-btn {
            background: none;
            border: none;
            color: #3498db;
            cursor: pointer;
            padding: 5px;
            margin: 5px 5px 5px 0;
            text-decoration: underline;
        }
        
        .follow-up-btn:hover {
            color: #2980b9;
        }
        
        #user-input {
            width: 75%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 16px;
        }
        
        #submit-btn {
            padding: 10px 20px;
            background-color: #2c3e50;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
            margin-left: 10px;
        }
        
        #submit-btn:hover {
            background-color: #34495e;
        }
        
        .quiz-container {
            display: none;
            margin-top: 20px;
        }
        
        .quiz-question {
            background-color: white;
            padding: 15px;
            border-radius: 5px;
            margin-bottom: 15px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        .quiz-option {
            display: block;
            margin: 8px 0;
            padding: 8px;
            background-color: #f9f9f9;
            border-radius: 4px;
            cursor: pointer;
        }
        
        .quiz-option:hover {
            background-color: #eee;
        }
    </style>
</head>
<body>
    <header>
        <h1>NetLearn</h1>
        <p>Virtual Networking Classroom</p>
    </header>
    
    <main>
        <section id="chat-interface">
            <div id="chat-display"></div>
            <div>
                <input type="text" id="user-input" placeholder="Ask about networking (e.g., 'Explain TCP/IP', 'What is a VLAN?')">
                <button id="submit-btn">Submit</button>
            </div>
        </section>
        
        <section id="quiz-interface" class="quiz-container">
            <h2 id="quiz-title"></h2>
            <p id="quiz-description"></p>
            <div id="quiz-questions"></div>
            <button id="quiz-back-btn">Back to Chat</button>
        </section>
    </main>
    
    <script>
        // Enhanced knowledge base with comprehensive networking information
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

Would you like me to elaborate on any specific aspect of network fundamentals?`,
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

Would you like to dive deeper into any routing protocol or switching concept?`,
                followUp: ["How does OSPF calculate routes?", "Explain VLAN trunking", "What are the advantages of EIGRP?"]
            },
            "network security": {
                response: `Network security is crucial for protecting infrastructure:

1. Firewalls:
   • Packet filtering: Basic ACLs
   • Stateful inspection: Tracks connections
   • Next-gen: Application awareness
   • Web application firewalls

2. Encryption:
   • Symmetric: AES (fast, same key)
   • Asymmetric: RSA (key pairs)
   • SSL/TLS for secure communications

3. VPN Technologies:
   • IPsec: Secure site-to-site tunnels
   • SSL VPN: Clientless remote access
   • DMVPN: Dynamic multipoint VPNs

Which security area would you like to explore further?`,
                followUp: ["How does SSL/TLS handshake work?", "What's the difference between IDS and IPS?", "Explain DMZ in network security"]
            },
            "default": {
                response: "I can answer questions about computer networking topics. Try asking about:<br><br>" +
                          "- Network fundamentals (OSI model, TCP/IP)<br>" +
                          "- Routing and switching (VLANs, OSPF, EIGRP)<br>" +
                          "- Network security (firewalls, VPNs)<br>" +
                          "- Or type 'quiz' to test your knowledge!",
                followUp: []
            },
            "quiz": {
                response: "Select a quiz topic:",
                followUp: ["Network Fundamentals Quiz", "Routing & Switching Quiz", "Network Security Quiz"],
                isQuizMenu: true
            }
        };

        // Quiz database
        const quizDatabase = {
            "network fundamentals": {
                title: "Network Fundamentals Quiz",
                description: "Test your understanding of basic networking concepts, protocols, and the OSI model.",
                timeLimit: 15,
                questions: [
                    {
                        question: "Which layer of the OSI model is responsible for logical addressing and routing?",
                        options: [
                            "Physical",
                            "Data Link",
                            "Network",
                            "Transport"
                        ],
                        answer: 2,
                        explanation: "The Network layer (Layer 3) handles logical addressing (IP addresses) and routing between networks."
                    },
                    {
                        question: "What is the purpose of the TCP three-way handshake?",
                        options: [
                            "To encrypt data",
                            "To establish a connection",
                            "To compress data",
                            "To route packets"
                        ],
                        answer: 1,
                        explanation: "The three-way handshake (SYN, SYN-ACK, ACK) establishes a reliable TCP connection before data transfer."
                    }
                ]
            },
            "routing and switching": {
                title: "Routing & Switching Quiz",
                description: "Test your knowledge of routing protocols, switching concepts, and VLANs.",
                timeLimit: 20,
                questions: [
                    {
                        question: "Which routing protocol uses the Dijkstra algorithm to calculate the shortest path?",
                        options: [
                            "RIP",
                            "OSPF",
                            "EIGRP",
                            "BGP"
                        ],
                        answer: 1,
                        explanation: "OSPF is a link-state protocol that uses Dijkstra's algorithm to build its shortest path first tree."
                    },
                    {
                        question: "What is the purpose of VLANs?",
                        options: [
                            "To increase network bandwidth",
                            "To logically segment a network",
                            "To encrypt network traffic",
                            "To connect to the internet"
                        ],
                        answer: 1,
                        explanation: "VLANs (Virtual LANs) logically segment networks without requiring physical separation."
                    }
                ]
            },
            "network security": {
                title: "Network Security Quiz",
                description: "Test your knowledge of firewalls, encryption, VPNs, and security threats.",
                timeLimit: 20,
                questions: [
                    {
                        question: "Which encryption algorithm is asymmetric?",
                        options: [
                            "AES",
                            "DES",
                            "RSA",
                            "3DES"
                        ],
                        answer: 2,
                        explanation: "RSA is an asymmetric algorithm that uses public/private key pairs."
                    },
                    {
                        question: "What is the purpose of a DMZ?",
                        options: [
                            "To isolate internal networks from the internet",
                            "To increase network speed",
                            "To manage wireless access points",
                            "To filter spam emails"
                        ],
                        answer: 0,
                        explanation: "A DMZ (Demilitarized Zone) isolates publicly accessible services from internal networks."
                    }
                ]
            }
        };

        // Main application logic
        document.addEventListener('DOMContentLoaded', function() {
            const chatDisplay = document.getElementById('chat-display');
            const userInput = document.getElementById('user-input');
            const submitBtn = document.getElementById('submit-btn');
            const quizInterface = document.getElementById('quiz-interface');
            const quizTitle = document.getElementById('quiz-title');
            const quizDescription = document.getElementById('quiz-description');
            const quizQuestions = document.getElementById('quiz-questions');
            const quizBackBtn = document.getElementById('quiz-back-btn');
            
            // Display initial greeting
            displayResponse(knowledgeBase.default.response);
            
            // Handle user submissions
            submitBtn.addEventListener('click', handleSubmit);
            userInput.addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    handleSubmit();
                }
            });
            
            // Handle quiz back button
            quizBackBtn.addEventListener('click', function() {
                quizInterface.style.display = 'none';
                document.getElementById('chat-interface').style.display = 'block';
            });
            
            function handleSubmit() {
                const question = userInput.value.trim();
                if (question) {
                    displayUserMessage(question);
                    userInput.value = '';
                    
                    setTimeout(() => {
                        processQuestion(question.toLowerCase());
                    }, 500);
                }
            }
            
            function displayUserMessage(message) {
                chatDisplay.innerHTML += `<div class="question">You: ${message}</div>`;
                chatDisplay.scrollTop = chatDisplay.scrollHeight;
            }
            
            function displayResponse(message, followUp = []) {
                let responseHTML = `<div class="response">NetLearn: ${message}</div>`;
                
                if (followUp.length > 0) {
                    responseHTML += `<div class="follow-up">Follow-up questions:<br>`;
                    followUp.forEach(followUpQuestion => {
                        responseHTML += `<button class="follow-up-btn" onclick="handleFollowUp('${escapeHtml(followUpQuestion)}')">${followUpQuestion}</button>`;
                    });
                    responseHTML += `</div>`;
                }
                
                chatDisplay.innerHTML += responseHTML;
                chatDisplay.scrollTop = chatDisplay.scrollHeight;
            }
            
            function processQuestion(question) {
                // Check for quiz command
                if (question === 'quiz') {
                    displayResponse(knowledgeBase.quiz.response, knowledgeBase.quiz.followUp);
                    return;
                }
                
                // Check for quiz selection
                const quizTopics = Object.keys(quizDatabase);
                for (const topic of quizTopics) {
                    if (question.includes(topic.toLowerCase())) {
                        startQuiz(topic);
                        return;
                    }
                }
                
                // Check knowledge base
                let bestMatch = knowledgeBase.default;
                let highestScore = 0;
                
                for (const [key, value] of Object.entries(knowledgeBase)) {
                    if (key === 'default' || key === 'quiz') continue;
                    
                    const score = calculateMatchScore(question, key);
                    if (score > highestScore) {
                        highestScore = score;
                        bestMatch = value;
                    }
                }
                
                displayResponse(bestMatch.response, bestMatch.followUp);
            }
            
            function calculateMatchScore(question, keyword) {
                const words = question.split(' ');
                const keywordWords = keyword.split(' ');
                let score = 0;
                
                for (const word of words) {
                    for (const kw of keywordWords) {
                        if (word.includes(kw)) {
                            score += kw.length;
                        }
                    }
                }
                
                return score;
            }
            
            function startQuiz(topic) {
                const quiz = quizDatabase[topic];
                if (!quiz) return;
                
                // Hide chat interface
                document.getElementById('chat-interface').style.display = 'none';
                
                // Show quiz interface
                quizInterface.style.display = 'block';
                quizTitle.textContent = quiz.title;
                quizDescription.textContent = quiz.description;
                
                // Display questions
                quizQuestions.innerHTML = '';
                quiz.questions.forEach((q, index) => {
                    const questionDiv = document.createElement('div');
                    questionDiv.className = 'quiz-question';
                    questionDiv.innerHTML = `
                        <h3>Question ${index + 1}: ${q.question}</h3>
                        ${q.options.map((opt, i) => `
                            <label class="quiz-option">
                                <input type="radio" name="q${index}" value="${i}">
                                ${opt}
                            </label>
                        `).join('')}
                        <div class="quiz-explanation" style="display:none; margin-top:10px; color:#666;">
                            ${q.explanation}
                        </div>
                    `;
                    quizQuestions.appendChild(questionDiv);
                    
                    // Add event listeners to radio buttons
                    const radios = questionDiv.querySelectorAll('input[type="radio"]');
                    radios.forEach(radio => {
                        radio.addEventListener('change', function() {
                            const explanation = questionDiv.querySelector('.quiz-explanation');
                            explanation.style.display = 'block';
                        });
                    });
                });
            }
            
            window.handleFollowUp = function(question) {
                displayUserMessage(question);
                setTimeout(() => {
                    processQuestion(question.toLowerCase());
                }, 500);
            };
            
            function escapeHtml(unsafe) {
                return unsafe
                    .replace(/&/g, "&amp;")
                    .replace(/</g, "&lt;")
                    .replace(/>/g, "&gt;")
                    .replace(/"/g, "&quot;")
                    .replace(/'/g, "&#039;");
            }
        });
    </script>
</body>
</html>
