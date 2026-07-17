# Taskify-Project
Final Year Project for Computer Science Students



Taskify - Full Stack Task Management Application

Taskify is a modern full-stack task management web application that helps users organize, track, and manage their daily tasks efficiently. It provides a secure authentication system, an intuitive user interface, and powerful task management features to improve productivity.

Features
User Registration & Login
JWT Authentication
OTP Email Verification
Secure Password Management
Create, Update, Delete Tasks
Mark Tasks as Completed
Task Status Management
Responsive User Interface
User Profile Management
RESTful API Architecture
MongoDB Database Integration
Tech Stack
Frontend
React.js
React Router
CSS / Tailwind CSS
Axios
Backend
Node.js
Express.js
JWT Authentication
Nodemailer
bcrypt.js
Database
MongoDB
Mongoose
Project Structure
Taskify-Project/
│
├── client/          # React Frontend
├── server/          # Express Backend
├── README.md
└── package.json
Installation
Clone the Repository
git clone https://github.com/your-username/Taskify-Project.git
Navigate to the Project
cd Taskify-Project
Install Dependencies

For the frontend:

cd client
npm install

For the backend:

cd ../server
npm install
Configure Environment Variables

Create a .env file inside the server folder and add:

PORT=5000
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key
EMAIL=your_email
EMAIL_PASSWORD=your_email_password
Run the Application

Backend

npm run server

Frontend

npm run dev

Or run both together if configured:

npm run both
Screenshots


javascript
