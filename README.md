# Node.js Practical Exam - JWT Login + Profile API

Beginner-friendly JWT authentication project.

## Folder Structure

```text
nodejs_practical_exam/
│
├── src/
│   ├── db/
│   │   └── db.js
│   │
│   ├── middleware/
│   │   └── auth.js
│   │
│   ├── models/
│   │   └── User.js
│   │
│   └── app.js
│
├── .env
├── .env.example
├── .gitignore
├── package.json
└── server.js
```

## Setup

1. Extract the ZIP.
2. Open the project in VS Code.
3. Run:

```bash
npm install
```

4. Open `.env`.
5. Replace `your_mongodb_connection_string` with your MongoDB Atlas connection string.
6. Change `your_secret_key` to your own JWT secret.
7. Start the server:

```bash
npm run dev
```

## APIs

### Register

POST

`http://localhost:5000/register`

Body:

```json
{
  "name": "Raiyan",
  "email": "raiyan@gmail.com",
  "password": "123456"
}
```

### Login

POST

`http://localhost:5000/login`

Body:

```json
{
  "email": "raiyan@gmail.com",
  "password": "123456"
}
```

Copy the JWT token from the response.

### Profile

GET

`http://localhost:5000/profile`

In Postman:

Authorization -> Bearer Token -> paste the JWT token.

## Authentication Flow

Register
-> bcrypt hashes password
-> MongoDB stores user

Login
-> bcrypt compares password
-> JWT token is created

Profile
-> auth middleware verifies JWT
-> user ID is taken from token
-> profile is returned
