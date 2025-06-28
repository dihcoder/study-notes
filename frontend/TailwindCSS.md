## Install TailwindCSS using node

```bash
npm install -D tailwindcss postcss autoprefixer
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
