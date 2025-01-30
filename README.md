# FastAPI JWT Authentication with CRUD Operations

## 📌 Overview
This project is a FastAPI-based backend that implements **JWT-based authentication** and **CRUD operations** for user management. 
It provides secure endpoints to create, read, and delete users while ensuring authentication and authorization.

## 🚀 Features
- **User Registration** (hashed passwords stored securely)
- **JWT-based Authentication** (login and token generation)
- **Protected CRUD Operations** (only authenticated users can access them)
- **SQLAlchemy & SQLite** for database management
- **Pydantic for Data Validation**

## 🛠️ Tech Stack
- **FastAPI** (Backend Framework)
- **SQLAlchemy** (ORM for database interaction)
- **JWT (JSON Web Token)** (Authentication)
- **Passlib** (Password Hashing)
- *SQLite** (Database)

---

## 📂 Project Structure
```
.
├── main.py             # Main application file (routes)
├── models.py           # Database models (SQLAlchemy)
├── schemas.py          # Pydantic schemas for validation
├── crud.py             # CRUD functions for database interaction
├── auth.py             # Authentication logic (JWT & password hashing)
├── database.py         # Database connection setup
├── requirements.txt    # Required dependencies
├── README.md           # Project documentation
```

---

## 🔧 Setup and Installation

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/ProgHubs_JWT_02
cd ProgHubs_JWT_02
```

### 2️⃣ Create a Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
```

### 3️⃣ Install Dependencies
```bash
pip install -r requirements.txt
```

### 4️⃣ Configure the Database
Modify `database.py` to set up your **SQLite** database.

### 5️⃣ Run the Application
```bash
uvicorn main:app --reload
```

---

## 🔑 Authentication (JWT)

### 📝 1. Register a User
**Endpoint:** `POST /users/`
```json
{
  "username": "kitessa",
  "email": "kitessa@email.com",
  "password": "test123"
}
```

### 🔐 2. Obtain an Access Token (Login)
**Endpoint:** `POST /token`
```bash
curl -X 'POST' 'http://127.0.0.1:8000/token' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'username=kitessa@email.com&password=test123'
```
**Response:**
```json
{
  "access_token": "your_jwt_token",
  "token_type": "bearer"
}
```

### 🔒 3. Access Protected Routes
Use the token received from login to access protected routes:
```bash
curl -X 'GET' 'http://127.0.0.1:8000/users/' \
  -H "Authorization: Bearer your_jwt_token"
```

---

## 🛠️ API Endpoints
### **Public Routes:**
- `POST /users/` → Register a new user
- `POST /token` → Authenticate and get an access token

### **Protected Routes (Require JWT):**
- `GET /users/` → Get all users (Paginated)
- `GET /users/{user_id}` → Get a specific user
- `DELETE /users/{user_id}` → Delete a user

