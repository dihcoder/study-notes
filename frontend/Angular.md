# Angular Notes

## Install Angular CLI

```sh
npm install -g @angular/cli
ng --version
```

## Creating an Angular App

```sh
ng new app-name
ng serve
```

## Importing a Component
```sh
ng g c child
```

```ts
imports: [RouterOutlet, ChildComponent]
template: `<app-child />`
```

## Dynamic Attributes

```html
<button [attr.aria-label]="elementLabel"></button>
<button [id]="myId"></button>
<button [class]="myClass"></button>
```

## Conditionals in Angular Template

### New Syntax
```html
@if (showTitle) {
  <h1>My Title</h1>
} @else {
  <p>Title not shown</p>
}
```

### Older Syntax
```html
<h1 *ngIf="showTitle">My Title</h1>
<p *ngIf="!showTitle">Title not shown</p>
```

## Loops in Angular Template

### New Syntax
```html
@for (item of listItems; track item) {
  <p>{{ item }}</p>
}
```

### Older Syntax
```html
<p *ngFor="let item of listItems">{{ item }}</p>
```

## Passing Data Between Components

### @Input - Parent to Child

#### `child.component.ts`
```ts
import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-child',
  template: '<p>{{ data }}</p>'
})
export class ChildComponent {
  @Input() data!: string;
}
```

#### `parent.component.ts`
```ts
export class ParentComponent {
  parentMessage = 'Hello from Parent';
}
```

#### `parent.component.html`
```html
<app-child [data]="parentMessage"></app-child>
```

### @Output - Child to Parent via EventEmitter

#### `child.component.ts`
```ts
import { Component, EventEmitter, Output } from '@angular/core';

@Component({
  selector: 'app-child',
  template: '<button (click)="submit()">Click</button>'
})
export class ChildComponent {
  @Output() eventEmitter = new EventEmitter<string>();

  submit() {
    this.eventEmitter.emit("thanks");
  }
}
```

#### `parent.component.ts`
```ts
export class ParentComponent {
  login(event: string) {
    console.log(event);
  }
}
```

#### `parent.component.html`
```html
<app-child (eventEmitter)="login($event)"></app-child>
```

## Event Listeners in Angular

### Call a function on `keyup`

#### `_.component.html`
```html
<input type="text" (keyup)="keyUpHandler()">
```

#### `_.component.ts`
```ts
export class Component {
  keyUpHandler() {
    console.log("Key up!");
  }
}
```

## Creating a Counter Component

```sh
ng g c components/counter
```

#### `counter.component.html`
```html
<p>Counter value: {{ counterValue() }}</p>
<div>
    <button (click)="increment()">Increment</button>
    <button (click)="reset()">Reset</button>
    <button (click)="decrement()">Decrement</button>
</div>
```

#### `counter.component.ts`
```ts
import { Component, signal } from '@angular/core';

@Component({
  selector: 'app-counter',
  templateUrl: './counter.component.html',
  styleUrls: ['./counter.component.css']
})
export class CounterComponent {
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
}
```

## Routing in Angular

Angular is a SPA framework. Routes help define different pages while only loading bundles related to the accessed route.

### Immediate Loading:
```ts
export const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'about', component: AboutComponent }
];
```

### Lazy Loading:
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

## Angular Services

Angular Services are used to encapsulate data, make HTTP calls, or perform any task that’s not directly related to data rendering.

```sh
ng g s services/serviceName
ng g s services/todos
```

### Example:

#### `src/app/model/todo.type.ts`
```ts
export type Todo = {
  id: number;
  userId: number;
  completed: boolean;
  title: string;
}
```

#### `todos.service.ts`
```ts
import { Injectable } from '@angular/core';
import { Todo } from '../model/todo.type';
@Injectable({
  providedIn: 'root'
})
export class TodosService {
  todoItems: Array<Todo> = [
    {
      id: 0,
      userId: 1,
      completed: false,
      title: 'Go shopping'
    },
    {
      id: 1,
      userId: 1,
      completed: false,
      title: 'Mow the grass'
    }
  ];
  constructor() {}
}
```

## Making HTTP Calls with Angular Services

- Provide HTTP module/providers in the app config using `provideHttpClient()`
- Inject the `HttpClient` service
- Use the HTTP methods