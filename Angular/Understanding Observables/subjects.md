# Subjects

Subjects are a recommended and more powerful alternative to event emitters in Angular, especially for cross-component communication through services, they provide more flexibility and efficiency

- We should use subjects when we need more active control over data emission, especially for cross-component communication

- Subjects are more efficient behind the scenes and can also be used with _rxjs operators_

- For component-level communication if we use @Output, we should continue using the Angular event emitters

- Always remember to unsubscribe from subjects when they are no longer needed to prevent memory leaks

So this code is for the Subject approach:

In `user.component.ts`:

We use the subject's _next method_ to emit values instead of _emit_ for event emitters

```
import { UserService } from '../user.service';

constructor(
  private route: ActivatedRoute,
  private userService: UserService) {}

onActivate() {
  // this.userService.activatedEmitter.emit(true);
  this.userService.activatedEmitter.next(true);
}

```

In `user.component.html`:
`<button class="btn btn-primary" (click)="onActivate()">Activate</button>`

In `user.service.ts`:
First import Subject from rxjs

Then create a new Subject, specifying the data type it will emit _Subject<boolean>_

```
import { EventEmitter, Injectable } from "@angular/core";
import { Subject } from "rxjs";

@Injectable({providedIn: 'root'})
export class UserService {
  // activatedEmitter =  new EventEmitter<boolean>();
  activatedEmitter = new Subject<boolean>();
}
```

In `app.component.ts`:
We subscribe to the subject to handle the emitted data

We also use _ngOnDestroy()_ to unsubscribe from subjects when they are no longer needed to prevent memory leaks

```
import { Component, OnDestroy, OnInit } from '@angular/core';
import { UserService } from './user.service';
import { Subscription } from 'rxjs';

export class AppComponent implements OnInit, OnDestroy {
  userActivated = false;
  private activatedSub: Subscription;

constructor(private userService: UserService) {}

ngOnInit() {
    this.activatedSub = this.userService.activatedEmitter.subscribe(didActivate => {
      this.userActivated = didActivate;
    });
  }
  ngOnDestroy(): void {
      this.activatedSub.unsubscribe();
  }
}
```

in `app.component.html`:

`<p *ngIf="userActivated">Activated!</p>`
