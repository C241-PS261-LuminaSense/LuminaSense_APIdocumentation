# LuminaSense_APIdocumentation

#### Service URL
```
https://lumina-sense-sgithgzkka-et.a.run.app/
```

---

### 1. Register User

#### Endpoint
```
POST /register
```

#### Description
Registers a new user with a unique email and returns a success message upon successful registration.

#### Request Body
```json
{
    "name": "string",
    "email": "string",
    "password": "string",
    "passwordConfirmation": "string"
}
```

#### Response
**Success**
- Status: `201 Created`
- Body:
  ```json
  {
      "message": "Registration successful"
  }
  ```

**Errors**
- Status: `400 Bad Request`
  - Email already in use:
    ```json
    {
        "message": "Email already in use"
    }
    ```
  - Password confirmation does not match:
    ```json
    {
        "message": "Password confirmation does not match"
    }
    ```

- Status: `500 Internal Server Error`
  - General server error:
    ```json
    {
        "message": "Internal Server Error"
    }
    ```

---

### 2. Login User

#### Endpoint
```
POST /login
```

#### Description
Logs in an existing user and returns a JWT token.

#### Request Body
```json
{
    "email": "string",
    "password": "string"
}
```

#### Response
**Success**
- Status: `200 OK`
- Body:
  ```json
  {
      "token": "string"
  }
  ```

**Errors**
- Status: `401 Unauthorized`
  - Invalid email or password:
    ```json
    {
        "message": "Invalid email or password"
    }
    ```

- Status: `404 Not Found`
  - Email not found:
    ```json
    {
        "message": "Email not found"
    }
    ```

- Status: `500 Internal Server Error`
  - General server error:
    ```json
    {
        "message": "Internal Server Error"
    }
    ```

---

### 3. Restricted Access

#### Endpoint
```
GET /restricted
```

#### Description
Access a restricted route that requires a valid JWT token.

#### Request Header
```
Authorization: Bearer <token>
```

#### Response
**Success**
- Status: `200 OK`
- Body:
  ```json
  {
      "text": "Welcome, <user_name>"
  }
  ```

**Errors**
- Status: `401 Unauthorized`
  - Missing or invalid token:
    ```json
    {
        "message": "Unauthorized"
    }
    ```

- Status: `500 Internal Server Error`
  - General server error:
    ```json
    {
        "message": "Internal Server Error"
    }
    ```

---

### Summary

This API allows users to register and log in using a Hapi.js server. The login endpoint provides a JWT token that can be used to access restricted routes. The documentation outlines the necessary endpoints, request formats, and possible responses for each operation. Make sure to replace placeholder values with actual data where necessary.

### Notes
- Ensure the server is running and accessible at the provided base URL.
- Make sure to include the JWT token in the Authorization header when accessing restricted routes.
- Handle the environment variables and Firestore configurations appropriately in your server setup.

