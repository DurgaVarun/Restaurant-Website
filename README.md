# Restaurant-Website
# Restaurant Website (Flask)

A simple restaurant web application built with **Flask**, **MySQL**, and **Flask-WTF**.

The app includes:
- User registration with password hashing (`bcrypt`)
- User login with session-based authentication
- Contact form handling
- Restaurant pages for home, menu, about, and welcome

## Project Structure

```text
Restaurant-Website/
├── README.md
└── Website/
    ├── app.py                # Main Flask app and routes
    ├── forms.py              # Flask-WTF form definitions
    ├── static/
    │   ├── style.css
    │   ├── script1.js
    │   ├── menuscript.js
    │   └── restau.jpg
    └── templates/
        ├── home.html
        ├── register.html
        ├── Contact.html
        ├── menu.html
        ├── welcome.html
        └── About us.html
```

## Features

- **Registration** (`/register`)
  - Stores user credentials in MySQL
  - Passwords are hashed before storage using `bcrypt`
- **Login** (`/`)
  - Verifies password hash against the database
  - Sets session variables on successful login
- **Contact Form** (`/Contact.html`)
  - Validates and accepts user input from a contact form
- Static informational pages:
  - `/menu.html`
  - `/welcome.html`
  - `/About us.html`

## Tech Stack

- Python
- Flask
- Flask-WTF / WTForms
- Flask-MySQLdb
- MySQL
- bcrypt

## Prerequisites

- Python 3.10+ (recommended)
- MySQL server running locally
- A MySQL database named `tastybites`

## Database Setup

Create the database and users table:

```sql
CREATE DATABASE tastybites;
USE tastybites;

CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  username VARCHAR(100) NOT NULL,
  email VARCHAR(150) NOT NULL UNIQUE,
  password VARCHAR(255) NOT NULL
);
```

## Installation

1. Clone the repository and enter it:

```bash
git clone <your-repo-url>
cd Restaurant-Website
```

2. (Optional but recommended) create and activate a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate   # On Windows: .venv\Scripts\activate
```

3. Install dependencies:

```bash
pip install flask flask-wtf wtforms flask-mysqldb bcrypt
```

## Configuration

The current app config is defined directly in `Website/app.py`:

- `MYSQL_HOST`
- `MYSQL_USER`
- `MYSQL_PASSWORD`
- `MYSQL_DB`
- `secret_key`

Before running in production, move secrets and DB credentials to environment variables.

## Run the Application

From the project root:

```bash
python Website/app.py
```

By default, Flask runs at:

- `http://127.0.0.1:5000/`

## Notes

- Ensure MySQL is running and credentials match your local setup.
- The app currently runs in debug mode (`debug=True`).
- HTML templates include a filename with spaces (`About us.html`), which works but is not ideal for long-term maintainability.

## Future Improvements

- Use environment variables (`python-dotenv`) for secure config
- Add proper email validation (`wtforms.validators.Email`)
- Introduce migrations (Flask-Migrate/Alembic)
- Add unit and integration tests
- Improve route naming consistency (avoid spaces in URLs and template names)

---

If you'd like, I can also provide a `requirements.txt` and a `.env.example` for this project.
