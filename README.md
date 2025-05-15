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
    <!-- [Previous HTML structure remains the same until the learning modules section] -->
    
    <div id="learn" class="tab-content active">
        <h2 class="section-title">Learning Modules</h2>
        <div class="learning-modules">
            <div class="module-card" data-topic="network fundamentals">
                <div class="module-image" style="background-color: #3498db;">
                    Network Fundamentals
                </div>
                <div class="module-content">
                    <h3>Network Fundamentals</h3>
                    <p>Learn the core concepts of computer networking including OSI model, TCP/IP, and basic network topologies.</p>
                    <button class="btn learn-btn">Start Learning</button>
                </div>
            </div>
            <div class="module-card" data-topic="routing and switching">
                <div class="module-image" style="background-color: #e74c3c;">
                    Routing & Switching
                </div>
                <div class="module-content">
                    <h3>Routing & Switching</h3>
                    <p>Understand how data is routed across networks and how switches manage local network traffic.</p>
                    <button class="btn learn-btn">Start Learning</button>
                </div>
            </div>
            <div class="module-card" data-topic="network security">
                <div class="module-image" style="background-color: #2ecc71;">
                    Network Security
                </div>
                <div class="module-content">
                    <h3>Network Security</h3>
                    <p>Explore essential security concepts including firewalls, encryption, VPNs, and threat detection systems.</p>
                    <button class="btn learn-btn">Start Learning</button>
                </div>
            </div>
            <div class="module-card" data-topic="wireless networking">
                <div class="module-image" style="background-color: #9b59b6;">
                    Wireless Networking
                </div>
                <div class="module-content">
                    <h3>Wireless Networking</h3>
                    <p>Master wireless protocols, standards, and security measures for modern wireless networks.</p>
                    <button class="btn learn-btn">Start Learning</button>
                </div>
            </div>
            <div class="module-card" data-topic="cloud networking">
                <div class="module-image" style="background-color: #f39c12;">
                    Cloud Networking
                </div>
                <div class="module-content">
                    <h3>Cloud Networking</h3>
                    <p>Discover how networking works in cloud environments and best practices for cloud infrastructure.</p>
                    <button class="btn learn-btn">Start Learning</button>
                </div>
            </div>
            <div class="module-card" data-topic="network automation">
                <div class="module-image" style="background-color: #1abc9c;">
                    Network Automation
                </div>
                <div class="module-content">
                    <h3>Network Automation</h3>
                    <p>Learn how to automate network tasks using scripting, APIs, and infrastructure as code.</p>
                    <button class="btn learn-btn">Start Learning</button>
                </div>
            </div>
        </div>
    </div>

    <!-- [Rest of the HTML remains the same] -->

    <script>
        // [Previous JavaScript remains the same until the knowledge base section]

        // Enhanced knowledge base with module-specific information
        const knowledgeBase = {
            "network fundamentals": {
                response: "Network fundamentals cover the basic concepts of computer networking. Key topics include:\n\n" +
                "• The OSI model and its 7 layers\n" +
                "• TCP/IP protocol suite\n" +
                "• Common network topologies (star, bus, ring, mesh)\n" +
                "• Network devices (hubs, switches, routers)\n" +
                "• IP addressing and subnetting basics\n\n" +
                "Would you like me to explain any of these concepts in more detail?",
                followUp: ["Explain OSI model", "What is TCP/IP?", "Tell me about network topologies"]
            },
            "routing and switching": {
                response: "Routing and switching are core networking functions:\n\n" +
                "• Switching operates at Layer 2 (Data Link) using MAC addresses\n" +
                "• Routing operates at Layer 3 (Network) using IP addresses\n" +
                "• Common routing protocols: OSPF, EIGRP, BGP\n" +
                "• VLANs and trunking for network segmentation\n" +
                "• Spanning Tree Protocol (STP) for loop prevention\n\n" +
                "Which aspect would you like to explore further?",
                followUp: ["Difference between routing and switching", "Explain OSPF", "What are VLANs?"]
            },
            "network security": {
                response: "Network security protects infrastructure from threats. Key areas include:\n\n" +
                "• Firewalls and intrusion prevention systems\n" +
                "• Encryption methods (AES, RSA, SSL/TLS)\n" +
                "• VPN technologies (IPsec, SSL VPN)\n" +
                "• Authentication methods (802.1X, RADIUS)\n" +
                "• Common attacks (DDoS, MITM, phishing)\n\n" +
                "What specific security topic interests you?",
                followUp: ["How do firewalls work?", "Explain VPNs", "Types of cyber attacks"]
            },
            "wireless networking": {
                response: "Wireless networking enables mobile connectivity. Main concepts:\n\n" +
                "• IEEE 802.11 standards (a/b/g/n/ac/ax)\n" +
                "• Wireless security (WPA2, WPA3)\n" +
                "• SSIDs and BSSIDs\n" +
                "• Channel planning and interference\n" +
                "• Wireless controllers and access points\n\n" +
                "Which wireless topic would you like to discuss?",
                followUp: ["Compare WiFi standards", "Explain WPA3", "What causes WiFi interference?"]
            },
            "cloud networking": {
                response: "Cloud networking involves:\n\n" +
                "• Virtual networks and software-defined networking\n" +
                "• Cloud provider networking (AWS VPC, Azure VNet)\n" +
                "• Hybrid cloud connectivity\n" +
                "• Load balancing and auto-scaling\n" +
                "• Content delivery networks (CDNs)\n\n" +
                "What cloud networking concept would you like to explore?",
                followUp: ["What is SDN?", "Explain AWS VPC", "How do CDNs work?"]
            },
            "network automation": {
                response: "Network automation includes:\n\n" +
                "• Infrastructure as Code (IaC) tools\n" +
                "• APIs for network devices\n" +
                "• Configuration management (Ansible, Puppet)\n" +
                "• Network programmability (Python, NETCONF)\n" +
                "• CI/CD pipelines for networking\n\n" +
                "Which automation topic would you like to learn about?",
                followUp: ["Network automation tools", "Python for networking", "What is NETCONF?"]
            },
            "default": {
                response: "I'm sorry, I don't have information about that specific networking topic. Could you rephrase your question or ask about something else? I can help with topics like TCP/IP, routing, switching, network security, wireless networking, and more!",
                followUp: []
            }
        };

        // Set up learning module buttons
        document.querySelectorAll('.learn-btn').forEach(button => {
            button.addEventListener('click', function() {
                const moduleCard = this.closest('.module-card');
                const topic = moduleCard.getAttribute('data-topic');
                
                // Switch to AI Assistant tab
                switchTab('chat');
                
                // After a short delay to allow tab switch, ask about the topic
                setTimeout(() => {
                    askAboutTopic(topic);
                }, 300);
            });
        });

        // Function to ask the AI about a specific topic
        function askAboutTopic(topic) {
            const knowledge = knowledgeBase[topic] || knowledgeBase['default'];
            
            // Clear previous messages except the first welcome message
            const messages = document.querySelectorAll('.chat-messages .message');
            for (let i = 1; i < messages.length; i++) {
                messages[i].remove();
            }
            
            // Add the topic question
            addMessage(`Tell me about ${topic}`, 'user');
            
            // Show typing indicator
            typingIndicator.style.display = 'flex';
            
            // Simulate AI thinking
            setTimeout(() => {
                typingIndicator.style.display = 'none';
                
                // Add AI response
                addMessage(knowledge.response, 'ai');
                
                // Add follow-up questions as buttons
                if (knowledge.followUp && knowledge.followUp.length > 0) {
                    const followUpDiv = document.createElement('div');
                    followUpDiv.className = 'follow-up-questions';
                    followUpDiv.style.marginTop = '10px';
                    
                    knowledge.followUp.forEach(question => {
                        const btn = document.createElement('button');
                        btn.textContent = question;
                        btn.className = 'follow-up-btn';
                        btn.style.margin = '5px';
                        btn.style.padding = '5px 10px';
                        btn.style.backgroundColor = '#f1f0f0';
                        btn.style.border = 'none';
                        btn.style.borderRadius = '4px';
                        btn.style.cursor = 'pointer';
                        
                        btn.addEventListener('click', () => {
                            chatInput.value = question;
                            sendMessage();
                        });
                        
                        followUpDiv.appendChild(btn);
                    });
                    
                    document.querySelector('.chat-messages').appendChild(followUpDiv);
                }
            }, 1500);
        }

        // [Rest of the JavaScript remains the same]
    </script>
</body>
</html>
