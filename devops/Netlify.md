# 🚀 Deploying Angular Applications on Netlify

This guide explains how to deploy an Angular application on [Netlify](https://www.netlify.com/), a free and easy-to-use platform for hosting static websites and SPAs.

---

## ✅ Prerequisites

- Node.js and Angular CLI installed
- Free Netlify account
- Angular project already created

---

## 🔧 Step 1: Build the Project

Before uploading to Netlify, you need to compile the Angular project for production:

```bash
ng build --configuration production
```

By default, the final files will be in the `dist/<project-name>/browser` folder.

---

## 📁 Step 2: Adjust the `baseHref` (optional, but recommended)

Open the `angular.json` file and add the `baseHref` option in:

```json
"options": {
  "baseHref": "/"
}
```

Or use the command with the flag:

```bash
ng build --configuration production --base-href "/"
```

---

## ☁️ Step 3: Deploy to Netlify via Git

1. Upload your project to GitHub, GitLab or Bitbucket

2. Go to [https://app.netlify.com](https://app.netlify.com)

3. Click on **"Add new site" > "Import an existing project"**

4. Connect to the repository

5. Configure:

   * **Base Directory**: `/`
   * **Build Command**: `ng build --configuration production`
   * **Publish Directory**: `dist/<nome-do-projeto>/browser`

6. Click **"Deploy Site"**

---

## ⚙️ Extra Tips

* For Angular routes to work correctly, create a `_redirects` file inside the `dist/<project>/browser` folder with the following content:

```
/*    /index.html   200
```

Or add this via **"Redirects and rewrites"** in the site settings in the Netlify dashboard.

---

## 🌐 After Deployment

* The site will be available on a free Netlify URL (`https://sitename.netlify.app`)
* You can set up a custom domain for free

---

## 📚 References

* [Official Netlify documentation](https://docs.netlify.com/)
* [Deploying SPAs on Netlify](https://docs.netlify.com/routing/redirects/)

---

# 🚀 Deploying Vite Applications on Netlify

## Local build with Vite, automatic deploy with Netlify

Vite generates your ready application in the `dist/` folder using:

```bash
npm run build
```

In Netlify, just configure:

- Build command: `npm run build`
- Publish directory: `dist`

## Deploy directly from GitHub with Netlify + Vite

If you connect your GitHub repository to Netlify. Then every time you do a `git push`, Netlify:

- Runs `npm install`
- Executes `npm run build`
- Publishes the contents of `dist/`

## Netlify Functions Compatibility

If your Vite application has serverless functions using Netlify Functions, you can use them normally.

**Example structure with functions:**

```pgsql
my-project/
├─ netlify/
│  └─ functions/
│     └─ hello.ts
├─ src/
├─ index.html
├─ vite.config.ts
├─ tsconfig.json
```

**In netlify.toml, you define:**

```toml
[build]
  command = "npm run build"
  publish = "dist"

[functions]
  directory = "netlify/functions"
```

**And access its functions with fetch on the frontend:**

```ts
fetch('/.netlify/functions/hello')
```

> Vite handles the frontend, Netlify hosts and executes the functions on the backend.
