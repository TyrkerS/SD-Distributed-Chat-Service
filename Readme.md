# DISTRIBUTED CHAT SERVICE - PYTHON gRCP

**Language:** Python  
**README Language:** English

---

## ⭐ Project Summary
This project implements a simple **distributed chat service** using **gRPC** and Protocol Buffers in Python.  
It provides a server that exposes RPC methods for sending and receiving messages and a client that connects to the server to participate in chat sessions. The implementation is intended for a Distributed Systems lab (Practica 1) and showcases basic RPC communication, protobuf-based message schemas, and simple concurrency handling on the server side.

---

## 🧩 Technologies & Skills Demonstrated
- **gRPC & Protocol Buffers** (`.proto`) for RPC interface definition and code generation.  
- **Python networking** with `grpcio` and generated protobuf Python modules.  
- **Concurrent server handling** (basic multithreading / async patterns) to support multiple clients.  
- **CLI client application** demonstrating RPC calls and message handling.  
- **Packaging & scripts** to start server/client easily on Windows via batch files.

Skills gained:
- Defining service contracts with protobuf  
- Generating and using gRPC Python stubs  
- Building a simple networked application and reasoning about distributed interactions

---

## 📁 Project Structure

```
SD-Distributed-Chat-Service/
├── chatservice.proto            → Protocol Buffers service definition
├── chatservice_pb2.py           → Generated protobuf classes
├── chatservice_pb2_grpc.py      → Generated gRPC classes
├── Server.py                    → gRPC server implementation
├── Client.py                    → gRPC client example
├── start-server.bat             → Batch script to start the server (Windows)
├── start-client.bat             → Batch script to start a client (Windows)
└── Readme.md                    → Original project instructions (Catalan)
```

### Design Philosophy
- **Clear service definition:** All message types and RPC methods are defined in `chatservice.proto`.  
- **Generated stubs:** Use the generated Python modules to decouple transport from business logic.  
- **Simple and instructive:** Focus on demonstrative clarity for educational purposes.

---

## 🔍 Project Details

### Protocol & API
The `.proto` file (`chatservice.proto`) defines the message formats (e.g., `ChatMessage`) and service RPCs (e.g., `SendMessage`, `StreamMessages`). The generated Python modules (`chatservice_pb2.py` / `chatservice_pb2_grpc.py`) provide the client and server classes to implement and call.

### Server (Server.py)
- Implements the gRPC service handlers.  
- Maintains client streams / connections and broadcasts messages to connected clients.  
- Handles basic concurrency for multiple clients.

### Client (Client.py)
- Connects to the server endpoint.  
- Sends messages typed by the user.  
- Subscribes to incoming message streams from the server and prints them on the console.

---

## ▶️ How to Build & Run

### 1. Create a Python virtual environment (recommended)
```bash
python3 -m venv venv
source venv/bin/activate   # Linux / macOS
venv\Scripts\activate      # Windows
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

If `requirements.txt` is not present, install:
```bash
pip install grpcio grpcio-tools
```

### 3. (Optional) Regenerate gRPC Python code from .proto
If you modify `chatservice.proto`, regenerate stubs:
```bash
python -m grpc_tools.protoc -I. --python_out=. --grpc_python_out=. chatservice.proto
```

### 4. Start the server
On Windows:
```cmd
start-server.bat
```
Or on Linux/macOS:
```bash
python Server.py
```

### 5. Start one or more clients
On Windows:
```cmd
start-client.bat
```
Or:
```bash
python Client.py
```

Clients will connect to the server and participate in the chat session.

---

## ✔ Summary
This repository provides a compact, educational implementation of a **gRPC-based chat service** in Python, suitable for Distributed Systems coursework. It demonstrates protobuf service design, server-client interactions, simple concurrency, and practical usage of gRPC in Python.

