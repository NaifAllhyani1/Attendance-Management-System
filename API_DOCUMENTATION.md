# Attendance Management System API Documentation

This API allows interaction with the Attendance Management System, built using Java, MySQL, and NetBeans IDE. It manages student attendance, user authentication, and attendance reports.

# API Endpoints

### 1. Authentication
#### Login
- **URL**: `/api/login`
- **Method**: `POST`
- **Request Body**:
  ```json
  {
    "username": "exampleUser",
    "password": "examplePassword"
  }
  ```
- **Response**:
  ```json
  {
    "token": "your_auth_token"
  }
  ```
- **Description**: Authenticates a user and returns an authentication token.

#### Logout
- **URL**: `/api/logout`
- **Method**: `POST`
- **Headers**: 
  ```json
  {
    "Authorization": "Bearer your_auth_token"
  }
  ```
- **Description**: Logs out the user and invalidates the session.

## Database Tables
### Users Table
- **Table Name**: `users`
- **Columns**:
  - `id`: Integer, Primary Key
  - `username`: String, unique
  - `password`: String, encrypted
  - `role`: String, defines if the user is admin, teacher, or student
### 2. Attendance Management
#### Mark Attendance
- **URL**: `/api/attendance`
- **Method**: `POST`
- **Request Body**:
  ```json
  {
    "student_id": 123,
    "date": "2024-10-18",
    "status": "present"
  }
  ```
- **Response**:
  ```json
  {
    "message": "Attendance marked successfully"
  }
  ```

#### Get Attendance
- **URL**: `/api/attendance/{student_id}`
- **Method**: `GET`
- **Response**:
  ```json
  {
    "student_id": 123,
    "attendance": [
      {"date": "2024-10-01", "status": "present"},
      {"date": "2024-10-02", "status": "absent"}
    ]
  }
  ```
## Authentication

All API endpoints (except login) require a valid JSON Web Token (JWT) to be included in the `Authorization` header of the HTTP request. Example:

```bash
Authorization: Bearer your_auth_token

### 7. **Error Handling**
Define the common errors that can occur when using the API and how they are communicated. For instance:

```markdown
## Error Codes

| Error Code | Message                 | Description                                      |
|------------|-------------------------|--------------------------------------------------|
| 401        | Unauthorized             | Invalid or missing authentication token.         |
| 404        | Not Found                | The requested resource does not exist.           |
| 500        | Internal Server Error    | A server error occurred.                         |

## Versioning
Current version: v1. All URLs should start with `/api/v1/`.

