markdown# 📝 BlogApp

A full-stack blog platform where users can create, read, update, and delete blog posts, like posts, and leave comments.

---

## 🚀 Tech Stack

### Frontend
- React (Vite)
- React Router DOM
- Axios
- Context API

### Backend
- Java Spring Boot
- Spring Security + JWT Authentication
- Spring Data JPA
- MySQL

---

## ✨ Features

- 🔐 JWT-based login & registration
- 📝 Create, edit, and delete your own blog posts
- 🗂️ Filter posts by category
- ❤️ Like / unlike posts
- 💬 Comment on posts
- 📄 Pagination on home feed
- 🔒 Protected routes (only logged-in users can write/edit/delete)

---

## 🗂️ Project Structure
'''
root/
├── frontend/                  # React app (Vite)
│   ├── src/
│   │   ├── api/               # Axios instance & API calls
│   │   ├── components/        # Reusable UI components
│   │   ├── context/           # Auth context
│   │   ├── pages/             # All page components
│   │   └── main.jsx
│
├── backend/                   # Spring Boot app
│   └── src/main/java/com/example/LoanApp/
│       ├── Config/            # Security & CORS config
│       ├── Controller/        # REST controllers
│       ├── Dto/               # Request/Response DTOs
│       ├── Entity/            # JPA entities
│       ├── Repository/        # Spring Data repositories
│       ├── Security/          # JWT filter & user details
│       └── Service/           # Business logic

'''

## ⚙️ Setup & Installation

### Prerequisites
- Node.js >= 18
- Java >= 17
- MySQL

---

### Backend Setup

1. Clone the repository
```bash
   git clone https://github.com/your-username/blogapp.git
   cd blogapp/backend
```

2. Configure your database in `application.properties`
```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/blogapp
   spring.datasource.username=your_mysql_username
   spring.datasource.password=your_mysql_password
   spring.jpa.hibernate.ddl-auto=update
   jwt.secret=your_jwt_secret_key
```

3. Run the backend
```bash
   ./mvnw spring-boot:run
```
   Server runs on `http://localhost:8080`

---

### Frontend Setup

1. Navigate to the frontend folder
```bash
   cd blogapp/frontend
```

2. Install dependencies
```bash
   npm install
```

3. Start the dev server
```bash
   npm run dev
```
   App runs on `http://localhost:8081`

---

## 🔌 API Endpoints

### Auth
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/auth/register` | Register new user |
| POST | `/auth/login` | Login & get JWT token |
| POST | `/refresh` | Refresh JWT token |

### Posts
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/posts/getAll` | Get all posts |
| GET | `/api/posts/{authorId}` | Get posts by author |
| POST | `/api/posts/create` | Create a new post |
| PUT | `/api/posts/update/{postId}` | Update a post |
| DELETE | `/api/posts/delete/{postId}` | Delete a post |

### Comments
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/comments/post/{postId}` | Get comments for a post |
| POST | `/api/comments/post` | Add a comment |
| PUT | `/api/comments/update/{id}` | Update a comment |
| DELETE | `/api/comments/delete/{id}` | Delete a comment |

### Likes
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/likes/toggle` | Toggle like on a post |
| GET | `/api/likes/status` | Get like status & count |
| GET | `/api/likes/count` | Get total likes for a post |

---

## 🔐 Authentication

All protected endpoints require a Bearer token in the request header:
Authorization: Bearer <your_jwt_token>

The token is stored in `localStorage` after login and automatically attached to every request via the Axios interceptor.
