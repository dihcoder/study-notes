## 🟠 Deploying Angular on Netlify

### Build for Production

```bash
ng build --configuration=production
```

### Redirects

Add a `_redirects` file

```
/* /index.html 200
```

Include `src/_redirects` in `angular.json` under `assets`.

### Environment Variables

Create `.env`:

```env
NG_APP_BASE_URL=http://localhost:5200
```

Update `environment.ts` and `environment.prod.ts`:

```ts
export const environment = {
  Url: process.env['NG_APP_BASE_URL']
};
```

Install env loader:

```bash
ng add @ngx-env/builder
```

### Netlify Settings

* Build Command: `ng build`
* Publish Directory: `dist/client/browser`
* Environment Variables: `NG_APP_BASE_URL`
