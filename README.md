# 💪 Fitness Tracker App

A full-stack fitness tracking application built with the **MERN Stack** (MongoDB, Express, React, Node.js). Log your workouts, track calories burned, and visualize your fitness progress with interactive charts.

---

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Installation & Setup](#-installation--setup)
- [Running the App](#-running-the-app)
- [API Endpoints](#-api-endpoints)
- [How to Use](#-how-to-use)
- [Environment Variables](#-environment-variables)

---

## ✨ Features

- **User Authentication**
  - Sign up with email and password
  - Secure login with JWT tokens
  - Password hashing with bcrypt

- **Workout Management**
  - Add workouts with details (exercise name, sets, reps, weight, duration)
  - View workouts by date
  - Track exercises in different categories

- **Dashboard & Analytics**
  - View today's total calories burned
  - See total workouts completed
  - Calculate average calories per workout
  - **Weekly Chart** — visualize 7-day calorie burn trends
  - **Category Pie Chart** — breakdown of calories by exercise type

- **User-Friendly Interface**
  - Clean, responsive UI with Material-UI (MUI)
  - Dark/Light theme support
  - Mobile-optimized design

---

## 🛠 Tech Stack

### Frontend
- **React** 18 — UI library
- **Redux Toolkit** — state management
- **Axios** — HTTP client
- **Material-UI (MUI)** — component library & charts
- **Styled Components** — CSS-in-JS styling
- **React Router** — client-side routing
- **Redux Persist** — persist Redux state to localStorage

### Backend
- **Node.js** + **Express** — server & API
- **MongoDB** — database
- **Mongoose** — ODM (object data modeling)
- **JWT (jsonwebtoken)** — authentication
- **bcrypt** — password hashing
- **CORS** — cross-origin requests
- **dotenv** — environment variables

---

## 📁 Project Structure

```
Fitness-Tracker-App/
├── client/                          # React frontend
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── api/
│   │   │   └── index.js             # Axios API calls
│   │   ├── components/
│   │   │   ├── AddWorkout.jsx       # Add workout form
│   │   │   ├── Navbar.jsx           # Navigation bar
│   │   │   ├── SignIn.jsx           # Sign in form
│   │   │   ├── SignUp.jsx           # Sign up form
│   │   │   └── cards/               # Dashboard cards
│   │   │       ├── CategoryChart.jsx
│   │   │       ├── WeeklyStatCard.jsx
│   │   │       └── WorkoutCard.jsx
│   │   ├── pages/
│   │   │   ├── Authentication.jsx   # Auth page
│   │   │   ├── Dashboard.jsx        # Main dashboard
│   │   │   └── Workouts.jsx         # Workouts list
│   │   ├── redux/
│   │   │   ├── store.js             # Redux store config
│   │   │   └── reducers/
│   │   │       └── userSlice.js     # User state
│   │   ├── utils/
│   │   │   ├── Themes.js            # Theme config
│   │   │   └── data.js              # Utility functions
│   │   ├── App.js
│   │   └── index.js
│   └── package.json
│
├── server/                          # Express backend
│   ├── controllers/
│   │   └── User.js                  # User & workout logic
│   ├── models/
│   │   ├── User.js                  # User schema
│   │   └── Workout.js               # Workout schema
│   ├── routes/
│   │   └── User.js                  # API routes
│   ├── middleware/
│   │   └── verifyToken.js           # JWT verification
│   ├── error.js                     # Error handler
│   ├── index.js                     # Server entry point
│   ├── .env                         # Environment variables (not committed)
│   └── package.json
│
└── README.md
```

---

## 📦 Prerequisites

Before you start, ensure you have:

- **Node.js** (v16 or higher) — [Download](https://nodejs.org/)
- **npm** (comes with Node.js)
- **MongoDB** — [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) (cloud) or local installation

---

## 🚀 Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/rishavchanda/Fitness-Tracker-App.git
cd Fitness-Tracker-App
```

### 2. Install Server Dependencies

```bash
cd server
npm install
```

### 3. Configure Server Environment Variables

Create a `.env` file in the `server` folder:

```bash
# server/.env
JWT=your_jwt_secret_key_here
MONGODB_URL=your_mongodb_connection_string
```

**Example:**
```
JWT=mysecretkey123456
MONGODB_URL=mongodb+srv://username:password@cluster.mongodb.net/fitness-tracker
```

> **Note:** `JWT` is used for signing authentication tokens. Use a strong, random string in production.

### 4. Install Client Dependencies

```bash
cd ../client
npm install
```

### 5. Configure Client (Optional)

If running locally, update the API base URL in `client/src/api/index.js`:

```javascript
const API = axios.create({
  baseURL: "http://localhost:8081/api/",  // Change from deployed URL to localhost
});
```

Or create a `.env` file in the `client` folder:

```
REACT_APP_API_URL=http://localhost:8081/api/
```

---

## 🎯 Running the App

### Start the Backend Server

```bash
cd server
npm start
```

The server runs on **http://localhost:8081** and connects to MongoDB.

### Start the Frontend (in a new terminal)

```bash
cd client
npm start
```

The app opens on **http://localhost:3000** in your browser.

---

## 🔌 API Endpoints

All endpoints require a JWT token in the `Authorization` header (except signup/signin):

```
Authorization: Bearer <token>
```

### Authentication

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/user/signup` | Register a new user |
| POST | `/api/user/signin` | Login user |

### User Dashboard

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/user/dashboard` | Get dashboard stats (calories, workouts, charts) |

### Workouts

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/user/workout?date=YYYY-MM-DD` | Get workouts for a specific date |
| POST | `/api/user/workout` | Add a new workout |

---

## 📱 How to Use

1. **Sign Up** — Create an account with your email and password.
2. **Sign In** — Log in with your credentials.
3. **Dashboard** — View today's stats and 7-day progress.
4. **Add Workout** — Click "Add Workout" and enter exercise details.
5. **Track Progress** — View weekly trends and calorie breakdown by category.

---

## 🔐 Environment Variables

### Server (`.env`)

```env
# JWT secret for token signing (use a strong random string)
JWT=your_jwt_secret_here

# MongoDB connection string (Atlas or local)
MONGODB_URL=mongodb+srv://username:password@cluster.mongodb.net/database_name
```

### Client (optional `.env`)

```env
# API base URL (defaults to deployed backend if not set)
REACT_APP_API_URL=http://localhost:8081/api/
```

---

## 🤝 Contributing

Feel free to fork, modify, and submit pull requests!

---

## 📄 License

This project is open source and available under the ISC License.

---

## 👨‍💻 Author

**Rishav Patel**

Happy Tracking! 🏋️‍♂️
