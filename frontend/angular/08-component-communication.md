## 🟠 Passing Data Between Components

### @Input (Parent → Child)

```ts
// child.component.ts
@Input() data!: string;
```

```html
<!-- parent.component.html -->
<app-child [data]="parentMessage" />
```

### @Output (Child → Parent)

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

### Input Signals (Parent → Child)

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
