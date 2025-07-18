## 🟠 Components, Services, Directives etc.

### Components

A `component` is a fundamental building block of an application, representing a self-contained and reusable part of the user interface (UI).

### Services

A `service` is a class that provides a specific piece of functionality or data to multiple components or other services within an application. Services are designed to encapsulate business logic, data fetching operations, or any other reusable code that is independent of the user interface.

### Directives

A `directive` is a class that adds behavior to elements in an Angular application. Essentially, directives are used to manipulate the Document Object Model (DOM) by modifying the appearance, structure, or behavior of elements, components, or other directives.

### RouterOutlet

The `RouterOutlet` is a directive that acts as a placeholder within a component's template. Its primary function is to dynamically load and display different components based on the current URL route.

### 🔗 Importing a Component

```ts
// Typescript
imports: [RouterOutlet, ChildComponent]
template: `<app-child />`
```