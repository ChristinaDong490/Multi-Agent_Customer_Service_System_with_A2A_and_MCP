# Multi-Agent Customer Service System with A2A and MCP

## Overview

This project implements a **multi-agent customer service automation system** that coordinates specialized conversational agents using **Agent-to-Agent (A2A)** communication and retrieves real customer data through the **Model Context Protocol (MCP)**.

The system simulates how modern service platforms handle queries by routing tasks, negotiating between specialists, and performing multi-step operations over a shared database.

## System Architecture
### **MCP Server**

The MCP server acts as the backend data service, connecting to a database and **exposing tools** that the agents can call during conversation.

### Database Tables

- **Customers**
- **Tickets**

### Exposed MCP Tools

| Tool | Description |
| --- | --- |
| get_customer(customer_id) | Retrieve a customer profile |
| list_customers(status, limit) | List customers by status |
| update_customer(customer_id, data) | Update customer fields |
| create_ticket(customer_id, issue, priority) | Create a support ticket |
| get_customer_history(customer_id) | Retrieve historical tickets |

### **Agents Layer**

| Agent | Responsibilities |
| --- | --- |
| **Router Agent** | Parses user query, detects intent, assigns tasks, mediates agent communication, synthesizes final answer |
| **Customer Data Agent** | Calls MCP tools to fetch or update records, validates data, returns structured results |
| **Support Agent** | Handles customer support logic, can escalate tasks, generates service responses, requests data when needed |

## Installation & Setup

### **1. Clone Repo**

```bash
git clone https://github.com/ChristinaDong490/Multi-Agent_Customer_Service_System_with_A2A_and_MCP.git
```

### **2. Install Dependencies**

Python 3.10+ recommended.

```bash
pip install flask flask-cors requests termcolor pyngrok bitsandbytes -q
```

### **3. Initialize the SQLite database**

```bash
python database_setup.py
```

This creates:

- `customers` table
- `tickets` table
- Inserts sample customers & tickets

### **4. Run the MCP Server**
```bash
start_server()
check_server_status()
```
