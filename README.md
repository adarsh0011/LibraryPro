# Library - Full Stack Application

## Overview

This project is a Library Management System implemented as a full-stack application. The application consists of a backend built with Spring Boot and a frontend implemented as a Single Page Application (SPA) using React. The application provides a comprehensive solution for managing library resources, users, and rentals, with authentication and role-based access control.

The backend is divided into two modules: REST and DTO, while the frontend is a separate React application. The system supports CRUD operations for users and resources, rental management, and user authentication. It also includes advanced features such as JWT-based authentication, role-based access control, and secure data transmission. The frontend application was built using **React** framework, **Shadcn UI** for re-built components and **Bootstrap** for styling.

## Key Features

### Backend (Spring Boot)

Among the newly added features are:

- **Authentication:** JWT-based authentication. AuthenticationController with login method added to handle authentication.
- **Authorization:** Role-based access control. BookController, UserController, RentController modified to include @PreAuthorize annotation with role parameter.

### Frontend (React)

- **User Interface**: Intuitive and responsive UI for managing users, books, and rentals.
- **Role-Based Views**: Different views and functionalities based on user roles (Admin, Librarian, Reader).
- **Authentication**: Login, logout, and password change functionality.
- **Form Validation**: Validation for user inputs in forms.
- **Modals and Alerts**: Confirmation modals for critical actions and alerts for user feedback.
- **Routing**: Protected routes based on user roles and authentication status.
- **Axios Integration**: Custom Axios instance for secure API communication with JWT tokens.
- **Context API**: UserContext and AlertContext for managing user state and displaying alerts.

## Project Structure

### Backend (new features)

1. **Controllers**:
   - `AuthenticationController`: Handles login and JWT token generation.
2. **Security**:
   - `SecurityConfig`: Configures security filters and authentication.
   - `JwtProvider`: Generates and validates JWT tokens.
   - `JwtAuthenticationFilter`: Filters incoming requests for JWT tokens.
   - `CustomUserDetails`: Loads user details for authentication.

### Frontend

1. **Components**: Alerts, Forms, Modals, Cards, Layouts.
2. **Pages**: Home, Login, PageNotFound, CreateUser, Books, ActiveRents, etc.
3. **Routing**: Protected routes based on user roles. Example: /books for Librarians and Readers, /create-user for Admins.
4. **Contexts**: UserContext: Manages authenticated user state. AlertContext: Displays alerts and notifications.
5. **API Communication**: Custom Axios instance with JWT token interceptor.

## Authentication, Authorization and Security

### Backend

- **JWT Authentication:**
  - Users log in using their credentials (LoginDTO).
  - A JWT token is generated and returned to the client.
  - The token is included in the Authorization header for subsequent requests.
- **Role-Based Access Control:**
  - Endpoints are protected using @PreAuthorize annotations.
  - Example: Only Admins can create users, while Librarians and Readers can view books.
- **HTTPS**: Ensures secure data transmission.
- **JWT Signatures**: Prevent tampering with tokens.
- **CORS**: Configures allowed origins for frontend-backend communication.

### Frontend

- **Token Storage:**
  - JWT tokens are stored in localStorage.
  - The token is automatically included in API requests using an Axios interceptor.
- **Protected Routes:**
  - Routes are protected based on user roles using RequireAuth components.
  - Unauthorized users cannot access restricted views.

## Setup and Testing the Project

### Prerequisites

- Docker
- Java 21
- Maven
- Node.js and npm.

### Installation

1. Clone this repository.
2. Backend setup:
   - Navigate to the backend directory `cd backend`
   - Set up MongoDB replica set by running services directly from docker-compose using IDE or by executing `docker-compose up -d` command.
   - Create a key.properties file in the src/main/resources directory: `touch src/main/resources/key.properties`
   - Add the following line to the **key.properties** file: `secret.key=your-secret-key-here` (Replace your-secret-key-here with a securely generated key. You can use a Base64-encoded string or generate a random key using a tool like RandomKeygen.)
   - Build the project: `mvn clean install`
   - Run the application: use `mvn spring-boot:run` command from REST directory in your terminal (or run main method from RestApplication class in your IDE).
3. Frontend setup:
   - Navigate to the frontend directory `cd frontend`
   - Install dependencies: `npm install`
   - Start the development server: `npm run dev`

### Testing

Access the application by opening https://localhost:5173 URL in your browser. Log in with different roles (Admin, Librarian, Reader) to test functionalities. Example accounts stored in the database after starting application:

- **Admin**:

```
email: adarsh.admin@gmail.com
password: P@ssw0rd!
```

- **Librarian**:

```
email: adarsh.librarian@gmail.com
password: P@ssw0rd!
```

- **Reader**:

```
email: adarsh.reader@gmail.com
password: P@ssw0rd!
```

You can also register as a reader using register form.

### Screenshots



## Author

### Adarsh
