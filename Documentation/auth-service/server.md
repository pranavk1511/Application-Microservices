# README for Flask JWT Authentication

This README provides an overview and usage guide for a simple Flask application that implements JSON Web Token (JWT) authentication.

## Overview

This Flask application includes two main routes for user authentication:

1. **/login**: Handles user login with Basic Authentication and issues a JWT upon successful authentication.
2. **/validate**: Validates JWT passed in the Authorization header.

## Setup

1. Install the required packages: Flask, psycopg2-binary, PyJWT.
```bash
   pip install Flask psycopg2-binary PyJWT
```
2. Set up a PostgreSQL database and configure the environment variables:
   - `DATABASE_HOST`: PostgreSQL host address.
   - `DATABASE_NAME`: Name of the database.
   - `DATABASE_USER`: Database user.
   - `DATABASE_PASSWORD`: Database password.
   - `AUTH_TABLE`: Name of the table containing user authentication information.
   - `JWT_SECRET`: Secret key for JWT encoding.

3. Run the Flask application.

## Usage

### 1. User Login (/login)

Send a POST request to `/login` with Basic Authentication credentials.

Example using `curl`:
```bash
curl -X POST -u username:password http://localhost:5000/login
```

Upon successful authentication, the server responds with a JWT.

### 2. Validate JWT (/validate)

Send a POST request to `/validate` with the JWT included in the Authorization header.

Example using `curl`:
```bash
curl -X POST -H "Authorization: Bearer your_jwt_here" http://localhost:5000/validate
```

The server responds with the decoded JWT payload if the token is valid.

## JWT Payload Structure

The JWT payload includes the following information:

- `username`: User's username.
- `exp`: Token expiration time.
- `iat`: Token issuance time.
- `admin`: Authorization flag.

## Important Notes

- Ensure that the PostgreSQL database is set up with the required authentication table.
- Securely manage the `JWT_SECRET` as it is crucial for token encoding and decoding.

Feel free to customize the code according to your specific requirements.
