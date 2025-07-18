## 🟠 Routing in Angular

### Immediate Loading

```ts
export const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'about', component: AboutComponent }
];
```

### Lazy Loading

```ts
export const routes: Routes = [
  {
    path: '',
    pathMatch: 'full',
    loadComponent: () => import('./pages/home/home.component').then(m => m.HomeComponent)
  },
  {
    path: 'about',
    loadComponent: () => import('./pages/about/about.component').then(m => m.AboutComponent)
  }
];
```

### RouterOutlet and Header Example

```ts
// PARENT: app.component.ts
imports: [RouterOutlet, HeaderComponent],
template: `
  <app-header />
  <main><router-outlet /></main>
`
```

```ts
// CHILD: header.component.ts
imports: [RouterLink],
template: `
<header>
  <nav>
    <span routerLink="/">Home</span>
    <ul><li routerLink="/about">About</li></ul>
  </nav>
</header>
`
```
