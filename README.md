
# Task Management Application

A full-stack Task Management application built using React, Node.js, Express.js, and MongoDB.

## Features

### Authentication
- Email and password login
- JWT-based authentication
- Protected routes
- Secure password hashing using bcrypt
- Invalid login handling

### Dashboard
- Total task count
- Completed task count
- Pending task count
- High-priority task count

### Task Management
- Create tasks
- View tasks
- Edit tasks
- Delete tasks
- Change task status
- Set priority
- Set due date

### Search, Filter and Sort
- Search tasks by title
- Filter by status
- Filter by priority
- Sort by due date
- Sort by priority
- Sort by title
- Ascending and descending order

### Validation
- Required field validation
- Email validation
- Task title validation
- Task description validation
- Due date validation
- Priority validation
- Status validation
- MongoDB ObjectId validation

## Technologies Used

### Frontend
- React
- React Router
- Axios
- CSS

### Backend
- Node.js
- Express.js
- MongoDB
- Mongoose
- JWT
- bcryptjs

## Project Structure

```text
task-management-app/
│
├── backend/
│   ├── config/
│   │   └── db.js
│   ├── controllers/
│   │   ├── authController.js
│   │   └── taskController.js
│   ├── middleware/
│   │   └── authMiddleware.js
│   ├── models/
│   │   ├── User.js
│   │   └── Task.js
│   ├── routes/
│   │   ├── authRoutes.js
│   │   └── taskRoutes.js
│   ├── .env
│   ├── .env.example
│   ├── .gitignore
│   ├── package.json
│   └── server.js
│
├── frontend/
│   ├── src/
│   │   ├── compo/
│   │   │   ├── Navbar.jsx
│   │   │   ├── ProtectedRoute.jsx
│   │   │   ├── TaskCard.jsx
│   │   │   └── TaskForm.jsx
│   │   ├── pages/
│   │   │   ├── Dashboard.jsx
│   │   │   ├── Login.jsx
│   │   │   └── Tasks.jsx
│   │   ├── services/
│   │   │   └── api.js
│   │   ├── App.jsx
│   │   ├── App.css
│   │   ├── index.css
│   │   └── main.jsx
│   ├── package.json
│   └── .gitignore
│
├── .gitignore
└── README.md

Prerequisites

Install the following before running the project:

Node.js
npm
MongoDB Atlas account or local MongoDB
Git
Backend Setup

Open a terminal and go to the backend folder:

cd backend

Install dependencies:

npm install

Create a .env file inside the backend folder:

PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret

Replace the values with your actual MongoDB connection string and JWT secret.

Start the backend:

node server.js

The server should run on:

http://localhost:5000
Frontend Setup

Open another terminal:

cd frontend

Install dependencies:

npm install

Start the React development server:

npm run dev

The frontend should run on:

http://localhost:5173
Login

Use the test account created during development.

Email: test@example.com
Password: 123456

For a real deployment, use a secure password and do not expose credentials in source code.

API Documentation
Authentication
Login
POST /api/auth/login

Request body:

{
  "email": "test@example.com",
  "password": "123456"
}

Successful response:

{
  "success": true,
  "message": "Login successful",
  "token": "JWT_TOKEN",
  "user": {
    "id": "USER_ID",
    "email": "test@example.com"
  }
}
Tasks

All task APIs require:

Authorization: Bearer JWT_TOKEN
Get all tasks
GET /api/tasks

Optional query parameters:

search
status
priority
sortBy
order

Example:

GET /api/tasks?search=project&status=Pending&priority=High&sortBy=dueDate&order=asc
Get one task
GET /api/tasks/:id
Create task
POST /api/tasks

Request body:

{
  "title": "Complete Assessment",
  "description": "Finish the task management project",
  "dueDate": "2026-10-01",
  "priority": "High",
  "status": "Pending"
}
Update task
PUT /api/tasks/:id

Example request:

{
  "title": "Complete Assessment Updated",
  "status": "Completed"
}
Delete task
DELETE /api/tasks/:id
Get task statistics
GET /api/tasks/stats

Example response:

{
  "success": true,
  "stats": {
    "totalTasks": 5,
    "completedTasks": 2,
    "pendingTasks": 3,
    "highPriorityTasks": 1
  }
}
HTTP Status Codes
Status	Meaning
200	Request successful
201	Resource created
400	Invalid request or validation error
401	Authentication required or invalid
404	Resource not found
500	Server error
Security
Passwords are hashed using bcrypt.
JWT is used for authentication.
Protected APIs require a valid JWT.
Tasks are associated with the authenticated user.
Environment variables are used for database credentials and JWT secrets.
.env files are excluded from Git.
Development credentials should not be committed to the repository.
Running the Application

Start the backend:

cd backend
node server.js

Start the frontend in another terminal:

cd frontend
npm run dev

Then open:

http://localhost:5173
