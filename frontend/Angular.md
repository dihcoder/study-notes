# 📘 Angular Summary (Latest Version)

A complete overview of modern Angular features, syntax, and tooling.

## 🟠 What is Angular

Angular is a TypeScript-based open-source web application framework developed and maintained by Google. It's primarily used for building dynamic and interactive single-page applications (SPAs) and offers a structured approach for developing large-scale applications.

### Framework vs. Library

Angular is a framework, which provides a complete structure and set of tools for building applications, whereas React is a JavaScript library that requires additional libraries and frameworks to build a complete application.

### TypeScript

Angular is written in TypeScript, a superset of JavaScript that adds static typing and other features, making it easier to manage and scale large projects.

### Single-Page Applications (SPAs)

Angular is designed to create SPAs, which are web applications that load a single HTML page and dynamically update content as the user interacts with it, providing a smoother user experience.

### Declarative Code

With Angular, `you write declarative code`. That means instead of manually updating the DOM (imperative code), you define what the UI should look like based on the application state, and Angular automatically updates the DOM when that state changes.

### Component-Based Architecture

Angular uses a component-based architecture, where applications are built from reusable, independent components, promoting modularity and maintainability.

### Separation of Concerns

Angular embraces SoC at multiple levels through its architecture and tooling:
1. **Components** → Handle presentation (UI logic)
   - Each component has its own template (HTML), style (CSS or SCSS) and logic (TypeScript).
2. **Services** → Handle business logic & data
   - Services are singleton classes designed to: fetch or update data, perform calculations and share logic between components.
4. **Routing Module** → Handles navigation and app structure
   - Routing configuration is separated from the component logic, allowing you to define paths, route guards, lazy loading, etc.
5. **Modules** → Organize features and app structure
   - Angular modules group related pieces together (components, services, pipes and directives).
6. **Directives and Pipes** → Handle DOM behavior and data formatting
   - They’re small, reusable units that isolate small concerns like: Show/hide logic and data transformation (e.g., currency or date formatting).

### Features

Angular includes a variety of features like routing, form management, client-server communication, and a suite of developer tools, all integrated into the framework. 

### Scalability

Angular is well-suited for building both small and large, enterprise-level applications, making it a popular choice for various projects. 

---

## 🟠 Angular Major Versions – Summary Table

<br/>

| Version      | Release Date | Key Highlights                                                                 |
|--------------|--------------|---------------------------------------------------------------------------------|
| Angular 2    | Sep 2016     | Rewrite from AngularJS, TypeScript, component-based architecture               |
| Angular 4    | Mar 2017     | Skipped v3, smaller bundles, improved Angular Universal                        |
| Angular 5    | Nov 2017     | Faster compiler, new HttpClient, PWA support                                   |
| Angular 6    | May 2018     | `ng add`, `ng update`, Angular Elements, RxJS 6                                |
| Angular 7    | Oct 2018     | Virtual scrolling, drag-drop (CDK), CLI prompts                                |
| Angular 8    | May 2019     | Ivy preview, differential loading, Web Workers                                |
| Angular 9    | Feb 2020     | Ivy default, smaller bundles, improved type checking                           |
| Angular 10   | Jun 2020     | TypeScript 3.9, `tsconfig.base.json`, ecosystem focus                          |
| Angular 11   | Nov 2020     | HMR, Webpack 5 (experimental), test harnesses                                  |
| Angular 12   | May 2021     | Full Ivy, removed View Engine, ESLint support                                  |
| Angular 13   | Nov 2021     | Removed View Engine completely, faster testing, TS 4.4                         |
| **Angular 14**   | **Jun 2022**     | `Standalone components` (preview), typed forms, improved CLI                    |
| Angular 15   | Nov 2022     | Standalone APIs stable, better lazy loading, DX improvements                   |
| **Angular 16**   | **May 2023**     | Introduced `Signals`, SSR hydration, finer change detection                      |
| Angular 17   | Nov 2023     | Built-in `@if`/`@for`, full hydration for SSR, Signals in routing              |
| Angular 18   | May 2024     | Optional Zone.js, expanded Signals API, performance and hydration updates      |

---

## 🟠 Angular CLI

Is a command-line tool used to initialize, develop, scaffold, and maintain Angular applications. It streamlines the development workflow by providing a set of commands that automate common tasks, eliminating the need for manual setup and configuration. 

### Installation

