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
```bash
holbertonschool-hbnb/
├── part2/         # API Backend
├── part3/         # Database Models
├── part4/         # Frontend
└── uml/           # UML Diagrams
```
# Technology Stack

**Backend**: Python, Flask, Flask-RESTX  
**Database**: SQLAlchemy, PostgreSQL (prod), SQLite (dev), Alembic  
**Frontend**: HTML5, CSS3, JavaScript (ES6)  
**Testing**: pytest, Jest  
**Tools**: Git, Postman, VSCode, Docker  

---

# Project Phases

- **Part 2**: API backend with Flask-RESTX  
- **Part 3**: Database models with SQLAlchemy  
- **Part 4**: Frontend implementation (HTML, CSS, JS)  

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






