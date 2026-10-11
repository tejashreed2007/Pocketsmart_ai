# Project Documentation

## 1. Project Overview

**Project Name:** PocketSmart AI

PocketSmart AI is an AI-powered web application designed to help users plan expenses and obtain personalized recommendations based on their budgets and preferences.

The application focuses on home interior planning, party planning, and jewelry recommendations. It combines a web-based interface, backend processing, database storage, and AI integration to simplify everyday planning decisions.

## 2. Purpose of the Documentation

This document provides an overview of the project, its architecture, technologies, main features, installation process, and usage instructions.

It is intended for developers, students, project evaluators, and users who want to understand the application.

## 3. Main Features

### 3.1 Home Interior Planning

Helps users explore interior design ideas that match their budget and preferences.

### 3.2 Party Planning

Provides suggestions for organizing parties and allocating expenses according to the user's requirements.

### 3.3 Jewelry Recommendations

Generates jewelry suggestions based on budget and preferences. Outfit-image analysis is available where implemented.

### 3.4 AI-Powered Recommendations

Uses a configured AI service to generate personalized suggestions.

### 3.5 Fallback Recommendations

Provides alternative suggestions when the external AI service is unavailable, where implemented.

### 3.6 User Authentication

Supports user registration and login where the relevant functionality is implemented.

### 3.7 Recommendation History

Allows users to review saved recommendations where history storage is implemented.

## 4. System Requirements

### Hardware Requirements

* Computer or laptop.
* Sufficient RAM and storage for Python and project dependencies.
* Internet connection for dependency installation and external AI requests.

### Software Requirements

* Python.
* A compatible Python package manager.
* FastAPI.
* SQLite.
* SQLAlchemy.
* A modern web browser.
* Git, if the repository is cloned.
* Google Gemini API credentials, if required by the configured AI integration.

Refer to `requirements.txt` and the project's configuration files for the actual dependencies and setup requirements.

## 5. Project Structure

The project may contain the following logical components. Refer to the repository for the exact file and directory names.

```text
PocketSmart_AI/
├── app/
├── static/
├── templates/
├── tests/
├── main.py
├── requirements.txt
├── README.md
└── Project Documentation/
```

The exact structure depends on the source code version. Update this tree if the actual repository uses different directories or entry points.

## 6. Installation and Setup

### Step 1: Obtain the Project

Clone the GitHub repository or download and extract its ZIP archive.

### Step 2: Open the Project Directory

Open a terminal in the extracted project directory.

### Step 3: Create a Virtual Environment

```bash
python -m venv venv
```

Activate it on Linux or macOS:

```bash
source venv/bin/activate
```

On Windows, use:

```powershell
venv\Scripts\activate
```

### Step 4: Install Dependencies

```bash
pip install -r requirements.txt
```

If installation fails, check your Python version, internet connection, and dependency configuration.

### Step 5: Configure Environment Variables

Create the environment configuration file required by the application. Add the AI API key and other settings using the exact variable names expected by the source code.

Never publish API keys, passwords, or other secrets in a public GitHub repository.

### Step 6: Initialize the Database

Follow the database setup procedure defined by the application. Confirm that the database and required tables are created successfully.

### Step 7: Start the Application

Use the correct startup command for the actual backend entry point and framework configuration.

For a standard FastAPI application with a `main.py` file exposing an `app` object, the command may be:

```bash
uvicorn main:app --reload
```

If the application object is defined in another module, adjust the command accordingly.

### Step 8: Open the Application

Open the local address and port shown in the terminal or specified in the project configuration.

## 7. Application Workflow

1. The user opens PocketSmart AI.
2. The user selects the required planning category.
3. The user enters a budget and relevant preferences.
4. The frontend submits the request to the backend.
5. The backend validates the submitted data.
6. The application generates recommendations using the configured AI service or its fallback mechanism.
7. The backend returns the result.
8. The frontend displays the recommendations.
9. Where implemented, the recommendation is saved to the user's history.

## 8. Technology Stack

| Technology        | Purpose                           |
| ----------------- | --------------------------------- |
| HTML              | Web page structure                |
| CSS               | Interface styling                 |
| JavaScript        | Client-side interactions          |
| Jinja2            | Server-rendered templates         |
| Python            | Application programming           |
| FastAPI           | Backend APIs and request handling |
| SQLite            | Relational database               |
| SQLAlchemy        | Database interaction              |
| Google Gemini API | AI-generated recommendations      |
| Pydantic          | Request and data validation       |
| Pytest            | Automated testing                 |
| HTTPX             | HTTP client and API testing       |

## 9. Database Documentation

SQLite is used for persistent data storage.

Depending on the implementation, the database may contain:

* User account records.
* Recommendation requests.
* Generated recommendation results.
* Budget and category information.
* Creation timestamps.

SQLAlchemy provides an interface for database operations. The actual table names, columns, and relationships should be documented according to the project's model definitions.

## 10. API Documentation

FastAPI can provide interactive API documentation when the relevant configuration is enabled.

For a standard FastAPI setup, the documentation is commonly available at:

* `/docs` — Interactive Swagger UI.
* `/redoc` — ReDoc API documentation.

The exact URL depends on the application configuration.

Use these pages to inspect the actual endpoints, request formats, response schemas, and available operations.

## 11. Configuration and Security

* Store API credentials in environment variables.
* Exclude environment files containing secrets from version control.
* Validate incoming requests.
* Use secure password storage if authentication is implemented.
* Apply authorization checks to private records.
* Validate uploaded files if image processing is supported.
* Avoid exposing confidential information in logs or error messages.

## 12. Troubleshooting

### Dependency Installation Failure

Check that the correct Python environment is activated and that the required packages are available.

### AI Recommendations Not Working

Verify the API key, network connectivity, service configuration, and API usage limits.

### Database Errors

Check the database path, initialization process, permissions, and SQLAlchemy configuration.

### Application Does Not Start

Review the terminal output, confirm the configured entry point, and resolve missing dependencies or import errors.

### Recommendation History Is Empty

Confirm that history storage is implemented, database writes are successful, and the correct user account is being used.

## 13. Limitations

* AI-generated recommendations may not always be accurate.
* External AI functionality depends on service availability and configuration.
* Fallback suggestions may be less personalized.
* Product prices and availability require verification from reliable sources.
* Some features depend on the capabilities implemented in the current source code.

## 14. Future Enhancements

Potential improvements include:

* More advanced budget analytics.
* Additional recommendation categories.
* Improved personalization.
* Enhanced visualizations for expense planning.
* Exportable planning reports.
* More comprehensive automated testing.
* Additional security and accessibility improvements.

## 15. Conclusion

PocketSmart AI combines web development, database management, and artificial intelligence to provide a practical budget planning and recommendation platform.

This documentation explains the application's intended features, technology stack, setup process, workflow, and limitations. It serves as a reference for understanding, running, maintaining, and extending the project.
