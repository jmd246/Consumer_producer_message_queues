# 📦 Distributed Order Processing System (Message Queue)

This project demonstrates a simple **distributed system** using a **point-to-point messaging queue** pattern. It consists of two independent Java applications that communicate asynchronously through a message broker.

---

## 🚀 Overview

The system simulates an order processing workflow:

- **Order Producer**
  - Creates `Order` objects
  - Serializes them into JSON
  - Sends messages to a queue

- **Order Consumer**
  - Receives JSON messages from the queue
  - Deserializes them back into Java objects
  - Displays the reconstructed `Order`

Both applications run on **separate ports**, illustrating how distributed services communicate without being tightly coupled.

---

## 🏗️ Architecture

```
[ Order Producer ]  --->  [ Message Broker / Queue ]  --->  [ Order Consumer ]
       (Port A)                                         (Port B)
```

### Key Characteristics:
- Asynchronous communication  
- Point-to-point messaging (1 producer → 1 consumer)  
- Loose coupling between services  
- Independent deployment and scaling  

---

## 🔧 Technologies Used

- **Java**
- **Message Broker** (Atremis)
- **Jackson** (for JSON serialization/deserialization)
- **LocalDateTime API** (Java Time)

---

## 📦 Data Model

```java
import com.fasterxml.jackson.annotation.JsonFormat;
import java.time.LocalDateTime;

public class Order {
    int id;
    String email;

    // format: MM-dd-yyyy HH:mm:ss
    @JsonFormat(shape = JsonFormat.Shape.STRING, pattern = "MM-dd-yyyy HH:mm:ss")
    LocalDateTime orderDate;

    double totalPrice;
}
```

---

## 📬 How It Works

### 1. Order Creation (Producer)
- A Java `Order` object is created
- The object is converted into a JSON string using Jackson
- The JSON is sent to the message queue

### 2. Message Handling (Broker)
- The message broker stores the message in a queue
- Ensures reliable delivery to the consumer

### 3. Order Processing (Consumer)
- The consumer reads the message from the queue
- Converts the JSON back into a Java `Order` object
- Outputs the result to the console or logs

---

## 📄 Example Message Flow

### JSON sent by Producer:
```json
{
  "id": 101,
  "email": "customer@example.com",
  "orderDate": "03-19-2026 14:30:00",
  "totalPrice": 249.99
}
```

### Java object reconstructed by Consumer:
```java
Order{id=101, email='customer@example.com', orderDate=2026-03-19T14:30, totalPrice=249.99}
```

---

## ▶️ Running the Project

### Prerequisites
- Java 8+
- Running message broker (RabbitMQ / Kafka / ActiveMQ)

### Steps

1. Start your message broker  
2. Run the **Order Consumer** (listening for messages)  
3. Run the **Order Producer**  
4. Trigger order creation (via code or API)  
5. Observe the consumer output  

---

## 🎯 Key Concepts Demonstrated

- Distributed system fundamentals  
- Producer–Consumer pattern  
- Message queues (point-to-point)  
- Asynchronous communication  
- JSON serialization/deserialization  
- Service decoupling  

---

## 💡 Why This Matters

This project reflects real-world backend architecture patterns used in:

- E-commerce platforms  
- Payment processing systems  
- Event-driven microservices  
- Order and inventory systems  

Using messaging queues allows systems to:
- Scale independently  
- Improve reliability  
- Handle high throughput  
- Avoid tight coupling between services  

---

## 📌 Future Improvements

- Add multiple consumers (competing consumers pattern)  
- Implement retry and dead-letter queues  
- Add REST API for order submission  
- Persist orders to a database  
- Add logging and monitoring  

---

## 👨‍💻 Joshua Doucette

Your Name  
