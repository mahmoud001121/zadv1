# 🔧 Fix for Netlify Build Error

## The Problem

Next.js 16 uses Turbopack by default, but your Serwist plugin (for PWA/Service Worker) only works with webpack.

## The Solution (2 minutes)

### Step 1: Update package.json

In your netlify folder, open `package.json` and change the build script:

**Change from:**
```json
{
  "scripts": {
    "build": "next build"
  }
}
```

**Change to:**
```json
{
  "scripts": {
    "build": "next build --webpack"
  }
}
```

### Step 2: Push and Redeploy

```bash
cd /path/to/your/netlify/folder
git add package.json
git commit -m "Fix: Force webpack build for Serwist compatibility"
git push
```

Netlify will auto-deploy and the build will succeed!

---

## Alternative: Update netlify.toml

Or you can update the build command in `netlify.toml`:

**Change from:**
```toml
[build]
  command = "npm run build"
```

**Change to:**
```toml
[build]
  command = "npm run build -- --webpack"
```

Then push and redeploy.

---

## Why This Works

- Serwist plugin requires webpack
- Next.js 16 defaults to Turbopack
- Adding `--webpack` flag forces Next.js to use webpack
- Build will succeed and your PWA will work perfectly

That's it! 🚀
