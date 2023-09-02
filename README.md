### Backend Developer Test

**Objective:**
Build a complex RESTful API using Javascript, Express.js, JWT authentication, PostgreSQL, and Prisma ORM for a sophisticated task management application. the time given to complete this exam is maximum of 7 days.

**Requirements:**

1. **Database Setup:**
   - Set up a PostgreSQL database and use prisma orm.
   - Create the following tables:
     - `users` table with fields:
       - `id` (Primary Key, Serial)
       - `username` (String, unique, required)
       - `email` (String, unique, required)
       - `password` (String)
       - `created_at` (Timestamp)
     - `projects` table with fields:
       - `id` (Primary Key, Serial)
       - `name` (String, required)
       - `description` (Text)
       - `created_at` (Timestamp)
     - `tasks` table with fields:
       - `id` (Primary Key, Serial)
       - `title` (String, required)
       - `description` (Text)
       - `due_date` (Date)
       - `completed` (Boolean, default to `false`)
       - `project_id` (Foreign Key to `projects`)
       - `user_id` (Foreign Key to `users`)
       - `created_at` (Timestamp)

2. **API Endpoints:**
   - Create the following API endpoints with appropriate routes:
     - User Authentication:
       - `POST /api/auth/register` - User registration with the following fields:
         - `username` (String)
         - `email` (String)
         - `password` (String)
       - `POST /api/auth/login` - User login with JWT token generation. Use a JWT secret key for token signing.
     - Project Management:
       - `GET /api/projects` - Fetch all projects for the authenticated user.
       - `POST /api/projects` - Create a new project with the following fields:
         - `name` (String, required)
         - `description` (Text)
       - `GET /api/projects/:projectId` - Fetch a specific project by ID.
       - `PUT /api/projects/:projectId` - Update a specific project by ID with the ability to modify `name` and `description` fields.
       - `DELETE /api/projects/:projectId` - Delete a specific project by ID.
     - Task Management:
       - `GET /api/projects/:projectId/tasks` - Fetch all tasks for a specific project.
       - `POST /api/projects/:projectId/tasks` - Create a new task within a project with the following fields:
         - `title` (String, required)
         - `description` (Text)
         - `due_date` (Date)
       - `GET /api/tasks/:taskId` - Fetch a specific task by ID.
       - `PUT /api/tasks/:taskId` - Update a specific task by ID with the ability to modify `title`, `description`, `due_date`, and `completed` fields.
       - `DELETE /api/tasks/:taskId` - Delete a specific task by ID.

3. **Authentication Middleware:**
   - Protect the `/api/projects`, `/api/projects/:projectId`, `/api/projects/:projectId/tasks`, `/api/projects/:projectId/tasks/:taskId`, and `/api/projects/:projectId/tasks/:taskId` endpoints with JWT authentication. Users must be authenticated to access these endpoints.

4. **Prisma ORM:**
   - Use Prisma to interact with the PostgreSQL database.
   - Create Prisma models for the `users`, `projects`, and `tasks` tables.
   - Use Prisma client for CRUD operations on these tables.

5. **Validation:**
   - Implement validation for user registration, project creation, and task creation:
     - Ensure `username` and `email` are unique and not empty during registration.
     - Ensure `name` is not empty during project creation.
     - Ensure `title` is not empty during task creation.

6. **Testing:**
   - Write comprehensive tests using a testing framework of your choice (e.g., Jest, Mocha, etc.) to test all API endpoints and authentication. Ensure excellent code coverage.

7. **Documentation:**
   - Create a detailed README.md file with clear instructions on how to set up and run the application.
   - Document the API endpoints, their request/response structures, and provide examples( you can use postman and share the public link).


**Additional Requirements:**

8. **User Roles and Authorization:**
   - Implement a role-based access control system with at least two roles: "user" and "admin."
   - Only "admins" should be able to delete projects and tasks. Users can only delete their own tasks and projects.
   - "Admins" should be able to create, read, update, and delete projects and tasks owned by any user.
   - Regular "users" can create, read, update, and delete their own projects and tasks.

9. **User Profile:**
   - Implement an endpoint to retrieve the user's profile information, including their projects and tasks.

**Evaluation Criteria (Continued):**

- Effective implementation of role-based access control.
- Proper handling of user permissions for project and task management.
- Secure handling of user profiles.
- Ability to retrieve and display user-specific data.
- Comprehensive testing of authorization rules.

**Advanced Features (Optional - Bonus Points):**

10. **Task Assignments:**
    - Implement the ability to assign tasks to specific users within a project.
    - Create API endpoints to assign and unassign tasks to/from users.
    - Ensure that only project members can be assigned tasks.

11. **File Uploads:**
    - Allow users to attach files (e.g., images, documents) to tasks.
    - Implement file upload and storage functionality.
    - Create API endpoints to upload, retrieve, and delete task attachments.

12. **Real-time Updates:**
    - Implement real-time updates using WebSocket or a similar technology to notify users when a task is assigned or updated.

13. **Search and Filter:**
    - Implement search and filtering capabilities for projects and tasks, allowing users to find specific items efficiently.

**Evaluation Criteria:**
- Code quality, organization, and readability.
- Proper use of Express.js, JWT authentication, Prisma ORM, and PostgreSQL.
- Correct implementation of API endpoints and validation.
- Passing test cases with excellent code coverage.
- Clear and well-documented README.
- Bonus points will be awarded for implementing advanced features.
- Candidates should explain their thought process, architectural decisions, and trade-offs in the README.
- Evaluate how well the candidate's code is structured for scalability and maintainability.
- Assess the candidate's ability to handle complex business logic and data relationships.

**Submission:**
- Create a public GitHub repository for this project.
- Share the repository URL with the candidate to submit their code.
