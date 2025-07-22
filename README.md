# Nuxt Vapor Mode Demo

> Performance comparison between Vue 3.6 Vapor Mode and traditional VDOM rendering

A demo showcasing Vue's new Vapor Mode compilation with benchmark tests inspired by [js-framework-benchmark](https://github.com/krausest/js-framework-benchmark).

## Features

- Built on [Nuxt](https://nuxt.com/) with Vue 3.6 alpha
- [Vapor Mode](https://github.com/vuejs/core/releases/tag/v3.6.0-alpha.1) components with `<script setup vapor>`
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
- Bundle size (no VDOM runtime)so VDOM is still present
- Memory usage
- Rendering performance for large lists

> [!NOTE]
> This demo uses the interop plugin, so VDOM is still present.

> [!IMPORTANT]
> There are [some significant limitations](https://github.com/vuejs/core/releases/tag/v3.6.0-alpha.1) in the current alpha version of Vue 3.6 Vapor Mode, including no support for SSR hydration.

## License

Made with ❤️

Published under [MIT License](./LICENSE).
