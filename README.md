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
    <!-- [Previous HTML structure remains the same until the JavaScript section] -->
    
    <script>
        // [Previous JavaScript remains the same until the knowledge base section]

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
   • Firewalls: Security filtering

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

3. Key Differences:
   • Switches: Faster, work within same network
   • Routers: Connect different networks
   • Switches use hardware (ASICs) for forwarding
   • Routers use software for path determination

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

4. Authentication:
   • 802.1X: Port-based NAC
   • RADIUS/TACACS+: AAA services
   • Multi-factor authentication

5. Common Threats:
   • DDoS: Overwhelm resources
   • MITM: Eavesdropping attacks
   • Phishing: Social engineering
   • Zero-day exploits

Which security area would you like to explore further?`,
                followUp: ["How does SSL/TLS handshake work?", "What's the difference between IDS and IPS?", "Explain DMZ in network security"]
            },
            "wireless networking": {
                response: `Wireless networking enables mobile connectivity:

1. IEEE 802.11 Standards:
   • 802.11a: 5GHz, 54Mbps
   • 802.11b: 2.4GHz, 11Mbps
   • 802.11g: 2.4GHz, 54Mbps
   • 802.11n (WiFi 4): MIMO, 600Mbps
   • 802.11ac (WiFi 5): 5GHz, 1.3Gbps
   • 802.11ax (WiFi 6): OFDMA, 10Gbps

2. Wireless Security:
   • WEP: Broken, avoid
   • WPA: TKIP encryption
   • WPA2: AES-CCMP (current standard)
   • WPA3: SAE, 192-bit encryption

3. Components:
   • Access Points (APs)
   • Wireless Controllers
   • SSIDs for network identification
   • BSSIDs (MAC of AP)

4. Design Considerations:
   • Channel planning (1,6,11 for 2.4GHz)
   • Power settings
   • Roaming between APs
   • Interference from other devices

What specific wireless topic would you like to discuss?`,
                followUp: ["How does MIMO improve performance?", "Explain WPA3 security features", "What's the difference between 2.4GHz and 5GHz?"]
            },
            "cloud networking": {
                response: `Cloud networking transforms traditional infrastructure:

1. Key Concepts:
   • Virtual Networks (VPC/VNet)
   • Software Defined Networking (SDN)
   • Network Function Virtualization (NFV)
   • Hybrid cloud connectivity

2. Major Providers:
   • AWS: VPC, Direct Connect
   • Azure: VNet, ExpressRoute
   • GCP: VPC, Cloud Interconnect

3. Services:
   • Load Balancers (ALB/NLB)
   • Content Delivery Networks (CDN)
   • Auto-scaling groups
   • Serverless networking

4. Security:
   • Security Groups (stateful)
   • Network ACLs (stateless)
   • Web Application Firewalls
   • DDoS protection services

Which cloud networking concept would you like to explore?`,
                followUp: ["How does AWS VPC peering work?", "Explain Azure ExpressRoute", "What are the benefits of SDN?"]
            },
            "network automation": {
                response: `Network automation revolutionizes operations:

1. Tools and Technologies:
   • Ansible: Agentless automation
   • Puppet/Chef: Configuration management
   • Terraform: Infrastructure as Code
   • Python scripting (Netmiko, NAPALM)

2. Protocols and APIs:
   • NETCONF/YANG: Standardized config
   • REST APIs: Modern device interfaces
   • gRPC: High-performance telemetry

3. Use Cases:
   • Configuration management
   • Device provisioning
   • Change management
   • Compliance enforcement
   • Monitoring and remediation

4. CI/CD Pipelines:
   • Version control (Git)
   • Automated testing
   • Continuous deployment
   • Rollback procedures

What automation topic interests you most?`,
                followUp: ["How to use Ansible for network automation?", "Explain NETCONF/YANG models", "Python scripts for network tasks"]
            },
            "subnetting": {
                response: `Subnetting is essential for efficient IP addressing:

1. Key Concepts:
   • CIDR Notation (e.g., /24)
   • Subnet Masks (e.g., 255.255.255.0)
   • Network vs Host portions
   • VLSM (Variable Length Subnet Masking)

2. Calculation Steps:
   1. Determine needed subnets/hosts
   2. Borrow bits from host portion
   3. Calculate subnet mask
   4. Determine subnet ranges
   5. Identify network/broadcast addresses

