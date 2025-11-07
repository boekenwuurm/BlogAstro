# Boekenwuurm — Personal Blog (Astro)

Hi — this is the personal blog/source for boekenwuurm.nl. 
It’s an Astro site with a small, focused theme: writing, projects and things I tinker with.
It loads from wordpress.

## Quick links
- Project config: [astro.config.mjs](astro.config.mjs)  
- Home page that lists posts: [src/pages/index.astro](src/pages/index.astro)  
- About page and hero image: [src/pages/about.astro](src/pages/about.astro) and [src/assets/blog-placeholder-about.xcf](src/assets/blog-placeholder-about.xcf)  
- Where posts are fetched: [`getPosts`](src/lib/wordpress.ts)  
- Content collections config: [src/content.config.ts](src/content.config.ts)  
- Package metadata & scripts: [package.json](package.json)  
- TypeScript config: [tsconfig.json](tsconfig.json)

## Install and run (local)
1. Install dependencies:
   ```sh
   npm install
   ```
   (pnpm is available too — this repo includes a `pnpm-lock.yaml`.)

2. Start the dev server:
   ```sh
   npm run dev
   ```
   Open http://localhost:4321

3. Build for production:
   ```sh
   npm run build
   npm run preview
   ```

## Project structure 
├── public/ — static files served as-is
├── src/
│   ├── pages/ — site routes ([index.astro](src/pages/index.astro), [about.astro](src/pages/about.astro))
│   ├── components/ — reusable UI components
│   ├── layouts/ — page layouts (used by pages above)
│   ├── assets/ — images and source artwork ([blog-placeholder-about.xcf](src/assets/blog-placeholder-about.xcf))
│   ├── lib/ — small scripts and fetchers (e.g. [`getPosts`](src/lib/wordpress.ts))
│   ├── styles/ — global and component styles
│   ├── types/ — project types
├── astro.config.mjs
├── README.md
├── package.json
└── tsconfig.json

How posts arrive on the homepage
- The homepage imports [`getPosts`](src/lib/wordpress.ts) and renders posts returned by your WordPress instance. See [src/pages/index.astro](src/pages/index.astro) to tweak rendering or image handling.


Astro looks for `.astro` or `.md` files in the `src/pages/` directory. Each page is exposed as a route based on its file name.

There's nothing special about `src/components/`, but that's where we like to put any Astro/React/Vue/Svelte/Preact components.

The `src/content/` directory contains "collections" of related Markdown and MDX documents. Use `getCollection()` to retrieve posts from `src/content/blog/`, and type-check your frontmatter using an optional schema. See [Astro's Content Collections docs](https://docs.astro.build/en/guides/content-collections/) to learn more.

Any static assets, like images, can be placed in the `public/` directory.

## Commands

All commands are run from the root of the project, from a terminal:

| Command                   | Action                                           |
| :------------------------ | :----------------------------------------------- |
| `npm install`             | Installs dependencies                            |
| `npm run dev`             | Starts local dev server at `localhost:4321`      |
| `npm run build`           | Build your production site to `./dist/`          |
| `npm run preview`         | Preview your build locally, before deploying     |
| `npm run astro ...`       | Run CLI commands like `astro add`, `astro check` |
| `npm run astro -- --help` | Get help using the Astro CLI                     |

## Want to learn more?

Check out [our documentation](https://docs.astro.build) or jump into our [Discord server](https://astro.build/chat).

## Credit

This theme is based off of the lovely [Bear Blog](https://github.com/HermanMartinus/bearblog/).
