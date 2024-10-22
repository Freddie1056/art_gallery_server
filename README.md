# Art Gallery Server

This is a Flask-based API for an Art Marketplace. The platform allows users to register, log in, and upload artworks. Users can also post reviews for artworks. The app supports functionality for both artists and regular users, offering routes to create, retrieve, update, and delete users, artworks, and reviews.

## Features

- **User Registration and Authentication**:
  - Users can register with their name, email, and password.
  - Passwords are securely hashed using `bcrypt`.
  - Users can log in with valid credentials.
  - Artists are distinguished from regular users by a boolean flag.
  
- **Artwork Management**:
  - Artists can create and manage their artworks.
  - Artworks have fields like title, description, and price, and are linked to their respective artists.
  
- **Review System**:
  - Users can write reviews and rate artworks.
  - Reviews are linked to both users and artworks.

## Technologies

- **Flask**: Web framework.
- **SQLite**: Database system used for data storage.
- **SQLAlchemy**: ORM used to interact with the database.
- **bcrypt**: For password hashing.
- **Flask-Session**: For managing user sessions.

## Installation

To run the project locally, follow these steps:

### 1. Clone the Repository
  ``bash
git clone <repository_url>
cd <repository_name>

### 2. Set Up a Virtual Environment

**On Linux/macOS:**

``bash
python -m venv venv
source venv/bin/activate


**On Windows:**

1. Open PowerShell as an administrator.
2. Run the following command to create a virtual environment: `python -m venv venv`

3. Activate the virtual environment:
   - **On Linux/macOS:** `source venv/bin/activate`
   - **On Windows:** `venv\Scripts\activate.bat`

4. Install required packages: `pip install -r requirements.txt`

### 3. Create a Database

Create a SQLite database named `art_gallery.db` in the project root directory.

### 4. Run the Server

Run the following command to start the Flask server:

1. **On Linux/macOS:** `flask run`
2. **On Windows:** `python -m flask run`

Now you can access the API endpoints at `http://localhost:5000`.

## API Documentation

### User Registration

- **Endpoint:** `/register`
- **Method:** `POST`
- **Request Body:**
  ``json
  {
    "name": "John Doe",
    "email": "john.doe@example.com",
    "password": "password123"
  }
  Response:

json

{
  "message": "User registered successfully"
}

2. ***Login (POST /login)

Request Body:

json

{
  "email": "john@example.com",
  "password": "securepassword"
}

Response:

json

{
  "message": "Login successful",
  "user": {
    "id": 1,
    "name": "John Doe",
    "email": "john@example.com",
    "is_artist": true
}


3. ***Get All Users (GET /users)

Response:

json

[
  {
    "id": 1,
    "name": "John Doe",
    "email": "john@example.com",
    "is_artist": true
  }
]

Artworks
1. ***Create a New Artwork (POST /artworks)

Request Body:

json

{
  "title": "Sunset",
  "description": "A beautiful sunset painting",
  "price": 500,
  "artist_id": 1
}

Response:

json

{
  "message": "Artwork created successfully"
}

2. ***Get All Artworks (GET /artworks)

Response:

json

[
  {
    "id": 1,
    "title": "Sunset",
    "description": "A beautiful sunset painting",
    "price": 500,
    "artist_id": 1
  }
]

3. ***Get Artwork by ID (GET /artworks/<id>)

Response:

json

{
  "id": 1,
  "title": "Sunset",
  "description": "A beautiful sunset painting",
  "price": 500,
  "artist_id": 1
}

##License

This project is licensed under the MIT License.