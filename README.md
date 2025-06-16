# Notes Service API

A robust RESTful API for a note-taking application built with Node.js and Hapi.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/license/mit)
![Node.js version](https://img.shields.io/badge/Node.js-v18.16.0-green)
![Hapi.js](https://img.shields.io/badge/Framework-Hapi.js-orange)
![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-blue)
![ESLint](https://img.shields.io/badge/Linter-ESLint-4B32C3)

## Table of Contents

- [About The Project](#about-the-project)
  - [Key Features](#key-features)
  - [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation & Setup](#installation--setup)
  - [Environment Variables](#environment-variables)
- [API Documentation](#api-documentation)
  - [Users API](#users-api)
  - [Authentications API](#authentications-api)
  - [Notes API](#notes-api)
  - [Collaborations API](#collaborations-api)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## About The Project

This project is a RESTful API for a feature-rich note-taking application. It handles user management, secure JWT-based authentication, and real-time collaboration on notes. The entire backend is built with **Node.js** and the **Hapi** framework, utilizing **PostgreSQL** for reliable data persistence.

### Key Features

- 👤 **User Management**: Seamless user registration and data retrieval.
- 🔐 **Secure Authentication**: JWT-based authentication flow with `access_token` and `refresh_token`.
- 📝 **CRUD for Notes**: Full Create, Read, Update, and Delete operations for notes.
- 🤝 **Note Ownership & Collaboration**: Each note has a designated owner, who can grant collaboration rights to other users.
- 🗄️ **Database Migrations**: Structured database schema management powered by `node-pg-migrate`.

### Tech Stack

This project is built with modern technologies:

| Technology   | Description                                                  |
|--------------|--------------------------------------------------------------|
| **Node.js**  | JavaScript runtime environment for the server.               |
| **Hapi.js**  | A rich framework for building applications and services.     |
| **PostgreSQL**| A powerful, open-source object-relational database system.   |
| **JWT**      | JSON Web Tokens for secure authentication.                   |
| **bcrypt**   | A library for hashing passwords.                             |
| **Joi**      | A library for data validation.                               |
| **ESLint**   | A tool for identifying and reporting on patterns in JavaScript. |

## Getting Started

To get a local copy up and running, follow these simple steps.

### Prerequisites

- Node.js **v18.16.0** or higher.
- A running **PostgreSQL** server.

### Installation & Setup

1. **Clone the repository:**
   ```sh
   git clone <your-repo-url>
   cd <repository-folder>
   ```

2. **Install NPM packages:**
   ```sh
   npm install
   ```

3. **Setup Environment Variables:**
   Create a `.env` file in the root directory. See the example below for the required variables.

4. **Run Database Migrations:**
   Ensure your PostgreSQL server is running and the `.env` file is correctly configured.
   ```sh
   npm run migrate up
   ```

5. **Run the Server:**
   - For development with live-reloading (nodemon):
     ```sh
     npm run start-dev
     ```
   - For production:
     ```sh
     npm run start-prod
     ```

   The server will start on the `HOST` and `PORT` specified in your `.env` file.

### Environment Variables

Create a file named `.env` and populate it with the following keys:

```env
# Server Configuration
HOST=localhost
PORT=5000

# Database Configuration (for node-postgres)
PGHOST=localhost
PGPORT=5432
PGUSER=your_db_user
PGPASSWORD=your_db_password
PGDATABASE=notesapp

# JWT Configuration
ACCESS_TOKEN_KEY=your_super_secret_access_token_key
REFRESH_TOKEN_KEY=your_super_secret_refresh_token_key
ACCESS_TOKEN_AGE=1800
```

## API Documentation

All API endpoints are listed below. Protected routes require an `Authorization: Bearer <token>` header.

### Users API

- **`POST /users`**: Registers a new user.
- **`GET /users/{id}`**: Retrieves a user's public profile by ID.
- **`GET /users?username={query}`**: Searches for users by username.

### Authentications API

- **`POST /authentications`**: Logs a user in and returns access/refresh tokens.
- **`PUT /authentications`**: Refreshes the access token.
- **`DELETE /authentications`**: Logs a user out by invalidating the refresh token.

### Notes API (Authentication Required)

- **`POST /notes`**: Creates a new note.
- **`GET /notes`**: Retrieves all notes for the authenticated user (owned or collaborated on).
- **`GET /notes/{id}`**: Retrieves a specific note by ID.
- **`PUT /notes/{id}`**: Updates a specific note by ID.
- **`DELETE /notes/{id}`**: Deletes a specific note by ID.

### Collaborations API (Authentication Required)

- **`POST /collaborations`**: Adds a collaborator to a note.
- **`DELETE /collaborations`**: Removes a collaborator from a note.

## Contributing

We welcome contributions! If you'd like to help improve the project:

1. **Fork** the repository.
2. Create your **Feature Branch** (`git checkout -b feature/AmazingFeature`).
3. **Commit** your changes (`git commit -m 'feat: Add some AmazingFeature'`).
4. **Push** to the Branch (`git push origin feature/AmazingFeature`).
5. Open a **Pull Request**.

## License

This project is licensed under the [MIT License](https://opensource.org/license/mit). See the `LICENSE` file for more details.

## Contact

**Satria Nur Saputro**

- Email: [satrianursaputro06@gmail.com](mailto:satrianursaputro06@gmail.com)