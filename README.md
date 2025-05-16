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
        .tab-container {
            display: flex;
            margin-bottom: 20px;
            border-bottom: 1px solid #ddd;
        }
        .tab {
            padding: 10px 20px;
            cursor: pointer;
            background-color: #f1f1f1;
            margin-right: 5px;
            border-radius: 5px 5px 0 0;
        }
        .tab.active {
            background-color: #3498db;
            color: white;
        }
        .content-area {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            padding: 20px;
            min-height: 500px;
        }
        .chat-container {
            height: 400px;
            overflow-y: auto;
            margin-bottom: 20px;
            border-bottom: 1px solid #eee;
            padding-bottom: 20px;
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
        .quiz-container {
            display: none;
        }
        .quiz-question {
            margin-bottom: 20px;
            padding: 15px;
            background-color: #f9f9f9;
            border-radius: 5px;
        }
        .quiz-options {
            margin-top: 10px;
        }
        .quiz-option {
            display: block;
            margin: 5px 0;
            padding: 8px;
            background-color: #eee;
            border-radius: 4px;
            cursor: pointer;
        }
        .quiz-option:hover {
            background-color: #ddd;
        }
        .notes-container {
            display: none;
        }
        .topic-container {
            display: none;
        }
        .active-content {
            display: block;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>NetLearn</h1>
            <p>Virtual Networking Classroom</p>
        </header>
        
        <div class="tab-container">
            <div class="tab active" data-tab="chat">Chat</div>
            <div class="tab" data-tab="topics">Topics</div>
            <div class="tab" data-tab="quizzes">Quizzes</div>
            <div class="tab" data-tab="notes">Notes</div>
        </div>
        
        <div class="content-area">
            <!-- Chat Tab -->
            <div class="chat-container active-content" id="chatContainer">
                <!-- Chat messages will appear here -->
            </div>
            
            <div class="input-area" id="chatInputArea">
                <input type="text" id="userInput" placeholder="Ask me anything about networking..." autocomplete="off">
                <button id="sendBtn">Send</button>
            </div>
            
            <!-- Topics Tab -->
            <div class="topic-container" id="topicsContainer">
                <h2>Networking Topics</h2>
                <div class="topics-list" id="topicsList">
                    <!-- Topics will be dynamically loaded here -->
                </div>
            </div>
            
            <!-- Quizzes Tab -->
            <div class="quiz-container" id="quizzesContainer">
                <h2>Networking Quizzes</h2>
                <div class="quizzes-list" id="quizzesList">
                    <!-- Quizzes will be dynamically loaded here -->
                </div>
                <div class="quiz-questions" id="quizQuestions" style="display:none;">
                    <!-- Quiz questions will appear here -->
                </div>
            </div>
            
            <!-- Notes Tab -->
            <div class="notes-container" id="notesContainer">
                <h2>My Notes</h2>
                <textarea id="notesTextarea" style="width:100%; height:400px;"></textarea>
                <button id="saveNotesBtn">Save Notes</button>
            </div>
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

        // Networking Topics
        const topics = {
            "Network Fundamentals": {
                content: `Network fundamentals form the foundation of all networking concepts...`,
                subtopics: ["OSI Model", "TCP/IP Protocol Suite", "Network Topologies", "Network Devices"]
            },
            "Routing and Switching": {
                content: `Routing and switching are core functions in networking...`,
                subtopics: ["Switching Concepts", "Routing Protocols", "VLANs", "STP"]
            },
            "Network Security": {
                content: `Network security is crucial for protecting infrastructure...`,
                subtopics: ["Firewalls", "Encryption", "VPNs", "Authentication"]
            }
        };

        // Quiz Database
        const quizzes = {
            "Network Fundamentals Quiz": {
                description: "Test your understanding of basic networking concepts",
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
            },
            "Routing and Switching Quiz": {
                description: "Test your knowledge of routing protocols and switching concepts",
                questions: [
                    {
                        question: "Which routing protocol uses the Dijkstra algorithm?",
                        options: ["RIP", "OSPF", "EIGRP", "BGP"],
                        answer: 1,
                        explanation: "OSPF is a link-state protocol that uses Dijkstra's algorithm."
                    }
                ]
            }
        };

        // ==================== UI FUNCTIONALITY ==================== //
        
        // Tab switching
        document.querySelectorAll('.tab').forEach(tab => {
            tab.addEventListener('click', () => {
                // Remove active class from all tabs
                document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
                // Add active class to clicked tab
                tab.classList.add('active');
                
                // Hide all content areas
                document.querySelectorAll('.chat-container, .topic-container, .quiz-container, .notes-container').forEach(container => {
                    container.style.display = 'none';
                });
                
                // Show the selected content area
                const tabName = tab.getAttribute('data-tab');
                document.getElementById(`${tabName}Container`).style.display = 'block';
                
                // Special handling for quizzes tab
                if (tabName === 'quizzes') {
                    loadQuizzesList();
                }
                
                // Special handling for topics tab
                if (tabName === 'topics') {
                    loadTopicsList();
                }
            });
        });

        // Load quizzes list
        function loadQuizzesList() {
            const quizzesList = document.getElementById('quizzesList');
            quizzesList.innerHTML = '';
            
            for (const [quizName, quizData] of Object.entries(quizzes)) {
                const quizElement = document.createElement('div');
                quizElement.className = 'quiz-item';
                quizElement.innerHTML = `
                    <h3>${quizName}</h3>
                    <p>${quizData.description}</p>
                    <button class="start-quiz" data-quiz="${quizName}">Start Quiz</button>
                `;
                quizzesList.appendChild(quizElement);
            }
            
            // Add event listeners to quiz buttons
            document.querySelectorAll('.start-quiz').forEach(button => {
                button.addEventListener('click', function() {
                    startQuiz(this.getAttribute('data-quiz'));
                });
            });
        }

        // Start a quiz
        function startQuiz(quizName) {
            const quiz = quizzes[quizName];
            const quizQuestions = document.getElementById('quizQuestions');
            const quizzesList = document.getElementById('quizzesList');
            
            quizzesList.style.display = 'none';
            quizQuestions.style.display = 'block';
            quizQuestions.innerHTML = `<h3>${quizName}</h3>`;
            
            quiz.questions.forEach((q, index) => {
                const questionElement = document.createElement('div');
                questionElement.className = 'quiz-question';
                questionElement.innerHTML = `
                    <p><strong>Question ${index + 1}:</strong> ${q.question}</p>
                    <div class="quiz-options">
                        ${q.options.map((option, i) => `
                            <div class="quiz-option" data-question="${index}" data-answer="${i}">${option}</div>
                        `).join('')}
                    </div>
                    <div class="quiz-explanation" id="explanation-${index}" style="display:none; margin-top:10px; padding:10px; background:#e8f5e9; border-radius:5px;">
                        ${q.explanation}
                    </div>
                `;
                quizQuestions.appendChild(questionElement);
            });
            
            // Add back button
            const backButton = document.createElement('button');
            backButton.textContent = 'Back to Quizzes';
            backButton.addEventListener('click', () => {
                quizQuestions.style.display = 'none';
                quizzesList.style.display = 'block';
            });
            quizQuestions.appendChild(backButton);
            
            // Add event listeners to options
            document.querySelectorAll('.quiz-option').forEach(option => {
                option.addEventListener('click', function() {
                    const questionIndex = this.getAttribute('data-question');
                    const answerIndex = this.getAttribute('data-answer');
                    const correctAnswer = quiz.questions[questionIndex].answer;
                    const explanation = document.getElementById(`explanation-${questionIndex}`);
                    
                    if (parseInt(answerIndex) === correctAnswer) {
                        this.style.backgroundColor = '#c8e6c9';
                    } else {
                        this.style.backgroundColor = '#ffcdd2';
                    }
                    
                    explanation.style.display = 'block';
                });
            });
        }

        // Load topics list
        function loadTopicsList() {
            const topicsList = document.getElementById('topicsList');
            topicsList.innerHTML = '';
            
            for (const [topicName, topicData] of Object.entries(topics)) {
                const topicElement = document.createElement('div');
                topicElement.className = 'topic-item';
                topicElement.innerHTML = `
                    <h3>${topicName}</h3>
                    <div class="subtopics">
                        ${topicData.subtopics.map(subtopic => `
                            <div class="subtopic">${subtopic}</div>
                        `).join('')}
                    </div>
                    <div class="topic-content" style="display:none;">
                        ${topicData.content}
                    </div>
                `;
                topicsList.appendChild(topicElement);
            }
        }

        // Notes functionality
        document.getElementById('saveNotesBtn').addEventListener('click', function() {
            const notes = document.getElementById('notesTextarea').value;
            localStorage.setItem('netlearn-notes', notes);
            alert('Notes saved successfully!');
        });

        // Load saved notes
        window.addEventListener('load', function() {
            const savedNotes = localStorage.getItem('netlearn-notes');
            if (savedNotes) {
                document.getElementById('notesTextarea').value = savedNotes;
            }
            
            // Display initial greeting in chat
            displayMessage('bot', generalKnowledge.greetings.response);
        });

        // ==================== CHAT FUNCTIONALITY ==================== //
        const chatContainer = document.getElementById('chatContainer');
        const userInput = document.getElementById('userInput');
        const sendBtn = document.getElementById('sendBtn');

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
            for (const [key, value] of Object.entries(topics)) {
                if (input.toLowerCase().includes(key.toLowerCase())) {
                    return {
                        response: value.content,
                        followUp: value.subtopics.map(sub => `Tell me about ${sub}`)
                    };
                }
            }
            
            return generalKnowledge.default;
        }
    </script>
</body>
</html>
