# API Documentation

## Endpoint: `/users/register`

### Description

This endpoint is used to register a new user in the system. It validates the input data, hashes the user's password, and creates a new user in the database. Upon successful registration, it returns a JSON Web Token (JWT) and the user details.

### Method

`POST`

### Request Body

The request body should be in JSON format and include the following fields:

| Field                | Type   | Required | Description                                        |
| -------------------- | ------ | -------- | -------------------------------------------------- |
| `fullname.firstname` | String | Yes      | The first name of the user (minimum 3 characters). |
| `fullname.lastname`  | String | No       | The last name of the user (minimum 3 characters).  |
| `email`              | String | Yes      | The email address of the user (must be valid).     |
| `password`           | String | Yes      | The password for the user (minimum 6 characters).  |

### Response

#### Success Response

- **Status Code:** `201 Created`
- **Body:**
  ```json
  {
      "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
      "user": {
          "_id": "64f1c2e5b5d6c2a1b8e4f123",
          "fullname": {
              "firstname": "John",
              "lastname": "Doe"
          },
          "email": "john.doe@example.com"
      }
  }
  ```

## Endpoint: `/users/login`

### Description

This endpoint is used to authenticate an existing user. It validates the input data, checks the user's credentials, and returns a JSON Web Token (JWT) along with the user details upon successful login.

### Method

`POST`

### Request Body

The request body should be in JSON format and include the following fields:

| Field      | Type   | Required | Description                                |
| ---------- | ------ | -------- | ------------------------------------------ |
| `email`    | String | Yes      | The email address of the user (must be valid). |
| `password` | String | Yes      | The password for the user (minimum 6 characters). |

### Response

#### Success Response

- **Status Code:** `200 OK`
- **Body:**
  ```json
  {
      "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
      "user": {
          "_id": "64f1c2e5b5d6c2a1b8e4f123",
          "fullname": {
              "firstname": "John",
              "lastname": "Doe"
          },
          "email": "john.doe@example.com"
      }
  }
  ```

## Endpoint: `/users/profile`

### Description
This endpoint retrieves the profile information of the currently authenticated user.

### Method
`GET`

### Authentication
Requires a valid JWT token in either:
- Cookie named 'token'
- Authorization header using Bearer scheme

### Response

#### Success Response
- **Status Code:** `200 OK`
- **Body:**
  ```json
  {
    "_id": "64f1c2e5b5d6c2a1b8e4f123",
    "fullname": {
      "firstname": "John",
      "lastname": "Doe"
    },
    "email": "john.doe@example.com"
  }
  ```

# Captains API Documentation

## Endpoint: `/captains/register`

### Description
Register a new captain with vehicle details.

### Method
`POST`

### Request Body
```json
{
    "fullname": {
        "firstname": "John", // Required, minimum 3 characters
        "lastname": "Doe"    // Optional, minimum 3 characters if provided
    },
    "email": "john.doe@example.com", // Required, must be valid email format
    "password": "password123", // Required, minimum 6 characters
    "vehicle": {
        "color": "Black",    // Required, minimum 3 characters
        "plate": "ABC123",   // Required, minimum 3 characters
        "capacity": 4,       // Required, minimum 1
        "vehicleType": "car" // Required, must be one of: "car", "motorcycle", "auto"
    }
}
```

### Response
#### Success (201 Created)
```json
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...", // JWT token valid for 24 hours
    "captain": {
        "_id": "64f1c2e5b5d6c2a1b8e4f123",
        "fullname": {
            "firstname": "John",
            "lastname": "Doe"
        },
        "email": "john.doe@example.com",
        "status": "inactive", // Default captain status
        "vehicle": {
            "color": "Black",
            "plate": "ABC123",
            "capacity": 4,
            "vehicleType": "car"
        }
    }
}
```

## Endpoint: `/captains/login`

### Description
Authenticate a captain and get access token.

### Method
`POST`

### Request Body
```json
{
    "email": "john.doe@example.com", // Required, must be valid email
    "password": "password123"        // Required, minimum 6 characters
}
```

### Response
#### Success (200 OK)
```json
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...", // JWT token valid for 24 hours
    "captain": {
        "_id": "64f1c2e5b5d6c2a1b8e4f123",
        "fullname": {
            "firstname": "John",
            "lastname": "Doe"
        },
        "email": "john.doe@example.com",
        "status": "inactive",
        "vehicle": {
            "color": "Black",
            "plate": "ABC123",
            "capacity": 4,
            "vehicleType": "car"
        }
    }
}
```
