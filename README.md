# HBNB - AirBnB Clone Project

<div align="center">

![Holberton School](https://img.shields.io/badge/Holberton-School-red?style=for-the-badge&logo=holberton&logoColor=white)  ![Python](https://img.shields.io/badge/Python-3.8+-blue?style=for-the-badge&logo=python&logoColor=white)  ![Flask](https://img.shields.io/badge/Flask-RESTful-green?style=for-the-badge&logo=flask&logoColor=white)  ![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-ORM-orange?style=for-the-badge&logo=postgresql&logoColor=white)  ![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow?style=for-the-badge&logo=javascript&logoColor=black)  ![HTML5](https://img.shields.io/badge/HTML5-Frontend-purple?style=for-the-badge&logo=html5&logoColor=white)  
![CSS3](https://img.shields.io/badge/CSS3-Responsive-pink?style=for-the-badge&logo=css3&logoColor=white)  

**A complete full-stack AirBnB clone with RESTful API, database integration, and interactive frontend**

[Live Demo](#quick-start-guide) • [Documentation](#project-overview) • [Testing](#testing-documentation) • [API Reference](#api-endpoints)

</div>

---

## Table of Contents
- [Project Overview](#project-overview)  
- [Key Features](#key-features)  
- [Architecture & Design](#architecture--design)  
- [Project Structure](#project-structure)  
- [Technology Stack](#technology-stack)  
- [Project Phases](#project-phases)  
- [Installation & Setup](#installation--setup)  
- [Quick Start Guide](#quick-start-guide)  
- [API Endpoints](#api-endpoints)  
- [Model Validation Rules](#model-validation-rules)  
- [Testing Documentation](#testing-documentation)  
- [Performance & Optimization](#performance--optimization)  
- [Security Features](#security-features)  
- [API Documentation](#api-documentation)  
- [Frontend Features](#frontend-features)  
- [Deployment Guide](#deployment-guide)  
- [Contributing](#contributing)  
- [License](#license)  
- [Authors](#authors)  

---

## Project Overview
**HBNB** is a full-stack web application replicating the core functionality of AirBnB. It demonstrates advanced web development principles including RESTful API design, database modeling, and modern frontend integration.

### Learning Objectives
- Full-stack web development (backend + frontend)  
- RESTful API design with Flask  
- Database design with SQLAlchemy ORM  
- Responsive frontend with HTML, CSS, and JS  
- Software testing at all levels  

---

## Key Features

### Backend
- RESTful API with full CRUD support  
- Input validation and structured JSON responses  
- Modular service and repository layers  
- Comprehensive unit and integration testing  

### Database
- SQLAlchemy ORM with PostgreSQL/SQLite  
- One-to-many and many-to-many relationships  
- Database migrations (Alembic)  
- Constraints and indexes for data integrity  

### Frontend
- Responsive, mobile-first design  
- Place search with filters and advanced criteria  
- User authentication (login/signup)  
- Booking system with calendar  
- Image gallery with lazy loading  

---

## Architecture & Design
- **Patterns**: Repository, Facade, MVC  
- **UML Diagrams**: Class, Package, Sequence, and System Architecture  

---

## Project Structure
```
holbertonschool-hbnb/
├──  README.md                     # Project documentation
├──  .gitignore                    # Git ignore patterns
│
├──  part2/                        #  API Backend Implementation
│   ├──  README.md                 # Backend documentation
│   ├──  run.py                    # Application entry point
│   ├──  config.py                 # Configuration settings
│   ├──  requirements.txt          # Python dependencies
│   │
│   ├──  app/                      # Main application package
│   │   ├──  __init__.py           # App factory and configuration
│   │   │
│   │   ├──  api/                  # API endpoint definitions
│   │   │   └──  v1/               # API version 1
│   │   │       ├──  amenities.py  # Amenities CRUD endpoints
│   │   │       ├──  places.py     # Places CRUD endpoints
│   │   │       ├──  reviews.py    # Reviews CRUD endpoints
│   │   │       └──  users.py      # Users CRUD endpoints
│   │   │
│   │   ├──  models/               # Data model definitions
│   │   │   ├──  base_model.py     # Base model with common fields
│   │   │   ├──  amenity.py        # Amenity model
│   │   │   ├──  place.py          # Place model with location data
│   │   │   ├──  review.py         # Review model with ratings
│   │   │   └──  user.py           # User model with authentication
│   │   │
│   │   ├──  persistence/          # Data storage layer
│   │   │   └──  repository.py     # Repository pattern implementation
│   │   │
│   │   └──  services/             # Business logic layer
│   │       ├──  facade.py         # Service facade pattern
│   │       └──  test.py           # Service testing utilities
│   │
│   └──  tests/                    # Comprehensive test suite
│       ├──  test_api.py           # API endpoint tests
│       ├──  test_models.py        # Model validation tests
│       └──  test_services.py      # Business logic tests
│
├──  part3/                        #  Database Implementation
│   ├──  hbnb/                     # Main application package
│   │   ├──  __init__.py           # Package initialization
│   │   │
│   │   ├──  models/               # SQLAlchemy ORM models
│   │   │   ├──  base.py           # Base model with SQLAlchemy
│   │   │   ├──  amenity.py        # Amenity ORM model
│   │   │   ├──  place.py          # Place ORM with relationships
│   │   │   ├──  review.py         # Review ORM with foreign keys
│   │   │   └──  user.py           # User ORM with constraints
│   │   │
│   │   ├──  routes/               # Flask route definitions
│   │   │   ├──  amenities.py      # Amenity routes
│   │   │   ├──  places.py         # Place routes
│   │   │   ├──  reviews.py        # Review routes
│   │   │   └──  users.py          # User routes
│   │   │
│   │   └──  templates/            # Jinja2 templates
│   │       ├──  base.html         # Base template
│   │       ├──  index.html        # Home page template
│   │       └──  place.html        # Place detail template
│   │
│   ├──  instance/                 # Instance-specific configurations
│   │   ├──  config.py             # Local configuration
│   │   └──  database.db           # SQLite database file
│   │
│   └──  venv/                     # Virtual environment
│
├──  part4/                        #  Frontend Implementation
│   ├──  index.html                #  Main landing page
│   ├──  login.html                #  User authentication page
│   ├──  place.html                #  Place details page
│   ├──  scripts.js                #  Main JavaScript functionality
│   ├──  styles.css                #  CSS styles and responsive design
│   │
│   ├──  js/                       # JavaScript modules
│   │   ├──  api.js                # API communication module
│   │   ├──  auth.js               # Authentication handling
│   │   ├──  search.js             # Search and filter functionality
│   │   └──  booking.js            # Booking system logic
│   │
│   ├──  img/                      # Image assets
│   │   ├──  logo.png              # Application logo
│   │   ├──  placeholder.jpg       # Image placeholders
│   │   └──  icons/                # UI icons and graphics
│   │
│   └──  tests/                    # Frontend testing
│       ├──  test_ui.js            # UI component tests
│       ├──  test_api.js           # API integration tests
│       └──  test_auth.js          # Authentication flow tests
│
└──  uml/                          #  UML Diagrams & Documentation
    ├──  hbnb-technical-doc.md     # Technical architecture documentation
    ├──  class_diagram.png         # Entity relationship diagram
    ├──  package_diagram.png       # Component architecture
    ├──  sequence_diagram_getplace.png      # GET place API flow
    ├──  sequence_diagram_postplace.png     # POST place API flow
    ├──  sequence_diagram_review.png        # Review creation flow
    └──  sequence_diagram_start.png         # Application startup flow
```

    
# Technology Stack
<table>
<tr>
<td align="center">

**Backend Technologies**
![Python](https://img.shields.io/badge/Python-3.8+-blue?style=flat&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-3.1.0-green?style=flat&logo=flask&logoColor=white)
![Flask-RESTX](https://img.shields.io/badge/Flask--RESTX-1.3.0-lightgreen?style=flat&logo=swagger&logoColor=white)

</td>
<td align="center">

**Database Technologies**
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-ORM-orange?style=flat&logo=postgresql&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Production-blue?style=flat&logo=postgresql&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-Development-lightblue?style=flat&logo=sqlite&logoColor=white)

</td>
<td align="center">

**Frontend Technologies**
![HTML5](https://img.shields.io/badge/HTML5-Semantic-red?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-Grid/Flexbox-blue?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow?style=flat&logo=javascript&logoColor=black)

</td>
</tr>
<tr>
<td align="center">

**Testing & Quality**
![pytest](https://img.shields.io/badge/pytest-Testing-green?style=flat&logo=pytest&logoColor=white)
![Coverage](https://img.shields.io/badge/Coverage-7.6+-blue?style=flat&logo=codecov&logoColor=white)
![Jest](https://img.shields.io/badge/Jest-Frontend-red?style=flat&logo=jest&logoColor=white)

</td>
<td align="center">

**Development Tools**
![Git](https://img.shields.io/badge/Git-Version_Control-orange?style=flat&logo=git&logoColor=white)
![VSCode](https://img.shields.io/badge/VSCode-IDE-blue?style=flat&logo=visualstudiocode&logoColor=white)
![Postman](https://img.shields.io/badge/Postman-API_Testing-orange?style=flat&logo=postman&logoColor=white)

</td>
<td align="center">

**Architecture Patterns**
![REST](https://img.shields.io/badge/REST-API_Design-green?style=flat&logo=rest&logoColor=white)
![MVC](https://img.shields.io/badge/MVC-Architecture-purple?style=flat&logo=mvc&logoColor=white)
![Repository](https://img.shields.io/badge/Repository-Pattern-blue?style=flat&logo=repository&logoColor=white)

</td>
</tr>
</table>

---

# Project Phases
```bash
holbertonschool-hbnb/
├── part2/                   # API Backend
│   ├── app/
│   │   ├── __init__.py      # App initialization and configuration
│   │   ├── api/
│   │   │   └── v1/          # API endpoints 
│   │   │       ├── amenities.py
│   │   │       ├── places.py
│   │   │       ├── reviews.py
│   │   │       └── users.py
│   │   ├── models/          # Data models
│   │   │   ├── amenity.py
│   │   │   ├── base_model.py
│   │   │   ├── place.py
│   │   │   ├── review.py
│   │   │   └── user.py
│   │   ├── persistence/     # Data storage
│   │   │   └── repository.py
│   │   └── services/        # Business logic
│   │       ├── facade.py
│   │       └── test.py
│   ├── config.py            # Configuration settings
│   ├── run.py               # Application entry point
│   ├── requirements.txt     # Project dependencies
│   └── tests/               # API test suite
│
├── part3/                   # Database Models
│   ├── hbnb/                # Main application package
│   │   ├── __init__.py
│   │   ├── models/          # SQLAlchemy ORM models
│   │   │   ├── amenity.py
│   │   │   ├── base.py
│   │   │   ├── place.py
│   │   │   ├── review.py
│   │   │   └── user.py
│   │   ├── routes/          # API routes
│   │   └── templates/       # Flask templates
│   ├── instance/            # Instance-specific configs
│   └── venv/                # Virtual environment
│
├── part4/                   # Frontend Implementation
│   ├── img/                 # Image assets
│   ├── js/                  # JavaScript modules
│   ├── tests/               # Frontend tests
│   ├── index.html           # Main landing page
│   ├── login.html           # User authentication page
│   ├── place.html           # Place details page
│   ├── scripts.js           # Main JavaScript file
│   └── styles.css           # CSS styles
│
└── uml/                     # UML diagrams
```
---

# Installation & Setup

## Prerequisites
- Python 3.8+  
- pip  
- Git  
- PostgreSQL (optional, for production)  

## Clone Repository
```bash
git clone https://github.com/Bushra2252/holbertonschool-hbnb.git
cd holbertonschool-hbnb
```

# Backend Setup
```bash
cd part2
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python run.py
```
API runs on http://127.0.0.1:5000

# Database Setup
```
cd part3
source venv/bin/activate
pip install sqlalchemy alembic psycopg2-binary
alembic upgrade head
```
# Frontend Setup
```
cd part4
python3 -m http.server 8080
```
Frontend runs on http://127.0.0.1:8080

# Quick Start Guide

1. Run the backend API  
2. Open Swagger docs at `http://127.0.0.1:5000/doc/`  
3. Start the frontend server  
4. Access frontend in browser  

---

# API Endpoints

## Users
- `POST /api/v1/users/` – Create new user  
- `GET /api/v1/users/` – List all users  
- `GET /api/v1/users/<id>` – Get specific user  
- `PUT /api/v1/users/<id>` – Update user  

## Places
- `POST /api/v1/places/` – Create new place  
- `GET /api/v1/places/` – List all places  
- `GET /api/v1/places/<id>` – Get specific place  
- `PUT /api/v1/places/<id>` – Update place  

## Reviews
- `POST /api/v1/reviews/` – Create review  
- `GET /api/v1/reviews/` – List all reviews  
- `GET /api/v1/reviews/<id>` – Get review  
- `PUT /api/v1/reviews/<id>` – Update review  

## Amenities
- `POST /api/v1/amenities/` – Create amenity  
- `GET /api/v1/amenities/` – List amenities  
- `GET /api/v1/amenities/<id>` – Get amenity  
- `PUT /api/v1/amenities/<id>` – Update amenity  

---

# Model Validation Rules

- **Users**: First/last name required, email unique, password secure  
- **Places**: Title required, price positive, valid coordinates  
- **Reviews**: Text length 10–500, rating 1–5  
- **Amenities**: Name required, unique  

---

# Testing Documentation

- Backend tests with pytest (`pytest tests/ -v`)  
- Frontend tests with Jest (`npm test`)  
- Coverage reports included  

---

# Performance & Optimization

- Database indexing for faster queries  
- Connection pooling  
- Browser caching for frontend assets  
- API response time < 200ms  

---

# Security Features

- Password hashing (bcrypt)  
- Input sanitization  
- CSRF and SQL injection protection  
- HTTPS recommended in production  

---

# API Documentation

- Swagger UI available at `/doc/`  
- OpenAPI specification included  
- Postman collection for testing  

---

# Frontend Features

- Landing page with featured places  
- Search/filter by location, price, and amenities  
- Booking calendar  
- Responsive layout (mobile-first)  

---

# Deployment Guide

- Dockerfile and docker-compose provided  
- Supports Heroku, AWS, DigitalOcean, Vercel  

---

# Contributing

- Fork repo, create feature branch, open PR  
- Follow PEP8 (Python), ES6 (JS), semantic HTML/CSS  
- Add tests and update docs with new features  

---

# License

MIT License – Educational use for Holberton School curriculum.  

---

# Authors

- **Raghad Albeladi & Najwa Aljunaidell** – Holberton School Software Engineering Program  
- GitHub Repo: [holbertonschool-hbnb](https://github.com/Bushra2252/holbertonschool-hbnb)  







