## 🟠 Angular CLI

Is a command-line tool used to initialize, develop, scaffold, and maintain Angular applications. It streamlines the development workflow by providing a set of commands that automate common tasks, eliminating the need for manual setup and configuration. 

### Installation

```bash
npm install -g @angular/cli
ng --version
```

### Creating and Running an App

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

### Component/Service Generation

```bash
ng g c component-name
ng g c directory/component-name
ng g s services/service-name
```