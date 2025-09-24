# TodoRails - Spring Boot Task Management Application

A full-stack web application built with Spring Boot for managing personal tasks and todos with user authentication and secure access control.

## 🚀 Quick Start

```bash
# Clone the repository
git clone https://github.com/prudhviraj2005/TodoRails.git

# Navigate to project directory
cd TodoRails

# Run the application
./mvnw spring-boot:run
# or on Windows
mvnw.cmd spring-boot:run

# Access the application
# Open your browser and go to: http://localhost:8080
```

## 📋 Brief Project Overview

TodoRails is a modern task management web application that allows users to create accounts, securely log in, and manage their personal todo lists. The application features a clean, responsive interface with full CRUD operations for task management.

### Key Features:
- 🔐 **User Authentication & Authorization** - Secure login/registration system
- ✅ **Task Management** - Create, read, update, delete tasks
- 📅 **Due Date Tracking** - Set and monitor task deadlines
- 📊 **Dashboard Overview** - View today's tasks and completion statistics
- 🎨 **Responsive UI** - Clean interface with Thymeleaf templates
- 🔒 **Security** - Spring Security integration with password encryption
- 💾 **Data Persistence** - H2 in-memory database for development

---

## 🎯 Interview Summary & Technical Deep Dive

### Project Architecture & Technology Stack

**Backend Technologies:**
- **Spring Boot 3.3.4** - Main framework for rapid application development
- **Spring Security** - Authentication, authorization, and security
- **Spring Data JPA** - Data access layer with ORM capabilities
- **Hibernate** - JPA implementation for database operations
- **H2 Database** - In-memory database for development (easily switchable to MySQL/PostgreSQL)
- **Maven** - Dependency management and build automation
- **Java 21** - Latest LTS version with modern language features

**Frontend Technologies:**
- **Thymeleaf** - Server-side template engine for dynamic HTML
- **HTML5 & CSS3** - Modern web standards
- **JavaScript** - Client-side functionality
- **Bootstrap-styled components** - Responsive design

