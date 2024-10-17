# Recipe Blog - Using Node.js, Express, MongoDB, and Mongoose

This is a full-stack recipe blog application built using **Node.js** and **Express** for the backend, **MongoDB** with **Mongoose** for database management, and **Bootstrap** for front-end styling. The app also uses npm packages like `connect-flash`, `cookie-parser`, and `express-session` for enhanced functionality such as session management and flash messages.

## Prerequisites
Before running the project, ensure you have the following installed:
- Node.js
- MongoDB

## Setup

### 1. Create `.env` file
You need to create a `.env` file in the root directory to store your MongoDB database credentials. Here’s an example (replace `<username>` and `<password>` with your MongoDB credentials):

```bash
MONGODB_URI = mongodb+srv://<username>:<password>@cluster0.mongodb.net/recipeBlog?retryWrites=true&w=majority
SECRET_KEY = your_secret_key
```

### 2. Installation
To run the project locally, follow these steps:

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/recipe-blog.git
   cd recipe-blog
   ```

2. Install the necessary dependencies:
   ```bash
   npm install
   ```

   This will install the required packages, including:
   - **Express.js** for the backend framework
   - **Mongoose** for MongoDB interaction
   - **express-session** for session management
   - **connect-flash** for flash messages
   - **cookie-parser** for parsing cookies
   - **Bootstrap** for front-end styling

3. Start the server:
   ```bash
   npm start
   ```

4. Navigate to `http://localhost:3000` to view the app.

---

## Features

### Flash Messages
The app uses `connect-flash` to display flash messages (e.g., for form validation feedback or success messages).

### Sessions
`express-session` is used to maintain session data for logged-in users, and `cookie-parser` helps parse cookies for session management.

### MongoDB & Mongoose
The app uses MongoDB as the database and Mongoose for interacting with MongoDB, making schema definitions and database interaction easier.

### Express.js
The app is built using **Express.js**, a lightweight and flexible web framework for Node.js that simplifies request handling and routing.

### Bootstrap
The app is styled using **Bootstrap 5**, allowing for a responsive and modern UI. You can easily customize the styling further using Bootstrap classes in the HTML templates.

---

## Technologies & Packages

- **Node.js**: Backend runtime environment.
- **Express.js**: Web framework for building the application.
- **MongoDB**: NoSQL database for storing recipe data.
- **Mongoose**: ODM library to interact with MongoDB.
- **Bootstrap**: Front-end framework for responsive styling.
- **connect-flash**: Middleware for flash messages.
- **cookie-parser**: Middleware for parsing cookies.
- **express-session**: Session middleware for handling user sessions.

---

## Example Code

Here’s an example of how `express()`, `express-session`, `connect-flash`, `cookie-parser`, and `Bootstrap` are used in the project:

```javascript
const express = require('express');
const session = require('express-session');
const flash = require('connect-flash');
const cookieParser = require('cookie-parser');
const mongoose = require('mongoose');
const app = express();

// Middleware setup
app.use(cookieParser());
app.use(express.json());
app.use(express.urlencoded({ extended: true }));
app.use(session({
  secret: process.env.SECRET_KEY,
  resave: false,
  saveUninitialized: true,
}));
app.use(flash());

// Serve static files (including Bootstrap)
app.use(express.static('public'));

// Connect to MongoDB
mongoose.connect(process.env.MONGODB_URI, { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() => console.log('MongoDB connected'))
  .catch(err => console.log(err));

// Routes
app.get('/', (req, res) => {
  res.render('index', { title: 'Recipe Blog' });
});

// Start server
app.listen(3000, () => {
  console.log('Server running on port 3000');
});
```

---

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---