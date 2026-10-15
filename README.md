# EduPortal LMS

**A full-stack Learning Management System integrating React, Node.js, Express, Oracle Database, and MongoDB.**

EduPortal LMS is a web-based learning management system designed to support academic administration and learning activities through role-based access for students, instructors, and administrators.

The project explores full-stack application architecture, RESTful API development, relational database design, document-oriented data storage, authentication, and authorization.

## Core Modules

The system is organized around the following functional areas:

- **Authentication and Authorization:** JWT-based authentication and role-based access control.
- **User Management:** Student, instructor, and administrator accounts.
- **Course Management:** Course organization and enrollment management.
- **Academic Records:** Grades, attendance, and assignment data.
- **Assessments:** Quiz and question management.
- **Notifications:** Document-based notification storage.
- **Course Content:** Management of course-related learning materials.

These modules describe the project's intended functional scope. Individual features may require additional configuration or integration to operate end-to-end.

## Technology Stack

| Layer | Technology |
|---|---|
| Frontend | React, JavaScript, JSX |
| Backend | Node.js, Express.js |
| Relational Database | Oracle Database |
| Document Database | MongoDB |
| Database Integration | Sequelize, Mongoose |
| Authentication | JSON Web Tokens (JWT) |
| API Architecture | REST |

## System Architecture

EduPortal LMS uses a layered architecture separating the user interface, backend services, and database systems.

```text
              React Frontend
                    |
                REST API
                    |
            Node.js + Express
                    |
          Authentication & RBAC
                    |
             Application Routes
                    |
          +---------+---------+
          |                   |
     Oracle Database       MongoDB
          |                   |
    Users, Courses,       Notifications,
    Enrollments,          Quiz Questions,
    Grades, Attendance    Course Content
```

The backend provides API endpoints and coordinates access to the application's data stores.

## Database Design

### Oracle Database

Oracle is used for structured academic data, including:

- Users
- Courses
- Enrollments
- Grades
- Attendance
- Assignments
- Quizzes

The SQL schema is available in [`docs/schema.sql`](docs/schema.sql).

### MongoDB

MongoDB is used for document-oriented application data, including:

- Notifications
- Quiz questions
- Course content

This hybrid approach demonstrates the use of relational and document databases within a single application architecture.

## Role-Based Access Control

The application defines three user roles:

| Capability | Student | Instructor | Admin |
|---|---|---|---|
| View own courses | Yes | Yes | Yes |
| Browse and enroll | Yes | No | Yes |
| View grades | Yes | No | Yes |
| View attendance | Yes | No | Yes |
| Create assignments | No | Yes | Yes |
| Grade students | No | Yes | Yes |
| Mark attendance | No | Yes | Yes |
| Manage users | No | No | Yes |
| Manage courses | No | Yes | Yes |

These permissions represent the documented access-control design.

## Project Structure

```text
eduportal-lms/
├── backend/
│   ├── config/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── package.json
│   └── server.js
├── frontend/
│   └── src/
│       ├── api.js
│       └── LMSFrontend.jsx
├── docs/
│   └── schema.sql
├── .gitignore
└── README.md
```

## Getting Started

### Prerequisites

- Node.js and npm
- Oracle Database
- MongoDB Community Server
- A JavaScript development environment

### 1. Clone the Repository

```bash
git clone https://github.com/talhasultan014/eduportal-lms.git
cd eduportal-lms
```

### 2. Configure Oracle Database

Create a dedicated application database user with only the permissions required by the schema.

Use the SQL definitions in `docs/schema.sql` to initialize the relational database.

Configure the connection for your local Oracle instance.

### 3. Configure MongoDB

Start MongoDB and configure the application's connection string, for example:

```env
MONGO_URI=mongodb://localhost:27017/lms_db
```

### 4. Configure the Backend

Navigate to the backend directory:

```bash
cd backend
npm install
```

Create a local `.env` file containing the environment variables required by the backend configuration.

Example configuration:

```env
ORACLE_USER=lms_user
ORACLE_PASSWORD=replace_with_local_password
ORACLE_CONNECT_STRING=localhost:1521/XEPDB1

MONGO_URI=mongodb://localhost:27017/lms_db

JWT_SECRET=replace_with_a_long_random_secret
JWT_EXPIRES_IN=7d

PORT=5000
NODE_ENV=development
FRONTEND_URL=http://localhost:3000
```

The exact required variables should be checked against the backend configuration.

Start the backend:

```bash
node server.js
```

### 5. Frontend Integration

The repository includes React frontend source files in `frontend/src`.

A complete standalone frontend build configuration is not currently included. To run the interface, these components must be integrated into a compatible React project with the required dependencies and API configuration.

## Security Considerations

- JWT is used for application authentication.
- Role-based authorization separates student, instructor, and administrator permissions.
- Local environment files are excluded from version control.
- Database credentials and JWT secrets must be configured securely.
- Application database accounts should follow the principle of least privilege.

This is an academic software project and has not been presented as a production-hardened application.

## Project Background

Developed as a Database Management Systems academic project, EduPortal LMS demonstrates practical experience with database modeling, backend API design, authentication, and frontend integration.

## Author

**Muhammad Talha Sultan**

GitHub: [@talhasultan014](https://github.com/talhasultan014)

---

*An academic full-stack development project presented as part of a software engineering portfolio.*