# Artworks & Reviews API

## Overview

This project is a Flask-based API for managing a simple art gallery system, allowing users to:

- Register as artists or reviewers
- Upload artworks for sale
- Leave reviews and ratings on various artworks

The API utilizes Flask for routing, SQLAlchemy for database interaction, and bcrypt for securely hashing passwords.

## 📋 Table of Contents

- [Technologies](#technologies)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Running the App](#running-the-app)
- [API Endpoints](#api-endpoints)
  - [User Registration](#user-registration)
  - [Login](#login)
  - [Artworks](#artworks)
  - [Reviews](#reviews)
- [Database Models](#database-models)
- [Example curl Requests](#example-curl-requests)
- [Troubleshooting](#troubleshooting)
- [License](#license)

## 🛠 Technologies

- **Python**: Core programming language
- **Flask**: Web framework for routing and handling HTTP requests
- **Flask-SQLAlchemy**: ORM for database interaction
- **SQLite**: Lightweight database for storing users, artworks, and reviews
- **bcrypt**: For securely hashing passwords
- **SQLAlchemy Serializer**: For converting SQLAlchemy models to JSON

## 🗂 Project Structure

    ``plaintext
.
├── app.py                  # Main Flask application
├── database.db             # SQLite database (auto-generated)
├── models.py               # SQLAlchemy models for User, Artwork, and Review
├── requirements.txt        # Project dependencies
└── README.md               # Project documentation

## ⚙️ Installation

   ### 1. Clone the repository:
git clone https://github.com/your-repo/flask-artwork-reviews-api.git
cd flask-artwork-reviews-api

   ### 2. virtual environment:
   python -m venv venv
   source venv/bin/activate

   ### 3. Install dependencies:
   pip install -r requirements.txt

   ### 4. database setup:
   flask shell
   from app import db
   db.create_all()
   exit()

   ### 5. Create a `.env` file:
   touch.env

   ### 6. Configure environment variables:
   Add the following environment variables to the `.env` file:

   ### 4. Configure environment variables:
   Create a `.env` file in the root directory and add the following environment variables:
   
   ### 5. Run the app:
   flask run
   Server will start at http://localhost:5000

## 📚 API Endpoints
### User Registration

- **URL**: `/api/register`
- **Method**: POST
- **Request Body**: JSON object with `username`, `email`, and `password` fields
- **Response Body**: JSON object with `message` field indicating success or failure 
### Login

- **URL**: `/api/login`
- **Method**: POST
- **Request Body**: JSON object with `email` and `password` fields
- **Response Body**: JSON object with `access_token` field containing a JWT token if login is successful
### Artworks

- **URL**: `/api/artworks`
- **Method**: GET
- **Response Body**: JSON array of artworks, each with `id`, `title`, `description`, `price`, `created_at`, and `author_id` fields
- **URL**: `/api/artworks/<id>`
- **Method**: GET
- **Response Body**: JSON object with the artwork details, including `id`, `title`, `description`, `price`, `created_at`, and `author_id` fields
### Reviews

- **URL**: `/api/artworks/<id>/reviews`
- **Method**: POST
- **Request Body**: JSON object with `rating` and `comment` fields
- **Response Body**: JSON object with `message` field indicating success or failure
- **URL**: `/api/artworks/<id>/reviews/<review_id>`
- **Method**: GET
- **Response Body**: JSON object with the review details, including `id`, `rating`, `comment`, `created_at`, and `author_id` fields
- **URL**: `/api/artworks/<id>/reviews/<review_id>`
- **Method**: PUT
- **Request Body**: JSON object with `rating` and/or `comment` fields
- **Response Body**: JSON object with `message` field indicating success or failure
- **URL**: `/api/artworks/<id>/reviews/<review_id>`
- **Method**: DELETE
- **Response Body**: JSON object with `message` field indicating success or failure

## Database Models

- `User` model: `id`, `username`, `email`, `password_hash`
- `Artwork` model: `id`, `title`, `description`, `price`, `created_at`, `author_id` (foreign key referencing `User.id`)
- `Review` model: `id`, `rating`, `comment`, `created_at`, `author_id` (foreign key referencing `User.id`), `artwork_id`
## Example curl Requests
### User Registration
## Troubleshooting
- If you encounter a `401 Unauthorized` error, make sure you are sending the correct `Authorization` header in your request. The header should contain the value `Bearer <access_token>`.
## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

---
