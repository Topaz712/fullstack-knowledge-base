# More on View Encapsulation

- In the past video we learned that Angular encapsulates styles for components by default to prevent style conflicts and if we want to override encapsulation for a specific component, we can modify the encapsulation property in the `@Component` decorator

## There are Three Modes of Encapsulation in Angular

1. Emulated which is the "Default" - This is the default mode where Angular adds unique attributes to component elements to ensure style isolation

2. None - By disabling encapsulation using None means that the component won't get those unique attributes added by Angular, styles defined in the component's CSS file can affect other components globally and can affect other parts of our app

3. Native - This mode uses the Shadow DOM technology, it provides style isolation like Emulated, but only in browsers that support Shadow DOM

_Emulated is the most commonly used mode because it provides style isolation in a cross-browser way_
_None & Native can be used if we need to apply styles globally or leverage Shadow DOM technology in supported browsers_

**So basically Angular's view encapsulation ensures that component styles are isolated by default and we can choose to override this behavior based on our specific requirements, but Emulated mode seems to be the preferred choice for maintaining component style separation**
