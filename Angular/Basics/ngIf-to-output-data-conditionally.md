# Using ngIf to Output Data Conditionally

To use _ngIf_ a star is required `*ngIf="expression"` becuase it's a _structural directive_ which means it **changes the structure of our DOM**, it either adds an element or it doesn't.

**ngIf has to be any expression returning true or false** deciding whether something should be added or not

## It's important to know that it's either added or removed from the DOM, it's not always there, it's not hidden, it's just not there
