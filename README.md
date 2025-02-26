# **Social Media Application**

## **Project Overview**

This project is a social media application that allows users to create, retrieve, update, and delete posts. It includes features like retrieving posts by tags, managing user authentication, and handling file uploads. The application is built using modern JavaScript (ES6 modules) and follows a modular structure for scalability and maintainability.

---

## **Key Features**

### **1. Retrieve Posts by Tags (`GET /tags`)**  
Retrieves a list of posts filtered by specific tags.  
**Implementation Details**: Likely follows similar logic to other retrieval endpoints.

---

### **2. Get Single Post (`GET /posts/:id`)**  
Retrieves a single post by its unique ID.  
**Implementation**: Handled by the `PostController.getOne` function.

---

### **3. Create Post (`POST /posts`)**  
- Requires authentication (`checkAuth` middleware).  
- Validates the request body using `postCreateValidation` middleware.  
- Handles potential validation errors using `handleValidationErrors` middleware.  
- Creates a new post using the `PostController.create` function.

---

### **4. Delete Post (`DELETE /posts/:id`)**  
- Requires authentication (`checkAuth` middleware).  
- Deletes a post by its ID using the `PostController.remove` function.

---

### **5. Update Post (`PATCH /posts/:id`)**  
- Requires authentication (`checkAuth` middleware).  
- Validates the request body using `postCreateValidation` middleware.  
- Handles potential validation errors using `handleValidationErrors` middleware.  
- Updates a post by its ID using the `PostController.update` function.

---

## **Project Structure**
server/
├── index.js // Main application file
├── models/
│ ├── User.js // User model
│ └── Post.js // Post model
├── controllers/
│ ├── auth.js // Authentication routes
│ └── posts.js // Post routes
├── middleware/
│ ├── checkAuth.js // JWT verification middleware
│ └── handleValidationErrors.js // Validation error handling
├── uploads/ // Folder for uploaded images
└── package.json // Project dependencies and scripts


### **Key Structural Elements**:  
- **`index.js`**: Application entry point.  
- **`models/`**: Mongoose data models for users and posts.  
- **`controllers/`**: API endpoint definitions for authentication and posts.  
- **`middleware/`**: Middleware functions for authentication, validation, and error handling.  
- **`uploads/`**: Folder for storing uploaded files (e.g., images).  
- **ES6 Modules**: Used for modern JavaScript syntax and modularity.

---

## **Challenges and Mitigation**

### **1. Challenge**: Handling File Uploads Efficiently  
**Solution**: Use Multer for file uploads with optimized configuration. For production, consider cloud storage solutions like AWS S3 to handle scalability and reliability.

---

### **2. Challenge**: Ensuring Secure Authentication  
**Solution**: Implement JWT (JSON Web Tokens) for secure authentication, enforce input validation, and use BCrypt for secure password hashing.

---

### **3. Challenge**: Managing Complex Data Relationships in MongoDB  
**Solution**: Design a robust database schema using Mongoose. Leverage Mongoose's query capabilities to handle complex data relationships efficiently.

---

## **Team Members & Instructor**

- **Team Members**: Myrzabek Nurasyl  
- **Instructor**: Bekzat Ajan  

---

## **Submission Date**  
**02.01.2025**
