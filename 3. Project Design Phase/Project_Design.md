# Project Design Phase

## 1. Introduction

The project design phase defines the overall architecture, modules, database structure, and user interaction flow of PocketSmart AI.

PocketSmart AI is a web-based application that combines budget planning with AI-powered recommendations for home interiors, party planning, and jewelry selection.

## 2. System Architecture

The application follows a layered architecture consisting of the presentation layer, application backend, AI service integration, and database layer.

### 2.1 Presentation Layer

The presentation layer provides the user interface through which users can register, log in, enter their budgets, submit preferences, and view recommendations.

**Technologies:** HTML, CSS, JavaScript, and Jinja2 templates.

### 2.2 Application Layer

The backend receives user requests, validates inputs, processes application logic, communicates with the AI service, and returns responses.

**Technology:** Python with FastAPI.

### 2.3 Artificial Intelligence Layer

The AI integration generates recommendations according to the user's budget and preferences. When the external AI service is unavailable, the application can use fallback recommendations where implemented.

**Technology:** Google Gemini API.

### 2.4 Database Layer

The database stores application information, such as user records and recommendation history, according to the implemented database models.

**Technologies:** SQLite and SQLAlchemy.

## 3. Architecture Diagram

```text
+---------------------------+
|          User             |
+-------------+-------------+
              |
              v
+---------------------------+
|       Web Interface       |
| HTML, CSS, JavaScript     |
|     Jinja2 Templates      |
+-------------+-------------+
              |
              v
+---------------------------+
|       FastAPI Backend     |
| Input Validation          |
| Application Logic         |
| Request Processing        |
+-------+-------------+-----+
        |             |
        v             v
+---------------+  +------------------+
| AI Service    |  | SQLite Database  |
| Gemini API    |  | SQLAlchemy ORM   |
+-------+-------+  +------------------+
        |             |
        +------+------+
               |
               v
+---------------------------+
| Recommendations / Results |
+---------------------------+
```

## 4. Major System Modules

### 4.1 Authentication Module

Handles user registration, login, and access to user-specific features.

### 4.2 Home Interior Planning Module

Collects budget information and design preferences to generate suitable interior recommendations.

### 4.3 Party Planning Module

Processes party requirements and budget information to suggest appropriate planning ideas.

### 4.4 Jewelry Recommendation Module

Generates jewelry suggestions according to budget and preferences. Outfit-image analysis is included where supported by the implementation.

### 4.5 AI Recommendation Module

Connects the backend to the configured AI service and processes generated recommendations.

### 4.6 Fallback Recommendation Module

Provides predefined or locally generated suggestions when the AI service is unavailable, if configured in the application.

### 4.7 History Module

Manages previously generated recommendations and allows users to review saved results where implemented.

## 5. Database Design

The application uses SQLite as its relational database and SQLAlchemy for database operations.

The following are conceptual entities. Their exact names and fields should match the database models in the source code.

### 5.1 User Entity

Stores information required for user accounts.

Possible fields:

* User ID
* Username
* Email
* Password hash or authentication credential reference
* Account creation timestamp

### 5.2 Recommendation Entity

Stores generated recommendation records.

Possible fields:

* Recommendation ID
* User ID
* Recommendation category
* Budget
* User preferences or request details
* Generated recommendation
* Creation timestamp

### 5.3 Relationship

A user may have multiple recommendation records. Each saved recommendation can be associated with its corresponding user through a user identifier.

```text
+------------------+       +----------------------+
|      User        |       |    Recommendation    |
+------------------+       +----------------------+
| user_id (PK)     | 1   * | recommendation_id(PK)|
| username         |------>| user_id (FK)         |
| email            |       | category             |
| password_hash    |       | budget               |
+------------------+       | result               |
                           | created_at           |
                           +----------------------+
```

## 6. Data Flow Design

1. The user opens the application.
2. The user selects a planning or recommendation feature.
3. The user enters a budget and relevant preferences.
4. The frontend sends the request to the backend.
5. The backend validates the submitted data.
6. The backend requests an AI-generated recommendation when the AI service is configured and available.
7. If necessary, the application uses its fallback mechanism.
8. The backend returns the result to the frontend.
9. The application displays the recommendation.
10. Where history storage is implemented, the result is saved for future access.

## 7. User Interface Design

The interface should provide a simple and consistent experience across the application.

### Main Interface Components

* Home page introducing PocketSmart AI.
* Registration and login pages.
* Budget and preference input forms.
* Separate planning interfaces for interior design, parties, and jewelry.
* Recommendation results section.
* Recommendation history page, where implemented.
* Error messages and loading indicators.

### Design Principles

* Clear navigation.
* Readable typography.
* Consistent colors and spacing.
* Responsive layouts for different screen sizes.
* Accessible input labels and understandable error messages.
* Clear presentation of recommendations and budget information.

## 8. API Design

The backend uses FastAPI to define HTTP endpoints. The following table describes the expected endpoint categories; exact paths and HTTP methods must be verified against the implemented application.

| API Category            | Purpose                               |
| ----------------------- | ------------------------------------- |
| Authentication          | Registration and login                |
| Interior planning       | Generate interior recommendations     |
| Party planning          | Generate party suggestions            |
| Jewelry recommendations | Generate jewelry suggestions          |
| History                 | Retrieve saved recommendation records |
| Health check            | Check application availability        |

## 9. Security Design

* Keep external API keys in environment variables.
* Validate user input on the backend.
* Store passwords securely using an appropriate password-hashing method.
* Protect authenticated endpoints.
* Apply authorization checks to user-specific records.
* Avoid exposing sensitive information in error messages or logs.
* Validate uploaded files and restrict accepted file types and sizes.

## 10. Conclusion

The design phase establishes the proposed architecture, system modules, data flow, database relationships, interface principles, and security considerations of PocketSmart AI.

This design provides a foundation for implementing, testing, and documenting the application while allowing the architecture to be adjusted to match the actual source code.
