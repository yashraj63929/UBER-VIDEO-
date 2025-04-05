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
