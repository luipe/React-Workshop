# React Overview and Components

## Traditional web development
* HTML, CSS and Javascript in separate files
* See example: https://codesandbox.io/s/inspiring-matsumoto-cv15w8?file=/index.html

### Problems
* Complexity and readability

    * Distributed logic (CSS, HTML, JS)

* Duplication of code and logic
* Hard to maintain

    * Difficult to understand the data flow within

### More complex website
<figure style="width: 100%">
  <img src="img/facebookTng.jpg" style="width: 100%; box-shadow: none"/>
</figure>

Would be better to:
* Structure the page in logical **components**
* Have file per component, including styling and interactivity
* Re-use components as needed

=> Those are (some of) the goals of React

## What is React?

JavaScript library (or toolkit) to build user interfaces

### Timeline

* 2011 developed at Facebook
* 2012 used at Instagram
* 2013 Open Source
* current version (2022): React 18
* still actively developed


### Main concepts
* components
    * nested, styled, configurable & reusable
* unidirectional data flow
    * data flows only from parent to child components via props
* virtual DOM
    * DOM
        * Document Object Model = internal representation of the webpage
        * independent of platform or language
    * virtual: 
        * Dynamically generated from JS, not a static HTML file
* JSX/TSX
    * Javascript (Typescript) Syntax Extension
    * looks like HTML
    * produces elements for the DOM


## My first React component

Example code:
https://codesandbox.io/s/romantic-pine-uin9dl?file=/src/App.tsx

React component *Hello World*
```tsx
function HelloWorld() {
  return <h1>Hello World!</h1>;
}
```
as a so-called *functional component*


### Simplified Notation
React component *Hello World*

```tsx
const HelloWorld = () => <h1>Hello World!</h1>;
```
as functional component using the *arrow function* notation of JavaScript.


### Inclusion in DOM
```tsx
ReactDOM.render(<HelloWorld />, document.getElementById('root'));
```

* element tagged as `root` in DOM (index.html)
* entry point for React to render translated result


### Browser Output
<figure style="width: 100%">
  <img src="img/codeExamples/HelloWorld.jpg" style="width: 100%; box-shadow: none; border: 5px solid black"/>
</figure>

## What files do you see?

**public**
* **index.html** entry point of web page

**src**
* **App.tsx** The main React component
* **index.tsx** inclusion of component in DOM
* **styles.css** style sheet

**root folder**
* **package.json** dependencies to packages
* **tsconfig.json** typescript configuration


----

## React components

*What we know now:*
* building blocks of the application

*What we will learn:*
* **JSX** syntax
* configuration via **props**
* can have their own (local) **state**

*Further information*
* styling using Inline-Styles or **css**

## JSX Syntax

* expressions with HTML-like syntax
```tsx
    <h1>Hello World!</h1> 
```

* using components (like HTML tags)
```tsx
    <div className="App">
      <HelloWorld />
      <p>Some other text</p>
    </div>
```

* Inline Typescript expressions
```tsx
    const name = 'John Doe';
    
    return <h1>Hello {name}!</h1>;
```

* Conditional and functional expressions (no if/else or for-loops)
```tsx
    <h1>Hello {name !== undefined ? <b>{name}</b> : <b>unknown</b>}!</h1>
```

To remember:

* TSX looks like html but is indeed typescript expressions
* Our code compiler transpiles TSX to js in the background
* You can put any valid TypeScript expression inside the curly braces in tsx.
* You can use React without tsx, but it is not recommended.

```tsx
<h1>Hello world</h1>

// transpiled (React 17.+)
JSX.createElement('h1', {children: ['Hello world']})
```

```tsx
<div className="App">
  <HelloWorld/>
  <p>Some other text</p>
</div>

// transpiled (React 18.+)
JSX.createElement('div', {
  className: "App", 
  children: [
    JSX.createElement(HelloWorld, {}),
    JSX.createElement('p', {children: ['Some other text']})
  ]
})
```

```tsx
<h1>Hello {name}!</h1>;

// transpiled (React 18+)
JSX.createElement('h1',
  {
    children: [
      'Hello ',
      name,
      '!'
    ]
  }
)
```

```tsx
<h1>Hello {name !== undefined ? <b>{name}</b> : <b>unknown</b>}!</h1>

// transpiled (React 18+)
JSX.createElement('h1', {
  children: [
    'Hello ',
    name !== undefined ? 
      JSX.createElement('b', {children: [name]}) : 
      JSX.createElement('b', {children: ['unknown']}),
    '!'
  ]
})
```

Hence, this is invalid, because `let modifiedCount = count + 12` is not a valid typescript expression.
```tsx
<h1>Count: {let modifiedCount = count + 12 }</h1>

// transpiled (React 18+)
JSX.createElement('h1', {
  children: [
    'Count: ',
    let modifiedCount = count + 12, // ❌
    '!'
  ]
})
```