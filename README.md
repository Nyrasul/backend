## Core Technologies & Tools

This backend utilizes the following technologies and tools:

*   **Node.js:** A JavaScript runtime environment for server-side execution.
*   **Express.js:** A Node.js web application framework simplifying API and web application development.
*   **MongoDB:** A NoSQL document database for data storage.
*   **JSON Web Tokens (JWT):** A standard for creating access tokens used for authentication.
*   **Express Validator:** Middleware for validating incoming request data.
*   **BCrypt:** A library for securely hashing passwords.
*   **Multer:** Middleware for handling file uploads.
*   **Insomnia/Postman:** Tools for testing APIs.
*   **MongoDB Compass:** A GUI for managing MongoDB databases.

## Development Steps

The backend development follows these key steps:

### Project Setup

*   Initialize a Node.js project: `npm init -y`
*   Install Express: `npm install express`
*   Install Mongoose (MongoDB ODM): `npm install mongoose`
*   Install necessary packages: `npm install jsonwebtoken express-validator bcrypt multer`

### Project Structure

The project is structured as follows:

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

*   `index.js`: The entry point of the application.
*   `models/`: Contains Mongoose models for data schemas.
*   `routes/`: Houses route definitions for different API endpoints.
*   `middleware/`: Contains middleware functions for tasks like authentication and error handling.
*   `uploads/`: Stores uploaded files (e.g., images).

ES6 modules (`import`/`export`) are used for code organization.

### API Development

The API provides the following functionalities:

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

*   **CRUD Operations for Posts:**

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


*   **Image Uploads:**
    *   Uses Multer to handle file uploads.
    *   Stores uploaded images on the server (in the `uploads` folder).
    *   Returns the URLs of the uploaded images.

### Error Handling

*   Implements centralized error handling using middleware (`handleValidationErrors.js`).
*   Sends appropriate error responses to the client.

### API Testing

*   Use Insomnia or Postman to test API endpoints.
*   ![image](https://github.com/user-attachments/assets/c624a301-a850-440e-afea-727172528f37)


## Key Considerations

*   **Security:** Employs password hashing (BCrypt) and JWT for authentication. Sanitizes and validates all user inputs.
*   **Error Handling:** Implements robust error handling to prevent crashes and provide informative error messages.
*   **Code Structure:** Maintains a clean and organized code structure for maintainabili