3. Example: 192.168.1.0/24 divided into /26:
   • 4 subnets (2^2)
   • 62 hosts per subnet (2^6-2)
   • Subnet ranges:
     - 192.168.1.0-63
     - 192.168.1.64-127
     - 192.168.1.128-191
     - 192.168.1.192-255

Would you like practice problems or more examples?`,
                followUp: ["Show more subnetting examples", "How to calculate VLSM?", "IPv6 subnetting basics"]
            },
            "tcp vs udp": {
                response: `TCP and UDP are transport layer protocols:

TCP (Transmission Control Protocol):
• Connection-oriented (3-way handshake)
• Reliable delivery (acknowledgments)
• Ordered packet delivery
• Flow control (window sizing)
• Error checking and recovery
• Higher overhead (20-60 byte headers)
• Used by: HTTP, FTP, SMTP, SSH

UDP (User Datagram Protocol):
• Connectionless (no handshake)
• No delivery guarantees
• No ordering of packets
• No flow control
• Minimal error checking
• Lower overhead (8 byte headers)
• Used by: DNS, VoIP, video streaming, gaming

When to use each:
• TCP: When reliability is critical (web, email, file transfer)
• UDP: When speed is priority (real-time media, gaming)

Would you like examples of applications using each?`,
                followUp: ["Why does DNS use UDP?", "Explain TCP 3-way handshake", "How does VoIP handle UDP packet loss?"]
            },
            "default": {
                response: "I'm sorry, I don't have information about that specific networking topic. Could you rephrase your question or ask about something else? I can help with topics like TCP/IP, routing, switching, network security, wireless networking, subnetting, and more!",
                followUp: []
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
                    },
                    {
                        question: "Which protocol operates at the Transport layer and provides connectionless communication?",
                        options: [
                            "TCP",
                            "HTTP",
                            "UDP",
                            "IP"
                        ],
                        answer: 2,
                        explanation: "UDP (User Datagram Protocol) is connectionless and operates at the Transport layer, unlike TCP which is connection-oriented."
                    }
                ]
            },
            "ip addressing & subnetting": {
                title: "IP Addressing & Subnetting",
                description: "Challenge yourself with questions on IP addressing, subnetting, and CIDR notation.",
                timeLimit: 20,
                questions: [
                    {
                        question: "What is the network address for host 192.168.1.150/24?",
                        options: [
                            "192.168.1.0",
                            "192.168.1.1",
                            "192.168.0.0",
                            "192.168.1.255"
                        ],
                        answer: 0,
                        explanation: "With a /24 subnet mask, the network address is x.x.x.0 and the broadcast is x.x.x.255."
                    },
                    {
                        question: "How many usable host addresses are in a /28 subnet?",
                        options: [
                            "14",
                            "16",
                            "30",
                            "254"
                        ],
                        answer: 0,
                        explanation: "A /28 has 4 host bits (2^4=16 addresses). Subtract 2 for network and broadcast = 14 usable hosts."
                    },
                    {
                        question: "Which of these is a private IP address range?",
                        options: [
                            "10.0.0.0 - 10.255.255.255",
                            "172.15.0.0 - 172.31.255.255",
                            "192.168.0.0 - 192.169.255.255",
                            "169.254.0.0 - 169.254.255.255"
                        ],
                        answer: 0,
                        explanation: "The private ranges are 10.0.0.0/8, 172.16.0.0/12, and 192.168.0.0/16."
                    }
                ]
            },
            "routing protocols": {
                title: "Routing Protocols Test",
                description: "Evaluate your knowledge of various routing protocols like OSPF, EIGRP, and BGP.",
                timeLimit: 18,
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
                        question: "What is the administrative distance of EIGRP?",
                        options: [
                            "90",
                            "100",
                            "110",
                            "120"
                        ],
                        answer: 0,
                        explanation: "EIGRP has an AD of 90 for internal routes and 170 for external routes."
                    },
                    {
                        question: "Which protocol is considered the 'protocol of the Internet'?",
                        options: [
                            "OSPF",
                            "EIGRP",
                            "BGP",
                            "RIP"
                        ],
                        answer: 2,
                        explanation: "BGP (Border Gateway Protocol) is the path-vector protocol used to exchange routing information between autonomous systems on the Internet."
                    }
                ]
            }
        };

        // [Rest of the JavaScript implementation remains the same]
    </script>
</body>
</html>
