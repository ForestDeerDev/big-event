# Big Event - Event Management System

English | [简体中文](README.md)

A modern event/article management system based on Spring Boot + Vue 3.

## Tech Stack

### Backend Tech Stack

| Technology | Version | Description |
|------------|---------|-------------|
| Java | 21 | Programming Language |
| Spring Boot | 3.1.3 | Application Framework |
| MyBatis | 3.0.0 | ORM Framework |
| MySQL | 8.0+ | Relational Database |
| Redis | 3.2+ | Cache Database |
| JWT | 4.4.0 | Authentication |
| Aliyun OSS | 3.15.1 | Object Storage |
| PageHelper | 1.4.6 | Pagination Plugin |

### Frontend Tech Stack

| Technology | Version | Description |
|------------|---------|-------------|
| Vue | 3.3.4 | Frontend Framework |
| Vite | 4.4.11 | Build Tool |
| Element Plus | 2.4.1 | UI Component Library |
| Pinia | 2.1.7 | State Management |
| Vue Router | 4.2.5 | Routing Management |
| Axios | 1.5.1 | HTTP Client |
| Quill | 1.2.0 | Rich Text Editor |

## Features

### User Management
- User registration
- User login (JWT authentication)
- Profile modification
- Password reset
- Avatar upload

### Article Category Management
- Category list query
- Add category
- Modify category
- Delete category

### Article Management
- Article list query (pagination)
- Add article
- Modify article
- Delete article
- Article status management

### File Upload
- Support Aliyun OSS upload
- Support local storage (optional)

## Project Structure

```
big-event/
├── backend/                    # Backend code
│   ├── src/main/java/com/itheima/
│   │   ├── controller/         # Controller layer
│   │   ├── service/            # Service layer
│   │   ├── mapper/             # Data access layer
│   │   ├── pojo/               # Entity classes
│   │   ├── config/             # Configuration classes
│   │   ├── interceptors/       # Interceptors
│   │   ├── utils/              # Utility classes
│   │   └── exception/          # Exception handling
│   └── src/main/resources/
│       ├── mapper/             # MyBatis XML mapping files
│       └── application.yml     # Application configuration
├── frontend/                   # Frontend code
│   ├── src/
│   │   ├── api/                # API request encapsulation
│   │   ├── views/              # Page components
│   │   ├── router/             # Routing configuration
│   │   ├── stores/             # Pinia state management
│   │   ├── utils/              # Utility functions
│   │   └── assets/             # Static resources
│   └── package.json            # Frontend dependency configuration
├── resources/                  # Resource files
│   ├── Redis-x64-3.2.100/      # Redis Windows version
│   ├── 测试用例/               # Postman test cases
│   ├── big_event.sql           # Database initialization script
│   └── AliOSS.pdf              # Aliyun OSS configuration documentation
└── README.md                   # Project documentation
```

## Quick Start

### Prerequisites

- JDK 21+
- Maven 3.8+
- Node.js 18+
- MySQL 8.0+
- Redis 3.2+

### Backend Setup

1. **Create Database**

```sql
CREATE DATABASE big_event CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

2. **Execute SQL Script**

```sql
source resources/big_event.sql
```

3. **Configure Database Connection**

Copy `backend/src/main/resources/application-example.yml` to `application.yml` and modify the database password:

```yaml
spring:
  datasource:
    username: root
    password: YOUR_PASSWORD_HERE
```

4. **Configure Aliyun OSS (Optional)**

Modify the OSS configuration in `backend/src/main/java/com/itheima/utils/AliOssUtil.java`.

5. **Start Backend Service**

```bash
cd backend
mvn spring-boot:run
```

After the service starts, visit: http://localhost:8080

### Frontend Setup

1. **Install Dependencies**

```bash
cd frontend
npm install
```

2. **Start Development Server**

```bash
npm run dev
```

After the frontend starts, visit: http://localhost:5173

### Production Build

```bash
# Backend packaging
cd backend
mvn clean package

# Frontend build
cd frontend
npm run build
```

## API Endpoints

### User Endpoints

| Method | Path | Description |
|--------|------|-------------|
| POST | `/api/user/register` | User registration |
| POST | `/api/user/login` | User login |
| GET | `/api/user/userInfo` | Get user information |
| PUT | `/api/user/update` | Update user information |
| PUT | `/api/user/updatePwd` | Change password |
| PATCH | `/api/user/updateAvatar` | Update avatar |

### Category Endpoints

| Method | Path | Description |
|--------|------|-------------|
| GET | `/api/category/list` | Get category list |
| POST | `/api/category` | Add category |
| PUT | `/api/category` | Modify category |
| DELETE | `/api/category/:id` | Delete category |

### Article Endpoints

| Method | Path | Description |
|--------|------|-------------|
| GET | `/api/article/list` | Get article list (pagination) |
| GET | `/api/article/:id` | Get article details |
| POST | `/api/article` | Add article |
| PUT | `/api/article` | Modify article |
| DELETE | `/api/article/:id` | Delete article |

### File Upload Endpoints

| Method | Path | Description |
|--------|------|-------------|
| POST | `/api/upload` | Upload file |

## Directory Description

- `backend/` - Spring Boot backend application
- `frontend/` - Vue 3 frontend application
- `resources/` - Project resource files (database scripts, Redis, test cases)

## License

MIT License
