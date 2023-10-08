# Using Local References in Templates

- In Angular, we can use local references to easily access HTML elements in our templates instead of doing two way databinding
  - To create a local reference, we use a hashtag then the name of our choice, like in the video Max uses `#serverNameInput` in the `cockpit.component.html` like so:
  ```<input
    type="text"
    class="form-control"
    #serverNameInput>
  ```
  - Local references hold references to HTML elements, not just their values
  - We can pass local references as arguments in event bindings

**Local references can be used only within the template, not in TypeScript code**

- We can use local references to access and manipulate elements or their properties directly inside the template
  - This is useful, especially for when we want to get values from input elements or accessing element properties when an event is triggered
  * Local references help simplify two way databinding in situations where we only need the element's value at a specific moment, like when a button is clicked

**Dont forget to specify the type of the element when accessing its properties to avoid TypeScript errors, so the perks of this is that local references provide a convenient way to work with specific elements in our Angular templates**
