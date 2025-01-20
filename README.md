# Backend for a Social Media Application

Proposal for the backend development of a social media application.

## 1. Project Overview

**Objective:** To develop a robust and scalable backend API for a social media application, enabling users to create accounts, post content, interact with other users, and manage their profiles.

**Description:** This project focuses on building the server-side logic and database infrastructure. We will use Node.js with the Express.js framework to create RESTful APIs, MongoDB as our database, and JSON Web Tokens (JWT) for secure authentication. Multer will handle file uploads (images).

**Target Audience:** This backend will serve as the foundation for a web or mobile application used by individuals who want to connect with others, share content, and participate in online communities.

## 2. Learning Outcomes

**Skills to be Developed:**

*   RESTful API design and development (Node.js, Express.js)
*   Database management (MongoDB, Mongoose)
*   User authentication and authorization (JWT)
*   File handling and storage (Multer)
*   Error handling and debugging
*   Version control (Git)

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
| Week 10 | Deployment and documentation                   | Deployed backend and complete API documentation                               |

## 5. Technology Stack

**Technologies/Tools:**

*   **Back-End Framework:** Express.js (Node.js)
*   **Database:** MongoDB
*   **Version Control:** GitHub
*   **Deployment Tools:** Heroku (or similar)

**Why these tools?**

*   **Express.js:** Widely used, mature, simplifies API development. Lightweight and performant.
*   **MongoDB:** Flexible NoSQL database, well-suited for social media data.
*   **GitHub:** Industry standard for version control and collaboration.
*   **Heroku:** PaaS for simplified application deployment and hosting.

## 6. API Endpoints

The backend provides the following API endpoints:

**Post Management:**

*   **Upload Image (`POST /upload`):** Requires authentication. Handles single image uploads using Multer. Responds with `{ url: "/uploads/<original_filename>" }`.
*   **Get Latest Tags (`GET /tags`):** Retrieves latest post tags.
*   **Get All Posts (`GET /posts`):** Retrieves all posts.
*   **Get Posts by Tags (`GET /posts/tags`):** Retrieves posts filtered by tags.
*   **Get Single Post (`GET /posts/:id`):** Retrieves a single post by ID.
*   **Create Post (`POST /posts`):** Requires authentication. Validates input. Creates a new post.
*   **Delete Post (`DELETE /posts/:id`):** Requires authentication. Deletes a post by ID.
*   **Update Post (`PATCH /posts/:id`):** Requires authentication. Validates input. Updates a post by ID.

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

*   **Team Members:** \Myrzabek Nurasyl
*   **Instructor Name:** Bekzat Ajan
*   **Submission Date:** \02.01.2025
