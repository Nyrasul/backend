# Social Media Application

Proposal for the development of a social media application.

## 1. Project Overview

**Objective:** To develop a robust and scalable backend API for a social media application, enabling users to create accounts, post content, interact with other users, and manage their profiles.

**Description:** This project focuses on building the server-side logic and database infrastructure. We will use Node.js with the Express.js framework to create RESTful APIs, MongoDB as our database, and JSON Web Tokens (JWT) for secure authentication. Multer will handle file uploads (images).

**Target Audience:** This backend will serve as the foundation for a web or mobile application used by individuals who want to connect with others, share content, and participate in online communities.

## 2. Learning Outcomes

**Skills to be Developed:**

*   RESTful API design and development (Node.js, Express.js)
*   Frontend skills and routing(React)
*   HTTP requests from the browser or Node.js (Axios)
*   Database management (MongoDB, Mongoose)
*   User authentication and authorization (JWT)
*   File handling and storage (Multer)
*   Error handling and debugging
*   Version control (Git)
*   Api request control (Insomnia)

**Alignment with Course Goals:** This project aligns with the course objectives of mastering backend frameworks, designing RESTful APIs, working with databases, implementing secure authentication, and deploying applications.

## 3. Deliverables

**Expected Final Product:** A fully functional backend API with comprehensive documentation (e.g., Swagger/Postman), usage examples, and deployment on a platform like Heroku.

**Key Features:**

*   User registration and authentication
*   User profile management (CRUD)
*   Post management (CRUD)
*   Image uploads for posts
*   Retrieving posts by tags
*   Error handling and validation

## 4. Week-by-Week Plan

| Week    | Tasks and Goals                                 | Expected Outcome                                                              |
| :------ | :---------------------------------------------- | :--------------------------------------------------------------------------- |
| Week 1  | Form project team and finalize project details | Approved project proposal                                                    |
| Week 2  | Set up development environment, install dependencies | Functional development environment (Node.js, MongoDB, packages)             |
| Week 3  | Design database schema (User, Post models)       | Defined Mongoose schemas                                                     |
| Week 4  | Implement user authentication                 | Working authentication endpoints with JWT                                     |
| Week 5  | Develop core API endpoints for posts (CRUD)     | Working CRUD operations for posts                                               |
| Week 6  | Implement image upload functionality             | Functional image upload endpoint                                             |
| Week 7  | Implement tag retrieval for posts                | Functionality to retrieve posts by tags                                      |
| Week 8  | Implement error handling and validation          | Robust error handling and input validation                                    |
| Week 9  | Test API endpoints (Insomnia/Postman)       | Fully tested and debugged API                                                |
| Week 10 | Create visual side of website                  |  Fully tested and debugged frontend                              |
| Week 11 | Deployment and documentation                   | Deployed backend/frontend and complete API documentation       |

## 5. Technology Stack

**Technologies/Tools:**

*   **Back-End Framework:** Express.js (Node.js)
*   **Front-End Framework:** React (Node.js)
*   **Database:** MongoDB
*   **Version Control:** GitHub
*   **Deployment Tools:** Heroku (or similar)

**Why these tools?**

*   **Express.js:** Widely used, mature, simplifies API development. Lightweight and performant.
*   **React:**  Simplicity, low learning curve, lightweight API, flexibility.
*   **MongoDB:** Flexible NoSQL database, well-suited for social media data.
*   **GitHub:** Industry standard for version control and collaboration.
*   **Heroku:** PaaS for simplified application deployment and hosting.

## 6. API Endpoints

The backend provides the following API endpoints:
The API provides the following functionalities:

**User Management:**

*   **Registration (`POST /auth/register`):**
    *   Validates input data using Express Validator (e.g., required fields, email format).
    *   Hashes the password using BCrypt.
    *   Saves the new user to the MongoDB database.
    *   Handles potential errors.

*   **Authentication (Login) (`POST /auth/login`):**
    *   Finds the user in the database by email.
    *   Compares the entered password with the stored hash using BCrypt.
    *   Generates a JWT upon successful authentication.
    *   Sends the JWT to the client.

*   **Profile Information Retrieval (`GET /auth/me`):**
    *   Protected route accessible only to authenticated users.
    *   Uses middleware (`checkAuth.js`) to verify the JWT.
    *   Retrieves user information from the database using the user ID from the token.
      
**Post Management:**

* **Upload Image (`POST /upload`):**
    * Requires authentication (`checkAuth` middleware).
    * Uses Multer middleware (`upload.single('image')`) to handle single image uploads.
    * Upon successful upload, responds with a JSON object containing the URL of the uploaded image: `{ url: "/uploads/<original_filename>" }`.

* **Get Latest Tags (`GET /tags`):**
    * Retrieves a list of the latest tags associated with posts.
    * Implemented in the `PostController.getLastTags` function.

* **Get All Posts (`GET /posts`):**
    * Retrieves a list of all posts.
    * Implemented in the `PostController.getAll` function.

* **Get Posts by Tags (`GET /posts/tags`):**
    * Retrieves a list of posts filtered by tags (implementation details not provided).
    * Likely uses similar logic to `GET /tags`.

* **Get Single Post (`GET /posts/:id`):**
    * Retrieves a single post by its ID.
    * Implemented in the `PostController.getOne` function.

* **Create Post (`POST /posts`):**
    * Requires authentication (`checkAuth` middleware).
    * Validates the request body using `postCreateValidation` middleware.
    * Handles potential validation errors using `handleValidationErrors` middleware.
    * Creates a new post using the `PostController.create` function.

* **Delete Post (`DELETE /posts/:id`):**
    * Requires authentication (`checkAuth` middleware).
    * Deletes a post by its ID using the `PostController.remove` function.

* **Update Post (`PATCH /posts/:id`):**
    * Requires authentication (`checkAuth` middleware).
    * Validates the request body using `postCreateValidation` middleware.
    * Handles potential validation errors using `handleValidationErrors` middleware.
    * Updates a post by its ID using the `PostController.update` function.


## 7. Project Structure

server/
├── index.js             // Main application file
├── models/
│   └── User.js          // User model
│   └── Post.js          // Post model
├── routes/
│   └── auth.js          // Authentication routes
│   └── posts.js         // Post routes
├── middleware/
│   └── checkAuth.js     // JWT verification middleware
│   └── handleValidationErrors.js // Validation error handling
├── uploads/             // Folder for uploaded images
└── package.json


Key structural elements:

*   `index.js`: Application entry point.
*   `models/`: Mongoose data models.
*   `routes/`: API endpoint definitions.
*   `middleware/`: Middleware functions.
*   `uploads/`: Stored uploaded files.

ES6 modules are used.

## 8. Challenges and Mitigation

*   **Challenge:** Difficulty handling file uploads efficiently.
    *   **Solution:** Use Multer configuration options. Consider cloud storage (e.g., AWS S3) for production.
*   **Challenge:** Ensuring secure authentication.
    *   **Solution:** Use JWT, input validation, and secure password hashing (BCrypt).
*   **Challenge:** Managing complex data relationships in MongoDB.
    *   **Solution:** Design the database schema using Mongoose. Utilize Mongoose's query capabilities.

## 9. Team Members & Instructor

*   **Team Members:** Myrzabek Nurasyl
*   **Instructor Name:** Bekzat Ajan
*   **Submission Date:** 02.01.2025
