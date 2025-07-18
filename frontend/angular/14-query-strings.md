## 🟠 Using Query Strings in Angular

In Angular, you can access and manipulate query strings (URL parameters) using the `ActivatedRoute` and `Router` services.

---

### Reading query strings

Use `ActivatedRoute` to subscribe to changes in query parameters:

```ts
// Typescript
import { ActivatedRoute } from '@angular/router';

constructor(private route: ActivatedRoute) {}

ngOnInit() {
    this.route.queryParams.subscribe(params => {
        const courseId = params['course'];
        console.log(courseId); // Example: "2"
    });
}
```

---

### Updating or setting query strings

Use the `Router` service to navigate with updated query parameters:

```ts
// Typescript
import { Router } from '@angular/router';

constructor(private router: Router) {}

updateQuery() {
    this.router.navigate([], {
        queryParams: { course: '5', theme: 'dark' },
        queryParamsHandling: 'merge', // 'merge' keeps existing params; use 'preserve' or omit to replace all
    });
}
```

You can also remove a query parameter by setting it to `null`:

```ts
// Typescript
this.router.navigate([], {
    queryParams: { course: null },
    queryParamsHandling: 'merge'
});
```

---

### 🛠️ Common use cases

* `?page=2&limit=10` → Pagination
* `?category=electronics` → Product filtering
* `?utm_source=google` → Marketing tracking
* `?redirect=/dashboard` → Post-login redirection
* `?theme=dark&lang=en` → UI preferences

> 📌 Query strings are useful for passing temporary or shareable state via the URL without modifying app state directly.
