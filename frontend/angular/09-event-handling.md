## 🟠 Event Listeners

### Simple Events

```html
<!-- Template HTML -->
 <!-- (keyup) event for keyboard -->
<input type="text" (keyup)="keyUpHandler()">
```

```ts
// Typescript
keyUpHandler() {
  console.log("Key up!");
}
```

### Click Events

```html
<!-- Template HTML -->
<button (click)="onClick()">Sort User</button>
```

```ts
// Typescript
selectedUser = signal(DUMMY_USERS[randomIndex]);

onClick() {
  const randomIndex = Math.floor(Math.random() * DUMMY_USERS.length);
  this.selectedUser.set(DUMMY_USERS[randomIndex]);
}
```

### Events with $event object

```html
<!-- Template HMTL -->
<input type="text" (keyup)="keyUpHandler($event)">
```

```ts
// Typescript
keyUpHandler(event: KeyboardEvent) {
  console.log(`Key: ${event.key}`);
}
```
