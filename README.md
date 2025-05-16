<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NetLearn - Virtual Networking Classroom</title>
    <style>
        /* [Previous CSS styles remain exactly the same] */
        /* ... */
        
        /* Add these new styles for the quiz functionality */
        .quiz-screen {
            display: none;
        }
        
        .quiz-screen.active {
            display: block;
        }
        
        .quiz-question {
            background-color: white;
            border-radius: 8px;
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .quiz-options {
            margin-top: 1rem;
        }
        
        .quiz-option {
            display: block;
            margin: 0.5rem 0;
            padding: 0.8rem;
            background-color: #f5f7fa;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.2s;
        }
        
        .quiz-option:hover {
            background-color: #e0e5ec;
        }
        
        .quiz-option.selected {
            background-color: #3498db;
            color: white;
        }
        
        .quiz-option.correct {
            background-color: #27ae60;
            color: white;
        }
        
        .quiz-option.incorrect {
            background-color: #e74c3c;
            color: white;
        }
        
        .quiz-navigation {
            display: flex;
            justify-content: space-between;
            margin-top: 1.5rem;
        }
        
        .quiz-results {
            text-align: center;
            padding: 2rem;
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .quiz-score {
            font-size: 2rem;
            font-weight: bold;
            color: #3498db;
            margin: 1rem 0;
        }
        
        .quiz-feedback {
            margin-top: 1rem;
            font-style: italic;
            color: #666;
        }
        
        .back-to-quizzes {
            margin-top: 1.5rem;
        }
    </style>
</head>
<body>
    <!-- [Previous HTML remains exactly the same until the quiz section] -->
    <!-- ... -->

    <div id="quiz" class="tab-content">
        <h2 class="section-title">Tests & Quizzes</h2>
        <div class="quiz-list">
            <div class="quiz-card">
                <h3>Network Fundamentals Quiz</h3>
                <div class="quiz-meta">
                    <span>10 questions</span>
                    <span>15 minutes</span>
                </div>
                <p>Test your understanding of basic networking concepts, protocols, and the OSI model.</p>
                <a href="#" class="btn start-quiz" data-quiz="fundamentals">Start Quiz</a>
            </div>
            <div class="quiz-card">
                <h3>IP Addressing & Subnetting</h3>
                <div class="quiz-meta">
                    <span>10 questions</span>
                    <span>15 minutes</span>
                </div>
                <p>Challenge yourself with questions on IP addressing, subnetting, and CIDR notation.</p>
                <a href="#" class="btn start-quiz" data-quiz="subnetting">Start Quiz</a>
            </div>
            <div class="quiz-card">
                <h3>Routing Protocols Test</h3>
                <div class="quiz-meta">
                    <span>10 questions</span>
                    <span>15 minutes</span>
                </div>
                <p>Evaluate your knowledge of various routing protocols like OSPF, EIGRP, and BGP.</p>
                <a href="#" class="btn start-quiz" data-quiz="routing">Start Quiz</a>
            </div>
            <div class="quiz-card">
                <h3>Network Security Assessment</h3>
                <div class="quiz-meta">
                    <span>10 questions</span>
                    <span>15 minutes</span>
                </div>
                <p>Test your understanding of network security principles, tools, and best practices.</p>
                <a href="#" class="btn start-quiz" data-quiz="security">Start Quiz</a>
            </div>
            <div class="quiz-card">
                <h3>Wireless Networking Quiz</h3>
                <div class="quiz-meta">
                    <span>10 questions</span>
                    <span>15 minutes</span>
                </div>
                <p>Demonstrate your knowledge of wireless standards, protocols, and security measures.</p>
                <a href="#" class="btn start-quiz" data-quiz="wireless">Start Quiz</a>
            </div>
            <div class="quiz-card">
                <h3>Final Certification Exam</h3>
                <div class="quiz-meta">
                    <span>20 questions</span>
                    <span>30 minutes</span>
                </div>
                <p>Comprehensive exam covering all aspects of networking to earn your NetLearn certification.</p>
                <a href="#" class="btn start-quiz" data-quiz="final">Start Exam</a>
            </div>
        </div>
    </div>

    <!-- Quiz Screens (hidden by default) -->
    <div id="fundamentals-quiz" class="quiz-screen">
        <div class="quiz-container">
            <h2 class="section-title">Network Fundamentals Quiz</h2>
            <div class="quiz-progress">Question 1 of 10</div>
            
            <div class="quiz-question">
                <h3>1. Which layer of the OSI model is responsible for routing and logical addressing?</h3>
                <div class="quiz-options">
                    <div class="quiz-option" data-correct="false">Physical Layer</div>
                    <div class="quiz-option" data-correct="false">Data Link Layer</div>
                    <div class="quiz-option" data-correct="true">Network Layer</div>
                    <div class="quiz-option" data-correct="false">Transport Layer</div>
                </div>
            </div>
            
            <div class="quiz-navigation">
                <button class="btn prev-question" disabled>Previous</button>
                <button class="btn next-question">Next</button>
            </div>
        </div>
    </div>

    <!-- [Previous HTML remains the same for other sections] -->
    <!-- ... -->

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // [Previous JavaScript remains the same until the quiz section]
            // ...

            // Quiz Data
            const quizzes = {
                fundamentals: {
                    title: "Network Fundamentals Quiz",
                    questions: [
                        {
                            question: "Which layer of the OSI model is responsible for routing and logical addressing?",
                            options: [
                                "Physical Layer",
                                "Data Link Layer",
                                "Network Layer",
                                "Transport Layer"
                            ],
                            correct: 2,
                            explanation: "The Network Layer (Layer 3) handles logical addressing and routing of data packets between networks."
                        },
                        {
                            question: "What does TCP stand for in networking?",
                            options: [
                                "Transmission Control Protocol",
                                "Transfer Connection Protocol",
                                "Technical Communication Protocol",
                                "Transport Control Packet"
                            ],
                            correct: 0,
                            explanation: "TCP stands for Transmission Control Protocol, which provides reliable, ordered, and error-checked delivery of data."
                        },
                        {
                            question: "Which of these is NOT a network topology?",
                            options: [
                                "Star",
                                "Bus",
                                "Ring",
                                "Cube"
                            ],
                            correct: 3,
                            explanation: "Cube is not a standard network topology. Common topologies include star, bus, ring, mesh, and hybrid combinations."
                        },
                        {
                            question: "What is the purpose of a MAC address?",
                            options: [
                                "To identify a device on the internet",
                                "To uniquely identify a network interface",
                                "To specify a website location",
                                "To encrypt network traffic"
                            ],
                            correct: 1,
                            explanation: "A MAC (Media Access Control) address uniquely identifies a network interface at the hardware level."
                        },
                        {
                            question: "Which protocol is used to translate domain names to IP addresses?",
                            options: [
                                "HTTP",
                                "FTP",
                                "DNS",
                                "DHCP"
                            ],
                            correct: 2,
                            explanation: "DNS (Domain Name System) translates human-readable domain names to machine-readable IP addresses."
                        },
                        {
                            question: "What is the default port number for HTTP traffic?",
                            options: [
                                "21",
                                "25",
                                "80",
                                "443"
                            ],
                            correct: 2,
                            explanation: "HTTP uses port 80 by default, while HTTPS (secure HTTP) uses port 443."
                        },
                        {
                            question: "Which device operates at the Data Link layer of the OSI model?",
                            options: [
                                "Router",
                                "Switch",
                                "Hub",
                                "Repeater"
                            ],
                            correct: 1,
                            explanation: "Switches operate at the Data Link layer (Layer 2), using MAC addresses to forward frames to the correct destination."
                        },
                        {
                            question: "What is the main purpose of the Transport layer?",
                            options: [
                                "To handle physical connections",
                                "To provide end-to-end communication control",
                                "To encrypt data transmissions",
                                "To manage network addressing"
                            ],
                            correct: 1,
                            explanation: "The Transport layer (Layer 4) provides end-to-end communication control and reliability."
                        },
                        {
                            question: "Which of these is a connection-oriented protocol?",
                            options: [
                                "UDP",
                                "TCP",
                                "IP",
                                "ICMP"
                            ],
                            correct: 1,
                            explanation: "TCP is connection-oriented, establishing a connection before data transfer and ensuring reliable delivery."
                        },
                        {
                            question: "What does the acronym LAN stand for?",
                            options: [
                                "Local Area Network",
                                "Large Access Node",
                                "Linked Area Nodes",
                                "Logical Address Network"
                            ],
                            correct: 0,
                            explanation: "LAN stands for Local Area Network, a network that connects devices in a limited geographical area."
                        }
                    ]
                },
                subnetting: {
                    title: "IP Addressing & Subnetting Quiz",
                    questions: [
                        // [10 subnetting questions...]
                    ]
                },
                routing: {
                    title: "Routing Protocols Quiz",
                    questions: [
                        // [10 routing questions...]
                    ]
                },
                // [Other quizzes...]
            };

            // Quiz Variables
            let currentQuiz = null;
            let currentQuestion = 0;
            let score = 0;
            let userAnswers = [];

            // Quiz Functions
            function startQuiz(quizId) {
                currentQuiz = quizzes[quizId];
                currentQuestion = 0;
                score = 0;
                userAnswers = [];
                
                // Hide all quiz screens
                document.querySelectorAll('.quiz-screen').forEach(screen => {
                    screen.classList.remove('active');
                });
                
                // Show this quiz screen
                document.getElementById(`${quizId}-quiz`).classList.add('active');
                
                // Load first question
                loadQuestion();
            }

            function loadQuestion() {
                const question = currentQuiz.questions[currentQuestion];
                const quizContainer = document.querySelector(`#${currentQuiz}-quiz .quiz-container`);
                
                // Update progress
                quizContainer.querySelector('.quiz-progress').textContent = 
                    `Question ${currentQuestion + 1} of ${currentQuiz.questions.length}`;
                
                // Clear previous question
                const questionContainer = quizContainer.querySelector('.quiz-question');
                questionContainer.innerHTML = '';
                
                // Add question
                const questionTitle = document.createElement('h3');
                questionTitle.textContent = `${currentQuestion + 1}. ${question.question}`;
                questionContainer.appendChild(questionTitle);
                
                // Add options
                const optionsContainer = document.createElement('div');
                optionsContainer.className = 'quiz-options';
                
                question.options.forEach((option, index) => {
                    const optionElement = document.createElement('div');
                    optionElement.className = 'quiz-option';
                    optionElement.textContent = option;
                    optionElement.dataset.index = index;
                    
                    // Check if user already answered this question
                    if (userAnswers[currentQuestion] !== undefined) {
                        if (index === question.correct) {
                            optionElement.classList.add('correct');
                        } else if (index === userAnswers[currentQuestion] && index !== question.correct) {
                            optionElement.classList.add('incorrect');
                        }
                    }
                    
                    optionElement.addEventListener('click', () => selectOption(optionElement, index));
                    optionsContainer.appendChild(optionElement);
                });
                
                questionContainer.appendChild(optionsContainer);
                
                // Update navigation buttons
                const prevBtn = quizContainer.querySelector('.prev-question');
                const nextBtn = quizContainer.querySelector('.next-question');
                
                prevBtn.disabled = currentQuestion === 0;
                nextBtn.textContent = currentQuestion === currentQuiz.questions.length - 1 ? 'Finish' : 'Next';
            }

            function selectOption(optionElement, optionIndex) {
                // Only allow selection if not already answered
                if (userAnswers[currentQuestion] !== undefined) return;
                
                // Clear any previous selection
                optionElement.parentElement.querySelectorAll('.quiz-option').forEach(opt => {
                    opt.classList.remove('selected');
                });
                
                // Select this option
                optionElement.classList.add('selected');
                userAnswers[currentQuestion] = optionIndex;
                
                // Check if correct
                const question = currentQuiz.questions[currentQuestion];
                if (optionIndex === question.correct) {
                    score++;
                }
            }

            function showResults() {
                const quizContainer = document.querySelector(`#${currentQuiz}-quiz .quiz-container`);
                quizContainer.innerHTML = `
                    <div class="quiz-results">
                        <h2>${currentQuiz.title} Results</h2>
                        <div class="quiz-score">${score}/${currentQuiz.questions.length}</div>
                        <p>You scored ${Math.round((score / currentQuiz.questions.length) * 100)}%</p>
                        
                        ${score === currentQuiz.questions.length ? 
                            '<p class="quiz-feedback">Perfect score! Excellent work!</p>' :
                            score >= currentQuiz.questions.length * 0.7 ?
                            '<p class="quiz-feedback">Good job! You have a solid understanding of this topic.</p>' :
                            score >= currentQuiz.questions.length * 0.5 ?
                            '<p class="quiz-feedback">Not bad! Consider reviewing the material and trying again.</p>' :
                            '<p class="quiz-feedback">Keep studying! You might want to review the learning materials before trying again.</p>'
                        }
                        
                        <a href="#" class="btn back-to-quizzes">Back to Quizzes</a>
                    </div>
                `;
                
                // Add event listener for back button
                quizContainer.querySelector('.back-to-quizzes').addEventListener('click', function(e) {
                    e.preventDefault();
                    document.getElementById(`${currentQuiz}-quiz`).classList.remove('active');
                });
            }

            // Event Listeners for Quiz Navigation
            document.addEventListener('click', function(e) {
                // Start quiz buttons
                if (e.target.classList.contains('start-quiz')) {
                    e.preventDefault();
                    startQuiz(e.target.dataset.quiz);
                }
                
                // Next question button
                if (e.target.classList.contains('next-question')) {
                    if (userAnswers[currentQuestion] === undefined) {
                        alert('Please select an answer before proceeding.');
                        return;
                    }
                    
                    if (currentQuestion < currentQuiz.questions.length - 1) {
                        currentQuestion++;
                        loadQuestion();
                    } else {
                        showResults();
                    }
                }
                
                // Previous question button
                if (e.target.classList.contains('prev-question')) {
                    if (currentQuestion > 0) {
                        currentQuestion--;
                        loadQuestion();
                    }
                }
            });

            // AI Assistant Knowledge Base
            const aiKnowledge = {
                "OSI Model": `The OSI (Open Systems Interconnection) model is a conceptual framework that standardizes the functions of a communication system into seven layers:
                
                <strong>Layer 7 - Application:</strong> Interface for user applications (HTTP, FTP, SMTP)
                <strong>Layer 6 - Presentation:</strong> Data translation, encryption (SSL, JPEG)
                <strong>Layer 5 - Session:</strong> Manages connections between applications (NetBIOS, RPC)
                <strong>Layer 4 - Transport:</strong> End-to-end connections, reliability (TCP, UDP)
                <strong>Layer 3 - Network:</strong> Logical addressing and routing (IP, ICMP, routers)
                <strong>Layer 2 - Data Link:</strong> Physical addressing, error detection (Ethernet, switches)
                <strong>Layer 1 - Physical:</strong> Physical connections, raw bit transmission (cables, hubs)
                
                Remember: "All People Seem To Need Data Processing" (Application to Physical)`,

                "TCP vs UDP": `TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are both transport layer protocols but serve different purposes:
                
                <strong>TCP:</strong>
                - Connection-oriented (establishes connection first)
                - Reliable with error checking and recovery
                - Guaranteed delivery in correct order
                - Flow control to prevent overwhelming receiver
                - Slower due to overhead
                - Used for: Web browsing (HTTP), email (SMTP), file transfers (FTP)
                
                <strong>UDP:</strong>
                - Connectionless (no handshake)
                - No reliability guarantees
                - No ordering of packets
                - No flow control
                - Faster with less overhead
                - Used for: Video streaming, VoIP, online games, DNS
                
                Choose TCP when reliability matters, UDP when speed is priority.`,

                "Subnetting": `Subnetting divides a large network into smaller subnetworks for better management and security:
                
                <strong>Key Concepts:</strong>
                - <strong>Subnet Mask:</strong> Determines network vs host portions (e.g., 255.255.255.0)
                - <strong>CIDR Notation:</strong> Compact representation (e.g., /24 = 255.255.255.0)
                - <strong>Network Address:</strong> First address in subnet (host bits all 0)
                - <strong>Broadcast Address:</strong> Last address (host bits all 1)
                
                <strong>Example:</strong> 192.168.1.0/24
                - Network: 192.168.1.0
                - First host: 192.168.1.1
                - Last host: 192.168.1.254
                - Broadcast: 192.168.1.255
                
                Subnetting helps reduce network congestion and improve security by isolating traffic.`,

                // [Add more topics as needed...]
            };

            // AI Assistant Functionality
            document.querySelector('.chat-send-btn').addEventListener('click', function() {
                const input = document.querySelector('.chat-input');
                const message = input.value.trim();
                
                if (message) {
                    // Add user message
                    addMessage(message, 'user');
                    
                    // Generate AI response
                    let response = "I'm not sure about that topic. Could you ask about something else?";
                    
                    // Check for known topics
                    for (const topic in aiKnowledge) {
                        if (message.toLowerCase().includes(topic.toLowerCase())) {
                            response = aiKnowledge[topic];
                            break;
                        }
                    }
                    
                    // Special case for TCP/UDP
                    if (message.toLowerCase().includes("tcp") && message.toLowerCase().includes("udp")) {
                        response = aiKnowledge["TCP vs UDP"];
                    }
                    
                    // Add AI response after a short delay
                    setTimeout(() => {
                        addMessage(response, 'ai');
                        document.querySelector('.chat-messages').scrollTop = 
                            document.querySelector('.chat-messages').scrollHeight;
                    }, 500);
                    
                    // Clear input
                    input.value = '';
                }
            });

            function addMessage(content, sender) {
                const messagesContainer = document.querySelector('.chat-messages');
                const messageDiv = document.createElement('div');
                messageDiv.className = `message ${sender}`;
                
                const contentDiv = document.createElement('div');
                contentDiv.className = 'message-content';
                contentDiv.innerHTML = content;
                
                messageDiv.appendChild(contentDiv);
                messagesContainer.appendChild(messageDiv);
            }

            // [Rest of your existing JavaScript...]
        });
    </script>
</body>
</html>
