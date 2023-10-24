# react-fundamentals
Explore React's core concepts, hands-on examples, and best practices to kickstart your journey into the world of front-end development. Whether you're a beginner or looking to solidify your understanding, this repository provides the necessary guidance and materials to master React's fundamentals.

<img src="images/react.png">
# Contents
 
 - [JSX](#jsx)
 - [Adding styles](#adding-styles)
 - [Displaying data](#displaying-data)
 - [Conditional rendering](#conditional-rendering)
 - [Rendering lists](#rendering-lists)
 - [Responding to events](#responding-to-events)

- **[`export`](#export)**__,__**[`map`](#map)**__,__**[`for`](#map)**__,__
- React Hooks: **[`useState`](#usestate)**


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

## Displaying data
JSX enables you to integrate markup within JavaScript. Using curly braces, you can seamlessly switch back to JavaScript to incorporate variables from your code and present them to users. For instance, this code will render user.name:
```javascript
return (
  <h1>
    {user.name}
  </h1>
);
```
You can switch to JavaScript within JSX attributes using curly braces instead of quotes. For instance, className="avatar" assigns the string "avatar" as the CSS class, while src={user.imageUrl} takes the JavaScript variable user.imageUrl and uses its value as the src attribute.
```javascript
return (
  <img
    className="avatar"
    src={user.imageUrl}
  />
);
```
You can put more complex expressions inside the JSX curly braces too, for example, [string concatenation](https://javascript.info/operators#string-concatenation-with-binary):
```javascript
const user = {
  name: 'Hedy Lamarr',
  imageUrl: 'https://i.imgur.com/yXOvdOSs.jpg',
  imageSize: 90,
};

export default function Profile() {
  return (
    <>
      <h1>{user.name}</h1>
      <img
        className="avatar"
        src={user.imageUrl}
        alt={'Photo of ' + user.name}
        style={{
          width: user.imageSize,
          height: user.imageSize
        }}
      />
    </>
  );
}
```

## Conditional rendering
You can use the same techniques as you use when writing regular JavaScript code.
```jsx
let content;
if (isLoggedIn) {
  content = <AdminPanel />;
} else {
  content = <LoginForm />;
}
return (
  <div>
    {content}
  </div>
);
```
For shorter code, you can use the ? [operator for conditionals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator). It works within JSX, unlike `if`.
```jsx
<div>
  {isLoggedIn ? (
    <AdminPanel />
  ) : (
    <LoginForm />
  )}
</div>
```
When you don’t need the `else` branch, you can also use a shorter [logical && syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND#short-circuit_evaluation):
```jsx
<div>
  {isLoggedIn && <AdminPanel />}
</div>
```
## Rendering lists
You can use JavaScript features like [`for` loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for) and the [array `map` function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) to render lists of compenents.

```jsx
const products = [
  { title: 'Cabbage', id: 1 },
  { title: 'Garlic', id: 2 },
  { title: 'Apple', id: 3 },
];
```

Use `map` function to transform an array of products into an array of `<li>` items.<div id="map"/>

```jsx
const listItems = products.map(product =>
  <li key={product.id}>
    {product.title}
  </li>
);

return (
  <ul>{listItems}</ul>
);
```
For each item in a list, you should pass a string or a number that uniquely identifies that item among its siblings. 
```jsx
const products = [
  { title: 'Cabbage', isFruit: false, id: 1 },
  { title: 'Garlic', isFruit: false, id: 2 },
  { title: 'Apple', isFruit: true, id: 3 },
];

export default function ShoppingList() {
  const listItems = products.map(product =>
    <li
      key={product.id}
      style={{
        color: product.isFruit ? 'magenta' : 'darkgreen'
      }}
    >
      {product.title}
    </li>
  );

  return (
    <ul>{listItems}</ul>
  );
}
```

## Responding to events
You can respond to events by declaring `event handler` functions inside your components:
```jsx
function MyButton() {
  function handleClick() {
    alert('You clicked me!');
  }

  return (
    <button onClick={handleClick}>
      Click me
    </button>
  );
}
```

> [!NOTE]  
> Note that in onClick={handleClick}, there are no parentheses at the end. Avoid calling the event handler function; simply pass it down. React will automatically invoke the event handler when the user clicks the button.

## useState
This hook allows you to add state to a functional component. It returns a pair of values: the current state and a function to update it.

Import useState from React:
```jsx
import { useState } from 'react';
```
Now you can declare a state variable inside your component:
```jsx
function MyButton() {
  const [count, setCount] = useState(0);
  // ...
```
- `count`: represents the current state value
- `setCount`: is a function to update the state
- `useState(0)`:  is used to manage state within a functional component, In this case, it initializes a piece of state named count with an initial value of 0.

When you want to change state, call setCount() and pass the new value to it. Clicking this button will increment the counter:
```jsx
function MyButton() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <button onClick={handleClick}>
      Clicked {count} times
    </button>
  );
}
```
React will call your component function again. This time, count will be 1. Then it will be 2. And so on.

>[!NOTE]  
>Each button “remembers” its own count state and doesn’t affect other buttons.



>https://react.dev/learn#using-hooks
