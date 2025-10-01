
## Introduction

- React is a JavaScript library created by Facebook for building user interfaces.
- React is used to build single-page applications.
- React allows us to create reusable UI components.

## Working

- React creates a VIRTUAL DOM in memory. 
- Instead of manipulating the browser's DOM directly, 
- React creates a virtual DOM in memory, where it does all the necessary manipulating, before making the changes in the browser DOM.

## Major Features Of React :

* JSX(JavaScript Syntax Extension) or XML
* Virtual DOM
* One-way data binding
* Component-Based Architecture
* Performance
* Simplicity

## Setting up a React Environment :

- Install Node.Js
- In terminal: 
  - `npx create-react-app my-react-app`
  OR
  - `npm create vite@latest
  - Configure your project accordingly (name, libraries, language)
- To run the React app:
  1. `cd my-react-app`
  2. `npm start` 
     
     For React+vite:
  1. `cd my-react-app`
  2. `npm run dev`


# Components

Components are like functions that return HTML elements. 
Components are independent and reusable bits of code. They serve the same purpose as JavaScript functions, 
but work in isolation and return `HTML.Components` come in two types
- Class components (used in old React Codebases)
- Function components (Newer, used along with `Hooks`)

---

Components are defined in a `.JSX` file. JSX stands for JavaScript XML.
It makes it easier to write and add HTML in React.

JSX allows us to write HTML elements in JavaScript and place them in the DOM without any `createElement()` and/or `appendChild()` methods.
JSX converts HTML tags into react elements.

## Creating Components

### Class Components

A class component must include the extends React.Component statement. 
This statement creates an inheritance to React.Component, and gives your component access to React.Component's functions.
The component also requires a render() method, this method returns HTML.

>[!example] Class Component
> ```jsx
> class Car extends React.Component {
>   render() {
>     return <h2>Hi, I am a Car!</h2>;
>   }
> }
> ```

### Function Component

A Function component also returns HTML, and behaves much the same way as a Class component, but Function components can be written using much less code, are easier to understand.

> [!example] Function Component
> ```jsx
> function Car() {
>   return <h2>Hi, I am a Car!</h2>;
> }
> ```
> 

# Properties
React Props are like function Parameter in JavaScript and attributes in HTML.
To send props into a component, use the same syntax as HTML attributes.

```JSX
const myElement = <Car brand="Ford" />; //Adds brand element to the car element
```


The component receives the argument as a props object
```jsx
function Car(props) {
  return <h2>I am a { props.brand }!</h2>; //brand attribute in the component: 
}
```

# Hooks
Hooks were added to React in version 16.8. Hooks allow function components to have access to state and other React features. 
Because of this, class components are generally no longer needed.

### Hooks Rules:
- Hooks can only be called inside React function components.
- Hooks can only be called at the top level of a component.
- Hooks cannot be conditional.

>[!Warning] Hooks will not work in React class components.

### Component Cycle

1. Initialize Component.
2. Component Mounting.
3. Component Updation 
4. Component Unmount.

## Commonly used Hooks

### `useState`
The React useState Hook allows us to track state in a function component.
State generally refers to data or properties that need to be tracking in an application.

`useState` accepts an initial state and returns two values:
1. The current state.
2. A function that updates the state.

Syntax
```jsx
import { useState } from "react";

function FavoriteColor() {
  const [color, setColor] = useState(""); //destructuring useState from react as it is a named export
}
```

### `useEffect`

The `useEffect` Hook allows you to perform side effects in your components.
Some examples of side effects are: 
- fetching data 
- directly updating the DOM 
- timers

`useEffect` accepts two arguments. The second argument is optional.

```jsx
useEffect(<function>, <dependency>)
```

>[!Example] `useEffect` Examples
>>[!example] No dependency
>>```Jsx
>>useEffect(() => {
>>//Runs on every render
>>});
>>```
>
>>[!example] Empty Array
>>```jsx
>>useEffect(() => {
>>//Runs only on the first render
>>}, []);
>>```
>
>>[!example] `Props` or state values
>>```jsx
>>useEffect(() => {
>>//Runs on the first render
>>//And any time any dependency value changes
>>}, [prop, state])
>>```

### `useRef`

The useRef Hook allows you to persist values between renders.
It can be used to store a mutable value that does not cause a re-render when updated.
It can be used to access a DOM element directly.

>[!example]  
> ```jsx
> import { useRef } from 'react';
> 
> function MyComponent() {
>   const inputRef = useRef(null);
> 
>   // When the button is clicked, we can focus the input
>   const handleFocus = () => {
>     inputRef.current.focus();
>   };
> 
>   return (
>     <div>
>       <input type="text" ref={inputRef} />
>       <button onClick={handleFocus}>Focus the input</button>
>     </div>
>   );
> }
> ```

### Custom Hooks
Custom hooks are JavaScript functions whose names start with the word "**use**" (e.g., `useFetch`, `useLocalStorage`). They allow you to extract and reuse stateful logic from a component, making your code cleaner and more modular.
A custom hook can use other hooks like `useState`, `useEffect`, or `useRef`.

> [!example]
> ```jsx
> // A custom hook to get the window's width
> import { useState, useEffect } from 'react';
> 
> const useWindowWidth = () => {
>   const [width, setWidth] = useState(window.innerWidth);
> 
>   useEffect(() => {
>     const handleResize = () => setWidth(window.innerWidth);
>     window.addEventListener('resize', handleResize);
>     return () => window.removeEventListener('resize', handleResize);
>   }, []);
> 
>   return width;
> };
> 
> // Now you can use this custom hook in any component
> function ResponsiveComponent() {
>   const width = useWindowWidth();
> 
>   return (
>     <div>
>       <p>The current window width is: {width}px</p>
>     </div>
>   );
> }
> ```

# Routers
`create-react-app` doesn't include page routing.
React Router is the most popular solution.

**Add React Router**
To add React Router in your application, run this in the terminal from the root directory of the application:
`npm i react-router-dom`

### Folder Structure
To create an application with multiple page routes, let's first start with the file structure.

Within the `src` folder, we'll create a folder named pages with several files:

```
src\pages\:

Layout.js
Home.js
Blogs.js
Contact.js
NoPage.js
```
Each file will contain a very basic React component.
Router is used in the `index.js` file


