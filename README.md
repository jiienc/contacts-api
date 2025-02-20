# Contact Manager Backend Application

This is a backend application built using Express and MongoDB. 
It serves as a contact manager where users can register, authenticate, and perform CRUD (Create, Read, Update, Delete) operations on their contacts. 
The project demonstrates JWT authentication, MongoDB Atlas integration, and Express routing.

## Features

- **User Authentication**: Register, login, and get user details using JWT.
- **CRUD Operations on Contacts**: Create, read, update, and delete contacts.
- **MongoDB Atlas Integration**: Cloud-based database storage.
- **Protected Routes**: Users can only access and modify their own contacts.
- **Password Hashing**: Uses bcrypt for secure password storage.
- **Token-based Authentication**: Uses JWT for secure API access.

## Technologies Used

- **Node.js** - JavaScript runtime for backend development.
- **Express.js** - Web framework for handling routes and requests.
- **MongoDB** - NoSQL database for storing contacts and user information.
- **Mongoose** - ODM library for MongoDB.
- **JWT (JSON Web Token)** - Authentication mechanism.
- **bcrypt** - Password hashing for security.
- **dotenv** - Environment variable management.

## Prerequisites

Ensure you have the following installed:

- [Node.js](https://nodejs.org/) (v14 or higher)
- [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) account
- [Postman](https://www.postman.com/) or any API testing tool

## Installation and Setup

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/jiienc/contacts-api.git
   cd contacts-api
   ```
2. **Install Dependencies**:
   ```bash
   npm install
   ```
3. **Set Up Environment Variables**: Create a `.env` file in the root directory and add the following variables:
   ```env
   PORT=5000
   MONGO_URI=your_mongodb_atlas_connection_string
   ACCESS_TOKEN_SECRET=your_jwt_secret_key
   ```
4. **Run the Application**:
   ```bash
   npm run dev
   ```
   The server will start running on `http://localhost:5001`.

## API Endpoints

### Authentication

#### Register User

**POST** `/api/users/register`

**Request Body:**
```json
{
  "username": "JohnDoe",
  "email": "johndoe@example.com",
  "password": "securepassword"
}
```

**Response:**
```json
{
  "_id": "user_id",
  "email": "johndoe@example.com"
}
```

#### Login User

**POST** `/api/users/login`

**Request Body:**
```json
{
  "email": "johndoe@example.com",
  "password": "securepassword"
}
```

**Response:**
```json
{
  "accessToken": "your_jwt_token"
}
```

#### Get Current User

**GET** `/api/users/current`

**Headers:**
```
Authorization: Bearer <your_jwt_token>
```

**Response:**
```json
{
  "username": "JohnDoe",
  "email": "johndoe@example.com",
  "id": "user_id"
}
```

### Contacts (Protected Routes)

#### Get All Contacts

**GET** `/api/contacts`

**Headers:**
```
Authorization: Bearer <your_jwt_token>
```

**Response:**
```json
[
  {
    "_id": "contact_id",
    "name": "Alice",
    "email": "alice@example.com",
    "phone": "123456789",
    "user_id": "user_id"
  }
]
```

#### Create a New Contact

**POST** `/api/contacts`

**Headers:**
```
Authorization: Bearer <your_jwt_token>
```

**Request Body:**
```json
{
  "name": "Alice",
  "email": "alice@example.com",
  "phone": "123456789"
}
```

**Response:**
```json
{
  "_id": "contact_id",
  "name": "Alice",
  "email": "alice@example.com",
  "phone": "123456789",
  "user_id": "user_id"
}
```

#### Get a Single Contact

**GET** `/api/contacts/:id`

**Headers:**
```
Authorization: Bearer <your_jwt_token>
```

#### Update a Contact

**PUT** `/api/contacts/:id`

**Headers:**
```
Authorization: Bearer <your_jwt_token>
```

**Request Body:**
```json
{
  "name": "Alice Updated",
  "email": "alice.updated@example.com",
  "phone": "987654321"
}
```

#### Delete a Contact

**DELETE** `/api/contacts/:id`

**Headers:**
```
Authorization: Bearer <your_jwt_token>
```


## Contributing

If you'd like to contribute, feel free to fork the repository and submit a pull request. Please ensure your code follows the existing style and includes appropriate tests.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

