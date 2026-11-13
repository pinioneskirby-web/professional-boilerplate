# Professional Node.js TypeScript MySQL Boilerplate

## Project Description

A professional backend boilerplate built with Node.js, TypeScript, Express, and MySQL. It provides a structured foundation for developing REST APIs with centralized error handling, request validation, logging, security middleware, and database integration.

## Features

- Node.js and TypeScript
- Express REST API
- MySQL database integration using TypeORM
- Centralized error handling
- Request validation using Joi
- Structured logging using Winston
- Security middleware using Helmet and CORS
- API rate limiting
- User CRUD operations
- Password hashing using bcrypt
- Health check endpoint
- Pagination support
- Graceful server shutdown

## Technologies Used

- Node.js
- TypeScript
- Express.js
- MySQL
- TypeORM
- Joi
- Winston
- bcrypt
- Helmet

## Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/professional-boilerplate.git
cd professional-boilerplate
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Create a `.env` file in the project root directory.

```env
NODE_ENV=development
PORT=3000
DB_HOST=localhost
DB_PORT=3306
DB_USERNAME=root
DB_PASSWORD=
DB_DATABASE=boilerplate_db
FRONTEND_URL=http://localhost:4200
```

Update the database credentials according to your MySQL configuration.

### 4. Create the database

Open MySQL and execute:

```sql
CREATE DATABASE boilerplate_db;
```

### 5. Run the application

```bash
npm run dev
```

The server will run at:

`http://localhost:3000`

## Environment Variables

| Variable | Description |
|---|---|
| NODE_ENV | Application environment |
| PORT | Server port |
| DB_HOST | MySQL host |
| DB_PORT | MySQL port |
| DB_USERNAME | MySQL username |
| DB_PASSWORD | MySQL password |
| DB_DATABASE | Database name |
| FRONTEND_URL | Allowed frontend URL |

## API Endpoints

Base URL: `http://localhost:3000`

| Method | Endpoint | Description |
|---|---|---|
| GET | `/health` | Check server and database status |
| GET | `/api/users` | Get all users |
| GET | `/api/users/:id` | Get user by ID |
| POST | `/api/users` | Create a user |
| PUT | `/api/users/:id` | Update a user |
| DELETE | `/api/users/:id` | Delete a user |

## Running Migrations

Generate a migration:

```bash
npm run migration:generate -- src/migrations/InitialSchema
```

Run migrations:

```bash
npm run migration:run
```

Revert the last migration:

```bash
npm run migration:revert
```

**Note:** Migrations must be generated before they can be executed. In this project, automatic migration execution is configured for production mode.

## Running Seeders

Run the seed command:

```bash
npm run seed
```

Note: The seeder script requires `src/seeds/runSeeds.ts` to be created and implemented.

## Running the Build

```bash
npm run build
```

## Reflection

**1. What did you learn from this activity?**

I learned how to build a structured backend application using Node.js, TypeScript, Express, and MySQL. I also learned how to implement CRUD operations, validation, error handling, logging, and security middleware.

**2. What challenges did you encounter?**

One of the challenges I encountered was fixing errors related to TypeScript, database configuration, and middleware compatibility. I learned to troubleshoot these problems by checking the error messages and correcting the code.

**3. How will you apply what you learned?**

I can apply what I learned when developing future backend projects and APIs. This activity helped me understand how to organize a project and build a more reliable and maintainable application.

---

## Author

**Your Name**

Bachelor of Science in Information Technology