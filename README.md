
# Flask Login and Registration

A simple Flask web application with user registration, login, session management, and a protected dashboard. User accounts are stored in SQLite using Flask-SQLAlchemy.

## Features

- User registration and login
- Server-side input validation
- Unique email addresses
- Password hashing with Werkzeug
- SQLite database
- Session-based authentication
- Protected dashboard
- Logout functionality

## Requirements

- Python 3
- Flask
- Flask-SQLAlchemy

## How to Run

Open a terminal in the project folder.

Create a virtual environment:

```bash
python3 -m venv venv
```

Activate it on Linux:

```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Run the application:

```bash
python3 app.py
```

Open http://127.0.0.1:5000 in your browser.

The SQLite database is created automatically when the application starts.

## GET vs POST

GET requests retrieve pages and display forms. POST requests submit credentials to the server. POST is appropriate for login and registration because credentials are sent in the request body rather than placed in the URL. HTTPS is still required to protect data in transit.

## Why Client-Side Validation Is Not Security

Client-side validation improves user experience, but it can be bypassed or disabled. A user can send requests directly to the server without using the form. Therefore, the server must independently validate required fields, password length, matching passwords, and unique email addresses.

## Why Password Hashing Is Required

Passwords should never be stored as plain text. This application uses Werkzeug's `generate_password_hash()` to store a password hash and `check_password_hash()` to verify login attempts. Hashing helps protect passwords if the database is exposed.

## What Is a Session?

A session allows the application to remember that a user has logged in across multiple requests. In this application, the user's email is stored in Flask's session. The dashboard checks for that session before allowing access, and logout clears the session.

## Security Notes

- Set a strong, secret `SECRET_KEY` through an environment variable before deployment.
- Use HTTPS in production.
- Do not deploy Flask's development server or debug mode as a production server.
- Keep the SQLite database and virtual environment out of version control.
