<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Laiden's Networking Classroom - Virtual Networking Classroom</title>
    <style>
        /* [Previous CSS styles remain exactly the same] */
    </style>
</head>
<body>
    <!-- [Previous HTML structure remains the same] -->
    
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
            "default": {
                response: "I'm sorry, I can only answer questions about computer networking topics. Could you ask me something about networking concepts like TCP/IP, routing, switching, network security, wireless networking, or cloud networking?",
                followUp: []
            }
        };

        // Quiz database - 10 questions per quiz
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
                    },
                    {
                        question: "What is the default subnet mask for a Class B IP address?",
                        options: [
                            "255.0.0.0",
                            "255.255.0.0",
                            "255.255.255.0",
                            "255.255.255.255"
                        ],
                        answer: 1,
                        explanation: "Class B addresses use the first two octets for network identification, with a default subnet mask of 255.255.0.0."
                    },
                    {
                        question: "Which device operates at the Data Link layer of the OSI model?",
                        options: [
                            "Router",
                            "Hub",
                            "Switch",
                            "Firewall"
                        ],
                        answer: 2,
                        explanation: "Switches operate at Layer 2 (Data Link) and use MAC addresses to forward frames."
                    },
                    {
                        question: "What is the main function of ARP?",
                        options: [
                            "To resolve IP addresses to MAC addresses",
                            "To route packets between networks",
                            "To encrypt network traffic",
                            "To manage wireless connections"
                        ],
                        answer: 0,
                        explanation: "ARP (Address Resolution Protocol) maps IP addresses to MAC addresses on local networks."
                    },
                    {
                        question: "Which network topology provides the highest redundancy?",
                        options: [
                            "Star",
                            "Bus",
                            "Ring",
                            "Mesh"
                        ],
                        answer: 3,
                        explanation: "Mesh topology provides multiple paths between nodes, offering the highest redundancy."
                    },
                    {
                        question: "What is the purpose of a default gateway?",
                        options: [
                            "To connect devices within the same network",
                            "To route traffic between different networks",
                            "To encrypt all network communications",
                            "To filter malicious traffic"
                        ],
                        answer: 1,
                        explanation: "A default gateway routes traffic from a local network to other networks (typically a router)."
                    },
                    {
                        question: "Which protocol is used to automatically assign IP addresses to devices?",
                        options: [
                            "DNS",
                            "DHCP",
                            "FTP",
                            "SNMP"
                        ],
                        answer: 1,
                        explanation: "DHCP (Dynamic Host Configuration Protocol) automatically assigns IP addresses to devices on a network."
                    },
                    {
                        question: "What is the primary function of the Transport layer?",
                        options: [
                            "To physically transmit bits across the network",
                            "To establish end-to-end communication between applications",
                            "To convert data formats between systems",
                            "To manage network security policies"
                        ],
                        answer: 1,
                        explanation: "The Transport layer (Layer 4) provides end-to-end communication services for applications."
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
                        question: "What is the administrative distance of directly connected routes?",
                        options: [
                            "0",
                            "1",
                            "90",
                            "110"
                        ],
                        answer: 0,
                        explanation: "Directly connected routes have the most trusted administrative distance of 0."
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
                    },
                    {
                        question: "Which protocol prevents switching loops in a redundant topology?",
                        options: [
                            "VTP",
                            "STP",
                            "RIP",
                            "OSPF"
                        ],
                        answer: 1,
                        explanation: "STP (Spanning Tree Protocol) prevents switching loops by blocking redundant paths."
                    },
                    {
                        question: "What is the default administrative distance of OSPF?",
                        options: [
                            "90",
                            "100",
                            "110",
                            "120"
                        ],
                        answer: 2,
                        explanation: "OSPF has a default administrative distance of 110."
                    },
                    {
                        question: "Which switching method has the lowest latency?",
                        options: [
                            "Store-and-forward",
                            "Cut-through",
                            "Fragment-free",
                            "Adaptive switching"
                        ],
                        answer: 1,
                        explanation: "Cut-through switching has the lowest latency as it begins forwarding frames before receiving the entire frame."
                    },
                    {
                        question: "What is the purpose of a trunk port?",
                        options: [
                            "To connect end devices",
                            "To carry traffic for multiple VLANs",
                            "To provide internet access",
                            "To filter malicious traffic"
                        ],
                        answer: 1,
                        explanation: "Trunk ports carry traffic for multiple VLANs between switches."
                    },
                    {
                        question: "Which routing protocol is considered path vector?",
                        options: [
                            "RIP",
                            "OSPF",
                            "EIGRP",
                            "BGP"
                        ],
                        answer: 3,
                        explanation: "BGP (Border Gateway Protocol) is a path vector protocol used between autonomous systems."
                    },
                    {
                        question: "What is the purpose of VTP?",
                        options: [
                            "To synchronize VLAN information across switches",
                            "To route between VLANs",
                            "To encrypt VLAN traffic",
                            "To monitor VLAN performance"
                        ],
                        answer: 0,
                        explanation: "VTP (VLAN Trunking Protocol) synchronizes VLAN information across switches in the same domain."
                    },
                    {
                        question: "Which EIGRP table contains all learned routes?",
                        options: [
                            "Neighbor table",
                            "Topology table",
                            "Routing table",
                            "ARP table"
                        ],
                        answer: 1,
                        explanation: "EIGRP's topology table contains all routes learned from neighbors, while the routing table contains only the best routes."
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
                    },
                    {
                        question: "Which protocol provides secure remote access over a web browser?",
                        options: [
                            "IPsec",
                            "SSL VPN",
                            "PPTP",
                            "L2TP"
                        ],
                        answer: 1,
                        explanation: "SSL VPN provides secure remote access through a web browser without requiring client software."
                    },
                    {
                        question: "What is the primary purpose of 802.1X?",
                        options: [
                            "Wireless encryption",
                            "Port-based network access control",
                            "VLAN tagging",
                            "Quality of service"
                        ],
                        answer: 1,
                        explanation: "802.1X provides port-based network access control using authentication."
                    },
                    {
                        question: "Which type of firewall maintains state information?",
                        options: [
                            "Packet-filtering",
                            "Stateful",
                            "Proxy",
                            "Application-level"
                        ],
                        answer: 1,
                        explanation: "Stateful firewalls track the state of network connections."
                    },
                    {
                        question: "What is the purpose of a honeypot?",
                        options: [
                            "To attract and analyze attacks",
                            "To encrypt all network traffic",
                            "To block malicious websites",
                            "To filter spam emails"
                        ],
                        answer: 0,
                        explanation: "A honeypot is a security mechanism to detect and analyze attacks."
                    },
                    {
                        question: "Which protocol is used for AAA services?",
                        options: [
                            "RADIUS",
                            "SNMP",
                            "DHCP",
                            "DNS"
                        ],
                        answer: 0,
                        explanation: "RADIUS provides Authentication, Authorization, and Accounting (AAA) services."
                    },
                    {
                        question: "What is the primary security risk of WEP?",
                        options: [
                            "Weak encryption",
                            "No authentication",
                            "Slow performance",
                            "Complex configuration"
                        ],
                        answer: 0,
                        explanation: "WEP uses weak RC4 encryption that can be easily cracked."
                    },
                    {
                        question: "Which type of attack floods a network with ICMP echo requests?",
                        options: [
                            "Phishing",
                            "Ping of Death",
                            "Smurf",
                            "SYN flood"
                        ],
                        answer: 2,
                        explanation: "A Smurf attack floods a network with ICMP echo requests using broadcast addresses."
                    },
                    {
                        question: "What is the purpose of certificate authorities in PKI?",
                        options: [
                            "To issue and verify digital certificates",
                            "To encrypt all network traffic",
                            "To filter malicious websites",
                            "To authenticate wireless clients"
                        ],
                        answer: 0,
                        explanation: "Certificate Authorities (CAs) issue and verify digital certificates in a PKI system."
                    }
                ]
            },
            "wireless networking": {
                title: "Wireless Networking Quiz",
                description: "Test your knowledge of wireless standards, security, and deployment.",
                timeLimit: 15,
                questions: [
                    {
                        question: "Which wireless standard operates exclusively in the 5GHz band?",
                        options: [
                            "802.11a",
                            "802.11b",
                            "802.11g",
                            "802.11n"
                        ],
                        answer: 0,
                        explanation: "802.11a operates exclusively in the 5GHz band."
                    },
                    {
                        question: "What is the maximum theoretical speed of 802.11ac (Wave 2)?",
                        options: [
                            "54 Mbps",
                            "300 Mbps",
                            "1.3 Gbps",
                            "6.9 Gbps"
                        ],
                        answer: 3,
                        explanation: "802.11ac Wave 2 can theoretically reach up to 6.9 Gbps with 8 streams and 160MHz channels."
                    },
                    {
                        question: "Which security protocol introduced Simultaneous Authentication of Equals (SAE)?",
                        options: [
                            "WPA",
                            "WPA2",
                            "WPA3",
                            "WEP"
                        ],
                        answer: 2,
                        explanation: "WPA3 introduced SAE to replace the vulnerable PSK authentication method."
                    },
                    {
                        question: "What is the purpose of CSMA/CA in wireless networks?",
                        options: [
                            "Encrypt data transmissions",
                            "Prevent signal interference",
                            "Manage channel allocation",
                            "Authenticate wireless clients"
                        ],
                        answer: 1,
                        explanation: "CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance) helps prevent collisions in wireless transmissions."
                    },
                    {
                        question: "Which channels are non-overlapping in the 2.4GHz band?",
                        options: [
                            "1, 2, 3",
                            "1, 5, 9",
                            "1, 6, 11",
                            "3, 7, 11"
                        ],
                        answer: 2,
                        explanation: "Channels 1, 6, and 11 are non-overlapping in the 2.4GHz band."
                    },
                    {
                        question: "What is the primary benefit of MIMO technology?",
                        options: [
                            "Increased range",
                            "Higher data rates",
                            "Better security",
                            "Lower power consumption"
                        ],
                        answer: 1,
                        explanation: "MIMO (Multiple Input Multiple Output) increases data rates by using multiple antennas."
                    },
                    {
                        question: "Which wireless topology allows devices to communicate directly without an access point?",
                        options: [
                            "Infrastructure",
                            "Ad-hoc",
                            "Mesh",
                            "Point-to-multipoint"
                        ],
                        answer: 1,
                        explanation: "Ad-hoc mode allows devices to communicate directly without an access point."
                    },
                    {
                        question: "What is the purpose of a wireless site survey?",
                        options: [
                            "To detect unauthorized access points",
                            "To optimize access point placement",
                            "To monitor network usage",
                            "To test security vulnerabilities"
                        ],
                        answer: 1,
                        explanation: "A wireless site survey helps determine optimal access point placement for coverage and performance."
                    },
                    {
                        question: "Which technology allows a single access point to serve multiple SSIDs?",
                        options: [
                            "VLAN tagging",
                            "MIMO",
                            "Beamforming",
                            "Channel bonding"
                        ],
                        answer: 0,
                        explanation: "VLAN tagging allows a single access point to serve multiple SSIDs mapped to different VLANs."
                    },
                    {
                        question: "What is the main advantage of 802.11ax (Wi-Fi 6)?",
                        options: [
                            "Higher throughput in dense environments",
                            "Longer range",
                            "Simpler configuration",
                            "Lower cost"
                        ],
                        answer: 0,
                        explanation: "802.11ax (Wi-Fi 6) improves throughput in dense environments using OFDMA and other technologies."
                    }
                ]
            },
            "cloud networking": {
                title: "Cloud Networking Quiz",
                description: "Test your knowledge of virtual networks, cloud services, and hybrid connectivity.",
                timeLimit: 15,
                questions: [
                    {
                        question: "What is the AWS equivalent of a virtual network?",
                        options: [
                            "VNet",
                            "VPC",
                            "Subnet",
                            "Availability Zone"
                        ],
                        answer: 1,
                        explanation: "AWS uses VPC (Virtual Private Cloud) for virtual networking."
                    },
                    {
                        question: "Which Azure service provides dedicated private network connectivity?",
                        options: [
                            "VPN Gateway",
                            "ExpressRoute",
                            "Load Balancer",
                            "Traffic Manager"
                        ],
                        answer: 1,
                        explanation: "Azure ExpressRoute provides dedicated private network connectivity to Azure."
                    },
                    {
                        question: "What is the purpose of a security group in cloud networking?",
                        options: [
                            "To define network topology",
                            "To control inbound/outbound traffic",
                            "To manage user permissions",
                            "To encrypt data at rest"
                        ],
                        answer: 1,
                        explanation: "Security groups act as virtual firewalls controlling inbound and outbound traffic."
                    },
                    {
                        question: "Which technology enables network function virtualization?",
                        options: [
                            "SDN",
                            "NFV",
                            "IaaS",
                            "PaaS"
                        ],
                        answer: 1,
                        explanation: "NFV (Network Function Virtualization) virtualizes network functions that traditionally ran on dedicated hardware."
                    },
                    {
                        question: "What is the primary benefit of a content delivery network (CDN)?",
                        options: [
                            "Increased security",
                            "Reduced latency for end users",
                            "Lower cloud costs",
                            "Simpler network management"
                        ],
                        answer: 1,
                        explanation: "CDNs reduce latency by caching content at edge locations closer to end users."
                    },
                    {
                        question: "Which AWS service provides global network acceleration?",
                        options: [
                            "Direct Connect",
                            "Global Accelerator",
                            "Route 53",
                            "CloudFront"
                        ],
                        answer: 1,
                        explanation: "AWS Global Accelerator improves performance by routing traffic through AWS's global network."
                    },
                    {
                        question: "What is the purpose of a transit gateway?",
                        options: [
                            "To connect VPCs and on-premises networks centrally",
                            "To provide internet access",
                            "To encrypt all network traffic",
                            "To manage DNS records"
                        ],
                        answer: 0,
                        explanation: "Transit gateways simplify network architecture by centrally connecting VPCs and on-premises networks."
                    },
                    {
                        question: "Which Azure networking service provides load balancing at layer 7?",
                        options: [
                            "Azure Load Balancer",
                            "Application Gateway",
                            "Traffic Manager",
                            "Front Door"
                        ],
                        answer: 1,
                        explanation: "Azure Application Gateway provides layer 7 (application layer) load balancing."
                    },
                    {
                        question: "What is the primary purpose of a cloud NAT gateway?",
                        options: [
                            "To allow outbound internet access for private instances",
                            "To provide inbound access to instances",
                            "To encrypt traffic between regions",
                            "To connect multiple VPCs"
                        ],
                        answer: 0,
                        explanation: "NAT gateways allow private instances to initiate outbound internet connections while preventing inbound connections."
                    },
                    {
                        question: "Which GCP service provides global load balancing?",
                        options: [
                            "Cloud Load Balancing",
                            "Cloud Armor",
                            "Cloud CDN",
                            "Cloud Interconnect"
                        ],
                        answer: 0,
                        explanation: "GCP's Cloud Load Balancing provides global, cross-region load balancing."
                    }
                ]
            },
            "network automation": {
                title: "Network Automation Quiz",
                description: "Test your knowledge of automation tools, APIs, and infrastructure as code.",
                timeLimit: 15,
                questions: [
                    {
                        question: "Which protocol is used for network configuration management?",
                        options: [
                            "NETCONF",
                            "SNMP",
                            "RESTCONF",
                            "SSH"
                        ],
                        answer: 0,
                        explanation: "NETCONF is a network management protocol for installing, manipulating, and deleting configurations."
                    },
                    {
                        question: "What is the primary benefit of infrastructure as code?",
                        options: [
                            "Faster network speeds",
                            "Consistent, repeatable deployments",
                            "Better security",
                            "Lower hardware costs"
                        ],
                        answer: 1,
                        explanation: "Infrastructure as code enables consistent, repeatable deployments through version-controlled configuration files."
                    },
                    {
                        question: "Which tool is commonly used for network automation with YAML?",
                        options: [
                            "Ansible",
                            "Puppet",
                            "Chef",
                            "Terraform"
                        ],
                        answer: 0,
                        explanation: "Ansible uses YAML for its playbooks to automate network configurations."
                    },
                    {
                        question: "What is the purpose of YANG models in network automation?",
                        options: [
                            "To define network device configurations",
                            "To encrypt automation scripts",
                            "To visualize network topology",
                            "To monitor network performance"
                        ],
                        answer: 0,
                        explanation: "YANG is a data modeling language used to model configuration and state data for network devices."
                    },
                    {
                        question: "Which API type is commonly used for network automation?",
                        options: [
                            "SOAP",
                            "REST",
                            "GraphQL",
                            "gRPC"
                        ],
                        answer: 1,
                        explanation: "REST APIs are commonly used for network automation due to their simplicity and widespread support."
                    },
                    {
                        question: "What is the primary purpose of NAPALM?",
                        options: [
                            "To provide a multi-vendor API for network devices",
                            "To encrypt network automation traffic",
                            "To visualize network configurations",
                            "To monitor network performance"
                        ],
                        answer: 0,
                        explanation: "NAPALM (Network Automation and Programmability Abstraction Layer with Multivendor support) provides a unified API for different network devices."
                    },
                    {
                        question: "Which Python library is commonly used for SSH-based network automation?",
                        options: [
                            "Netmiko",
                            "NAPALM",
                            "PyEZ",
                            "ncclient"
                        ],
                        answer: 0,
                        explanation: "Netmiko is a multi-vendor library for SSH-based network device interaction."
                    },
                    {
                        question: "What is the primary benefit of CI/CD pipelines in network automation?",
                        options: [
                            "Faster network speeds",
                            "Automated testing and deployment of network changes",
                            "Better security",
                            "Lower hardware costs"
                        ],
                        answer: 1,
                        explanation: "CI/CD pipelines automate testing and deployment of network changes, improving reliability."
                    },
                    {
                        question: "Which protocol would you use to stream telemetry data from network devices?",
                        options: [
                            "SNMP",
                            "gRPC",
                            "NETCONF",
                            "REST"
                        ],
                        answer: 1,
                        explanation: "gRPC is commonly used for streaming telemetry data due to its efficiency."
                    },
                    {
                        question: "What is the purpose of Terraform in network automation?",
                        options: [
                            "To configure individual devices",
                            "To orchestrate entire network infrastructure",
                            "To monitor network performance",
                            "To visualize network topology"
                        ],
                        answer: 1,
                        explanation: "Terraform is an infrastructure as code tool that orchestrates entire network infrastructure deployments."
                    }
                ]
            }
        };

        // [Rest of the JavaScript implementation remains the same]
    </script>
</body>
</html>
