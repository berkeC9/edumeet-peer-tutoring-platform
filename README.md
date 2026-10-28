# EduMeet

A web platform built with PHP and MySQL that allows students to book 1-on-1 tutoring sessions with peer tutors.

## What it does

- **Students** can browse tutors by subject (Math, Physics, Programming, etc.), view profiles, and submit lesson requests for specific dates and times.
- **Tutors** can manage incoming requests (accept or reject) and view past lessons.
- **Reviews & Ratings:** After a lesson, students can leave a 1-5 star rating and written review.
- **Admin Dashboard:** Admins can view all registered users, see usage stats, and resolve reported accounts.
- **Security:** Passwords are encrypted using PHP `password_hash()` (bcrypt) and all SQL queries use PDO prepared statements.

## Tech Stack

- **Backend:** PHP (Vanilla with PDO)
- **Database:** MySQL
- **Frontend:** HTML, CSS, JavaScript (Vanilla, no external libraries)

## Database Tables

- `users`: Stores students, tutors, and admins with roles and hashed passwords.
- `subjects`: List of available tutoring subjects.
- `requests`: Lesson requests with status (`pending`, `accepted`, `rejected`), ratings, and reviews.
- `reports`: User complaints sent to admins for moderation.

## Setup & Running Locally

### 1. Requirements
- PHP 8.0+
- MySQL (or XAMPP)

### 2. Database Setup
1. Create a database named `tutor_system` in MySQL or phpMyAdmin.
2. Import `schema.sql`:
   ```bash
   mysql -u root -p tutor_system < schema.sql
   ```

### 3. Configure Database Connection
Copy `db.example.php` to `db.php` and set your MySQL username and password (default is `root` with empty password):
```bash
cp db.example.php db.php
```

### 4. Run the Server
You can run it directly with PHP's built-in web server:
```bash
php -S localhost:8000
```
Then visit `http://localhost:8000` in your browser. (Or place the folder in `C:/xampp/htdocs` if you prefer Apache).

## Demo Accounts

The `schema.sql` file comes with pre-seeded accounts so you can test each role immediately:

| Role | Email | Password |
| :--- | :--- | :--- |
| **Admin** | `admin@example.com` | `admin123` |
| **Tutor (Math)** | `mathtutor@example.com` | `mathtutor` |
| **Tutor (Software)** | `softwaretutor@example.com` | `softwaretutor` |
| **Student** | `student1@example.com` | `student1` |

## Project Files

- `index.php` - Landing page with subject search and tutor list
- `login.php` / `register.php` - Authentication and role-based registration
- `home.php` - Main hub (redirects based on role)
- `dashboard.php` - Tutor request management panel
- `make_request.php` - Lesson booking form for students
- `rate_lesson.php` - Rating and review submission
- `admin.php` - Admin control panel and user management
- `schema.sql` - Database tables and sample seed data
