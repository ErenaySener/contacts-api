# Contacts API

A RESTful backend API for managing personal contacts with user authentication and session management.

The project is built with Node.js, Express, MongoDB, and Mongoose. Each authenticated user can create and manage their own private contact list.

## Features

- User registration and login
- Password hashing with bcrypt
- Access and refresh token based sessions
- HTTP-only cookies for refresh sessions
- Protected routes with Bearer authentication
- Create, read, update, and delete contacts
- User-specific contact ownership
- Pagination
- Sorting
- Filtering by contact type and favourite status
- Request validation with Joi
- MongoDB persistence with Mongoose
- Centralized error handling
- Request logging with Pino

## Tech Stack

- Node.js
- Express
- MongoDB
- Mongoose
- JavaScript
- Joi
- bcrypt
- cookie-parser
- pino-http
- CORS

## Authentication

After a successful login, the API returns an access token.

Protected contact routes require the token in the `Authorization` header:

```text
Authorization: Bearer <accessToken>
