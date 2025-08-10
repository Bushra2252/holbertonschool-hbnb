# 🧭 High-Level Package Diagram

![Package Diagram](https://i.imgur.com/GO6aUJy.png)

This diagram illustrates the high-level structure of the project, divided into three main layers:

---

### 🔹 Presentation Layer
Handles user interactions through services and APIs.

### 🔹 Business Logic Layer
Contains core application logic and models like `User`, `Place`, `Review`, and `Amenity`.  
Accessed through a simplified interface using the **Facade** pattern.

### 🔹 Persistence Layer
Responsible for data access via DAOs and direct interaction with the database.
