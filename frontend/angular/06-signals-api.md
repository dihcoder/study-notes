## 🟠 Signals API

The `Signals API` is a reactive programming primitive designed to manage application state and enhance performance through fine-grained reactivity. Introduced in Angular 17, it provides a lightweight and intuitive way to handle data changes and optimize change detection.

### signal()

Creates a writable signal that holds a value and notifies its consumers when that value changes.

```ts
// Typescript
import { signal } from '@angular/core';

const count = signal(0); // Initialize a signal with value 0
count.set(1); // Update the signal's value
console.log(count()); // Read the signal's value
```

### computed()

Creates a read-only signal whose value is derived from other signals. It automatically re-evaluates when its dependencies change.

```ts
// Typescript
import { signal, computed } from '@angular/core';

const firstName = signal('John');
const lastName = signal('Doe');

const fullName = computed(() => `${firstName()} ${lastName()}`);

console.log(fullName()); // "John Doe"
```

### effect()

Allows execution of side effects in response to signal changes. Effects are useful for tasks like logging, synchronizing with localStorage, or interacting with third-party libraries.

```ts
// Typescript
import { signal, effect } from '@angular/core';

const message = signal('Hello');

effect(() => {
    console.log(`Message changed: ${message()}`);
});

message.set('World'); // Triggers the effect
```

### Data Binding with Signals

```ts
// Typescript
myVar = signal('value');
```

```html
<!-- Template HTML -->
<p>{{ myVar() }}</p>
```

### Counter Component Example

```ts
// Typescript
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

```html
<!-- Template HTML -->
<p>Counter value: {{ counterValue() }}</p>

<button (click)="increment()">Increment</button>
<button (click)="reset()">Reset</button>
<button (click)="decrement()">Decrement</button>
```
