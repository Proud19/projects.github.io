# Photo Sharing Web Application

## Overview
This project is a full-stack web application that allows users to share photos, leave comments, and manage user sessions. Initially developed as a simple photo display app, it was extended to include user authentication, session management, commenting, and photo uploading. The application follows a Model-View-Controller (MVC) architecture and is built using Node.js, Express, MongoDB, and React.
[Project Demo](https://www.youtube.com/watch?v=5NXo13-klLA&ab_channel=pm)

## Features and Achievements
- **User Authentication & Session Management**
  - Users can log in and log out securely.
  - Sessions are maintained using `express-session` middleware.
  - Users are redirected to the login page if not authenticated.
  - Sessions persist across page reloads (extra credit feature).

- **Photo Uploading**
  - Users can upload new photos.
  - Uploaded photos are stored on the server and indexed in MongoDB.
  - File uploads are handled using `multer` middleware.

- **Commenting System**
  - Users can add comments to photos.
  - Comments are associated with the user who posted them and include timestamps.
  - Comments update in real-time without requiring a page refresh.

- **User Registration**
  - Users can create accounts by providing a login name, password, and other details.
  - Passwords are stored securely using SHA-1 hashing and salting for security.
  - Registration includes input validation to prevent errors.

- **Security Enhancements**
  - Passwords are hashed and salted using `crypto`.
  - User sessions are protected with proper authentication middleware.
  - Unauthorized API access returns HTTP 401 (Unauthorized).

- **Testing and Validation**
  - Mocha tests ensure API endpoints function correctly.
  - Automated test coverage includes session management, login/logout, and comments.
  
## Technologies Used
### Frontend:
- **React.js**: For building the interactive user interface.
- **Axios**: For making API requests to the backend.

### Backend:
- **Node.js & Express.js**: For handling API requests and routing.
- **MongoDB & Mongoose**: For database management.
- **Express Middleware**:
  - `express-session`: Manages user sessions.
  - `body-parser`: Parses incoming JSON requests.
  - `multer`: Handles file uploads.
  
### Security:
- **Crypto (SHA-1 & Salted Hashing)**: Enhances password security.
- **Session-based Authentication**: Prevents unauthorized access.

### Testing & Development Tools:
- **Mocha & Chai**: For backend testing.
- **Nodemon**: For automatic server restarts during development.
- **ESLint**: For maintaining clean and readable JavaScript code.


## API Endpoints
### Authentication
- `POST /admin/login` – Logs in a user.
- `POST /admin/logout` – Logs out a user.
- `POST /user` – Registers a new user.

### Photos
- `GET /photos/:user_id` – Fetches photos of a specific user.
- `POST /photos/new` – Uploads a new photo.

### Comments
- `POST /commentsOfPhoto/:photo_id` – Adds a comment to a photo.




## Possible Future Enhancements
- Implement role-based access control (RBAC) for enhanced security.
- Add support for image captions and likes.
- Improve UI styling and add dark mode.


---
Developed for Stanford University's [CS142 Course](https://web.stanford.edu/class/cs142/)
