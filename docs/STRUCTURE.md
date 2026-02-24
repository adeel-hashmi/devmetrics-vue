# 📁 Directory Structure

Below is the complete topological map of our `src/` directory implementing Feature-Sliced Design.

```text
src/
├── app/                        # 1. Application Layer (The Glue)
│   ├── main.ts
│   ├── App.vue
│   ├── router/
│   └── store/
│
├── pages/                      # 2. Routing Layer (Nuxt-like Pages)
│   └── Home.vue
│
├── layouts/                    # 3. Layout Layer
│   └── DefaultLayout.vue
│
├── features/                   # 4. Domain Layer (Business Logic)
│   └── github/                 # Domain: GitHub Analytics
│       ├── api/                # Axios/Fetch services specific to GitHub
│       ├── components/         # Smart/Domain-bound components
│       ├── composables/        # Domain-specific logic
│       ├── store/              # Pinia state module
│       └── types/              # TypeScript interfaces for DTOs
│
├── shared/                     # 5. Shared/Cross-Cutting Layer
│   ├── components/ui/          # Dumb, highly reusable atomic UI
│   ├── composables/            # Global composables
│   ├── utils/                  # Pure JS/TS functions
│   └── types/                  # Global types
│
├── assets/                     # 6. Static Assets
└── styles/                     # 7. Global CSS/SCSS
```
