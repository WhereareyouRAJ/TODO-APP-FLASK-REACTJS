# 📝 TODO App with Flask & ReactJS

Welcome! This web app lets you save notes and manage them in a database. You can **create**, **read**, **update**, and **delete** your notes (CRUD). The app uses a REST API for communication between the frontend and backend.

---

## 📚 Table of Contents

- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
  - [Frontend Setup](#frontend-setup)
  - [Backend Setup](#backend-setup)
  - [REST API](#rest-api)
- [🖼️ Image Gallery](#image-gallery)
  - [REST API Preview](#rest-api-preview)
  - [Frontend Preview](#frontend-preview)
- [🚀 Containerization](#containerization)
  - [Frontend](#frontend-container)
  - [Backend](#backend-container)
  - [Run with Docker](#run-with-docker)
  - [Access the App](#access-the-app)

---

## 🛠️ Tech Stack

**Frontend:**
- ReactJS ⚛️
- TypeScript
- TailwindCSS
- Axios
- ShadcnUI
- React Router Dom
- React Hook Form
- Zustand
- React Query

**Backend:**
- Python (Flask) 🐍
- SQLite
- Flask Migrate
- SQLAlchemy & Flask SQLAlchemy
- REST API
- SwaggerUI
- Flask Smorest
- Flask JWT Extended
- MVC Pattern

---

## 🚦 Getting Started

You need **NodeJS** and **Python** installed.  
Reference versions: Python `3.13.0`, NodeJS `22.11.0`.

Install them here:
- [NodeJS](https://nodejs.org/en/)
- [Python](https://www.python.org/)

### 1️⃣ Clone the Project

```shell
git clone https://github.com/Remy349/todo-app-flask-reactjs.git
cd todo-app-flask-reactjs
```

You should see these folders:

```shell
/backend
/frontend
/preview
README.md
```

---

### 2️⃣ Frontend Setup

1. Go to `/frontend` and install dependencies:

    ```shell
    npm install
    ```

2. Start the frontend server:

    ```shell
    npm run dev
    ```

    You should see:

    ```
    VITE v5.4.11  ready in 349 ms
    ➜  Local:   http://localhost:5173/
    ```

---

### 3️⃣ Backend Setup

1. Go to `/backend` and create a Python virtual environment:

    ```shell
    python -m venv venv
    ```

2. Activate the environment and install requirements:

    - **Linux/Mac:**
      ```shell
      . venv/bin/activate
      ```
    - **Windows:**
      ```shell
      venv\Scripts\activate
      ```

    Then install dependencies:

    ```shell
    pip install -r requirements.txt
    ```

3. Create a `.env` file for JWT:

    ```shell
    JWT_SECRET_KEY="your_secret_key_here"
    ```

4. Start the backend server:

    ```shell
    flask run
    ```

    You should see:

    ```
    * Running on http://127.0.0.1:5000
    ```

---

## 🐳 Containerization

### Frontend Container

- Uses multi-stage Dockerfile:
  - Stage 1: Build with NodeJS
  - Stage 2: Serve with Nginx

Build the image:

```shell
cd frontend/
docker build -t react-frontend .
```

### Backend Container

Build the backend image:

```shell
cd backend/
docker build -t flask-backend .
```

---

### 🚢 Run with Docker (No Docker Compose)

Create a network and run both containers:

```shell
docker network create todo-net

docker run -d -p 3000:80 --network todo-net --name frontend react-frontend

docker run -d -p 5000:5000 --network todo-net --name backend flask-backend
```

---

### 🌐 Access the App

Open your browser and go to:

```
http://localhost:3000
```

---

Enjoy your TODO app! 🎉  
Feel free to contribute or ask questions.
