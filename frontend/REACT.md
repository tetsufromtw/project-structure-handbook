# React Project Folder Structure (FAANG-Inspired)

This is a modular and scalable React folder structure inspired by FAANG best practices. It is suitable for long-term maintenance, team collaboration, and strict separation of concerns.

---

## Root Folder

```
my-react-app/
├── public/                  # Static assets
│   ├── images/
│   └── favicon.ico
├── src/                     # Application source code
│   ├── assets/              # Fonts, images, and global static resources
│   ├── components/          # Reusable presentational components
│   │   ├── ui/              # Atomic UI elements (Button, Input, etc)
│   │   ├── layout/          # Structural components (Header, Footer, Sidebar)
│   │   └── icons/           # SVG icon components
│   ├── features/            # Feature-based domain modules
│   │   ├── auth/
│   │   │   ├── components/
│   │   │   ├── hooks/
│   │   │   ├── services/
│   │   │   └── types.ts
│   │   └── dashboard/
│   ├── pages/               # React Router entry points (if using react-router)
│   ├── hooks/               # Global custom React hooks
│   ├── lib/                 # Generic utilities and shared logic
│   │   ├── api.ts
│   │   ├── formatter.ts
│   │   └── storage.ts
│   ├── constants/           # App-wide constants and enums
│   ├── config/              # App configuration and feature flags
│   ├── styles/              # Global styles and CSS/Tailwind config
│   │   └── globals.css
│   ├── types/               # Global TypeScript types
│   │   └── index.ts
│   └── App.tsx              # App root
├── .env.local               # Local environment variables
├── package.json
├── tsconfig.json
├── tailwind.config.js
└── vite.config.ts or webpack.config.js
```

---

## ❌ Forbidden Practices

- ❌ Do NOT call APIs directly in components.
- ❌ Do NOT place business logic inside `components/ui/`. Keep them purely presentational.
- ❌ Do NOT place feature-specific logic in `lib/`. Use `features/*/services`.
- ❌ Do NOT place reusable components inside `features/`. Extract them to `components/`.
- ❌ Do NOT use absolute paths without aliasing via tsconfig.json.

---

## ✅ Recommendations

- ✅ Keep `components/` dumb and reusable.
- ✅ Group domain logic by `features/`.
- ✅ Maintain clear separation of types, constants, config, and services.
- ✅ Use environment-specific config under `.env.*` files.
- ✅ Use a linter, formatter, and type checker (ESLint, Prettier, TypeScript).

---

This structure is optimized for collaboration in high-scale engineering environments.
