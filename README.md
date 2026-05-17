# QuizForge Pro — AI-Powered Quiz Generator

Transform any content into professional quizzes with AI. Upload documents, paste text, share a URL, or analyze images — Gemini AI generates intelligent quizzes with explanations, analytics, and spaced repetition.

## 🚀 Deploy to Netlify (via GitHub)

### Step 1: Push to GitHub

1. Create a new repository on GitHub
2. Push this code:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: QuizForge Pro"
   git remote add origin https://github.com/YOUR_USERNAME/quizforge-pro.git
   git push -u origin main
   ```

### Step 2: Connect Netlify

1. Go to [netlify.com](https://netlify.com) and sign in
2. Click **"Add new site"** → **"Import an existing project"**
3. Connect your GitHub account and select the `quizforge-pro` repo
4. Netlify will auto-detect the `netlify.toml` config — just click **Deploy**

### Step 3: Set Environment Variables

In Netlify dashboard → **Site settings** → **Environment variables**, add:

| Variable | Value | Where to get it |
|---|---|---|
| `DATABASE_URL` | `postgresql://postgres.XXX:PASSWORD@aws-0-XX.pooler.supabase.com:6543/postgres` | Supabase → Settings → Database → Connection string (pooler) |
| `NEXT_PUBLIC_SUPABASE_URL` | `https://XXX.supabase.co` | Supabase → Settings → API → Project URL |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | `eyJ...` | Supabase → Settings → API → Anon/Public key |
| `SUPABASE_SERVICE_ROLE_KEY` | `eyJ...` | Supabase → Settings → API → Service role key |
| `GEMINI_API_KEY` | `AIza...` | [Google AI Studio](https://aistudio.google.com/apikey) |

**Optional** (for more rate limit capacity):
| Variable | Description |
|---|---|
| `GEMINI_API_KEY_2` through `GEMINI_API_KEY_6` | Additional Gemini API keys from different Google accounts |

### Step 4: Setup Supabase Database

1. Go to Supabase → **SQL Editor**
2. Run the SQL from `supabase-init.sql` to create all tables
3. Go to **Authentication** → **Providers** → disable "Confirm email" for easier signup
4. Optionally enable Google/GitHub OAuth providers

### Step 5: Trigger Redeploy

After setting environment variables, go to **Deploys** → **Trigger deploy** → **Deploy site**

## 🛠 Tech Stack

- **Frontend**: Next.js 16 + React 19 + Tailwind CSS 4 + shadcn/ui
- **Backend**: Next.js API Routes (Netlify Functions)
- **Database**: Supabase (PostgreSQL) + Prisma ORM
- **Auth**: Supabase Auth (Email/Password + Google + GitHub OAuth + Guest mode)
- **AI**: Google Gemini API (multi-key failover for rate limits)
- **State**: Zustand (client-side) + Supabase (server-side)
- **Deployment**: Netlify

## ✨ Features

- 🧠 AI quiz generation from text, PDFs, images, URLs, YouTube
- 📊 Analytics dashboard with performance tracking
- 🎯 Adaptive difficulty that adjusts to your level
- 🔄 Spaced repetition (Leitner box system) for review
- 🃏 Flashcard mode with flip animations
- 💀 Survival mode with lives system
- 🤖 AI Tutor that explains answers
- 📝 Study notes with AI summaries
- 🏪 Quiz marketplace & templates
- 👥 Collaborative quiz creation
- 🎮 Gamification (XP, levels, streaks, achievements)
- 📱 PWA support (installable)
- 🌙 Dark mode + multiple theme colors
- ⌨️ Keyboard shortcuts
- 🌐 Multi-language (English, Urdu, Chinese, Spanish, French, Arabic)
