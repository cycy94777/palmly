# 🚀 Palmly — Deployment Guide (GitHub + Vercel)

## Prerequisites

- A [GitHub](https://github.com) account (free)
- A [Vercel](https://vercel.com) account (free — sign up with GitHub)

---

## Step 1 — Create a GitHub Repository

### Option A: Upload via GitHub Web (easiest)

1. Go to [github.com/new](https://github.com/new)
2. Fill in:
   - **Repository name:** `palmly`
   - **Visibility:** Public *(required for Vercel free tier)*
   - Check **Add a README file**
3. Click **Create repository**
4. Inside the repo, click **Add file → Upload files**
5. Drag and drop these three files:
   - `index.html`
   - `README.md`
   - `DEPLOY.md`
6. Enter a commit message (e.g. `Initial commit`) and click **Commit changes**

### Option B: Git CLI

```bash
# 1. Initialize local repo
git init palmly
cd palmly

# 2. Copy your files into this folder
#    (index.html, README.md, DEPLOY.md)

# 3. Push to GitHub
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/palmly.git
git push -u origin main
```

> Replace `YOUR_USERNAME` with your GitHub username.

---

## Step 2 — Deploy to Vercel

1. Go to [vercel.com](https://vercel.com) → **Sign Up** → **Continue with GitHub**
2. Authorize Vercel to access your GitHub account
3. Click **Add New Project**
4. Find **palmly** in the repository list → click **Import**
5. On the configuration page:
   - **Framework Preset:** `Other` *(not Next.js or any other framework)*
   - **Root Directory:** `./` *(leave as default)*
   - **Build Command:** *(leave empty)*
   - **Output Directory:** *(leave empty)*
6. Click **Deploy**
7. Wait ~30 seconds until you see the success screen

---

## Step 3 — Get Your Live URL

After deployment, Vercel assigns a URL like:

```
https://palmly.vercel.app
```

**That is your live demo link.** Share it anywhere.

> Vercel provides HTTPS automatically — camera and microphone features work out of the box.

---

## Step 4 — Custom Domain (Optional)

If you own a domain (e.g. `palmly.io`):

1. In your Vercel project → **Settings → Domains**
2. Enter your domain → click **Add**
3. Follow the instructions to add a CNAME record at your DNS provider

---

## Updating the App

### Option A: GitHub Web

1. Open your GitHub repo
2. Click `index.html` → pencil icon (Edit)
3. Paste the updated content → **Commit changes**
4. Vercel auto-detects the change and redeploys in ~30 seconds

### Option B: Git CLI

```bash
cd palmly
git add index.html
git commit -m "Update app"
git push
# Vercel deploys automatically
```

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| Camera not working | Make sure you are on an **HTTPS** URL, not `http://` |
| Sign detection inaccurate | Good lighting, plain background, hand 40–60 cm from camera |
| 3D hand does not appear | Wait 2–3 s for CDN to load. Requires access to `cdnjs.cloudflare.com` |
| Vercel deploy fails | Set Framework to **Other**, leave Build Command **empty** |
| Mic not working | Use Chrome or Safari — Firefox has limited Web Speech API support |

---

## Architecture

```
Single HTML file — all dependencies loaded from CDN:

index.html
  ├── Three.js r128        → cdnjs.cloudflare.com
  ├── MediaPipe Hands      → cdn.jsdelivr.net
  ├── Google Fonts         → fonts.googleapis.com
  └── Web Speech API       → built into the browser, no CDN needed
```

No backend. No database. No API key. No build step.
Entirely client-side — free to run forever on Vercel's free tier.
