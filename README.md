# Pizza-Jolo

Pizza ordering web app with Vue.js frontend, Node.js/Express backend, MongoDB, JWT authentication

## Test account:
test_user
test_password

## Tech Stack

- **Frontend**: Vue.js 3, Vite, Axios
- **Backend**: Node.js, Express.js, MongoDB
- **Authentication**: JWT (JSON Web Tokens)

## Local Development

### Backend Setup

1. Navigate to the backend directory:
   ```bash
   cd app/pizza-express
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file based on `.env.example`:
   ```bash
   cp .env.example .env
   ```

4. Configure your environment variables in `.env`: 
   - `MONGO_URI`: Your MongoDB connection string
   - `MONGO_DB_NAME`: Your database name
   - `JWT_SECRET`: Secret key for JWT token generation
   - `FRONTEND_URL`: Frontend URL for CORS (default: http://localhost:5173)

5. Start the backend server:
   ```bash
   node index.js
   ```
   The server will run on port 3000 (or the PORT specified in .env)

### Frontend Setup

1. Navigate to the frontend directory:
   ```bash
   cd app/pizza-vue
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file based on `.env.example`:
   ```bash
   cp .env.example .env
   ```

4. Configure the API URL in `.env`:
   - `VITE_API_URL`: Backend API URL (default: http://localhost:3000)

5. Start the development server:
   ```bash
   npm run dev
   ```
   The frontend will run on http://localhost:5173
