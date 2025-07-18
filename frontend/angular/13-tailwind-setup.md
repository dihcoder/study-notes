## 🟠 TailwindCSS Setup in Angular

1. Install Tailwind and its peer dependencies with npm
   ```bash
   npm install tailwindcss @tailwindcss/postcss postcss --force
   ```
2. Create `.postcssrc.json` file in the root of your project
   ```json
   {
     "plugins": {
       "@tailwindcss/postcss": {}
     }
   }
   ```
3. Import Tailwind in `styles.css`
   ```css
   /* styles.css */
   @import "tailwindcss";
   ```
