# Computer Networks Lab (LAB_CN)

This repository contains practical implementations and experiments for Computer Networks Lab coursework, covering socket programming, network protocols, synchronization problems, and network topology design.

## 📋 Table of Contents

- [Overview](#overview)
- [Lab Experiments](#lab-experiments)
- [Network Topology Design](#network-topology-design)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [How to Run](#how-to-run)
- [Lab Programs Description](#lab-programs-description)
- [Contributing](#contributing)

## 🔍 Overview

This repository demonstrates fundamental concepts in computer networking including:
- TCP/IP socket programming in C
- Client-server architecture
- Multi-client handling using processes and threads
- Reader-Writer synchronization problem
- Network topology design and configuration using Cisco Packet Tracer
- IPv4 and IPv6 addressing and configuration
- Peer-to-Peer (P2P) network implementation
- Dual-stack networking (IPv4/IPv6)

## 🧪 Lab Experiments

### Lab 2: Basic Client-Server Communication
**Files:** `lab2_client.c`, `lab2_server.c`

A simple TCP-based client-server application demonstrating:
- Socket creation and binding
- Connection establishment
- Bidirectional message exchange
- Proper socket cleanup

**Features:**
- Server listens on port 8080
- Client connects to server at IP 192.168.0.154
- Exchange of greeting messages
- Graceful connection termination

### Lab 3: Interactive Echo Server
**Files:** `lab3_client.c`, `lab3_server.c`

An advanced implementation showcasing:
- **Client**: Interactive command-line interface for sending messages
- **Server**: Reader-Writer problem implementation using semaphores and threads
- Thread-based concurrent client handling
- Synchronization mechanisms for safe resource access

**Features:**
- Real-time message echoing
- Multi-threaded server architecture
- Reader-Writer synchronization using POSIX semaphores
- Support for up to 50 concurrent threads
- Continuous communication until "exit" command

### Multi-Client Server
**File:** `server.c`

A production-ready multi-client server using process forking:
- Handles multiple simultaneous client connections
- Process-based concurrency model
- Each client handled in a separate child process
- Zombie process prevention with SIGCHLD handling
- Robust error handling and logging

## 🌐 Network Topology Design

This repository also includes work done in **Cisco Packet Tracer**, including:

### Network Design Activities
- Designed and implemented various network topologies (Star, Mesh, Bus, Ring)
- Configured routers and switches for inter-network communication
- **Implemented IPv4 addressing schemes with proper subnetting**
- **Configured IPv6 addresses and demonstrated IPv6 connectivity**
- **Designed and implemented Peer-to-Peer (P2P) network architecture**
- Set up DHCP servers for dynamic IP allocation
- Implemented VLANs for network segmentation
- Configured static and dynamic routing protocols
- Tested connectivity using ping and traceroute commands
- Configured both IPv4 and IPv6 dual-stack environments

### Skills Demonstrated
- Network planning and IP addressing (IPv4 and IPv6)
- Router and switch configuration
- Protocol implementation and dual-stack networking
- Peer-to-Peer network design and implementation
- Network troubleshooting and testing
- Documentation of network designs
- Understanding of direct device-to-device communication

## 📦 Prerequisites

### For C Programs:
- GCC compiler (version 7.0 or higher)
- Linux/Unix operating system (Ubuntu, Debian, CentOS, etc.)
- POSIX threads library (pthread)
- Basic knowledge of C programming and networking concepts

### For Network Topology Design:
- Cisco Packet Tracer (version 7.3 or higher)
- Understanding of network fundamentals
- Knowledge of IPv4 and IPv6 addressing

## 🔧 Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/ankitkr9911/LAB_CN.git
cd LAB_CN
```

### 2. Install Required Tools
```bash
# For Ubuntu/Debian
sudo apt-get update
sudo apt-get install build-essential gcc

# Verify installation
gcc --version
```

### 3. Install Cisco Packet Tracer (Optional)
Download from [Cisco Networking Academy](https://www.netacad.com/courses/packet-tracer) and follow installation instructions for your operating system.

## 🚀 How to Run

### Lab 2: Basic Client-Server

**Terminal 1 (Server):**
```bash
gcc lab2_server.c -o server
./server
```

**Terminal 2 (Client):**
```bash
gcc lab2_client.c -o client
./client
```

### Lab 3: Interactive Echo Server

**Terminal 1 (Server):**
```bash
gcc lab3_server.c -o echo_server -lpthread
./echo_server
```

**Terminal 2 (Client):**
```bash
gcc lab3_client.c -o echo_client
./echo_client
```

Then type messages in the client terminal. Type `exit` to quit.

### Multi-Client Server

**Terminal 1 (Server):**
```bash
gcc server.c -o multi_server
./multi_server
```

**Terminal 2, 3, ... (Multiple Clients):**
```bash
gcc lab3_client.c -o client
./client
```

## 📚 Lab Programs Description

### 1. **Basic Socket Programming (Lab 2)**
   - Demonstrates fundamental socket operations
   - IPv4 address configuration
   - TCP connection establishment
   - Message transmission and reception

### 2. **Reader-Writer Problem (Lab 3 Server)**
   - Classic synchronization problem implementation
   - Multiple readers can access resource simultaneously
   - Writers need exclusive access
   - Uses semaphores for synchronization
   - Thread-safe implementation

### 3. **Multi-Client Handling (server.c)**
   - Process forking for concurrent clients
   - Independent client handling
   - Prevents zombie processes
   - Scalable architecture

### 4. **Network Configuration in Cisco Packet Tracer**
   - **IPv4 Configuration:**
     - Static IP addressing
     - Subnet mask configuration
     - Default gateway setup
     - IP address assignment to network devices
   
   - **IPv6 Configuration:**
     - IPv6 address assignment (Global Unicast, Link-Local)
     - IPv6 routing configuration
     - Dual-stack implementation
     - IPv6 connectivity testing
   
   - **Peer-to-Peer Network:**
     - Direct device-to-device communication
     - Crossover cable configuration
     - P2P file sharing simulation
     - Two-node network setup without intermediary devices
     - Configured static IP addresses for peer devices
     - Tested bidirectional communication between peers

## 🎓 Learning Outcomes

After completing these labs, you will understand:
- Socket programming in C
- Client-server communication protocols
- Process and thread management
- Synchronization mechanisms
- Concurrent programming concepts
- Network design principles
- IP addressing and routing (IPv4 and IPv6)
- Peer-to-Peer network architecture
- Network device configuration
- Dual-stack networking implementation
- Direct device communication without intermediary infrastructure

## 🛠️ Troubleshooting

### Common Issues:

**1. Address Already in Use**
```bash
# Wait for a few seconds or change the port number
# Or use SO_REUSEADDR socket option (already implemented in server code)
```

**2. Permission Denied**
```bash
# Use a port number above 1024
# Or run with sudo (not recommended)
```

**3. Connection Refused**
```bash
# Ensure server is running first
# Check if firewall is blocking the port
# Verify the IP address in client code matches server IP
```

**4. Compilation Errors with pthread**
```bash
# Make sure to link pthread library
gcc filename.c -o output -lpthread
```

## 📝 Notes

- Lab 2 and Lab 3 clients use different IP addresses (192.168.0.154 and 192.168.0.255). Update these according to your network configuration.
- Server programs bind to `INADDR_ANY`, accepting connections on all network interfaces.
- Lab 3 server uses port 8989 while others use 8080.
- The multi-client server (server.c) uses port 8080.
- Always compile with appropriate flags, especially `-lpthread` for threaded programs.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for:
- Bug fixes
- Code improvements
- Additional networking experiments
- Documentation enhancements
- New network topology designs

## 📄 License

This project is open source and available for educational purposes.

## 👤 Author

**Ankit Kumar**
- GitHub: [@ankitkr9911](https://github.com/ankitkr9911)

---
