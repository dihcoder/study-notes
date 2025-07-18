## 🟠 About Angular

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
