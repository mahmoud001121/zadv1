# AGENTS.md

## Commands
- `npm run dev` - Dev server on port 3000, logs to dev.log
- `npm run build` - Production build
- `npm run lint` - ESLint

## Stack
- Next.js 16 + React 19 + TypeScript
- Tailwind CSS 4 + shadcn/ui (Radix UI)
- Client-side storage (IndexedDB + LocalStorage)
- Zustand (state), next-intl (i18n), web-push (notifications)

## Storage
- **Client-side only**: Goals, settings, and user data stored in browser
- **No database required**: App works entirely client-side
- **Push subscriptions**: Stored in-memory on server (resets on restart)

## Deployment
- **Vercel** (Recommended) - See `VERCEL_DEPLOYMENT.md`
  - Free tier: No credit card required
  - No database setup needed
  - Set env vars: `NEXT_PUBLIC_VAPID_PUBLIC_KEY`, `VAPID_PRIVATE_KEY`, `VAPID_SUBJECT`
  - Optional: Use cron-job.org to keep server awake

## Notes
- No test suite configured (no test script in package.json)
- Notifications work offline via Service Worker
- TypeScript errors ignored in build (`ignoreBuildErrors: true`)
- Cron job configured in `vercel.json` for push notifications
- Push subscriptions reset when server restarts (Vercel free tier sleeps after 15 min)
