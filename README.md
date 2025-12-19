# Hero Community Help Network

A full-stack community help platform where users can post help requests, accept contributions, track progress, and view history.

**Frontend**: React + TypeScript + Vite + Tailwind CSS  
**Backend**: Node.js + Express.js + MongoDB (with Mongoose)  
**State Management**: React Context API  
**Authentication**: JWT-based (customizable)  
**Deployment Ready**: Vercel (frontend), Render/ Railway/ Cyclic (backend)

This app was originally generated in Google AI Studio (Build mode) and has been extended with a proper backend.

## Features
- User registration and login
- Post help requests (title, description, location, urgency)
- Accept requests and contribute as a "hero"
- Track in-progress and completed contributions
- View personal history and contributions
- Role-based views (user/admin)
- Responsive design with Tailwind CSS and Lucide icons

## Tech Stack

### Frontend
- React 18 + TypeScript
- Vite (fast dev server)
- React Router DOM v6
- Tailwind CSS
- Lucide-react icons
- Context API for global state

### Backend
- Node.js
- Express.js
- MongoDB + Mongoose ODM
- JWT for authentication
- CORS enabled
- Environment variables via `.env`

## Project Structure

```
hero-community-help-network/
├── client/                  # Frontend (React + Vite)
│   ├── src/
│   │   ├── pages/           # LoginPage.tsx, HomePage.tsx, AcceptedPage.tsx, etc.
│   │   ├── components/
│   │   ├── App.tsx
│   │   └── main.tsx
│   ├── vite.config.ts
│   └── package.json
│
├── server/                  # Backend (Express + MongoDB)
│   ├── src/
│   │   ├── controllers/     # Request, auth, user logic
│   │   ├── models/          # User.model.ts, Request.model.ts
│   │   ├── routes/          # api routes
│   │   ├── middleware/      # auth middleware
│   │   └── server.ts        # Main Express server
│   ├── .env
│   ├── tsconfig.json
│   └── package.json
│
├── .gitignore
└── README.md                # This file
```

## Prerequisites
- Node.js v18+ (https://nodejs.org)
- MongoDB Atlas account (or local MongoDB)
- npm or yarn

## Setup Instructions

### 1. Clone / Extract the Project
Place both `client` and `server` folders in your project directory.

### 2. Backend Setup (server folder)

```bash
cd server
npm install
```

Create `.env` in `/server`:
```env
PORT=5000
MONGO_URI=mongodb+srv://<username>:<password>@cluster0.xxxxx.mongodb.net/hero-help-db?retryWrites=true&w=majority
JWT_SECRET=your-super-secret-jwt-key-here
JWT_EXPIRE=7d
NODE_ENV=development
```

Start the backend:
```bash
npm run dev
```
Backend runs on `http://localhost:5000`

### 3. Frontend Setup (client folder)

```bash
cd ../client
npm install
```

Create `.env` in `/client`:
```env
VITE_API_URL=http://localhost:5000/api
```

Start the frontend:
```bash
npm run dev
```
Frontend runs on `http://localhost:5173`

## API Endpoints (Example)

| Method | Endpoint               | Description                     |
|--------|------------------------|---------------------------------|
| POST   | `/api/auth/register`   | Register new user               |
| POST   | `/api/auth/login`      | Login user → returns JWT        |
| GET    | `/api/requests`        | Get all help requests           |
| POST   | `/api/requests`        | Create new request (auth req)   |
| PATCH  | `/api/requests/:id/accept` | Accept a request            |
| PATCH  | `/api/requests/:id/complete` | Mark as completed         |

## Scripts

### Backend (`server/package.json`)
```json
"scripts": {
  "dev": "ts-node-dev src/server.ts",
  "build": "tsc",
  "start": "node dist/server.js"
}
```

### Frontend (`client/package.json`)
```json
"scripts": {
  "dev": "vite",
  "build": "vite build",
  "preview": "vite preview"
}
```

## Deployment

### Frontend (Vercel / Netlify)
- Push `client` folder to GitHub
- Connect to Vercel → Set build command: `npm run build`
- Output directory: `dist`

### Backend (Render / Railway / Cyclic.sh)
- Create new Web Service → Connect GitHub repo (`server` folder)
- Add environment variables (MONGO_URI, JWT_SECRET)
- Start command: `npm start`

### Alternative: Deploy Both Together
Use **Render** or **Railway** with a monorepo — set root directory properly.

## Security Notes
- Never expose JWT_SECRET or MongoDB credentials
- In production, serve frontend via HTTPS
- Use HttpOnly cookies for JWT (optional enhancement)

## Contributing
Feel free to fork and improve:
- Add email verification
- Real-time updates with Socket.io
- Image uploads for requests
