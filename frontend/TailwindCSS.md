## TailwindCSS

```bash
# Install using Node.js
npm install -D tailwindcss@latest postcss@latest autoprefixer@latest

# Verify if it was installed (you must see 'tailwindcss' listed)
ls node_modules/.bin/

# Generate config files ('tailwind.config.js' and 'postcss.config.js')
npx tailwindcss init -p
```

```js
# tailwind.config.js

/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

```css
# src/style.css

@tailwind base;
@tailwind components;
@tailwind utilities;
```

```ts
# main.ts

import './style.css';
```
