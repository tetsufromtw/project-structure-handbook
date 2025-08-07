# Angular FAANG-style Folder Structure

## Project Overview

This folder structure is inspired by large-scale FAANG frontend projects using Angular, emphasizing scalability, maintainability, and modularity.

## Folder Structure

```
my-angular-app/

├── src/
│   ├── app/
│   │   ├── core/                     # Singleton services, guards, interceptors, base modules
│   │   │   ├── services/
│   │   │   ├── guards/
│   │   │   ├── interceptors/
│   │   │   └── core.module.ts
│   │
│   │   ├── shared/                   # Shared reusable components, directives, pipes
│   │   │   ├── components/
│   │   │   ├── directives/
│   │   │   ├── pipes/
│   │   │   └── shared.module.ts
│   │
│   │   ├── features/                 # Feature modules (route-based)
│   │   │   ├── dashboard/
│   │   │   │   ├── components/
│   │   │   │   ├── pages/
│   │   │   │   ├── services/
│   │   │   │   ├── dashboard-routing.module.ts
│   │   │   │   └── dashboard.module.ts
│   │   │   └── auth/
│   │   │       ├── components/
│   │   │       ├── pages/
│   │   │       ├── services/
│   │   │       └── auth.module.ts
│   │
│   │   ├── layouts/                  # App-level layouts (e.g. AdminLayout, AuthLayout)
│   │   │   └── components/
│   │
│   │   ├── config/                   # App-wide configuration, environment tokens
│   │   ├── constants/                # Constant values, enums, route maps
│   │   ├── models/                   # Global interfaces and types
│   │   ├── utils/                    # Pure utility functions
│   │   ├── app-routing.module.ts
│   │   └── app.module.ts
│   │
│   ├── assets/                       # Static assets (images, icons, fonts)
│   │   └── images/
│   ├── environments/                 # Environment configs (dev, prod)
│   │   ├── environment.ts
│   │   └── environment.prod.ts
│   ├── index.html
│   ├── main.ts
│   ├── styles/                       # Global styles (scss)
│   │   └── styles.scss
│   └── theme/                        # Theme (dark, light, tokens)

├── angular.json
├── tsconfig.json
├── package.json
└── README.md
```

## ❌ Forbidden Practices

- ❌ Do NOT place business logic in UI components (use services).
- ❌ Do NOT duplicate pipes/directives (put shared ones in `shared/`).
- ❌ Do NOT inject services directly in feature components without providing them via the module when isolated scope is required.
- ❌ Do NOT call HTTP inside components — always use services.
- ❌ Do NOT create a feature module without lazy loading if it grows large.
