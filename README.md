# SvelteKit Project Boilerplate

Everything you need to build a Svelte project, powered by [`sv`](https://github.com/sveltejs/cli).

## Creating a project

If you're seeing this, you've probably already done this step. Congrats!

```bash
# create a new project in the current directory
npx sv create

# create a new project in my-app
npx sv create my-app
```

## Developing

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

To create a production version of your app:

```bash
npm run build
```

You can preview the production build with `npm run preview`.

> To deploy your app, you may need to install an [adapter](https://svelte.dev/docs/kit/adapters) for your target environment.

## Custom Elements

### Components from [shadcn-svelte](https://www.shadcn-svelte.com/)

`shadcn-svelte` is a library which provides a robust set of unstyled components that are ready to use as-is or to be styles using tailwindcss. The use of `shadcn-svelte` is a personal choice and can be opted out of completely, or replaced with any other components library.

> To install `shadcn-svelte` (this assumes you are using the default location of Svelte's \$lib directory, if you want to change this location, jump ahead to [Changing the \$lib directory]()):

```bash
npx shadcn-svelte@latest init
```

### Changing the \$lib directory
