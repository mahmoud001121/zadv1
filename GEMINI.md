# 🕌 زاد مسلم — Zad Muslim (Project Context)

Welcome to the **Zad Muslim** project. This is a modern Islamic web application designed to be a daily spiritual companion.

## 🌟 Project Overview
- **Name:** زاد مسلم (Zad Muslim)
- **Architecture:** Next.js 16 (App Router) + TypeScript
- **Primary Language:** Arabic (RTL support enabled)
- **Core Purpose:** Provides prayer times, Hijri calendar, Azkar (dhikr), Quran reading, and automated reminders/notifications.

## 🛠 Tech Stack
- **Frontend:** React 19, Tailwind CSS 4, Framer Motion (animations), shadcn/ui (Radix UI primitives).
- **State Management:** Zustand (with persistence for user settings).
- **Data Fetching:** TanStack Query (React Query).
- **Backend/Database:** Prisma ORM with SQLite (Local) / Turso (Production).
- **Audio:** Howler.js for Adhan and Quran recitations.
- **Notifications:** Web Push API and Service Workers for offline-capable reminders.

## 📁 Key Directory Structure
- `src/app/`: Next.js App Router routes and API endpoints (`/api/*`).
- `src/components/`: Feature-specific components:
    - `prayer/`: Prayer times, countdown, and adhan toasts.
    - `azkar/`: Dhikr lists and counters.
    - `quran/`: Quran reader and Mushaf view.
    - `layout/`: Global navigation and patterns.
    - `ui/`: Shared shadcn/ui primitives.
- `src/hooks/`: Business logic hooks (e.g., `usePrayerTimes`, `useGeolocation`, `usePushNotifications`).
- `src/store/`: Zustand stores for application state (`settings`, `quran`, `salawat`).
- `prisma/`: Database schema (`schema.prisma`) and seed data.
- `public/`: Static assets, including adhan audio files in `public/audio/`.

## 🚀 Getting Started

### Development Commands
- `npm run dev`: Starts the development server on port 3000 (logs to `dev.log`).
- `npm run build`: Compiles the project for production.
- `npm run lint`: Runs ESLint for code quality checks.

### Database Management (Prisma)
- `npm run db:generate`: Generates the Prisma client.
- `npm run db:push`: Synchronizes the schema with the local SQLite database.
- `npm run db:migrate`: Creates and runs database migrations.

## 📝 Development Conventions

### Styling & UI
- **Tailwind CSS 4:** Use utility classes for styling. Follow the established `zad-` color palette (e.g., `bg-zad-midnight`).
- **Dark Mode:** The app is dark-mode first. Use `dark:` modifiers if needed, but the root layout is set to `dark`.
- **Animations:** Use `framer-motion` for transitions and interactive elements.

### Architecture Patterns
- **Client Components:** Use `'use client'` at the top of files that utilize hooks (Zustand, Query, etc.).
- **Persistence:** User preferences (location, madhab, adhan settings) are stored in `useSettingsStore` and persisted to `localStorage`.
- **RTL Support:** The app defaults to `dir="rtl"`. Ensure layouts and components (especially flex/grid) handle RTL gracefully.

### Notifications & Service Workers
- The app uses a custom Service Worker (`public/sw.js`) for background tasks and push notifications.
- Environmental variables for VAPID keys are required for push notification functionality.

## ⚠️ Important Notes
- **Vercel Deployment:** Since Vercel has a read-only filesystem, use a hosted database like **Turso** for production instead of local SQLite.
- **No Tests:** Currently, there is no automated test suite configured. Ensure manual verification of core features (Prayer times, Audio playback) after changes.
