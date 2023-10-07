# Assigning an Alias to Custom Events

In the past videos we learned how to use `@Output` to enable other components to listen to our custom events, which are created using `EventEmitter`

Just like with `@Input`, we can assign an alias to custom events created with `@Output`
So we renamed `blueprintCreated` to `bpCreated` for clarity in the `cockpit.component.ts` so like: `@Output('bpCreated') blueprintCreated = new EventEmitter<{serverName: string, serverContent: string}>();` and with this event we can listen from outside, so in `app.component.html` to listen, we now need to rename it there too like so: `<app-cockpit (serverCreated)="onServerAdded($event)" (bpCreated)="onBlueprintAdded($event)"><app-cockpit>`

So basically when we use the custom event in our component, we continue to use the original event name "blueprintCreated" and when we listen to the event from outside the component, we use the alias `(bpCreated)="onBlueprintAdded($event)")` to access the event
