# 🐍 gwfreact Project 


## 📄 Overview:
  - The gwfreact project is a Python application designed to collect and analyze network data from various sources. 
  - It also tracks data patterns and provides analytics on network traffic.
  - This project is built using Python, Pandas, NumPy, and Matplotlib.

## ✨ Features:
 - Data Collection: Users can input network endpoints and receive processed data.
 - Data Processing: Raw data is transformed into structured formats, logging each transformation.
 - Track Patterns and Analytics: The app tracks each data point, recording timestamps and updating analysis metrics.
 - View Analytics: Users can view detailed analytics for each dataset, including patterns and history.
 - User Authentication: Secure user registration and login using JWT.
 - User Authorization: Ensure users can only access their own data and analytics.

## 💻 Tech Stack:
- **Frontend:** Streamlit
- **Backend:** Python, FastAPI
- **Database:** PostgreSQL
- **Libraries:** pandas, numpy, matplotlib, jwt, bcrypt

## 📂Project Structure 
```sh
gwfreact/
├── controllers/
│   ├── userController.py
│   └── dataController.py
├── middlewares/
│   └── jwtAuthMiddleware.py
├── models/
│   ├── User.py
│   └── Dataset.py
├── routes/
│   ├── userRoutes.py
│   └── dataRoutes.py
├── views/
│   ├── home.py
│   ├── login.py
│   └── register.py
├── utils/
│   ├── analytics/
│   │   └── analyzer.py
├── .env
├── main.py
├── requirements.txt
└── README.md
```


## ⚙️ Working: 
1. Main Application (main.py)
    - Setup: Loads environment variables, initializes FastAPI, connects to PostgreSQL, and sets up middleware.
    - API Routes: Defines routes for data operations, static content, and user authentication.
    - Server: Starts the server on a specified port.

2. Data Model (models/Dataset.py)
    - Schema Definition: Defines the structure of the dataset documents in PostgreSQL, including original data, processed data, analysis metrics, and query history.
    - Default Values: Uses UUID to generate unique identifiers and sets default values for analysis counts.

3. Data Controller (controllers/dataController.py)
    - Process Data: Handles the processing of raw data, storing them in the database and returning the result.
    - Analyze Data: Handles data analysis, logging each query and updating analysis counts.
    - Get Analytics: Provides analytics data for a given dataset, including analysis patterns and query history.

4. User Model (models/User.py)
    - Schema Definition: Defines the structure of the user documents in PostgreSQL, including username, email, and hashed password.
    - Password Hashing: Uses bcrypt to hash passwords before saving them to the database.

5. User Controller (controllers/userController.py)
    - Register User: Handles user registration, including hashing the password and saving the user to the database.
    - Login User: Handles user login, including verifying the password and generating a JWT.

6. Authentication Middleware (middlewares/jwtAuthMiddleware.py)
    - Verify JWT: Middleware to verify the JWT from headers and attach the user information to the request object.

7. Routes (routes/dataRoutes.py)
    - POST /data: Endpoint for processing new data (authenticated).
    - GET /analyze/:datasetId: Endpoint for analyzing datasets.
    - GET /analytics/:datasetId: Endpoint for retrieving analytics for a dataset (authenticated).

8. User Routes (routes/userRoutes.py)
    - POST /register: Endpoint for user registration.
    - POST /login: Endpoint for user login.

9. Static Routes (routes/staticRouter.py)
    - GET /: Endpoint for rendering the home page with all datasets (authenticated).

## 🔒 Authentication and Authorization

1. User Registration
      - Endpoint: `POST /user/register`
      - Users can create a new account by providing a username, email, and password. Passwords are hashed before storage.

2. User Login
     - Endpoint: `POST /user/login`
     - Users can log in using their email and password. On successful login, a JWT is generated and stored in headers.

3. JWT Authentication Middleware
     - Middleware checks for the JWT token in headers, verifies it, and attaches the user information to the request object.
     - Used to protect routes and ensure only authenticated users can access certain endpoints.

4. Authorization
     - Users can only access their own datasets and analytics.
     - Middleware ensures that each request is authenticated and the user can only see or modify their own data.

## 📦 Installation

1. Clone the Repository
```sh
  https://github.com/gwfprojekt/gwfreact.git
```
    
2. Install Dependencies
```sh
  pip install -r requirements.txt
```

3. Set Up Environment Variables
```sh
// Create a .env file in the root directory and Add your PostgreSQL URL:
  DATABASE_URL=your_postgresql_connection_string
```
4. Start the Server
```sh
  python main.py
```
5. Access the Application
```sh
  Open your browser and go to http://localhost:8000.
```

### 🔗 Connect with ME :
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gwfprojekt)
