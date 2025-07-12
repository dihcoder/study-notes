# 📘 Angular Summary (Latest Version)

A complete overview of modern Angular features, syntax, and tooling.

## 🚀 Install Angular CLI

```bash
npm install -g @angular/cli
ng --version
````

---

## 🏗 Creating and Running an Angular App

```bash
ng new app-name
# or
ng new app-name --inline-style --inline-template --skip-tests
# or
ng new app-name --directory=. --skip-git
ng serve
```

---

## 📦 Generate Components, Services, etc.

```bash
ng g c component-name
ng g c directory/component-name
ng g s services/service-name
```

---

## 🔗 Importing a Component

```ts
// app.component.ts
imports: [RouterOutlet, ChildComponent]
template: `<app-child />`
```

---

## 🧵 String Interpolation

```html
// _.component.html
<p>{{ item }}</p>
```

---

## 🧵 Getter

```ts
export class UserComponent {
  selectedUser = DUMMY_USERS[randomIndex];
  get imagePath() {
    return 'assets/users/' + this.selectedUser.avatar;
  }
}
```
---

## 🧵 Computed Function

Is meant to be used with signals

```ts
import { computed } from '@angular/core'
export class UserComponent {
  selectedUser = signal(DUMMY_USERS[randomIndex]);
  imagePath = computed(() => 'assets/users/' + this.selectedUser().avatar);
}
```

---

## 🔁 Loops in Templates

### ✅ New Syntax

```html
@for (item of listItems; track item) {
  <p>{{ item }}</p>
}
```

### 🕰 Older Syntax

```html
<p *ngFor="let item of listItems">{{ item }}</p>
```

---

## ❓ Conditionals in Templates

### ✅ New Syntax

```html
@if (showTitle) {
  <h1>My Title</h1>
} @else {
  <p>Title not shown</p>
}
```

### 🕰 Older Syntax

```html
<h1 *ngIf="showTitle">My Title</h1>
<p *ngIf="!showTitle">Title not shown</p>
```

---

## 🧬 Property Binding

```html
<img [src]="user.imageUrl" />
```

---

## 🧬 Dynamic Attributes

```html
<button [attr.aria-label]="elementLabel"></button>
<button [id]="myId"></button>
<button [class]="myClass"></button>
```

---

## 🔄 Data Binding with Signals

### Basic Signal Binding

```ts
myVar = signal('value');
```

```html
<p>{{ myVar() }}</p>
```

### Input Signal from Parent

```ts
// child.component.ts
childVar = input('default');
```

```html
<!-- child.component.html -->
<p>{{ childVar }}</p>

<!-- parent.component.html -->
<app-child [childVar]="parentVar()" />
```

---

## 📤 Passing Data Between Components

### Parent ➡️ Child - `@Input`

```ts
// child.component.ts
@Input() data!: string;
```

```html
<!-- parent.component.html -->
<app-child [data]="parentMessage" />
```

### Child ➡️ Parent - `@Output`

```ts
// child.component.ts
@Output() eventEmitter = new EventEmitter<string>();
submit() {
  this.eventEmitter.emit('thanks');
}
```

```html
<!-- child.component.html -->
<button (click)="submit()">Click</button>

<!-- parent.component.html -->
<app-child (eventEmitter)="login($event)"></app-child>
```

---

## 🖱 Event Listeners

### Simple Event

```html
<input type="text" (keyup)="keyUpHandler()">
```

```ts
keyUpHandler() {
  console.log("Key up!");
}
```

### Click Event

```html
<button (click)="onClick()">Sort User</button>
```

```ts
selectedUser = signal(DUMMY_USERS[randomIndex]);
onClick() {
  const randomIndex = Math.floor(Math.random() * DUMMY_USERS.length);
  this.selectedUser.set(DUMMY_USERS[randomIndex]);
}
```

### Event With Object

```html
<input type="text" (keyup)="keyUpHandler($event)">
```

```ts
keyUpHandler(event: KeyboardEvent) {
  console.log(`Key: ${event.key}`);
}
```

---

## 🧮 Counter Component with Signals

```bash
ng g c components/counter
```

### counter.component.ts

```ts
counterValue = signal(0);

increment() {
  this.counterValue.update(val => val + 1);
}

decrement() {
  this.counterValue.update(val => val - 1);
}

reset() {
  this.counterValue.set(0);
}
```

### counter.component.html

```html
<p>Counter value: {{ counterValue() }}</p>
<button (click)="increment()">Increment</button>
<button (click)="reset()">Reset</button>
<button (click)="decrement()">Decrement</button>
```

---

## 🧭 Routing in Angular

### Immediate Loading

```ts
export const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'about', component: AboutComponent }
];
```

### Lazy Loading with `loadComponent`

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

### router-outlet and HeaderComponent Example

```ts
// app.component.ts
imports: [RouterOutlet, HeaderComponent],
template: `
  <app-header />
  <main><router-outlet /></main>
`
```

```ts
// header.component.ts
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

---

## 🧰 Angular Services

### Creating a Service

```bash
ng g s services/todos
```

### todos.service.ts

```ts
@Injectable({ providedIn: 'root' })
export class TodosService {
  todoItems: Todo[] = [
    { id: 0, userId: 1, completed: false, title: 'Go shopping' },
    { id: 1, userId: 1, completed: false, title: 'Mow the grass' }
  ];
}
```

### todos.component.ts (With Signals)

```ts
todoItems = signal<Todo[]>([]);

ngOnInit() {
  this.todoItems.set(this.todoService.todoItems);
}
```

---

## 🌐 Making HTTP Calls

```ts
import { HttpClient } from '@angular/common/http';

@Component({...})
export class MyComponent {
  constructor(private http: HttpClient) {}

  ngOnInit() {
    this.http.get('/api/data').subscribe(console.log);
  }
}
```

```ts
// app.config.ts
provideHttpClient()
```

---

## 🌍 Deploy to Netlify

### 1. Build production

```bash
ng build --configuration=production
```

### 2. Add `_redirects` file

```
/* /index.html 200
```

Include `src/_redirects` in `angular.json` under `assets`.

### 3. Set up environment

Create `.env`:

```
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

### 4. Netlify Settings

* Build Command: `ng build`
* Publish Directory: `dist/client/browser`
* Environment Variables: `NG_APP_BASE_URL`

---

## 🎨 TailwindCSS Setup

```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init
```

Update `tailwind.config.js` and add Tailwind directives to `styles.css`.

---

> 📌 **Pro Tip:** Prefer using standalone components with the `imports` array instead of NgModules in modern Angular apps.

