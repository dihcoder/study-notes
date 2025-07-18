## 🟠 Data Binding in Angular

### String Interpolation

Is a one-way data-binding technique used to display dynamic data from a component's TypeScript code within an HTML template. It provides a simple and secure way to embed expressions directly into the HTML, making the displayed content reactive to changes in the component's data. 

```html
<!-- Template HTML -->
<p>{{ item }}</p>
```

### Property Binding

Is a one-way data binding mechanism that allows you to set the properties of HTML elements or Angular directives dynamically based on values from your component's TypeScript code.

```html
<!-- Template HTML -->
<img
   [src]="user.imageUrl"
   [alt]="user.imageAlt"
/>
```

### Attribute Binding

Attribute binding in Angular is a one-way data binding mechanism that allows you to set the value of an HTML element's attribute from a component's property. It is particularly useful when an HTML attribute does not have a corresponding DOM property, or when you need to manage specific attributes like aria-* for accessibility or colspan/rowspan in tables.

> OBS: Attributes are defined in the HTML and provide initial values for properties. Properties are part of the DOM and represent the current state of an element. For example, the value attribute of an <input> element sets its initial value, while the value property reflects the current value as the user interacts with it.

The syntax for attribute binding involves using square brackets `[]` around the attribute name, prefixed with `attr.`.

```html
<!-- Template HTML Syntax -->
<HTMLTag [attr.attribute_name]="template_expression" />

<!-- Example -->
<td [attr.colspan]="columnSpanValue">
  Content
</td>
```
In this example, `columnSpanValue` would be a property defined in your Angular component, and its value would dynamically set the colspan attribute of the `<td>` element. This enables dynamic control over HTML attributes based on your application's logic and data.

### Dynamic Attributes

```html
<!-- Template HTML -->
<button [attr.aria-label]="elementLabel"></button>
<button [id]="myId"></button>
<button [class]="myClass"></button>
```

### Getters

A getter is a special type of method in a TypeScript class that allows you to define a property whose value is calculated or derived when it is accessed, rather than being a stored value. It provides a way to control how a property's value is retrieved.

```ts
// Typescript
export class UserComponent {
  selectedUser = DUMMY_USERS[randomIndex];

  get imagePath() {
    return 'assets/users/' + this.selectedUser.avatar;
  }
}
```
