# Quick Deployment Guide for GitHub Pages

## Prerequisites
- GitHub account
- Git installed locally

## Steps

### 1. Initialize Git Repository
```bash
cd /Users/somikdas/.gemini/antigravity/scratch/splitwise-app
git init
git add .
git commit -m "Initial commit: SplitWise expense splitting app"
```

### 2. Create GitHub Repository
1. Go to https://github.com/new
2. Repository name: `splitwise-app`
3. Make it **Public**
4. DON'T initialize with README (we have files already)
5. Click "Create repository"

### 3. Push to GitHub
```bash
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/splitwise-app.git
git push -u origin main
```

### 4. Enable GitHub Pages
1. Go to your repository on GitHub
2. Click **Settings** → **Pages**
3. Under **Source**, select **main** branch
4. Click **Save**
5. Your site will be at: `https://YOUR_USERNAME.github.io/splitwise-app/`

### 5. Update Google OAuth
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Navigate to **APIs & Services** → **Credentials**
3. Click on your OAuth 2.0 Client ID
4. Under **Authorized JavaScript origins**, add:
   - `https://YOUR_USERNAME.github.io`
5. Click **Save**

### 6. Test Live App
Visit your GitHub Pages URL and test the app!

---

## Important Configuration

Before deploying, make sure you've:

1. ✅ Configured Google Cloud OAuth Client ID
2. ✅ Updated `js/config.js` with your Client ID
3. ✅ Added authorized origins for both localhost AND GitHub Pages

---

## Workspace Recommendation

I recommend setting this directory as your workspace:

```
/Users/somikdas/.gemini/antigravity/scratch/splitwise-app
```

This will make it easier to work with the files in future conversations.
