# Dockerized Web App Learning Project

> ⚠️ **Disclaimer:** This project is a fork of a random website found on the internet. It is used purely for learning purposes to practice Dockerizing a multi-service web application.

## Overview

This project demonstrates a **multi-container web application** using:

- **Frontend:** React (Create React App)  
- **Backend:** Node.js / Express  
- **Database:** MongoDB  

The goal of this project is **not to produce a full-featured product**, but to explore Docker concepts such as:

- Multi-stage builds for React frontend  
- Environment variable management (`.env` files and Docker build args)  
- Docker Compose orchestration of multiple services  
- Container networking and service-to-service communication  
- Persisting database data using Docker volumes  

---

## Services

| Service  | Description |
|----------|-------------|
| `frontend` | React app built with CRA and served via Nginx |
| `backend`  | Node.js / Express REST API server |
| `mongo`    | MongoDB database for backend data storage |

---

## Getting Started

### Prerequisites

- [Docker](https://www.docker.com/get-started)  
- [Docker Compose](https://docs.docker.com/compose/install/)

---

### Running the Application

1. Clone the repository:

```
git clone <repository-url>
cd <repository-folder>
```

2. Build and start all services with Docker Compose:

```
docker-compose up --build
```

3. Access the frontend in your browser at:

```
http://localhost:3000
```

4. The backend API is available at:

```
http://localhost:4000/api/
```

> The frontend calls the backend using the `REACT_APP_API_URL` environment variable embedded during the build.

---

### Environment Variables

- **Backend:** `.variables.env` file contains secrets, database URI, JWT keys, etc.  
- **Frontend:** Build-time environment variables (e.g., `REACT_APP_API_URL`) are passed via Docker build args.

---

### Notes

- MongoDB data is persisted using a Docker volume: `mongo_data`.  
- Ports are mapped as follows:
  - Frontend: `host 3000 → container 80`  
  - Backend: `host 4000 → container 4000`  
  - MongoDB: `host 27017 → container 27017` (optional)  

- **Important:** This project is intended for learning Docker only. It is **not production-ready**.

---

### Improvements for Learning

- Multi-stage Docker builds for smaller frontend image sizes.  
- Use of `REACT_APP_*` variables for environment-specific configuration.  

---