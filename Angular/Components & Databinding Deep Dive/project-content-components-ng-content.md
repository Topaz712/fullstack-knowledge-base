# Projecting Content into Components with ng-content

- Angular provides a way to pass complex HTML content into a component from outside

  - This is useful when we want to insert content between the opening and closing tags of our custom component because by default, content placed between the opening and closing tags of a custom component is discarded by Angular

- We can enable content projection using the special `ng-content` "doesn't have its own template" directive within our component's template

  - Place `ng-content` where we want to insert the external content like in `server-element.component.html` `<ng-content></ng-content`

```
<div
  class="panel panel-default">
  <div class="panel-heading">{{ element.name }}</div>
  <ng-content></ng-content>
  </div>
```

projected to app.component.html

```
<app-server-element
      *ngFor="let serverElement of serverElements"
      [srvElement="serverElements"]></app-server-element>
        *ngFor="let serverElement of serverElements"
        [srvElement]="serverElement"
        [name]="serverElement.name">
        <p #contentParagraph>
          <strong *ngIf="serverElement.type === 'server'" style="">{{ serverElement.content }}</strong>
          <em *ngIf="serverElement.type === 'blueprint'">{{ serverElement.content }}</em>
        </p>
      </app-server-element>
```

- Any content added between the opening and closing tags of the custom component will be projected into the specified ng-content location
  - This feature is valuable for creating reusable components like tab widgets, where each tab's content can be different and complex
  - `ng-content` allows us to display complex HTML code without the limitations of property binding and HTML tags escaping to prevent cross-site scripting attacks from happening, making it a powerful tool for dynamic component designs
