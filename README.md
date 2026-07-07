# 🚀 AI Social Scheduler

Manage and automate your social media presence — connect accounts, schedule posts across platforms, and let AI write and design your content for you.

**Live App:** [social-media-scheduler-beige-five.vercel.app](https://social-media-scheduler-beige-five.vercel.app)

---

## ✨ Features

- **Dashboard** — at-a-glance stats (scheduled/published posts, connected accounts) and a recent activity feed
- **Multi-Platform Account Management** — connect X, LinkedIn, Facebook, and Instagram via secure OAuth
- **Post Scheduler** — compose once, publish to multiple platforms, attach media, and pick a date/time
- **AI Composer** — generate on-brand captions with a tone preset (Professional, Creative, Funny, Minimalist, Excited)
- **AI Image Generation** — optionally generate accompanying visuals for a post
- **Auto-Publishing** — a cron-based scheduler publishes posts automatically at the scheduled time
- **JWT Authentication** — secure session handling across the app

---

## 🛠️ Tech Stack

| Layer | Tech |
|---|---|
| Frontend | React (TypeScript/JSX), Vite — deployed on **Vercel** |
| Backend | Node.js, Express — deployed on **Render** |
| Database | MongoDB (Atlas) |
| Social OAuth & Publishing | [Zernio API](https://zernio.com) — unified API for connecting/posting to social platforms |
| AI Text Generation | Google **Gemini API** |
| AI Image Generation | **Leonardo.ai** |
| Auth | JWT |

---

## 📸 Screenshots

**Dashboard**
![Dashboard](./screenshots/dashboard.png)

**Connected Accounts**
![Accounts](./screenshots/accounts.png)

**Post Scheduler**
![Scheduler](./screenshots/scheduler.png)

**AI Composer**
![AI Composer](./screenshots/ai-composer.png)

**Schedule an AI Generation**
![Schedule Generation](./screenshots/schedule-generation.png)

---

## 🔄 How It Works

1. **Connect** your social accounts (X, LinkedIn, Facebook, Instagram) through OAuth, powered by Zernio.
2. **Create** a post manually in the Scheduler, or head to **AI Composer** — describe what you want, pick a tone, and optionally generate an image.
3. **Schedule** the post for one or more platforms at your chosen date and time.
4. A **cron job** on the backend automatically publishes the post via Zernio when it's due.
5. Track results back on the **Dashboard**.

---

## ⚙️ Getting Started

### Prerequisites
- Node.js (v18+)
- MongoDB Atlas connection string
- API keys: Zernio, Google Gemini, Leonardo.ai

### Backend Setup
```bash
cd server
npm install
```

Create a `.env` file:
```env
PORT=5000
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
CLIENT_URL=http://localhost:5173

ZERNIO_API_KEY=your_zernio_api_key
GEMINI_API_KEY=your_gemini_api_key
LEONARDO_API_KEY=your_leonardo_api_key
```

```bash
npm run dev
```

### Frontend Setup
```bash
cd client
npm install
```

Create a `.env` file:
```env
VITE_API_URL=http://localhost:5000
```

```bash
npm run dev
```

---

## 🌐 Deployment Notes

- **Frontend (Vercel):** requires a `vercel.json` with SPA rewrites so client-side routes (e.g. `/dashboard`) don't 404 on refresh:
  ```json
  {
    "rewrites": [{ "source": "/(.*)", "destination": "/index.html" }]
  }
  ```
- **Backend (Render):** whitelist Render's outbound IPs (or allow `0.0.0.0/0` for dev) in MongoDB Atlas network access, since Render's IPs are dynamic.
- **Zernio free tier:** the first 2 connected social accounts are free per API key/workspace — this limit is shared across *all* users of the app, not per individual user.

---

## 📄 License

MIT

---

*Built by Arijit Roy*
