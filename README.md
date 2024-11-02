node -v
npm -v
mkdir todo-app
cd todo-app
npm init -y
npm install express mongoose body-parser cors
const express = require('express');
const mongoose = require('mongoose');
const bodyParser = require('body-parser');
const cors = require('cors');

const app = express();
const port = process.env.PORT || 3000;

// Connect to MongoDB database
mongoose.connect('mongodb://localhost/todo-app', { useNewUrlParser: true, useUnifiedTopology: true })
.then(() => console.log('MongoDB Connected'))
.catch(err => console.error(err));

// Middleware
app.use(bodyParser.json());
app.use(cors());

// Define routes (we'll add more later)
app.get('/', (req, res) => {
    res.send('Hello World!');
});

app.listen(port, () => {
    console.log(`Server listening on port ${port}`);
});
