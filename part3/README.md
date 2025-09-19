# HBnB Application

A clean, well‑structured **Flask REST API** for the Holberton Bed‑and‑Breakfast (HBnB) platform. Manage **users, amenities, places, reviews** via versioned endpoints.

<p align="center">
  <img alt="HBnB API Status Codes" src="https://tse4.mm.bing.net/th/id/OIP.adrfxjJ-_QUwG6RT5dzvpwHaCZ?pid=Api" width="800"/>
</p>


---

## Table of Contents

* [Overview](#overview)
* [Architecture](#architecture)
* [Project Structure](#project-structure)
* [Setup & Installation](#setup--installation)
* [Running the App](#running-the-app)
* [Configuration](#configuration)
* [API Docs](#api-docs)
* [Endpoints](#endpoints)

  * [Users](#users)
  * [Amenities](#amenities)
* [Request/Response Examples](#requestresponse-examples)
* [Tests](#tests)
* [Project Components](#project-components)
* [Business Logic Layer](#business-logic-layer)
* [Development Notes](#development-notes)
* [Roadmap](#roadmap)

---

## Overview

**HBnB** is a property management API inspired by Airbnb. It exposes **RESTful** endpoints for core resources and demonstrates a **layered architecture** (Presentation → Business → Persistence) with a **Facade** to keep controllers thin and readable.

Current scope: Users & Amenities (v1). Places & Reviews are coming next.

---

## Architecture

```
Client → API (Flask) → Facade/Services → Models (Business Rules) → Repository (In‑Memory → DB later)
```

* Presentation: Blueprints under `app/api/v1/`
* Business: Entities + rules in `app/models/`
* Persistence: In‑memory repo in `app/persistence/` (swappable later)
* Facade: `app/services/facade.py` centralizes orchestration

---

## Project Structure

```
hbnb/
├── app/
│   ├── __init__.py                 # Flask app factory
│   ├── api/
│   │   ├── __init__.py
│   │   └── v1/
│   │       ├── __init__.py         # v1 blueprint registration
│   │       ├── users.py            # User endpoints
│   │       ├── places.py           # (stub)
│   │       ├── reviews.py          # (stub)
│   │       └── amenities.py        # Amenity endpoints
│   ├── models/
│   │   ├── __init__.py
│   │   ├── base_model.py
│   │   ├── user.py
│   │   ├── place.py
│   │   ├── review.py
│   │   └── amenity.py
│   ├── services/
│   │   ├── __init__.py
│   │   └── facade.py               # Facade pattern
│   └── persistence/
│       ├── __init__.py
│       └── repository.py           # In‑memory repo impl
├── tests/
│   └── test_users_api.sh           # curl‑based smoke tests
├── run.py                          # App entrypoint
├── config.py                       # Settings
├── requirements.txt
└── README.md
```

---

## Setup & Installation

```bash
# 1) Clone & enter the project
cd hbnb

# 2) Create a virtual environment
python3 -m venv venv

# 3) Activate it
#   macOS/Linux
source venv/bin/activate
#   Windows (Powershell)
# .\venv\Scripts\Activate.ps1

# 4) Install dependencies
pip install -r requirements.txt
```

---

## Running the App

```bash
# Activate venv if not already
source venv/bin/activate

# Run
python run.py
# App starts on http://localhost:5000
```

---

## Configuration

Configuration values are read from `config.py` (and can be overridden with environment variables in future iterations):

* DEBUG: default True for local dev
* API\_PREFIX: default `/api/v1`
* REPOSITORY\_IMPL: in‑memory (planned: database)

---

## API Docs

Interactive docs (Swagger UI / Redoc) will be available at:

* Swagger UI: `http://localhost:5000/api/v1/`

Use this UI to explore and test endpoints without leaving the browser.

---

## Endpoints

### Users

| Method | Endpoint                  | Description                 | Success |
| :----: | ------------------------- | --------------------------- | :-----: |
|  POST  | `/api/v1/users/`          | Create a new user           |  `201`  |
|   GET  | `/api/v1/users/`          | List all users              |  `200`  |
|   GET  | `/api/v1/users/<user_id>` | Retrieve a specific user    |  `200`  |
|   PUT  | `/api/v1/users/<user_id>` | Update a user's information |  `200`  |

### Amenities

| Method | Endpoint                         | Description                     | Success |
| :----: | -------------------------------- | ------------------------------- | :-----: |
|  POST  | `/api/v1/amenities/`             | Create a new amenity            |  `201`  |
|   GET  | `/api/v1/amenities/`             | List all amenities              |  `200`  |
|   GET  | `/api/v1/amenities/<amenity_id>` | Retrieve a specific amenity     |  `200`  |
|   PUT  | `/api/v1/amenities/<amenity_id>` | Update an amenity's information |  `200`  |

---

## Request/Response Examples

#### Create a User

```bash
curl -s -X POST http://localhost:5000/api/v1/users/ \
  -H 'Content-Type: application/json' \
  -d '{"email":"user@example.com","first_name":"Ava","last_name":"Stone"}'
```

201 Created

```json
{
  "id": "2a77f8ac-0a8d-4c3a-9f3e-1f8b3f6a5a2e",
  "email": "user@example.com",
  "first_name": "Ava",
  "last_name": "Stone",
  "created_at": "2025-09-18T09:30:12Z",
  "updated_at": "2025-09-18T09:30:12Z"
}
```

#### Get All Users

```bash
curl -s http://localhost:5000/api/v1/users/
```

200 OK

```json
[
  { "id": "...", "email": "...", "first_name": "...", "last_name": "..." }
]
```

#### Create an Amenity

```bash
curl -s -X POST http://localhost:5000/api/v1/amenities/ \
  -H 'Content-Type: application/json' \
  -d '{"name":"WiFi"}'
```

201 Created

```json
{
  "id": "ae1a6a6d-6d6a-4a0b-9c7b-a1c0a6f2e0f3",
  "name": "WiFi",
  "created_at": "2025-09-18T09:31:44Z",
  "updated_at": "2025-09-18T09:31:44Z"
}
```

---

## Tests

Run the lightweight curl tests (ensure the server is running):

```bash
chmod +x tests/test_users_api.sh
./tests/test_users_api.sh
```

The script exercises Users and Amenities endpoints and prints concise results.

---

## Project Components

* `app/__init__.py`: App factory & extensions setup
* `app/api/v1/`: Versioned blueprints & route handlers

  * `users.py` / `amenities.py`: Concrete v1 resources
* `app/models/`: Domain entities and invariants
* `app/services/facade.py`: Facade coordinating models & repo
* `app/persistence/repository.py`: In‑memory repository
* `run.py`: Dev server entrypoint
* `config.py`: Settings
* `tests/test_users_api.sh`: cURL smoke tests

---

## Business Logic Layer

* BaseModel: UUID id, timestamps, shared helpers
* User: core user attributes & validation
* Place: rentable unit (planned endpoints)
* Review: feedback for places (planned endpoints)
* Amenity: amenity catalog with validation

---

## Development Notes

* Versioning: All routes under `/api/v1`
* Validation: Basic checks in models/services; expand with schema validation later
* Error Handling: Centralize into error handlers (planned)
* Persistence: Start with in‑memory repo → swap to SQL/NoSQL via a Repository interface
* Docs: Swagger UI mounted at `/api/v1/`

---

## Roadmap

* [x] Users API
* [x] Amenities API
* [ ] Places & Reviews endpoints
* [ ] Search (filter by city/amenities/price)
* [ ] Authentication & Authorization
* [ ] Database integration (SQLAlchemy or similar)
* [ ] Error handling & logging
* [ ] OpenAPI spec + schema examples
* [ ] CI (lint + test) & containerization
* [ ] Deployment

---

License: MIT
