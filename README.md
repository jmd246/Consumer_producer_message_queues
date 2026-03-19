# 📦 Distributed Order Processing System (Message Queue)

This project demonstrates a simple **distributed system** using a **point-to-point messaging queue** pattern. It consists of two independent applications that communicate asynchronously through a message broker.

## 🚀 Overview

The system simulates an order processing workflow:

- **Order Producer**: Creates `Order` objects and sends them as JSON messages  
- **Order Consumer**: Receives the JSON messages, converts them back into Java objects, and displays them  

Both applications run on **separate ports** and communicate via a **message broker**, showcasing decoupled, asynchronous communication.

---

## 🏗️ Architecture
