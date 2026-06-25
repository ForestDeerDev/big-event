# Big Event - 大事件管理系统

一个基于 Spring Boot + Vue 3 的现代化事件/文章管理系统。

## 技术栈

### 后端技术栈

| 技术 | 版本 | 说明 |
|------|------|------|
| Java | 21 | 编程语言 |
| Spring Boot | 3.1.3 | 应用框架 |
| MyBatis | 3.0.0 | ORM 框架 |
| MySQL | 8.0+ | 关系型数据库 |
| Redis | 3.2+ | 缓存数据库 |
| JWT | 4.4.0 | 身份认证 |
| Aliyun OSS | 3.15.1 | 对象存储 |
| PageHelper | 1.4.6 | 分页插件 |

### 前端技术栈

| 技术 | 版本 | 说明 |
|------|------|------|
| Vue | 3.3.4 | 前端框架 |
| Vite | 4.4.11 | 构建工具 |
| Element Plus | 2.4.1 | UI 组件库 |
| Pinia | 2.1.7 | 状态管理 |
| Vue Router | 4.2.5 | 路由管理 |
| Axios | 1.5.1 | HTTP 客户端 |
| Quill | 1.2.0 | 富文本编辑器 |

## 功能模块

### 用户管理
- 用户注册
- 用户登录（JWT 认证）
- 个人信息修改
- 密码重置
- 头像上传

### 文章分类管理
- 分类列表查询
- 添加分类
- 修改分类
- 删除分类

### 文章管理
- 文章列表查询（分页）
- 添加文章
- 修改文章
- 删除文章
- 文章状态管理

### 文件上传
- 支持阿里云 OSS 上传
- 支持本地存储（可选）

## 项目结构

```
big-event/
├── backend/                    # 后端代码
│   ├── src/main/java/com/itheima/
│   │   ├── controller/         # 控制层
│   │   ├── service/            # 服务层
│   │   ├── mapper/             # 数据访问层
│   │   ├── pojo/               # 实体类
│   │   ├── config/             # 配置类
│   │   ├── interceptors/       # 拦截器
│   │   ├── utils/              # 工具类
│   │   └── exception/          # 异常处理
│   └── src/main/resources/
│       ├── mapper/             # MyBatis XML 映射文件
│       └── application.yml     # 应用配置
├── frontend/                   # 前端代码
│   ├── src/
│   │   ├── api/                # API 请求封装
│   │   ├── views/              # 页面组件
│   │   ├── router/             # 路由配置
│   │   ├── stores/             # Pinia 状态管理
│   │   ├── utils/              # 工具函数
│   │   └── assets/             # 静态资源
│   └── package.json            # 前端依赖配置
├── resources/                  # 资源文件
│   ├── Redis-x64-3.2.100/      # Redis Windows 版本
│   ├── 测试用例/               # Postman 测试用例
│   ├── big_event.sql           # 数据库初始化脚本
│   └── AliOSS.pdf              # 阿里云 OSS 配置文档
└── README.md                   # 项目说明文档
```

## 快速开始

### 环境要求

- JDK 21+
- Maven 3.8+
- Node.js 18+
- MySQL 8.0+
- Redis 3.2+

### 后端启动

1. **创建数据库**

```sql
CREATE DATABASE big_event CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

2. **执行 SQL 脚本**

```sql
source resources/big_event.sql
```

3. **配置数据库连接**

复制 `backend/src/main/resources/application-example.yml` 为 `application.yml`，并修改数据库密码：

```yaml
spring:
  datasource:
    username: root
    password: YOUR_PASSWORD_HERE
```

4. **配置阿里云 OSS（可选）**

修改 `backend/src/main/java/com/itheima/utils/AliOssUtil.java` 中的 OSS 配置。

5. **启动后端服务**

```bash
cd backend
mvn spring-boot:run
```

服务启动后访问：http://localhost:8080

### 前端启动

1. **安装依赖**

```bash
cd frontend
npm install
```

2. **启动开发服务器**

```bash
npm run dev
```

前端启动后访问：http://localhost:5173

### 生产构建

```bash
# 后端打包
cd backend
mvn clean package

# 前端构建
cd frontend
npm run build
```

## API 接口

### 用户接口

| 方法 | 路径 | 说明 |
|------|------|------|
| POST | `/api/user/register` | 用户注册 |
| POST | `/api/user/login` | 用户登录 |
| GET | `/api/user/userInfo` | 获取用户信息 |
| PUT | `/api/user/update` | 更新用户信息 |
| PUT | `/api/user/updatePwd` | 修改密码 |
| PATCH | `/api/user/updateAvatar` | 更新头像 |

### 分类接口

| 方法 | 路径 | 说明 |
|------|------|------|
| GET | `/api/category/list` | 获取分类列表 |
| POST | `/api/category` | 添加分类 |
| PUT | `/api/category` | 修改分类 |
| DELETE | `/api/category/:id` | 删除分类 |

### 文章接口

| 方法 | 路径 | 说明 |
|------|------|------|
| GET | `/api/article/list` | 获取文章列表（分页） |
| GET | `/api/article/:id` | 获取文章详情 |
| POST | `/api/article` | 添加文章 |
| PUT | `/api/article` | 修改文章 |
| DELETE | `/api/article/:id` | 删除文章 |

### 文件上传接口

| 方法 | 路径 | 说明 |
|------|------|------|
| POST | `/api/upload` | 上传文件 |

## 目录说明

- `backend/` - Spring Boot 后端应用
- `frontend/` - Vue 3 前端应用
- `resources/` - 项目资源文件（数据库脚本、Redis、测试用例）

## 许可证

MIT License