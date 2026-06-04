# Backend Template

Welcome to the backend template for the Full Stack App Development module.

This repository contains a fully functional authentication system built using **Node.js**, **Express.js**, **MongoDB**, and **JWT Authentication**. Your goal is to understand the existing codebase and build the required features on top of it.

---

# 📚 Prerequisites

Before starting this assignment, make sure you are comfortable with:

* JavaScript Fundamentals
* Express Routing
* MongoDB & Mongoose
* REST APIs
* Async/Await
* JWT Authentication

If you're not confident with these concepts, revisit the previous modules before proceeding.

---

# 📁 Project Structure

```text
src
├── controllers
│   ├── login.controller.js
│   ├── register.controller.js
│   └── healthcheck.controller.js
│
├── db
│   └── connectDB.js
│
├── middleware
│   └── auth.middleware.js
│
├── models
│   └── User.js
│
├── routes
│   ├── auth.route.js
│   └── healthcheck.route.js
│
└── app.js

index.js
```

---

# 🚀 Getting Started

## 1. Clone the Repository

```bash
git clone <repo-url>
cd <repo-name>
```

## 2. Install Dependencies

```bash
npm install
```

## 3. Create a `.env` File

Create a `.env` file in the root directory and add the following variables:

```env
PORT=3000

MONGO_URI=YOUR_MONGODB_CONNECTION_STRING

JWT_SECRET=YOUR_SECRET_KEY
```

## 4. Run the Server

```bash
npm run dev
```

If everything is configured correctly, you should see:

```bash
MongoDB Connected
Server Running on Port 3000
```

---

# 🔄 Understanding the Request Flow

A typical request follows this flow:

```text
Client
↓
Route
↓
Controller
↓
Model
↓
MongoDB
```

For protected routes:

```text
Client
↓
Authentication Middleware
↓
Route
↓
Controller
↓
Model
↓
MongoDB
```

Understanding this flow is essential before you begin implementing your own features.

---

# 🔐 Authentication

Authentication has already been implemented for you.

The following APIs are available:

| Method | Endpoint             | Description            |
| ------ | -------------------- | ---------------------- |
| POST   | `/api/auth/register` | Register a new user    |
| POST   | `/api/auth/login`    | Login an existing user |

A JWT token will be returned upon successful login.

For protected routes, include the token in the request headers:

```text
Authorization: Bearer <token>
```

---

# 🛡️ Authentication Middleware

The template includes an authentication middleware that verifies JWT tokens before allowing access to protected routes.

After successful verification, the logged-in user's information can be accessed using:

```js
req.user
```

You should use this middleware whenever a route requires authentication.

For example:

```js
router.get("/all", verifyToken, getAllItems);
```

This ensures that only authenticated users can access the endpoint.

---

# 🏥 Healthcheck Route

To verify that your backend is running correctly:

| Method | Endpoint           |
| ------ | ------------------ |
| GET    | `/api/healthcheck` |

Expected Response:

```json
{
  "message": "Backend Running Successfully"
}
```

---

# 🛠️ Your Task

Your task is to build the backend functionality required for **one** of the project options provided in the module.

Authentication, database connection, JWT generation, middleware, and healthcheck routes have already been implemented for you.

Your responsibilities include:

* Creating the required model(s)
* Implementing controller logic
* Creating routes
* Registering routes inside `app.js`
* Testing endpoints using Postman
* Integrating your backend with Flutter

---

# 🛒 Project Option 1: Campus Marketplace

Build a marketplace platform where students can buy and sell items within the campus community.

## Required Files

```text
src
├── models
│   └── Listing.js
│
├── controllers
│   └── listing.controller.js
│
├── routes
│   └── listing.route.js
```

## Required APIs

| Method | Endpoint              | Description            |
| ------ | --------------------- | ---------------------- |
| POST   | `/api/listing/create` | Create a new listing   |
| GET    | `/api/listing/all`    | Fetch all listings     |
| PUT    | `/api/listing/update` | Update listing details |
| DELETE | `/api/listing/delete` | Delete a listing       |

## Listing Fields

```js
{
  userId,
  title,
  description,
  price,
  category,
  imageUrl,
  status,
  createdAt
}
```

---

# 🔍 Project Option 2: Lost & Found Portal

Build a platform where users can report lost or found items and browse existing reports.

## Required Files

```text
src
├── models
│   └── Item.js
│
├── controllers
│   └── item.controller.js
│
├── routes
│   └── item.route.js
```

## Required APIs

| Method | Endpoint           | Description              |
| ------ | ------------------ | ------------------------ |
| POST   | `/api/item/create` | Create a new item report |
| GET    | `/api/item/all`    | Fetch all reports        |
| PUT    | `/api/item/update` | Update report details    |
| DELETE | `/api/item/delete` | Delete a report          |

## Item Fields

```js
{
  userId,
  title,
  description,
  location,
  imageUrl,
  type,
  status,
  createdAt
}
```

---

# ⚠️ Files You Should Not Modify

The following components have already been implemented and generally do not require changes:

* User Model
* Authentication Controllers
* Authentication Routes
* Database Connection
* JWT Middleware
* Healthcheck Route

Focus on implementing the files required for your selected project.

---

# 💡 Before You Begin

Take some time to understand the project structure before jumping into development.

The codebase has been documented with the intention of helping you understand how a typical Express backend is organized. Read through the files carefully, follow the request flow, and make sure you understand what each function is doing.

Avoid blindly copying code or relying entirely on AI-generated solutions. The objective of this module is to help you understand how backend systems work under the hood.

---

# 🔒 Security Reminder

Never commit sensitive information to GitHub.

Make sure your `.gitignore` contains:

```text
node_modules
.env
```

Never expose:

* MongoDB connection strings
* JWT secrets
* API keys
* Private credentials

---

# ✅ Submission Checklist

Before submitting, ensure that:

* [ ] Backend runs successfully
* [ ] MongoDB is connected
* [ ] Register API works
* [ ] Login API works
* [ ] Protected routes work
* [ ] All required CRUD APIs are implemented
* [ ] Routes are registered correctly
* [ ] Frontend is connected to backend
* [ ] Project is pushed to GitHub
* [ ] `.env` is excluded from the repository

---

# 🚀 Good Luck

This template handles the boilerplate so that you can focus on learning the most important backend concepts:

* Express Routing
* MongoDB Models
* Controllers
* Middleware
* Authentication
* CRUD Operations
* API Integration

Build something cool, experiment freely, and most importantly, have fun!

Happy Coding! 💻🚀
