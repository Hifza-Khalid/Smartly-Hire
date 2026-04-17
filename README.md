<p align="center">
  <img src="logo.png" alt="Smartly Hire Logo" width="200"/>
</p>


# 🧠 Smartly Hire - AI-Powered Online Interview Platform

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![React](https://img.shields.io/badge/React-18.3-61DAFB?logo=react&logoColor=white)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-20.x-339933?logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?logo=mongodb&logoColor=white)](https://www.mongodb.com/atlas)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.x-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-Face%20Detection-FF6C37?logo=google&logoColor=white)](https://developers.google.com/mediapipe)
[![Status](https://img.shields.io/badge/Status-Active-success)]()


## 🚀 Overview

**Smartly Hire** is an AI-powered online interview platform designed to make recruitment **secure, efficient, and automated**. It provides real-time monitoring of candidates using face detection, emotion recognition, head-pose tracking, and behavioral analysis to ensure fair and proctored interviews.

> 🎓 **Final Year Project** | BS Software Engineering (Session 2022-2026)  
> 🆔 **FYP ID:** BSSE-FYP-F25-059 | **The Superior University, Lahore**

---

## ✨ Key Features

| Feature | Description |
|---------|-------------|
| 🤖 **AI Proctoring** | Real-time face detection, emotion analysis, head-pose tracking, and cheating detection |
| 📹 **Live Monitoring** | Webcam-based candidate behavior analysis with violation logging |
| 📝 **Automated Interviews** | Dynamic question generation (MCQ, coding, short answers) with timers |
| 📊 **Smart Reporting** | AI-generated interview reports with integrity scores and analytics |
| 👥 **Role-Based Access** | Separate dashboards for Admins (Recruiters) and Candidates |
| 🔒 **Secure Authentication** | JWT-based auth with role-based access control |
| ☁️ **Cloud Native** | Deployed on modern cloud platforms with microservices architecture |

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                         Client (Browser)                         │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────────┐  │
│  │ React +     │  │ Tailwind    │  │ WebRTC / Web Speech API  │  │
│  │ Tailwind    │  │ Components  │  │ Camera + Microphone      │  │
│  └─────────────┘  └─────────────┘  └─────────────────────────┘  │
└─────────────────────────────────────────────────────────────────┘
                                  │
                                  ▼
┌─────────────────────────────────────────────────────────────────┐
│                      API Gateway (Node.js + Express)             │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────────┐  │
│  │ Auth Module │  │ Job Module  │  │ Interview Module        │  │
│  │ JWT/RBAC    │  │ CRUD + AI   │  │ Scheduling + Answers    │  │
│  └─────────────┘  └─────────────┘  └─────────────────────────┘  │
└─────────────────────────────────────────────────────────────────┘
                    │                       │
                    ▼                       ▼
          ┌─────────────────┐     ┌─────────────────────────────┐
          │   MongoDB Atlas  │     │      AI Microservices       │
          │  (Users, Jobs,   │     │  ┌───────────┬───────────┐  │
          │   Interviews,    │◄────│  │ MediaPipe │  Mini-    │  │
          │   Violations)    │     │  │ FaceMesh  │  Xception │  │
          └─────────────────┘     │  ├───────────┼───────────┤  │
                                   │  │ COCO-SSD  │  Head     │  │
                                   │  │ (Objects) │  Pose     │  │
                                   │  └───────────┴───────────┘  │
                                   └─────────────────────────────┘
```

---

## 🧠 AI/ML Components

| Component | Technology | Purpose |
|-----------|------------|---------|
| **Face Detection** | MediaPipe Face Detection | Locate faces in webcam feed |
| **Face Landmarks** | MediaPipe FaceMesh (468 points) | Track facial expressions and head pose |
| **Object Detection** | COCO-SSD / YOLO | Detect phones, books, or unauthorized objects |
| **Emotion Recognition** | Mini-Xception CNN | Classify candidate emotional state |
| **Head Pose Estimation** | SolvePnP | Track candidate attention and gaze |
| **Integrity Scoring** | Weighted Deduction System | Calculate final honesty score |

---

## 🛠️ Tech Stack

### Frontend
- **Framework:** React 18 + Vite
- **Styling:** Tailwind CSS
- **State Management:** React Context / Hooks
- **HTTP Client:** Axios
- **Charts:** Chart.js

### Backend
- **Runtime:** Node.js
- **Framework:** Express.js
- **Authentication:** JWT + bcrypt
- **Database:** MongoDB Atlas (Mongoose ODM)

### AI Services
- **Face Processing:** MediaPipe (Client-side)
- **Object Detection:** TensorFlow.js + COCO-SSD
- **Emotion Analysis:** Mini-Xception CNN
- **API Framework:** Python + FastAPI (optional server-side)

### DevOps
- **Version Control:** Git + GitHub
- **Frontend Hosting:** Vercel / Netlify
- **Backend Hosting:** Render / Railway
- **Containerization:** Docker (for AI services)

---

## 🚦 Getting Started

### Prerequisites
- Node.js (v18 or higher)
- MongoDB Atlas account (or local MongoDB)
- Modern browser with webcam support

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/Hifza-Khalid/Smartly-Hire.git
cd Smartly-Hire
```

2. **Backend Setup**
```bash
cd backend
npm install
cp .env.example .env   # Configure your environment variables
npm run dev
```

3. **Frontend Setup**
```bash
cd frontend
npm install
npm run dev
```

4. **Environment Variables (.env)**
```env
# Backend
PORT=5000
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret

# Frontend
VITE_API_URL=http://localhost:5000/api
```

---

## 📊 Database Schema

<details>
<summary>Click to view key collections</summary>

| Collection | Description |
|------------|-------------|
| `users` | Admin & Candidate profiles (hashed passwords) |
| `jobs` | Job postings with requirements and questions |
| `applications` | Candidate job applications with resumes |
| `interview_sessions` | Live interview tracking and integrity scores |
| `questions` | Predefined or AI-generated questions |
| `answers` | Candidate responses with auto-evaluation |
| `violations` | Proctoring violation logs with timestamps |
| `reports` | Final interview evaluation reports (JSON/PDF) |

</details>

---

## 👥 Team

| Name | Role | Registration # |
|------|------|----------------|
| **Hifza Khalid** | Team Lead / ML Integration | SU92-BSSEM-F22-202 |
| **Baqir Sultan** | Backend / DevOps | SU92-BSSEM-F22-201 |
| **Muhammad Zubair** | Frontend / Database | SU92-BSSEM-F22-196 |

**Supervisor:** Mr. Sohail Irshad (Lecturer, The Superior University)

---

## 📈 Future Enhancements

- [ ] Audio voice-to-text transcription for verbal answers
- [ ] Color-blind accessible themes (high-contrast modes)
- [ ] Live streaming for recruiters to monitor interviews in real-time
- [ ] Mobile application (React Native)
- [ ] GPU-accelerated server-side AI processing
- [ ] Multi-language support for international candidates

---

## 📄 License

This project is submitted in partial fulfillment of the degree of **BS Software Engineering** at The Superior University, Lahore. All rights reserved.

---

## 🙏 Acknowledgements

- **Mr. Sohail Irshad** for his continuous guidance and mentorship
- **Department of Software Engineering** for providing the resources
- **MediaPipe & TensorFlow teams** for open-source ML libraries
- All test candidates who participated in system validation

---

<p align="center">
  Made with ❤️ by Team Smartly Hire
  <br/>
  <sub>© 2025 • The Superior University, Lahore</sub>
</p>
