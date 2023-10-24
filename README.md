# react-fundamentals
Explore React's core concepts, hands-on examples, and best practices to kickstart your journey into the world of front-end development. Whether you're a beginner or looking to solidify your understanding, this repository provides the necessary guidance and materials to master React's fundamentals.


# Contents
 - [`export`](#export)
 - [`JSX`](#jsx)
 - [Adding styles](#adding-styles)


## export
The export keyword is used in conjunction with functions, classes, variables, or other elements to make them accessible to other modules. It's part of the JavaScript module system and allows you to share functionality between different parts of your React application.

References:

[MSN](https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/export)

[ javascript.info](https://javascript.info/import-export)

## JSX
You have to wrap them into a shared parent, like a `<div>...</div>` or an empty `<>...</>` wrapper:

```jsx
function AboutPage() {
  return (
    <>
      <h1>About</h1>
      <p>Hello there.<br />How do you do?</p>
    </>
  );
}
```

## Adding styles
In React, you specify a CSS class with className. It works the same way as the HTML class attribute:
```html
<img className="avatar" />
```
Then you write the CSS rules for it in a separate CSS file:

```css
/* In your CSS */
.avatar {
  border-radius: 50%;
}
```
React does not prescribe how you add CSS files. In the simplest case, you’ll add a [`<link>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/link) tag to your HTML.
```html
<link href="/media/examples/link-element-example.css" rel="stylesheet" />
```

