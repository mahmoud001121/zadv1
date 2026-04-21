# ✅ Netlify Deployment - Final Checklist

## Before You Push to GitHub

### 1. Check package.json build script

Open `package.json` in your netlify folder and verify:

```json
{
  "scripts": {
    "build": "next build --webpack"
  }
}
```

✅ Must have `--webpack` flag

### 2. Check netlify.toml exists

File: `netlify.toml`

Should contain:
```toml
[build]
  command = "npm run build"
  publish = ".next"

[[plugins]]
  package = "@netlify/plugin-nextjs"
```

✅ Build command and Next.js plugin configured

### 3. Check required files exist

- ✅ `src/` folder (all your source code)
- ✅ `prisma/` folder (database schema)
- ✅ `public/` folder (static assets)
- ✅ `package.json`
- ✅ `next.config.ts`
- ✅ `tsconfig.json`
- ✅ `tailwind.config.ts`
- ✅ `netlify.toml`
- ✅ `.gitignore`
- ✅ `.env.example`

### 4. Verify .gitignore excludes

Open `.gitignore` and make sure it has:
```
node_modules
.next
.env
*.log
*.db
```

---

## Deploy to Netlify

### Step 1: Push to GitHub

```bash
cd ~/Documents/netlify  # or wherever your netlify folder is

git init
git add .
git commit -m "Ready for Netlify deployment"

# Create repo at https://github.com/new
git remote add origin https://github.com/YOUR_USERNAME/zad-muslim.git
git branch -M main
git push -u origin main
```

### Step 2: Deploy on Netlify

1. Go to https://netlify.com
2. Sign up with GitHub (FREE, no credit card)
3. Click "Add new site" → "Import an existing project"
4. Choose GitHub and select your repository
5. Build settings should auto-detect:
   - Build command: `npm run build`
   - Publish directory: `.next`
6. Add environment variables (click "Add environment variables"):

```
NEXT_PUBLIC_VAPID_PUBLIC_KEY
BDfKkya975WhlfmZAkyxvBaiInsvJ-RyqNIZXyhPWTIemqB8nfmrhLruP2r1Yizaw915G_qSZG8pMl6-f0xUIM8

VAPID_PRIVATE_KEY
6IDB6Vntsb7D9yTa18iCLP8KWsd4CzUL1IBc9pTl66I

VAPID_SUBJECT
mailto:zad-muslim@app.com
```

7. Click "Deploy site"

### Step 3: Wait for Build (2-3 minutes)

Watch the build logs. You should see:
- ✅ Dependencies installing
- ✅ `next build --webpack` running
- ✅ Build completing successfully
- ✅ Site published

### Step 4: Setup Cron Job (for notifications)

1. Go to https://cron-job.org
2. Sign up (free)
3. Create new cron job:
   - URL: `https://your-site.netlify.app/api/push/cron`
   - Schedule: Every 1 minute
4. Save

---

## Common Issues & Solutions

### ❌ Build fails with Turbopack error
**Solution:** Make sure `package.json` has `"build": "next build --webpack"`

### ❌ Missing dependencies
**Solution:** Make sure `package.json` includes `@netlify/plugin-nextjs`

### ❌ Environment variables not working
**Solution:** Add them in Netlify dashboard → Site settings → Environment variables

### ❌ 404 errors on routes
**Solution:** Make sure `netlify.toml` has the Next.js plugin configured

---

## Final Verification

After deployment succeeds:

✅ Visit your site URL
✅ Test prayer times (allow location)
✅ Test notifications (allow notifications)
✅ Test PWA installation
✅ Test offline mode
✅ Test all features

---

## Summary

**Key Fix:** `"build": "next build --webpack"` in package.json

This forces webpack instead of Turbopack, which is required for the Serwist PWA plugin.

**Everything else is already configured!**

Just push to GitHub and deploy! 🚀
