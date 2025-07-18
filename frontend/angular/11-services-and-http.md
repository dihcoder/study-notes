## 🟠 Angular Services

### Creating Services

```bash
ng g s services/serviceName
```

### Injecting Services into Components

```ts
// SERVICE: todos.service.ts
@Injectable({ providedIn: 'root' })
export class TodosService {
  todoItems: Todo[] = [
    { id: 0, userId: 1, completed: false, title: 'Go shopping' },
    { id: 1, userId: 1, completed: false, title: 'Mow the grass' }
  ];
}
```

```ts
// COMPONENT: todos.component.ts
todoItems = signal<Todo[]>([]);

ngOnInit() {
  this.todoItems.set(this.todoService.todoItems);
}
```

### HTTP Calls with HttpClient

```ts
import { HttpClient } from '@angular/common/http';

@Component({...})
export class MyComponent {
  constructor(private http: HttpClient) {}

  ngOnInit() {
    this.http.get('/api/data').subscribe(console.log);
  }
}
```

```ts
// app.config.ts
provideHttpClient()
```
