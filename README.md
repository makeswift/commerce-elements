# Commerce Elements

A collection of modern, accessible commerce UI components built with React, TypeScript, and Tailwind CSS.

## Requirements

- React 18+ or 19+
- Tailwind CSS 3+

## Installation

```bash
npm install commerce-elements
# or
yarn add commerce-elements
# or
pnpm add commerce-elements
```

Install the optional Tailwind plugins (recommended):

```bash
npm install -D @tailwindcss/container-queries @tailwindcss/typography tailwindcss-animate
```

## Setup

### 1. Configure Tailwind

Add the Commerce Elements preset and content path to your `tailwind.config.js`:

```js
import commerceElements from 'commerce-elements/tailwind';

export default {
  presets: [commerceElements],
  content: [
    './src/**/*.{js,ts,jsx,tsx}',
    './node_modules/commerce-elements/src/**/*.{js,ts,jsx,tsx}', // Add this line
  ],
  // ... your other config
};
```

### 2. Import Base Styles

Import the CSS variables in your main CSS file **after** your Tailwind directives:

```css
/* app.css or globals.css */
@tailwind base;
@tailwind components;
@tailwind utilities;

@import 'commerce-elements/styles';
```

Or import directly in your JavaScript/TypeScript:

```tsx
// main.tsx or App.tsx
import 'commerce-elements/styles';
```

### 3. Use Components

```tsx
import { Button } from 'commerce-elements';

function App() {
  return (
    <div>
      <Button variant="primary">Click me</Button>
      <Button variant="secondary" size="small">
        Small Button
      </Button>
    </div>
  );
}
```

## Using Tailwind Utilities

Once configured, you can use all the custom Tailwind utilities from Commerce Elements:

```tsx
<div className="bg-primary text-background">
  <h1 className="text-foreground font-heading">Hello World</h1>
  <p className="text-contrast-400">This uses the design system colors!</p>
</div>
```

**Available color utilities:**

- `bg-primary`, `text-primary`, `border-primary`
- `bg-accent`, `text-accent`, etc.
- `bg-success`, `bg-error`, `bg-warning`, `bg-info`
- `bg-background`, `bg-foreground`
- `bg-contrast-100` through `bg-contrast-500`

And many more custom utilities for typography, animations, and effects.

## Customization

Override CSS variables to customize the design system. You can do this in two ways:

**Option 1: Override after import**

```css
/* app.css */
@tailwind base;
@tailwind components;
@tailwind utilities;

@import 'commerce-elements/styles';

:root {
  --primary: 220 100% 50%; /* HSL: hue saturation lightness */
  --foreground: 0 0% 7%;
  --background: 0 0% 100%;
  /* ... override any variables */
}
```

**Option 2: Define before import** (your values take precedence)

```css
/* app.css */
@tailwind base;
@tailwind components;
@tailwind utilities;

:root {
  --primary: 220 100% 50%;
  /* ... your custom values */
}

@import 'commerce-elements/styles';
```

## Documentation

For detailed component documentation, examples, and interactive demos, visit our [Storybook](#) (coming soon).

## TypeScript

Full TypeScript support with included type definitions.

## License

MIT
