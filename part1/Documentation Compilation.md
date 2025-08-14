# HBnB Technical Documentation

**Project Team:**
- **Raghad Albeladi** (Task 2: Sequence Diagrams)
- **Najwa Aljunaidel** (Task 1: Class Diagram) 
- **Bushra Alotaibi** (Task 0: Package Diagram)

**Project:** HolbertonSchool HBnB  
**Date:** August 2025  
**Version:** 1.0  

---

## Table of Contents
1. [Introduction](#introduction)
2. [High-Level Architecture](#high-level-architecture)
3. [Business Logic Layer](#business-logic-layer)
4. [API Interaction Flow](#api-interaction-flow)
5. [Design Decisions and Rationale](#design-decisions-and-rationale)
6. [Conclusion](#conclusion)

---

## 1. Introduction

### Project Overview
The HBnB (Holberton Airbnb) project is a comprehensive web application that replicates the core functionality of Airbnb. This technical document serves as a detailed blueprint for the HBnB project, providing architectural guidance and design specifications for the implementation phases.

### Document Purpose
This document consolidates all architectural diagrams, design decisions, and system specifications created during the planning phase. It serves as:
- A reference guide for development teams
- A blueprint for system implementation
- Documentation of design decisions and their rationale
- A communication tool for stakeholders

### Document Scope
This documentation covers:
- High-level system architecture using package diagrams
- Detailed business logic layer class relationships
- API interaction flows through sequence diagrams
- Design patterns and architectural decisions

---

## 2. High-Level Architecture

### Package Diagram Overview
*Created by: Bushra Alotaibi*

![Package Diagram](https://i.imgur.com/GO6aUJy.png)

The HBnB application follows a layered architecture pattern with clear separation of concerns across three main layers:
2.1 🔹 Presentation Layer

Responsibility: Handles user interactions through services and APIs
Components: Web interfaces, mobile apps, RESTful API endpoints
Function: Manages all user-facing interactions and external service communications
Technologies: HTML, CSS, JavaScript, React/Vue.js, API Gateway

2.2 🔹 Business Logic Layer

Responsibility: Contains core application logic and models
Core Models: User, Place, Review, and Amenity
Design Pattern: Accessed through a simplified interface using the Facade pattern
Function: Implements business rules, validation, and core application workflows
Benefits: Simplified interface hides complex subsystem interactions

2.3 🔹 Persistence Layer

Responsibility: Responsible for data access via DAOs and direct interaction with the database
Components: Data Access Objects (DAOs), Database connections, ORM frameworks
Function: Handles all data storage, retrieval, and database operations
Technologies: SQL databases, ORM frameworks, connection pooling

Architecture Benefits

Modularity: Clear separation enables independent development and testing
Scalability: Each layer can be scaled independently based on system demands
Maintainability: Isolated concerns reduce complexity and improve code organization
Testability: Each layer can be tested in isolation with proper mocking
Facade Pattern Implementation: Provides a unified interface to the complex business logic subsystem

## 3. Business Logic Layer

### Class Diagram Structure
*Created by: Najwa Aljunaidel*

![Class digram](./Class%20Diagram.drawio.svg)


The business logic layer implements the core entities and their relationships within the HBnB system as illustrated in the UML class diagram above.
3.1 Core Entities
🔹 User Entity

Attributes:

+id: UUID - Unique identifier
+first_name: string - User's first name
+last_name: string - User's last name
+email: string - User email address
+password: string - Encrypted password
+is_admin: bool - Administrative privileges flag
+created_at: datetime - Account creation timestamp
+updated_at: datetime - Last modification timestamp


Methods:

+register() - User registration process+updateProfile() - Update user information
+delete() - Account deletion
+listPlaces() - List user's owned places
+listReviews() - List user's reviews



🔹 Place Entity

Attributes:

+id: UUID - Unique identifier
+title: string - Place name/title
+description: string - Detailed description
+price: float - Nightly rate
+latitude: float - Geographic coordinate
+longitude: float - Geographic coordinate
+owner: User - Reference to User (owner)
+created_at: datetime - Creation timestamp
+updated_at: datetime - Last modification timestamp


Methods:

+create() - Create new place
+updateProfile() - Update place information
+delete() - Remove place
+listPlaces() - List available places
+listAmenities() - List place amenities



🔹 Review Entity

Attributes:

+id: UUID - Unique identifier
+place: Place - Reference to Place
+user: User - Reference to User (reviewer)
+rating: float - Numeric rating (1-5)
+comment: string - Review text
+created_at: datetime - Review creation timestamp
+updated_at: datetime - Last modification timestamp


Methods:

+create() - Create new review
+update() - Update existing review
+delete() - Remove review
+listPlaces() - List reviewed places
+listByPlace() - List reviews for specific place



🔹 Amenity Entity

Attributes:

+id: UUID - Unique identifier
+name: string - Amenity name
+description: string - Amenity description
+created_at: datetime - Creation timestamp
+updated_at: datetime - Last modification timestamp


Methods:

+create() - Create new amenity
+updateProfile() - Update amenity information
+delete() - Remove amenity
+listPlaces() - List places with this amenity
+listAmenities() - List all amenities



3.2 Entity Relationships
Based on the class diagram, the relationships are:

User ↔ Place:

Relationship: One-to-Many (1 user can own multiple places)
Implementation: User has listPlaces() method


User ↔ Review:

Relationship: One-to-Many (1 user can write multiple reviews)
Implementation: User has listReviews() method


Place ↔ Review:

Relationship: One-to-Many (1 place can have multiple reviews)
Implementation: Review references Place entity


Place ↔ Amenity:

Relationship: Many-to-Many (Places can have multiple amenities, amenities can belong to multiple places)
Implementation: Both entities have list methods for cross-referencing



3.3 Business Rules Implementation

Authentication Required: User entity validates permissions for place and review operations
Ownership Validation: Place entity ensures only owners can modify place information
Review Restrictions: Review entity prevents users from reviewing their own places
Data Integrity: All entities use UUID for unique identification
Audit Trail: All entities maintain creation and update timestamps

4. API Interaction Flow
Sequence Diagrams Overview
Created by: Raghad Albeladi
The sequence diagrams illustrate the interaction flow between different components for key API operations. These diagrams show how the Presentation Layer (UI/API), Business Logic Layer (Services), and Persistence Layer (Database) communicate to handle user requests.
4.1 🔹 Sign Up / Login Flow
This diagram shows the authentication process when a user attempts to log into the system.
```
sequenceDiagram
    participant U as User
    participant UI as UI
    participant API as Controller/API
    participant Auth as Auth Service
    participant DB as Database
    U->>UI: Enter credentials
    UI->>API: POST /auth/login
    API->>Auth: IsUserAuthorized(userID, password)
    Auth->>DB: Validate credentials
    DB-->>Auth: User data
    Auth-->>API: true/false
    
    alt [if true]
        API->>DB: Generate session/token
        DB-->>API: Success
        API-->>UI: 200 OK + token
        UI-->>U: Login Successful
    else [else]
        API-->>UI: 401 Unauthorized
        UI-->>U: Error Message
    end
   ```
Key Interactions:

User submits credentials through the UI
API validates credentials through Auth Service
Database verification and token generation
Success or error response to user

4.2 🔹 Get Room Details Flow
This diagram illustrates how the system retrieves and displays detailed information about a specific place/room.
  ```sequenceDiagram
    participant U as USER
    participant UI as UI
    participant API as Backend/API
    participant DB as Database/Service
    U->>UI: click view room details
    UI->>API: GET /api/rooms/{roomId}
    API->>DB: GetRoomDetails(ID)
    DB-->>API: Return Room details model
    API-->>UI: Room details (JSON)
    UI-->>U: Render room details page
```
Key Interactions:

User requests to view room details
API fetches room information from database
Structured room data returned as JSON
UI renders the detailed room information

4.3 🔹 Add Review Flow
This diagram shows the process of adding a review for a place, including authentication and authorization checks.
```
sequenceDiagram
    participant U as User
    participant UI as UI
    participant API as Controller/API
    participant Auth as Auth Service
    participant Service as Model/Services
    participant DB as DB
    U->>UI: Click Add Review button
    UI->>API: call post:/api/rooms/{id}/review
    
    alt [authentication check]
        API->>Auth: IsUserAuthorized(userID,roomID)
        Auth-->>API: true/false
        
        alt [if true]
            API->>Service: AddValidateDataReview(data)
            Service->>DB: AddReview(Data)
            DB-->>Service: Success
            Service-->>API: success
            API-->>UI: 201 Create
            UI-->>U: Created Successfully
        else [else]
            API-->>UI: 403 Forbidden
            UI-->>U: Error Message
        end
    end
```
Key Interactions:

User initiates review creation
System verifies user authorization
Review data validation through Service layer
Database persistence with success confirmation

4.4 🔹 Delete Place Flow
This diagram demonstrates the place deletion process with proper authorization checks.

```
sequenceDiagram
    participant U as User
    participant UI as UI
    participant API as Backend/API
    participant Auth as Auth Service
    participant DB as DB/Services
    U->>UI: Click delete button
    UI->>API: call post:/api/room/{id}/delete
    
    alt [authorization check]
        API->>Auth: IsUserAuthorized(userID,roomID)
        Auth-->>API: true/false
        
        alt [if true]
            API->>DB: deleteRoom(roomId)
            DB-->>API: success
            API-->>UI: 204 ok
            UI-->>U: Deleted Successfully
        else [else]
            API-->>UI: 403 Forbidden
            UI-->>U: Error Message
        end
    end
```

Key Interactions:

User requests place deletion
Authorization verification for ownership
Database deletion operation
Success confirmation or error handling

API Design Principles
Based on the sequence diagrams, the system follows these key principles:

RESTful Architecture: Standard HTTP methods (GET, POST) and appropriate status codes
Authentication & Authorization: Comprehensive security checks for protected operations
Layered Communication: Clear separation between UI, API, Services, and Database layers
Error Handling: Proper error responses (401 Unauthorized, 403 Forbidden, 204 OK)
Data Validation: Service layer validates data before database operations
Consistent Response Format: Uniform JSON structure and HTTP status codes


5. Design Decisions and Rationale
5.1 Architectural Patterns
Layered Architecture
Decision: Implement three-tier architecture
Rationale:

Clear separation of concerns
Enhanced maintainability
Improved testability
Scalability benefits

Facade Pattern
Decision: Use facade pattern for business logic layer
Rationale:

Simplified interface for complex subsystems
Reduced coupling between layers
Easier to modify internal implementations
Improved code organization

5.2 Database Design
Relational Database Choice
Decision: Use SQL database for primary storage
Rationale:

ACID compliance for data integrity
Complex relationship support
Mature ecosystem and tools
Strong consistency requirements

Normalization Strategy
Decision: Third Normal Form (3NF) normalization
Rationale:

Eliminates data redundancy
Maintains data integrity
Optimizes storage space
Supports complex queries

5.3 API Design
RESTful API Design
Decision: Implement REST architectural style
Rationale:

Industry standard approach
Stateless and scalable
Clear resource-based URLs
Standard HTTP methods

JSON Data Format
Decision: Use JSON for data exchange
Rationale:

Lightweight and human-readable
Wide language support
Native JavaScript integration
Standard web format


6. Conclusion
This technical documentation provides a comprehensive blueprint for the HBnB project implementation. The layered architecture ensures maintainability and scalability, while the detailed class relationships support robust business logic implementation.


شع
