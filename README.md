# Task Manager Web Application

This is a full-stack task management application built with React for the frontend, Node.js/Express for the backend, and Sequelize with SQLite for the database. It allows users to sign up, log in, and manage their tasks with features like adding, viewing, updating, and deleting tasks, as well as filtering and searching.

## Features

*   **User Authentication**: Secure sign-up and login using JWT (JSON Web Tokens) and `bcrypt` for password hashing.
*   **Task Management**:
    *   Create new tasks with a title and status.
    *   View tasks grouped by their status: "To Do", "In Progress", and "Done".
    *   Update task titles and statuses.
    *   Delete tasks.
*   **Filtering and Search**: Filter tasks by status and search by title.
*   **Responsive Design**: Built with Tailwind CSS for a modern and responsive user interface.
*   **Animated UI**: Utilizes `framer-motion` for smooth transitions and animations.

## Tech Stack

**Frontend:**
*   **React.js**: A JavaScript library for building user interfaces.
*   **Vite**: A fast build tool for modern web projects.
*   **React Router DOM**: For declarative routing in React applications.
*   **Axios**: Promise-based HTTP client for making API requests.
*   **Tailwind CSS**: A utility-first CSS framework for rapid UI development.
*   **Framer Motion**: A production-ready motion library for React.
*   **React Hot Toast**: For elegant and accessible notifications.

**Backend:**
*   **Node.js**: JavaScript runtime environment.
*   **Express.js**: A fast, unopinionated, minimalist web framework for Node.js.
*   **Sequelize**: An ORM (Object-Relational Mapper) for Node.js, used to interact with the database.
*   **SQLite**: A self-contained, high-reliability, embedded, full-featured, public-domain, SQL database engine.
*   **JWT (jsonwebtoken)**: For creating and verifying access tokens.
*   **Bcrypt.js**: For hashing passwords securely.
*   **CORS**: Middleware to enable Cross-Origin Resource Sharing.
*   **Dotenv**: Loads environment variables from a `.env` file.

## Installation

To set up and run this project locally, follow these steps:

1.  **Clone the repository (if applicable):**
    ```bash
    # This step is usually for external setup, but in this environment, files are already present.
    # git clone <repository-url>
    # cd task-manager-fullstack
    ```

2.  **Install dependencies:**
    The project uses `concurrently` to run both the frontend and backend simultaneously.
    ```bash
    npm install
    ```

3.  **Environment Variables:**
    Create a `.env` file in the root directory of the project and add the following:
    ```
    NODE_ENV=development
    JWT_SECRET=your-super-secret-jwt-key-here # Replace with a strong, unique secret key
    PORT=5000
    ```

4.  **Run the application:**
    ```bash
    npm run dev
    ```
    This command will start both the backend server (on `http://localhost:5000`) and the frontend development server.

## Usage

1.  **Access the Application**: Once the development server is running, open your web browser and navigate to `http://localhost:5173` (or the port indicated by Vite).
2.  **Sign Up**: Create a new account using the sign-up page.
3.  **Log In**: Use your registered credentials to log in.
4.  **Dashboard**: After logging in, you will be redirected to the dashboard where you can:
    *   Add new tasks.
    *   View your tasks, categorized by "To Do", "In Progress", and "Done".
    *   Edit existing tasks (title and status).
    *   Delete tasks.
    *   Search for tasks by title.
    *   Filter tasks by status.

## API Endpoints

The backend provides the following REST API endpoints:

*   **Authentication:**
    *   `POST /api/auth/signup`: Register a new user.
    *   `POST /api/auth/login`: Log in an existing user and receive a JWT.

*   **Tasks:** (All task endpoints require authentication via JWT in the `Authorization` header)
    *   `GET /api/tasks`: Retrieve all tasks for the authenticated user.
    *   `POST /api/tasks`: Create a new task.
    *   `PUT /api/tasks/:id`: Update an existing task by ID.
    *   `DELETE /api/tasks/:id`: Delete a task by ID.

## Database Schema

The application uses an SQLite database managed by Sequelize, with the following tables:

*   **`users` table:**
    *   `id`: INTEGER (Primary Key, Auto-increment)
    *   `name`: STRING (NOT NULL)
    *   `email`: STRING (NOT NULL, UNIQUE)
    *   `password`: STRING (NOT NULL)
    *   `createdAt`: DATETIME
    *   `updatedAt`: DATETIME

*   **`tasks` table:**
    *   `id`: INTEGER (Primary Key, Auto-increment)
    *   `title`: STRING (NOT NULL)
    *   `status`: ENUM ('To Do', 'In Progress', 'Done') (Default: 'To Do')
    *   `userId`: INTEGER (Foreign Key, references `users.id`, NOT NULL)
    *   `createdAt`: DATETIME
    *   `updatedAt`: DATETIME
