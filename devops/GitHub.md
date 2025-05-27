# 🚀 Deploying Angular Projects to GitHub Pages

This guide walks you through deploying an Angular application to **GitHub Pages**, using the [`angular-cli-ghpages`](https://www.npmjs.com/package/angular-cli-ghpages) tool.

---

## ✅ Prerequisites

- Node.js and Angular CLI installed
- A GitHub repository created and linked to your project
- Project already built and tested locally

---

## 📦 Step 1: Install Deployment Package

Install the deployment package globally:

```bash
npm install -g angular-cli-ghpages
```

---

## 🛠️ Step 2: Set the `baseHref` in `angular.json`

Update the build configuration to include the correct base path:

```json
"baseHref": "/repo-name/"
```

Alternatively, pass it as a flag when building:

```bash
ng build --output-path=dist/repo-name/browser --base-href="/repo-name/"
```

> Replace `repo-name` with the name of your GitHub repository.

---

## 🚚 Step 3: Deploy to GitHub Pages

Run the following command to deploy the build:

```bash
npx angular-cli-ghpages --dir=dist/repo-name/browser
```

After that, your project should be live at:

```
https://your-username.github.io/repo-name
```

---

## 🔄 Restarting Deployment from Scratch

If needed, you can clear previous deployments and start fresh.

### Option 1: Reset using CLI

```bash
npx angular-cli-ghpages --dir=dist/repo-name --no-silent --no-skip-git
```

### Option 2: Manual Reset

```bash
git branch -D gh-pages
ng build --output-path=dist/repo-name/browser --base-href="/repo-name/"
npx angular-cli-ghpages --dir=dist/repo-name
```

---

## 📁 Special Case: Custom `outputPath`

If your `angular.json` has this structure:

```json
"outputPath": "dist/repo-name/web"
```

Follow these steps:

1. Delete the `gh-pages` branch locally and remotely:

```bash
git push origin --delete gh-pages
git branch -D gh-pages
```

2. Rebuild the project with the correct base-href:

```bash
ng build --base-href="/repo-name/"
```

3. Deploy using the correct directory:

```bash
npx angular-cli-ghpages --dir=dist/repo-name/web
```

---

## ⚙️ Final Step: Configure GitHub Pages

Go to your repository:

* Click **Settings** > **Pages**
* Under **"Deploy from a branch"**:

  * Select **Branch**: `gh-pages`
  * Select **Folder**: `/ (root)`
* Save

Your Angular app is now live! 🎉

---

## 📚 Resources

* [angular-cli-ghpages Documentation](https://www.npmjs.com/package/angular-cli-ghpages)
* [Angular Deployment Guide](https://angular.io/guide/deployment)
* [GitHub Pages Documentation](https://pages.github.com/)

---
