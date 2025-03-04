# ToDo List API

A simple and secure API for managing a to-do list, allowing users to perform CRUD operations (Create, Read, Update, Delete) on their tasks. The API uses JWT authentication for security and supports CORS for cross-origin requests.

## Live Demo

The API is hosted on Render and can be accessed at: [https://todoapiclient-tzfv.onrender.com](https://todoapiclient-tzfv.onrender.com)

## Features

- **User Authentication**: Register and log in with JWT authentication.
- **Task Management**: Create, read, update, and delete tasks.
- **Secure API**: Uses JWT tokens for authorization.
- **CORS Enabled**: Allows cross-origin requests.
- **Swagger Documentation**: Available for easy API exploration.

## Endpoints

### Authentication

| Method | Route     | Description                | Auth Required |
| ------ | --------- | -------------------------- | ------------- |
| POST   | /register | Register a new user        | ❌             |
| POST   | /login    | Authenticate and get a JWT | ❌             |

### Task Management

| Method | Route      | Description                     | Auth Required |
| ------ | ---------- | ------------------------------- | ------------- |
| GET    | /Items     | Retrieve all tasks for the user | ✅             |
| GET    | /Item/{id} | Retrieve a task by ID           | ✅             |
| POST   | /Item      | Add a new task                  | ✅             |
| PUT    | /Item/{id} | Update a task's completion      | ✅             |
| DELETE | /Item/{id} | Delete a task by ID             | ✅             |

## Getting Started

### Prerequisites

- .NET 6.0 SDK or higher
- MySQL database
- Postman or any API testing tool (optional)

### Installation

#### Clone the Repository

```sh
git clone https://github.com/HadassaO/ToDo-List.git
cd ToDo-List
```

#### Set Up the Database

Update the `appsettings.json` file with your MySQL connection string:

```json
{
    "ConnectionStrings": {
        "ToDoDB": "server=localhost;database=todo;user=root;password=yourpassword"
    }
}
```

#### Run the Application

```sh
dotnet watch run
```

The API will be available at `http://localhost:your_port`.

## Request Examples

### Authentication

#### Register a User

```http
POST /register
```

**Request Body (JSON):**

```json
{
    "UserName": "testuser",
    "Email": "test@example.com",
    "Password": "securepassword"
}
```

#### Log In and Get Token

```http
POST /login
```

**Request Body (JSON):**

```json
{
    "UserName": "testuser",
    "Password": "securepassword"
}
```

**Response (JSON):**

```json
{
    "token": "your-jwt-token"
}
```

### CRUD Operations

#### Get All Tasks

```http
GET /Items
```

**Headers:**

```
Authorization: Bearer <your-jwt-token>
```

#### Add a New Task

```http
POST /Item
```

**Headers:**

```
Authorization: Bearer <your-jwt-token>
```

**Request Body (JSON):**

```json
{
    "Name": "New Task",
    "IsComplete": false
}
```

#### Update a Task

```http
PUT /Item/{id}
```

**Headers:**

```
Authorization: Bearer <your-jwt-token>
```

**Request Body (JSON):**

```json
{
    "isComplete": true
}
```

#### Delete a Task

```http
DELETE /Item/{id}
```

**Headers:**

```
Authorization: Bearer <your-jwt-token>
```

## Additional Features

### CORS Support
CORS is enabled to allow any origin to access the API. This is useful during development when your frontend and backend are hosted on different ports.

### Swagger API Documentation
Once the application is running, Swagger documentation can be accessed at:

```
http://localhost:your_port/swagger
```

### Frontend Integration
For the frontend, refer to the **ToDo List React Client** and update the API URL in `service.js`.

## License

This project is licensed under the MIT License.

