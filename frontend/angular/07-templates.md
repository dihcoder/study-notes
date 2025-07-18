## 🟠 Angular Template Syntax

### Loops in Templates
- New syntax: `@for`
    ```html
    <!-- Template HTML -->
    @for (item of listItems; track item) {
        <p>{{ item }}</p>
    }
    ```
- Old syntax: `*ngFor`
    ```html
    <!-- Template HTML -->
    <p *ngFor="let item of listItems">{{ item }}</p>
    ```

### Conditionals in Templates
- New syntax: `@if`
    ```html
    <!-- Template HTML -->
    @if (showTitle) {
    <h1>My Title</h1>
    } @else {
    <p>Title not shown</p>
    }
    ```
- Old syntax: `*ngIf`
    ```html
        <!-- Template HTML -->
        <h1 *ngIf="showTitle">My Title</h1>
        <p *ngIf="!showTitle">Title not shown</p>
    ```
