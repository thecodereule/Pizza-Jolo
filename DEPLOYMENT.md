# Deployment Guide / Vodič za Deployment

## Hrvatski (Croatian)

### Deployment Backend-a na Render

1. **Poveži repozitorij s Renderom**:
   - Prijavi se na [Render](https://render.com)
   - Klikni "New +" → "Web Service"
   - Poveži svoj GitHub repozitorij

2. **Konfiguriraj servis**:
   - Render će automatski detektirati `render.yaml` konfiguraciju
   - Ili ručno konfiguriraj:
     - **Name**: pizza-jolo-backend
     - **Root Directory**: `app/pizza-express`
     - **Build Command**: `npm install`
     - **Start Command**: `node index.js`

3. **Postavi environment varijable**:
   Dodaj sljedeće environment varijable u Render dashboardu:
   - `MONGO_URI`: MongoDB connection string (npr. iz MongoDB Atlas-a)
   - `MONGO_DB_NAME`: Ime baze podataka
   - `JWT_SECRET`: Sigurnosni ključ za JWT tokene
   - `FRONTEND_URL`: URL tvog Vercel frontend-a (npr. https://tvoja-app.vercel.app)

4. **Deploy**:
   - Klikni "Create Web Service"
   - Render će automatski deployati backend
   - Zapiši deployed URL (npr. https://pizza-jolo-backend.onrender.com)

### Deployment Frontend-a na Vercel

1. **Poveži repozitorij s Vercelom**:
   - Prijavi se na [Vercel](https://vercel.com)
   - Klikni "Add New..." → "Project"
   - Importaj svoj GitHub repozitorij

2. **Konfiguriraj projekt**:
   - Vercel će automatski detektirati `vercel.json` konfiguraciju
   - Framework: Vite
   - Build Command: `cd app/pizza-vue && npm install && npm run build`
   - Output Directory: `app/pizza-vue/dist`

3. **Postavi environment varijablu**:
   Dodaj environment varijablu u Vercel dashboardu:
   - `VITE_API_URL`: URL tvog Render backend-a (npr. https://pizza-jolo-backend.onrender.com)

4. **Deploy**:
   - Klikni "Deploy"
   - Vercel će buildati i deployati frontend
   - Pristupi aplikaciji na Vercel URL-u

### Nakon Deploymenta

1. **Ažuriraj CORS**: Provjeri da `FRONTEND_URL` varijabla u Renderu odgovara tvom Vercel URL-u

2. **Testiraj aplikaciju**:
   - Posjeti svoj Vercel URL
   - Testiraj registraciju, login i naručivanje pizze
   - Provjeri da API pozivi rade ispravno

3. **Automatski redeploy**:
   - Render i Vercel će automatski redeployati kad pushneš na main branch

## Environment Varijable

### Backend (.env u app/pizza-express)
```
MONGO_URI=mongodb+srv://korisnik:lozinka@cluster.mongodb.net/
MONGO_DB_NAME=pizza-jolo
JWT_SECRET=tvoj-tajni-kljuc
FRONTEND_URL=https://tvoja-vercel-app.vercel.app
```

### Frontend (.env u app/pizza-vue)
```
VITE_API_URL=https://tvoj-render-backend.onrender.com
```

## Riješavanje Problema

- **CORS greške**: Provjeri da `FRONTEND_URL` u backend-u odgovara Vercel URL-u
- **API connection problemi**: Provjeri da `VITE_API_URL` u frontendu odgovara Render URL-u
- **Database connection**: Provjeri MongoDB connection string i whitelistaj Render IP u MongoDB Atlas-u
- **Build failures**: Provjeri build logove u Vercel/Render dashboardu

---

## English

### Deploy Backend to Render

1. **Connect Repository to Render**:
   - Sign up at [Render](https://render.com)
   - Click "New +" → "Web Service"
   - Connect your GitHub repository

2. **Configure Service**:
   - Render will auto-detect `render.yaml` configuration
   - Or manually configure:
     - **Name**: pizza-jolo-backend
     - **Root Directory**: `app/pizza-express`
     - **Build Command**: `npm install`
     - **Start Command**: `node index.js`

3. **Set Environment Variables**:
   Add these environment variables in Render dashboard:
   - `MONGO_URI`: MongoDB connection string (e.g., from MongoDB Atlas)
   - `MONGO_DB_NAME`: Database name
   - `JWT_SECRET`: Secret key for JWT tokens
   - `FRONTEND_URL`: Your Vercel frontend URL (e.g., https://your-app.vercel.app)

4. **Deploy**:
   - Click "Create Web Service"
   - Render will automatically deploy the backend
   - Note the deployed URL (e.g., https://pizza-jolo-backend.onrender.com)

### Deploy Frontend to Vercel

1. **Connect Repository to Vercel**:
   - Sign up at [Vercel](https://vercel.com)
   - Click "Add New..." → "Project"
   - Import your GitHub repository

2. **Configure Project**:
   - Vercel will auto-detect `vercel.json` configuration
   - Framework: Vite
   - Build Command: `cd app/pizza-vue && npm install && npm run build`
   - Output Directory: `app/pizza-vue/dist`

3. **Set Environment Variable**:
   Add this environment variable in Vercel dashboard:
   - `VITE_API_URL`: Your Render backend URL (e.g., https://pizza-jolo-backend.onrender.com)

4. **Deploy**:
   - Click "Deploy"
   - Vercel will build and deploy the frontend
   - Access your app at the Vercel URL

### Post-Deployment

1. **Update CORS**: Ensure `FRONTEND_URL` in Render matches your Vercel URL

2. **Test Application**:
   - Visit your Vercel URL
   - Test registration, login, and pizza ordering
   - Verify API calls work correctly

3. **Auto-redeploy**:
   - Both Render and Vercel will auto-redeploy on push to main branch

## Environment Variables

### Backend (.env in app/pizza-express)
```
MONGO_URI=mongodb+srv://user:password@cluster.mongodb.net/
MONGO_DB_NAME=pizza-jolo
JWT_SECRET=your-secret-key
FRONTEND_URL=https://your-vercel-app.vercel.app
```

### Frontend (.env in app/pizza-vue)
```
VITE_API_URL=https://your-render-backend.onrender.com
```

## Troubleshooting

- **CORS errors**: Check that `FRONTEND_URL` in backend matches Vercel URL
- **API connection issues**: Check that `VITE_API_URL` in frontend matches Render URL
- **Database connection**: Verify MongoDB connection string and whitelist Render IP in MongoDB Atlas
- **Build failures**: Check build logs in Vercel/Render dashboard
