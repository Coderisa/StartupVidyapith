# 🚀 Startup Vidyapith

**Banasthali Vidyapith – Startup Innovation Portal**

A full‑stack platform that connects students, founders, and administrators within the Banasthali Vidyapith ecosystem. It features semantic startup discovery, founder profiles, event management, blogging, community chat, and an AI‑powered recommendation engine.

---

## ✨ Features

- **🔐 Authentication** – Secure login with Banasthali ID + email + password; OTP verification for sign‑up; password reset.
- **👤 Founder Profiles** – Multi‑step profile creation (bio, looking for, business stage, skills, interests). Includes product management and Q&A.
- **🎓 Student Dashboard** – Track applications, manage profile, upload resume, view acceptance notifications.
- **📅 Events** – Create, edit, delete events (hiring, workshops, hackathons) with TTS (Text‑to‑Speech) for accessibility.
- **📝 Blogging** – Write, edit, publish, and delete blog posts with categories, tags, and comments.
- **💬 Community Chat** – Create, join, and leave chat rooms. Messages are stored in the database and fetched via REST API.
- **🧠 Semantic Startup Search** – AI‑powered search that understands intent using Sentence‑Transformers (`/recommend`).
- **🔗 Similar Startups** – Cluster‑based recommendations (`/similar_startups`) to discover related ventures.
- **🤖 AI Tools** – Cover letter generator & professional photo assistant (MediaPipe face detection).

---

## 🛠️ Tech Stack

| Area                | Technologies |
|---------------------|--------------|
| **Frontend**        | React, React Router, Axios, CSS Modules, Emoji Picker, MediaPipe |
| **Backend**         | Node.js, Express, MongoDB (Atlas), Mongoose, JWT, Bcrypt, Nodemailer |
| **ML Service**      | Python, FastAPI, Uvicorn, Sentence‑Transformers, Scikit‑Learn, Joblib |
| **Containerization**| Docker, Docker Compose |
| **Deployment**      | Frontend: Vercel; Backend & ML: Render |

---

## 🧩 Architecture Overview

The platform is built as three independent services:

1. **Frontend** – React SPA (served by Vercel or locally via Vite).
2. **Backend** – Node/Express REST API.
3. **ML Service** – FastAPI microservice for semantic search.

---

## 📋 Prerequisites

- [Node.js](https://nodejs.org/) (v16+)
- [Python](https://www.python.org/) (v3.8+)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) (with WSL 2 enabled)
- [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) account (or local MongoDB)
- [Git](https://git-scm.com/)

---

## 🐳 Quick Start with Docker (Recommended)

This is the fastest way to get the entire application running locally.

### 1. Clone the repository
```bash
git clone https://github.com/Coderisa/StartupVidyapith.git
cd StartupVidyapith

2. Set up environment variables
Create a .env file in the root folder (next to docker-compose.yml) with your MongoDB Atlas credentials:

env
# MongoDB Atlas Connection
MONGODB_URI=mongodb+srv://YOUR_USERNAME:YOUR_PASSWORD@cluster0.xxxxx.mongodb.net/banasthali_startup?retryWrites=true&w=majority

# JWT Secret (generate a strong random string)
JWT_SECRET=your_super_secret_jwt_key

# Frontend URL (keep as localhost for local testing)
FRONTEND_URL=http://localhost:5173

# Node Environment
NODE_ENV=development

3. Build and start all services

docker compose up --build

4. Access the application
Frontend: http://localhost:5173
Backend API: http://localhost:5000
ML Service Docs: http://localhost:8000/docs

🛠️ Local Development (Without Docker)
If you prefer to run each service separately:

Backend
bash
cd Backend
npm install
npm start
# Runs on http://localhost:5000
Frontend
bash
cd Frontend
npm install
npm run dev
# Runs on http://localhost:5173
ML Service
bash
cd ml-service
pip install -r requirements.txt
uvicorn recommender_api:app --host 0.0.0.0 --port 8000
# Runs on http://localhost:8000
🔐 Environment Variables
Backend .env
env
PORT=5000
MONGODB_URI=mongodb+srv://...
JWT_SECRET=your_jwt_secret
FRONTEND_URL=http://localhost:5173
NODE_ENV=development
Frontend .env.local
env
VITE_API_BASE_URL=http://localhost:5000/api
VITE_API_URL=http://localhost:5000
VITE_ML_SERVICE_URL=http://localhost:8000
👥 Demo Accounts
Use these pre‑created accounts to test the platform:

Role	Banasthali ID	Email	Password
Student	BTCSE20201	priya.sharma@gmail.com	Student@123
Founder	BTFDR20201	meera.joshi@techstartup.com	Founder@123
Admin	BTADM20201	sunita.verma@banasthali.in	Admin@123
🚀 Deployment
Frontend → Vercel
Push your code to GitHub.

Import the repository on Vercel.

Set Root Directory to Frontend/.

Add environment variables:

VITE_API_BASE_URL = https://your-backend.onrender.com/api

VITE_API_URL = https://your-backend.onrender.com

VITE_ML_SERVICE_URL = https://your-ml-service.onrender.com

Backend → Render
Create a new Web Service on Render.

Connect your GitHub repo.

Set Root Directory to Backend/.

Build Command: npm install

Start Command: node -r crypto server.js

Add environment variables (same as your local .env).

ML Service → Render
Create a new Web Service on Render.

Set Root Directory to ml-service/.

Build Command: pip install -r requirements.txt

Start Command: uvicorn recommender_api:app --host 0.0.0.0 --port $PORT

Add environment variable: PORT = 8000.

📂 Project Structure
text
StartupVidyapith/
├── Backend/                 # Node.js + Express API
│   ├── routes/              # API routes
│   ├── models/              # MongoDB schemas
│   ├── database/            # Database connection
│   ├── server.js            # Entry point
│   ├── Dockerfile
│   └── package.json
├── Frontend/                # React + Vite app
│   ├── src/                 # React components
│   ├── public/              # Static assets
│   ├── Dockerfile
│   ├── nginx.conf           # Nginx config for React Router
│   └── package.json
├── ml-service/              # Python FastAPI microservice
│   ├── recommender_api.py   # FastAPI app
│   ├── train_semantic.py    # Training script
│   ├── requirements.txt
│   └── Dockerfile
├── docker-compose.yml       # Docker orchestration
├── .env                     # Secrets (NOT committed)
└── README.md
🤝 Contributing
Contributions are welcome! Please open an issue or submit a pull request.

Fork the repository.

Create a new branch (git checkout -b feature/amazing-feature).

Commit your changes (git commit -m 'Add some amazing feature').

Push to the branch (git push origin feature/amazing-feature).

Open a Pull Request.

📄 License
This project is licensed under the MIT License – see the LICENSE file for details.

---

🙏 Acknowledgments
Banasthali Vidyapith for inspiring the platform.
Sentence‑Transformers for the semantic search model.
The open‑source community for all the amazing tools.

Made with ❤️ by the Startup Vidyapith Team