```bash
npm install -g @angular/cli
ng --version
````

---

### Creating and Running an Angular App

```bash
ng new app-name
# or
ng new app-name --inline-style --inline-template --skip-tests
# or
ng new projet-name --directory=.
# or
ng new app-name --directory=. --skip-git
ng serve
```

---

## 🟠 Components, Services, Directives etc.

A `component` is a fundamental building block of an application, representing a self-contained and reusable part of the user interface (UI).

A `service` is a class that provides a specific piece of functionality or data to multiple components or other services within an application. Services are designed to encapsulate business logic, data fetching operations, or any other reusable code that is independent of the user interface.

A `directive` is a class that adds behavior to elements in an Angular application. Essentially, directives are used to manipulate the Document Object Model (DOM) by modifying the appearance, structure, or behavior of elements, components, or other directives.

The `RouterOutlet` is a directive that acts as a placeholder within a component's template. Its primary function is to dynamically load and display different components based on the current URL route. 

### Component/Service Generation

```bash
ng g c component-name
ng g c directory/component-name
ng g s services/service-name
```
---

### 🔗 Importing a Component

```ts
// app.component.ts
imports: [RouterOutlet, ChildComponent]
template: `<app-child />`
```

---

## 🟠 Dynamic Content

### *`String Interpolation`*

Is a one-way data-binding technique used to display dynamic data from a component's TypeScript code within an HTML template. It provides a simple and secure way to embed expressions directly into the HTML, making the displayed content reactive to changes in the component's data. 

```html
<!-- component-name.component.html -->
<p>{{ item }}</p>
```

---

## 🟠 Property Binding

Is a one-way data binding mechanism that allows you to set the properties of HTML elements or Angular directives dynamically based on values from your component's TypeScript code.

```html
<!-- component-name.component.html -->
<img
   [src]="user.imageUrl"
   [alt]="user.imageAlt"
/>
```

---

## Getter

A getter is a special type of method in a TypeScript class that allows you to define a property whose value is calculated or derived when it is accessed, rather than being a stored value. It provides a way to control how a property's value is retrieved.

```ts
export class UserComponent {
  selectedUser = DUMMY_USERS[randomIndex];
  get imagePath() {
    return 'assets/users/' + this.selectedUser.avatar;
  }
}
```

---

## 🟠 Signals API

The `Signals API` is a reactive programming primitive designed to manage application state and enhance performance through fine-grained reactivity. Introduced in Angular 17, it provides a lightweight and intuitive way to handle data changes and optimize change detection.

### Key components of the Signals API include:

- `signal()`: Creates a writable signal that holds a value and notifies its consumers when that value changes.
  ```ts
    import { signal } from '@angular/core';

    const count = signal(0); // Initialize a signal with value 0
    count.set(1); // Update the signal's value
    console.log(count()); // Read the signal's value
  ```

- `computed()`: Creates a read-only signal whose value is derived from other signals. It automatically re-evaluates when its dependencies change.
  ```ts
    import { signal, computed } from '@angular/core';

    const firstName = signal('John');
    const lastName = signal('Doe');
    const fullName = computed(() => `${firstName()} ${lastName()}`);
    console.log(fullName()); // "John Doe"
  ```

- `effect()`: Allows execution of side effects in response to signal changes. Effects are useful for tasks like logging, synchronizing with localStorage, or interacting with third-party libraries.
  ```ts
    import { signal, effect } from '@angular/core';

    const message = signal('Hello');
    effect(() => {
      console.log(`Message changed: ${message()}`);
    });
    message.set('World'); // Triggers the effect
  ```

---

## 🟠 Loops in Templates

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

## 🟠 Conditionals in Templates

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

## 🟠 Dynamic Attributes

```html
<button [attr.aria-label]="elementLabel"></button>
<button [id]="myId"></button>
<button [class]="myClass"></button>
```

---

## 🟠 Data Binding with Signals

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

## 🟠 Passing Data Between Components

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

## 🟠 Event Listeners

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

## 🟠 Counter Component with Signals

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

## 🟠 Routing in Angular

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

## 🟠 Angular Services

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

## 🟠 Making HTTP Calls

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

## 🟠 Deploy to Netlify

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

## 🟠 TailwindCSS Setup

1. Install @tailwindcss/postcss and its peer dependencies via npm.
   ```bash
   npm install tailwindcss @tailwindcss/postcss postcss --force
   ```
2. Configure PostCSS Plugins: Create a `.postcssrc.json` file in the root of your project and add the `@tailwindcss/postcss` plugin to your PostCSS configuration.
   ```json
   // .postcssrc.json
   {
     "plugins": {
       "@tailwindcss/postcss": {}
     }
   }
   ```
3. Import Tailwind CSS: Add an `@import` to `./src/styles.css` that imports Tailwind CSS.
   ```css
   /* styles.css */
   @import "tailwindcss";
   ```

---

> 📌 **Pro Tip:** Prefer using standalone components with the `imports` array instead of NgModules in modern Angular apps.

