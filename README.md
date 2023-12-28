If we use @apply directive we can apply many Tailwind CSS utilities with one custom class name.
Where we write the code is also important.


This is my css file and it's explanation

```
@tailwind base; /* Contains fundamental reset and normalization styles */
@tailwind components; /* Houses reusable component styles for buttons, cards, forms, etc. */

.btn {
    @apply py-4 px-2 text-white bg-purple-900 rounded-lg hover:bg-sky-500 hover:text-black
}
/* we are writing @apply to just apply all the tailwind directive written to
multiple component using a custom class.

It is mainly useful while having a compnent of same style but a lot of it 
example a calculator.*/

@tailwind utilities;


/* Also adding custom class means writing your own css and not just using @apply directive */
/* 
Adding Custom Classes Before Utility Layer:
    Benefits:
        Precedence: Your custom classes take priority, ensuring they override utilities if needed.
        Organization: Clear separation of custom styles from Tailwind's defaults.
        Maintainability: Easier to manage and update custom styles without conflicts.

Adding Custom Classes After Utility Layer:
    Potential Issues:
        Specificity Wars: You might need highly specific selectors to override utilities, making CSS harder to read and maintain.
        Accidental Overrides: Utilities could unintentionally override custom styles, leading to unexpected results. 
*/
```
Now imagine if we write more and more custom classes it will all end up in clutter so to fix it we will use the @layer directive so that we don't have to add the code between the layers but we can define which custom class belongs to which layer inside Tailwind CSS which results in much more cleaner code

```
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
/* Base layer styles */
}

@layer components {
/* Component styles */
  .btn-sm {
      @apply text-sm py-4 px-2 text-white bg-purple-900 rounded-lg hover:bg-sky-500 hover:text-black
  }
}
```
