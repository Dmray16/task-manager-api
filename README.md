# Task Management API design 
This API allows users to register, log in, and manage their own tasks.
## End Points
http://localhost:3000/api
POST /auth/register

### Request
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "password123"
}
#### Response
{
  "success": true,
  "message": "User registered successfully",
  "user": {
    "id": "65abc123",
    "name": "John Doe",
    "email": "john@example.com"
  }
}
##### Fail 
{
  "success": false,
  "message": "All fields are required."
}
{
  "success": false,
  "message": "Email already exists."
}

POST /auth/login

{
  "email": "john@example.com",
  "password": "password123"
}
#### Response
{
  "success": true,
  "message": "Login successful",
  "token": "JWT_TOKEN",
  "user": {
    "id": "65abc123",
    "name": "John Doe",
    "email": "john@example.com"
  }
}
##### Fail
{
  "success": false,
  "message": "Invalid email or password."
}

POST /tasks
Authorization: Bearer JWT_TOKEN
{
  "title": "Finish assignment",
  "description": "Complete API project",
  "status": "pending"
}
#### response
{
  "success": true,
  "task": {
    "id": "task123",
    "title": "Finish assignment",
    "description": "Complete API project",
    "status": "pending"
  }
}

GET /api/tasks
Authorization: Bearer JWT_TOKEN
{
  "success": true,
  "tasks": [
    {
      "id": "task123",
      "title": "Finish assignment",
      "status": "pending"
    }
  ]
}

PUT/api/tasks/:id
Authorization: Bearer JWT_TOKEN
{
  "title": "Finish Express Project",
  "status": "completed"
}
{
  "success": true,
  "message": "Task updated",
  "task": {
    "id": "task123",
    "title": "Finish Express Project",
    "status": "completed"
  }
}

DELETE/api/tasks/:id
Authorization: Bearer JWT_TOKEN
{
  "success": true,
  "message": "Task deleted"
}
