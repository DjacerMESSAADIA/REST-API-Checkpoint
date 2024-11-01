# REST API checkpoint

A simple REST API built with Node.js, Express, and MongoDB for managing user data.

## Description

This project implements a basic REST API that allows you to perform CRUD (Create, Read, Update, Delete) operations on user data.

## Features

- Get all users
- Create new users
- Update existing users
- Delete users
- MongoDB integration
- Error handling
- Environment variable configuration


## Project Structure

```
rest-api-checkpoint/
│  
├── models/
│   └── User.js
├── server.js
├── package.json
└── README.md
```

## Installation

1. Install dependencies:
```bash
npm install
```

2. Create a `.env` file in the config directory with the following variables:
```
MONGO_URI=mongodb://localhost:27017/userDB
PORT=5000
```

3. Start the server:
```bash
node server.js
```

## API Endpoints

### GET /api/users
- Description: Retrieve all users
- Method: GET
- Response: Array of user objects

### POST /api/users
- Description: Create a new user
- Method: POST
- Body: 
```json
{
    "name": "John Doe",
    "email": "john@example.com",
    "age": 30
}
```
- Response: Created user object

### PUT /api/users/:id
- Description: Update a user by ID
- Method: PUT
- Parameters: id (user ID)
- Body: Fields to update
```json
{
    "name": "John Updated",
    "age": 31
}
```
- Response: Updated user object

### DELETE /api/users/:id
- Description: Delete a user by ID
- Method: DELETE
- Parameters: id (user ID)
- Response: Success message

## User Schema

```javascript
{
    name: String,      // required
    email: String,     // required, unique
    age: Number,       // required
    createdAt: Date    // automatically set
}
```

## Error Handling

The API includes error handling for:
- Invalid requests
- Database connection errors
- Not found errors
- Validation errors

### Error Response Format
```json
{
    "message": "Error description here"
}
```

## Tests to run with Postman

1. **GET Request**:
   - URL: `http://localhost:5000/api/users`
   - Method: GET

2. **POST Request**:
   - URL: `http://localhost:5000/api/users`
   - Method: POST
   - Headers: `Content-Type: application/json`
   - Body: Raw JSON

3. **PUT Request**:
   - URL: `http://localhost:5000/api/users/:id`
   - Method: PUT
   - Headers: `Content-Type: application/json`
   - Body: Raw JSON

4. **DELETE Request**:
   - URL: `http://localhost:5000/api/users/:id`
   - Method: DELETE

## Environment Variables

- `PORT`: The port number for the server (default: 5000)
- `MONGO_URI`: MongoDB connection string
