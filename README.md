# SvelteKit Project Boilerplate

## Creating a project

This boilerplate handles the project creation step. If you want to create a new project and not use this boilerplate, the commands to do so are as follows:

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

> To install `shadcn-svelte` (this assumes you are using the default location of Svelte's \$lib directory, if you want to change this location, jump ahead to [Changing the \$lib directory](#changing-the-lib-directory)):

```bash
npx shadcn-svelte@latest init
```

### Changing the \$lib directory

If you are not using the default alias $lib, you'll need to update your `svelte.config.js` file to include those aliases.

```js
const config = {
  // ... other config
  kit: {
    // ... other config
    alias: {
      "@/*": "./path/to/lib/*",
    },
  },
};
```

### Installing `shadcn-svelte` components

`shadcn-svelte` does not install all of its components by default. Components are opt-in, meaning any component that is utilized in the project must be installed explicity. These components are installed into the `$lib/components` directory.

> Installing the Button component:

```bash
npx shadcn-svelte@latest add button
```

> Installing the Sheet component:

```bash
npx shadcn-svelte@latest add sheet
```

The install command for each components can be found on that component's page in the `shadcn-svelte` docs.

### Custom Styling

This boilerplate uses `tailwindcss`. There is not install step required, as it can be selected during the SvelteKit startup process. A number of custom properties are added by default when installing `shadcn-svelte`. These properties can all be add/removed/edited as needed.

In the `app.css` file, the `@theme` block is used to customize `tailwind` properties.

#### Customizing Fonts

> Fonts can be loaded from a local file (Ex. woff2) or from a link (Ex. Google Fonts), and then are utilized in the `@theme` block:

```css
    --font-primary: "Poppins", sans-serif;
    --font-secondary: "Urbanist", sans-serif;
```

##### Loading Fonts from Google Fonts

> The import url for any fonts must be included as the first entry in the file, this example imports the `Poppins` and `Urbanist` fonts:

```css
@import url("https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Urbanist:ital,wght@0,100..900;1,100..900&display=swap")
```

##### Loading Fonts from a Local File

> Local fonts must be imported using the `@font-face` block:

```css
@font-face {
  font-family: Poppins;
  font-style: normal;
  font-weight: 200 700;
  font-display: swap;
  src: url("/fonts/Poppins.woff2") format("woff2");
}
```

### Layout Choices

This boilerplate predefines a basic header and footer, which is present on every page. The Header also comes predefined with some navigation links and some common pages. This header has been styles to collapse into a side sheet when the screen size in decreased. As with everything else, this is all customizable.

### Icons from `lucide-svelte`

The icon library of choice for this boilerplate is [`lucide-svelte`](https://lucide.dev/icons/)

> `lucide-svelte` should install automatically when the initial `npm init` command is run, but if it doesn't:

```bash
npm install @lucide/svelte
```