### 🏗️ Application Architecture

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Frontend      │    │    Backend       │    │    Database     │
│   (Thymeleaf)   │◄──►│  (Spring Boot)   │◄──►│   (H2/MySQL)    │
│                 │    │                  │    │                 │
│ • Dashboard     │    │ • Controllers    │    │ • User Entity   │
│ • Task Forms    │    │ • Services       │    │ • Task Entity   │
│ • Auth Pages    │    │ • Repositories   │    │ • Relationships │
└─────────────────┘    └──────────────────┘    └─────────────────┘
```

### 🔧 Core Components Explanation

#### 1. **Security Layer (Spring Security)**
- **Custom UserDetailsService**: Loads user data for authentication
- **Password Encryption**: BCrypt hashing for secure password storage
- **Session Management**: HTTP session-based authentication
- **CSRF Protection**: Configured to prevent cross-site request forgery
- **Route Protection**: Secured endpoints requiring authentication

```java
@Configuration
public class SecurityConfig {
    // Custom security configuration
    // Form-based authentication
    // Password encoding with BCrypt
}
```

#### 2. **Data Layer (JPA/Hibernate)**
- **User Entity**: Stores user account information
- **Task Entity**: Manages todo items with relationships
- **Repository Pattern**: Spring Data JPA repositories for data access
- **Entity Relationships**: One-to-Many mapping (User → Tasks)

```java
@Entity
public class Task {
    @ManyToOne
    @JoinColumn(name = "user_id")
    private User user;
    // Task properties and methods
}
```

#### 3. **Business Logic Layer (Services)**
- **UserService**: Handles user registration, authentication logic
- **TaskService**: Manages CRUD operations for tasks
- **Validation**: Input validation and business rule enforcement
- **Data Processing**: Filtering tasks by user, due dates, completion status

#### 4. **Presentation Layer (Controllers)**
- **AuthController**: Login, registration, logout endpoints
- **TaskController**: Task CRUD operations
- **PageController**: Dashboard and navigation
- **RESTful Design**: Clear URL structure and HTTP methods

### 🛠️ Key Implementation Highlights

#### User Authentication Flow:
1. User registers → Password encrypted with BCrypt → Stored in database
2. Login attempt → Spring Security validates credentials
3. Successful login → Session created → Access to protected resources
4. Session management → Automatic logout on inactivity

#### Task Management Features:
- **Today's Tasks**: Filter and display tasks due today
- **Task Status**: Mark tasks as completed/pending
- **Due Date Management**: Set and track task deadlines
- **User Isolation**: Each user sees only their own tasks
- **Data Validation**: Server-side validation for all inputs

#### Database Design:
```sql
Users Table:              Tasks Table:
+----+----------+         +----+--------+----------+--------+
| ID | Username |         | ID | Title  | Due Date | User   |
| 1  | john_doe |  <----> | 1  | Task 1 | 2024-01  | john   |
| 2  | jane_doe |         | 2  | Task 2 | 2024-02  | jane   |
+----+----------+         +----+--------+----------+--------+
```

### 🎨 Frontend Implementation

- **Server-Side Rendering**: Thymeleaf templates for dynamic content
- **Responsive Design**: Mobile-friendly interface
- **Form Handling**: Proper form validation and error messaging
- **Navigation**: Intuitive user interface with consistent styling
- **AJAX Integration**: Smooth user interactions without page refreshes

### 🚦 Development Best Practices Implemented

✅ **Clean Code Architecture**: Separation of concerns with layered architecture  
✅ **Security First**: Proper authentication and authorization  
✅ **Database Design**: Normalized schema with proper relationships  
✅ **Error Handling**: Comprehensive exception handling  
✅ **Configuration Management**: Environment-specific configurations  
✅ **Build Automation**: Maven for dependency management  
✅ **Version Control**: Git with meaningful commit messages  

### 🔍 Technical Challenges Solved

1. **Security Integration**: Implemented Spring Security with custom user details
2. **Database Relationships**: Managed One-to-Many relationships between Users and Tasks
3. **Session Management**: Proper user session handling and timeout
4. **Data Validation**: Both client-side and server-side validation
5. **Environment Configuration**: Easy switching between H2 and production databases

### 📈 Scalability Considerations

- **Database**: Easy migration from H2 to PostgreSQL/MySQL for production
- **Caching**: Ready for Redis integration for session management
- **API**: Architecture supports REST API expansion
- **Deployment**: Containerization-ready with Docker
- **Load Balancing**: Stateless design supports horizontal scaling

### 🎯 Interview Talking Points

**When discussing this project:**

1. **"I built a full-stack task management application using Spring Boot..."**
2. **"Implemented secure user authentication with Spring Security and BCrypt..."**
3. **"Used JPA/Hibernate for database operations with proper entity relationships..."**
4. **"Created a responsive frontend using Thymeleaf templates..."**
5. **"Followed MVC architecture with clear separation of concerns..."**
6. **"Implemented proper error handling and data validation..."**
7. **"Used Maven for build automation and dependency management..."**

---

## 🛠️ Technical Specifications

| Component | Technology | Version |
|-----------|------------|---------|
| Framework | Spring Boot | 3.3.4 |
| Java | OpenJDK | 21 |
| Database | H2 (Dev) / MySQL (Prod) | Latest |
| Template Engine | Thymeleaf | Latest |
| Security | Spring Security | Latest |
| Build Tool | Maven | 3.9+ |
| Server | Embedded Tomcat | Latest |

## 📁 Project Structure

```
TodoRails/
├── src/
│   ├── main/
│   │   ├── java/org/todo/todorails/
│   │   │   ├── config/          # Security configuration
│   │   │   ├── controller/      # Web controllers
│   │   │   ├── model/          # Entity classes
│   │   │   ├── repository/     # Data access layer
│   │   │   ├── service/        # Business logic
│   │   │   └── TodoRailsApplication.java
│   │   └── resources/
│   │       ├── static/         # CSS, JS, Images
│   │       ├── templates/      # Thymeleaf templates
│   │       └── application.properties
│   └── test/                   # Unit tests
├── target/                     # Build output
├── pom.xml                     # Maven configuration
└── README.md                   # Project documentation
```

## 🚀 Getting Started - Detailed Setup

### Prerequisites
- Java 21 or higher
- Maven 3.6+ (or use included wrapper)
- Git

### Installation Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/prudhviraj2005/TodoRails.git
   cd TodoRails
   ```

2. **Build the project**
   ```bash
   ./mvnw clean compile
   ```

3. **Run the application**
   ```bash
   ./mvnw spring-boot:run
   ```

4. **Access the application**
   - Open browser to `http://localhost:8080`
   - Register a new account or use demo credentials

### Database Configuration

**Development (H2 - Default):**
```properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.h2.console.enabled=true
```

**Production (MySQL):**
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/todorails
spring.datasource.username=your_username
spring.datasource.password=your_password
```

## 🧪 Testing

Run the test suite:
```bash
./mvnw test
```

## 📝 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Home page |
| GET | `/login` | Login page |
| POST | `/login` | Process login |
| GET | `/register` | Registration page |
| POST | `/register` | Process registration |
| GET | `/dashboard` | User dashboard |
| GET | `/addtask` | Add task form |
| POST | `/addtask` | Create new task |
| POST | `/task/markDone` | Mark task complete |
| POST | `/task/delete` | Delete task |

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Contact

**Prudhviraj Chowhan**
- GitHub: [@prudhviraj2005](https://github.com/prudhviraj2005)
- Email: korraprudhvirajchowhan@gmail.com

---

**⭐ If you found this project helpful, please give it a star!**