# Navigating Programmatically

- We can programmatically navigate to a different route using the Angular router

- First we inject the router into our component by adding it to the constructor then in our method we use the navigate method provided by the router to navigate to a new route
  - The navigate method takes an argument, which is an array defining the path segments of the new route

in `home.component.ts`:

```
import { Component, OnInit } from '@angular/core';

import { Router } from '@angular/router';

@Component({
  selector: 'app-home',
  templateUrl: './home.component.html',
  styleUrls: ['./home.component.css']
})
export class HomeComponent implements OnInit {

  constructor(private router: Router) { }

  ngOnInit() {
  }

  onLoadServers() {
    this.router.navigate(['/servers']);
  }
}

```

_We can use either absolute or relative paths for navigation_ and if we use an absolute path,we need to specify the complete path in the array

By clicking a button or triggering an event, we can programmatically navigate to a different route without the page reloading

in `home.component.html`:

```
<button class="btn btn-primary" (click)="onLoadServers()">Load Servers</button>

```
