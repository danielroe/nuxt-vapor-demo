# Nuxt Vapor Mode Demo

> Performance comparison between Vue 3.6 Vapor Mode and traditional VDOM rendering

A demo showcasing Vue's new Vapor Mode compilation with benchmark tests inspired by [js-framework-benchmark](https://github.com/krausest/js-framework-benchmark).

## Features

- Built on [Nuxt](https://nuxt.com/) with native Vapor Mode support ([nuxt/nuxt#35772](https://github.com/nuxt/nuxt/pull/35772) preview) enabled via `vue: { vapor: true }` in `nuxt.config.ts`; track [nuxt/nuxt#35759](https://github.com/nuxt/nuxt/pull/35759) for the upstream implementation
- [Vapor Mode](https://github.com/vuejs/core/releases/tag/v3.6.0-rc.1) components with `<script setup vapor>` (Vue 3.6 rc)
- Side-by-side performance comparison
- Benchmark operations: create, update, delete, swap rows
- Real-time performance measurements

## Try it out locally

```bash
# install dependencies
pnpm install

# serve in dev mode at localhost:3000
pnpm dev

# build for production
pnpm build

# preview in production mode
pnpm preview
```

## How to use

1. Toggle between Vapor and traditional Vue components
2. Run benchmark operations to compare performance
3. Observe execution times and rendering differences

## Technical notes

Vapor Mode enables direct DOM manipulation without Virtual DOM overhead, potentially improving:
- Bundle size (no VDOM runtime)
- Memory usage
- Rendering performance for large lists

> [!NOTE]
> This demo mixes Vapor and VDOM components, so Nuxt automatically installs Vue's interop plugin and the VDOM runtime is still present.

> [!IMPORTANT]
> Vapor Mode is [feature-complete in the Vue 3.6 RC](https://github.com/vuejs/core/releases/tag/v3.6.0-rc.1), including SSR hydration, but [some limitations remain](https://github.com/vuejs/core/releases/tag/v3.6.0-rc.1): no Options API support, and features that depend on VNodes or the component public instance proxy are unavailable in Vapor components.

## License

Made with ❤️

Published under [MIT License](./LICENSE).
