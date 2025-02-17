# FastAPI Posts & Users API

This repository contains a simple RESTful API built with **FastAPI** that allows you to create, read, and delete posts and users. The application uses **SQLAlchemy** for ORM (Object Relational Mapping), **Pydantic** for data validation, and **bcrypt** for password hashing.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Database](#database)
- [License](#license)

## Features

- **Post Management**: Create, retrieve, and delete posts.
- **User Management**: Create and retrieve users with secure password hashing.
- **Dependency Injection**: Utilizes FastAPI's dependency injection for managing database sessions.
- **Modern Python**: Uses type annotations and Pydantic models for clear, self-documenting code.

## Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/Rupesh-Singh-Karki/Blog-Application.git
   cd fastapi-posts-users-api
   ```

2. **Create and activate a virtual environment (optional but recommended):**

   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows use: venv\Scripts\activate
   ```

3. **Install the required packages:**

   ```bash
   pip install fastapi uvicorn sqlalchemy pydantic bcrypt
   ```

   Alternatively, if a `requirements.txt` file is provided:

   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. **Start the FastAPI server:**

   ```bash
   uvicorn main:app --reload
   ```

   - The `--reload` flag makes the server restart automatically on code changes.
   - By default, the server runs on `http://0.0.0.0:8000`.

2. **Access the interactive API documentation:**

   - **Swagger UI:** [http://localhost:8000/docs](http://localhost:8000/docs)
   - **ReDoc:** [http://localhost:8000/redoc](http://localhost:8000/redoc)

## API Endpoints

### Posts

- **Create a Post**
  - **URL:** `/posts/`
  - **Method:** `POST`
  - **Request Body:**
    ```json
    {
      "title": "Post Title",
      "content": "Post content goes here",
      "user_id": 1
    }
    ```
  - **Response:** Returns the created post with a `201 Created` status.

- **Read a Post by ID**
  - **URL:** `/posts/{post_id}`
  - **Method:** `GET`
  - **Response:** Returns the post if found, otherwise a `404 Not Found` error.

- **Delete a Post by ID**
  - **URL:** `/posts/{post_id}`
  - **Method:** `DELETE`
  - **Response:** Returns a success message if deleted, otherwise a `404 Not Found` error.

### Users

- **Create a User**
  - **URL:** `/users/`
  - **Method:** `POST`
  - **Request Body:**
    ```json
    {
      "username": "johndoe",
      "password": "your_plain_text_password"
    }
    ```
  - **Response:** Creates a user with the password hashed using bcrypt and returns a `201 Created` status.

- **Read a User by ID**
  - **URL:** `/users/{user_id}`
  - **Method:** `GET`
  - **Response:** Returns the user if found, otherwise a `404 Not Found` error.

## Database

- The application uses **SQLAlchemy** for interacting with the database.
- Database sessions are managed using FastAPI dependencies.
- Ensure that your `database.py` and `models.py` files are properly configured to connect to your database.
- The tables are automatically created at startup using:
  
  ```python
  models.Base.metadata.create_all(bind=engine)
  ```
---

Feel free to open issues or submit pull requests if you have any suggestions or improvements!

