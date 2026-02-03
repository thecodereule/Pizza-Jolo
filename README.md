# Pizza-Jolo

Pizza ordering web app with Vue.js frontend, Node.js/Express backend, MongoDB, JWT authentication

## Tech Stack

- **Frontend**: Vue.js 3, Vite, TailwindCSS, Axios
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

## Production Deployment

### Backend Deployment on Render

1. **Connect Repository to Render**:
   - Sign up/login to [Render](https://render.com)
   - Click "New +" → "Web Service"
   - Connect your GitHub repository

2. **Configure Service**:
   - Render will automatically detect the `render.yaml` configuration
   - Or manually configure:
     - **Name**: pizza-jolo-backend
     - **Root Directory**: `app/pizza-express`
     - **Build Command**: `npm install`
     - **Start Command**: `node index.js`

3. **Set Environment Variables**:
   Add the following environment variables in Render dashboard:
   - `MONGO_URI`: Your MongoDB connection string (e.g., from MongoDB Atlas)
   - `MONGO_DB_NAME`: Your database name
   - `JWT_SECRET`: A secure random string for JWT signing
   - `FRONTEND_URL`: Your Vercel frontend URL (e.g., https://your-app.vercel.app)
   - `PORT`: Will be set automatically by Render

4. **Deploy**:
   - Click "Create Web Service"
   - Render will automatically deploy your backend
   - Note the deployed URL (e.g., https://pizza-jolo-backend.onrender.com)

### Frontend Deployment on Vercel

1. **Connect Repository to Vercel**:
   - Sign up/login to [Vercel](https://vercel.com)
   - Click "Add New..." → "Project"
   - Import your GitHub repository

2. **Configure Project**:
   - Vercel will automatically detect the `vercel.json` configuration
   - Framework Preset: Vite
   - Root Directory: Leave as default (Vercel will use the config)
   - Build Command: `cd app/pizza-vue && npm install && npm run build`
   - Output Directory: `app/pizza-vue/dist`

3. **Set Environment Variables**:
   Add the following environment variable in Vercel dashboard:
   - `VITE_API_URL`: Your Render backend URL (e.g., https://pizza-jolo-backend.onrender.com)

4. **Deploy**:
   - Click "Deploy"
   - Vercel will build and deploy your frontend
   - Access your app at the provided Vercel URL

### Post-Deployment

1. **Update CORS**: Make sure the `FRONTEND_URL` environment variable in Render matches your Vercel deployment URL

2. **Test the Application**:
   - Visit your Vercel URL
   - Test user registration, login, and pizza ordering functionality
   - Verify API calls are working correctly

3. **Continuous Deployment**:
   - Both Render and Vercel will automatically redeploy when you push to your main branch
   - You can also set up preview deployments for pull requests

## Environment Variables Reference

### Backend (.env in app/pizza-express)
```
MONGO_URI=mongodb+srv://username:password@cluster.mongodb.net/
MONGO_DB_NAME=pizza-jolo
JWT_SECRET=your-secret-key-here
FRONTEND_URL=https://your-vercel-app.vercel.app
PORT=3000
```

### Frontend (.env in app/pizza-vue)
```
VITE_API_URL=https://your-render-backend.onrender.com
```

## Troubleshooting

- **CORS errors**: Ensure `FRONTEND_URL` in backend matches your Vercel deployment URL
- **API connection issues**: Check that `VITE_API_URL` in frontend matches your Render backend URL
- **Database connection**: Verify MongoDB connection string and whitelist Render's IP in MongoDB Atlas
- **Build failures**: Check build logs in Vercel/Render dashboard for specific errors
