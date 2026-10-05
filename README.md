# Contacts API

A RESTful backend API for managing personal contacts with user authentication and session management.

The API is built with Node.js, Express, MongoDB and Mongoose. Each authenticated user can create and manage their own private contact list.

## Features

- User registration and login
- Password hashing with bcrypt
- Database-backed access and refresh sessions
- HTTP-only cookies for refresh sessions
- Bearer token authentication
- User-specific contact ownership
- Create, read, update and delete contacts
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
```

Refresh sessions are stored using HTTP-only cookies.

The project uses database-backed sessions rather than JWT authentication.

## Authentication Endpoints

| Method | Endpoint | Description |
| --- | --- | --- |
| POST | `/auth/register` | Register a new user |
| POST | `/auth/login` | Log in and create a session |
| POST | `/auth/refresh` | Refresh the current session |
| POST | `/auth/logout` | Log out and remove the session |

## Contact Endpoints

All contact routes require authentication.

| Method | Endpoint | Description |
| --- | --- | --- |
| GET | `/contacts` | Get the authenticated user's contacts |
| POST | `/contacts` | Create a new contact |
| GET | `/contacts/:contactId` | Get a contact by ID |
| PATCH | `/contacts/:contactId` | Update a contact |
| DELETE | `/contacts/:contactId` | Delete a contact |

## Contact Fields

Contacts support the following fields:

- `name`
- `phoneNumber`
- `email`
- `isFavourite`
- `contactType`

Available contact types:

```text
work
home
personal
```

## Pagination, Sorting and Filtering

The contacts endpoint supports query parameters such as:

```text
page
perPage
sortBy
sortOrder
contactType
isFavourite
```

Example:

```text
GET /contacts?page=1&perPage=10&sortBy=name&sortOrder=asc&contactType=personal
```

## Environment Variables

Create a `.env` file in the project root.

Use `.env.example` as a reference:

```env
PORT=3000
MONGODB_USER=
MONGODB_PASSWORD=
MONGODB_URL=
MONGODB_DB=
```

## Getting Started

Clone the repository:

```bash
git clone https://github.com/ErenaySener/contacts-api.git
```

Install dependencies:

```bash
npm install
```

Create your `.env` file and configure the MongoDB connection.

Start the development server:

```bash
npm run dev
```

Start the production server:

```bash
npm start
```

By default, the API runs on:

```text
http://localhost:3000
```

The root endpoint returns:

```json
{
  "message": "Contacts API is running"
}
```

## Project Structure

```text
src/
├── controllers/
├── db/
│   └── models/
├── middlewares/
├── routers/
├── services/
├── utils/
├── index.js
└── server.js
```

## What This Project Demonstrates

- REST API architecture
- Authentication and session management
- MongoDB data modeling
- Middleware-based request processing
- Input validation
- Protected resources
- Pagination and filtering
- Error handling
- Separation of routes, controllers and services

## Author

**Erenay Sener**

GitHub: [ErenaySener](https://github.com/ErenaySener)
