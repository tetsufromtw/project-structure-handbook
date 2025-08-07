# Next.js FAANG-style Folder Structure

## Project Overview

This folder structure is designed for large-scale production-grade applications using **Next.js with App Router**, inspired by FAANG best practices. Compared to a plain React project, the key differences are:

- **App Router (`app/`)** replaces the traditional `src/pages/` directory.
- API routes are colocated in the same project via `app/api/`.
- Next.js has more conventions (e.g. `page.tsx`, `layout.tsx`, `loading.tsx`) rather than purely custom routing.
- Built-in support for `Server Components`, file-based routing, and SSR.

## Folder Structure

```
my-next-app/

├── public/                      # Static assets (images, icons, etc)
│   └── images/
│   └── favicon.ico
│
├── src/
│   ├── app/                    # Next.js App Router entry
│   │   ├── layout.tsx         # Global layout
│   │   ├── page.tsx           # Root page
│   │   ├── api/               # API routes (Next.js functions)
│   │   └── (routes)/          # Route groups
│   │       └── dashboard/
│   │           ├── layout.tsx
│   │           └── page.tsx
│   │
│   ├── components/            # Reusable UI components
│   │   ├── ui/                # Atomic presentational components
│   │   ├── layout/            # Structural layout pieces (e.g. Header, Sidebar)
│   │   ├── charts/            # Visualization-specific components
│   │   └── icons/             # Icon components (SVG wrappers)
│   │
│   ├── features/              # Feature-based structure (auth, settings, etc)
│   │   ├── auth/
│   │   │   ├── components/
│   │   │   ├── hooks/
│   │   │   ├── services/
│   │   │   └── types.ts
│   │
│   ├── hooks/                 # Global reusable React hooks
│   ├── lib/                   # Shared logic (API clients, formatters, helpers)
│   ├── styles/                # Tailwind config and global styles
│   ├── types/                 # Global TypeScript types
│   ├── constants/             # Constants and enums
│   └── config/                # Runtime config, env flags, etc.
│
├── .env.local                 # Local environment variables
├── next.config.js             # Next.js config
├── tailwind.config.ts         # Tailwind config
├── tsconfig.json              # TS config
├── package.json
└── README.md
```

## ❌ Forbidden Practices

- ❌ Do NOT put business logic inside `components/ui/`. These should be purely presentational.
- ❌ Do NOT call APIs directly inside `page.tsx` or `layout.tsx`. Abstract via `features/*/services` or `lib/api.ts`.
- ❌ Do NOT colocate feature-specific components in `components/ui/`. Use `features/*/components` instead.
- ❌ Do NOT put shared utilities in `features/`. They belong in `lib/`.
- ❌ Avoid importing large 3rd-party libraries globally if they are only used in specific routes.
