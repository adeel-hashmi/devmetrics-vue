# 🏗 Architecture & Mental Model

This project abandons the traditional "monolith" `src/components` folder structure in favor of a **Feature-Sliced Design (FSD)** inspired architecture. This ensures high scalability, predictable dependency graphs, and clear separation of business logic from UI rendering.

## Layer Breakdown

1. **`app/` (Initialization Layer):** Contains the application's entry points, global router configuration, and root store initialization. The "glue" that binds the framework.
2. **`pages/` (Routing Layer):** Components here correspond strictly to URL routes. They do not contain heavy logic; instead, they compose Layouts and Feature modules.
3. **`layouts/` (Structural Layer):** Reusable page wrappers (e.g., structural shells with Navigation) using Vue's `<slot>` mechanism to project content.
4. **`features/` (Domain Layer):** The core business logic resides here, grouped by domain (e.g., `github`). Each feature encapsulates its own API services, Pinia stores, domain-bound UI components, and TypeScript interfaces.
5. **`shared/` (Infrastructure Layer):** Strictly generic, domain-agnostic code. Includes atomic UI components (Buttons, Inputs), global utilities, and cross-cutting composables.

## Key Design Decisions (Vue vs React)

- **State Management:** Pinia is utilized per-feature using the Composition API `Setup Store` pattern. Stores act as localized, reactive data caches rather than a single monolithic state tree (like Redux).
- **Component Typology:** \* _Smart Components_ (Feature-bound) inject stores and handle business events.
  - _Dumb Components_ (Shared UI) rely exclusively on Vue `defineProps` and `defineEmits` with no side effects.
- **Reactivity:** Strict usage of Vue 3's Composition API (`<script setup>`) with `ref` and `computed` for precise proxy-based reactivity tracking, avoiding React-style render cycle manual memoization.
