# What is React?

> JS that produces HTML



# Configuration

### `create-react-app`

> a boilerplate to jump start React projects
>
> hiding all the config by default, not exposed to Babel, Webpack, dev/prod environment, or any other config

> contains: 
>
> * package.json
> * run the app locally
> * run tests
> * build the bundle
> * eject script; uncover all the config that is hidden beneath.

```javascript
# Install the package globally with npm
$ npm i -g create-react-app

# And then use the default script to start as many projects as you like
$ create-react-app testFolder
```

### `npm install`

> node package manager
>
> to install dependencies before running the project

### `npm start`

> initiate boilerplate package
>
> run a local server *localhost:8080*

### To kill current port

`netstat -ano | findstr :8080`

`taskkill /PID 2096 /F`



# Prerequisites

### JSX

> JS that produces HTML
>
> Subset / dialect of JS that converts HTML code to JS behind the scene
>
> Web Pack & Babble translate JSX to Vanilla JS that can be understand by browser
>
> Insert HTML into DOM when component is rendered
>
> Different with HTML, make the code cleaner & readable

```react
return <div />;
return <div></div>;
```



# Fundamentals of React

### Bundle.js

> Web Pack & Babble compile all JS into a single file

### React Workflow

> 1. Write JS in the package
> 2. Web Pack & Babble compile all files together
> 3. Translate JSX to Vanilla JS that can be understand by browser
> 4. Convert to ES5 to run in the browser
> 5. Run a local server

### Key Points

* embed any [JavaScript expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Expressions) in JSX by wrapping it in {}

  ```react
  const element = (
    <h1>
      Hello, {formatName(user)}!
    </h1>
  );
  ```



* use quotes to specify string literals as attributes

  ```react
  const element = <div tabIndex="0"></div>;
  ```



* JSX over multiple lines: wrapping in () to avoid the pitfalls of automatic semicolon insertion

  ```react
  const element = (
    <h1>
      Hello, {formatName(user)}!
    </h1>
  );
  ```

  ​

* After compilation, JSX expressions become regular JavaScript objects.

  ```react
  function getGreeting(user) {
    if (user) {
      return <h1>Hello, {formatName(user)}!</h1>;
    }
    return <h1>Hello, Stranger.</h1>;
  }
  ```



* If a tag is empty, you may close it immediately with `/>`, like XML:

  ```react
  const element = <img src={user.avatarUrl} />;
  ```



* Since JSX is closer to JavaScript than HTML, React DOM uses `camelCase` property naming convention instead of HTML attribute names.

  > `class` > [`className`](https://developer.mozilla.org/en-US/docs/Web/API/Element/className) 
  >
  > `tabindex` > `tabIndex`



# Elements

> Elements are the smallest building blocks of React apps
>
> An element describes what you want to see on the screen
>
> Elements are what components are "made of"

```react
const element = <h1>Hello, world</h1>;
```



# Updating the Rendered Element

React elements are ***immutable***. The only way to update the UI is to create a new element, and pass it to `ReactDOM.render()`.

```react
function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  ReactDOM.render(
    element,
    document.getElementById('root')
  );
}

setInterval(tick, 1000);
// It calls ReactDOM.render() every second from a setInterval() callback.
```

Most React apps only call `ReactDOM.render()`



# React Only Updates What's Necessary

> React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.
>
> Only the text node whose contents has changed gets updated by React DOM.



# Components

> Individual components / views that produce HTML
>
> Split the UI into independent, reusable pieces
>
> Multiple components nest together to make complex application simpleProject has dependencies (js files with tools)
>
> Like JavaScript functions. They accept arbitrary inputs (called "***props***") and return React elements describing what should appear on the screen



### Function

> Accepts a single "props" object argument with data and returns a React element.

```react
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```



### ES6 class

> Classes have some additional features called ***local state***: a feature available only to classes.

```react
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```



### [When to use Class-based component instead of Functional component](https://stackoverflow.com/questions/36097965/react-when-to-use-es6-class-based-components-vs-functional-es6-components/36098616#36098616)

> ***Pure functions***: always render and behave the same, given the same props
>
> > Why?
> >
> > To make performance optimizations specific to these components by avoiding unnecessary checks and memory allocations.
>
> Use ***stateless functions*** (functional components) whenever possible.
>
> There are scenarios where you'll need to use a regular React class:
>
> - The component needs to ***maintain state***
> - The component is ***re-rendering too much*** and you need to ***control*** that via `shouldComponentUpdate`
> - You need a [container component](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0)
>
> To have some additional functionality, e.g. *event handler* **onInputChange**

> Create a Component class if you have your own event handler definitions. That way you can pre-bind those event handlers to the component in the constructor instead of creating a fresh new function on every render. Note this is not needed if all your event handlers come from props.

#### Handling User Events

```react
class SearchBar extends Component {
  render() {
    return <input onChange={this.onInputChange} />;
  }
  
  //Event Handle method
  onInputChange(event) {	//Event Object: events triggered by native elements
      console.log(event.target.value);
  }
}

export default SearchBar;
```

#### Compact Mode

```react
class SearchBar extends Component {
  render() {
    return <input onChange={event => console.log(event.target.value)} />;
  }
}

export default SearchBar;
```



### Rendering a component

> When React sees an element representing a user-defined component, it passes JSX attributes to this component as a single object. We call this object "props".
>
> 1. We call `ReactDOM.render()` with the `<Welcome name="Sara" />` element.
> 2. React calls the `Welcome` component with `{name: 'Sara'}`as the props.
> 3. Our `Welcome` component returns a `<h1>Hello, Sara</h1>` element as the result.
> 4. React DOM efficiently updates the DOM to match `<h1>Hello, Sara</h1>`.
>
> Always start component names with a capital letter.
>
> For example, `<div />` represents a DOM tag, but `<Welcome />` represents a component and requires `Welcome` to be in scope.
>
> Naming props from the component's own point of view rather than the context in which it is being used.

```react
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="Sara" />;
ReactDOM.render(
  element,
  document.getElementById('root')
);
```



### Props are Read-only

Whether you declare a component [as a function or a class](https://facebook.github.io/react/docs/components-and-props.html#functional-and-class-components), it must ***never modify its own props***. All React components must act like pure functions with respect to their props.

```react
function sum(a, b) {	//Pure, do not change their inputs
  return a + b;
}
```

```react
function withdraw(account, amount) {	//impure, changes its input
  account.total -= amount;
}
```



### State (hash table structure)

> State is similar to props, but it is private and fully controlled by the component.
>
> The only place where you can assign `this.state` is the constructor.
>
> State Updates May Be ***Asynchronous***
>
> React may batch multiple `setState()` calls into a single update for performance.
>
> Because `this.props` and `this.state` may be updated asynchronously, you should not rely on their values for calculating the next state.
>
> If you don't use something in `render()`, it shouldn't be in the state.
>
> Any state is always owned by some specific component, and any data or UI derived from that state can only affect components "below" them in the tree.
>
> If you imagine a component tree as a waterfall of props, each component's state is like an additional water source that joins it at an arbitrary point but also flows down.
>
> Plain JS object uses to record & react user events
>
> Each Class-based component has its own state object 
>
> Whenever a component state is changed, the component immediately re-renders as well as its children

```react
// Wrong
this.state.comment = 'Hello';

// Correct
this.setState({comment: 'Hello'});
```





```
ReactDOM.render (
	JSX,
	document.getElementById()
);
```



### Converting a Function to a Class

You can convert a functional component like `Clock` to a class in five steps:

1. Create an [ES6 class](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Classes) with the same name that extends `React.Component`.
2. Add a single empty method to it called `render()`.
3. Move the body of the function into the `render()` method.
4. Replace `props` with `this.props` in the `render()` body.
5. Delete the remaining empty function declaration.

```react
function Clock(props) {
  return (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {props.date.toLocaleTimeString()}.</h2>
    </div>
  );
}
```

```react
class Clock extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <h2>It is {this.props.date.toLocaleTimeString()}.</h2>
      </div>
    );
  }
}
```



### [Adding Lifecycle Methods to a Class](https://facebook.github.io/react/docs/state-and-lifecycle.html#adding-lifecycle-methods-to-a-class)

In applications with many components, it's very important to free up resources taken by the components when they are destroyed.

```react
//runs after the component output has been rendered to the DOM
componentDidMount() 

//whenever the DOM produced by the component is removed
componentWillUnmount()
```



### Handling Events

> - React events are named using camelCase, rather than lowercase
> - With JSX you pass a function as the event handler, rather than a string

```react
<button onclick="activateLasers()">	//HTML
  Activate Lasers
</button>

<button onClick={activateLasers}>	//React
  Activate Lasers
</button>
```



### this

> JavaScript works quite surprisingly here. Because **in JavaScript function context is defined while calling the function, not while defining it**! This is what can surprise many when coming to JS from different fields. Such late binding is a powerful mechanism which allows us to re-use loosely coupled functions in variety of contexts.



### [Inline If with Logical && Operator](https://facebook.github.io/react/docs/conditional-rendering.html#inline-if-with-logical--operator)

```
function Mailbox(props) {
  const unreadMessages = props.unreadMessages;
  return (
    <div>
      <h1>Hello!</h1>
      {unreadMessages.length > 0 &&
        <h2>
          You have {unreadMessages.length} unread messages.
        </h2>
      }
    </div>
  );
}
```



### Inline If-Else with Conditional [Operator](https://facebook.github.io/react/docs/conditional-rendering.html#inline-if-else-with-conditional-operator)

`condition ? true : false`



### [Preventing Component from Rendering](https://facebook.github.io/react/docs/conditional-rendering.html#preventing-component-from-rendering)

> In rare cases you might want a component to hide itself even though it was rendered by another component. To do this return `null` instead of its render output.

>Returning `null` from a component's `render` method does not affect the firing of the component's lifecycle methods. For instance, `componentWillUpdate` and `componentDidUpdate` will still be called.



### Maps

```react
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map((number) => number * 2);
console.log(doubled);
```



#### Rendering Multiple Components

Loop through the `numbers` array using the JavaScript [`map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) function. We return an `<li>` element for each item

```react
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li>{number}</li>
);

ReactDOM.render(
  <ul>{listItems}</ul>,
  document.getElementById('root')
);
```



# What's in Components

### Props are Read-only

Whether you declare a component [as a function or a class](https://facebook.github.io/react/docs/components-and-props.html#functional-and-class-components), it must ***never modify its own props***. All React components must act like pure functions with respect to their props.

```react
function sum(a, b) {	//Pure, do not change their inputs
  return a + b;
}
```

```react
function withdraw(account, amount) {	//impure, changes its input
  account.total -= amount;
}
```



### State (hash table structure)

> State is similar to props, but it is private and fully controlled by the component.
>
> The only place where you can assign `this.state` is the constructor.
>
> State Updates May Be ***Asynchronous***
>
> React may batch multiple `setState()` calls into a single update for performance.
>
> Because `this.props` and `this.state` may be updated asynchronously, you should not rely on their values for calculating the next state.
>
> If you don't use something in `render()`, it shouldn't be in the state.
>
> Any state is always owned by some specific component, and any data or UI derived from that state can only affect components "below" them in the tree.
>
> If you imagine a component tree as a waterfall of props, each component's state is like an additional water source that joins it at an arbitrary point but also flows down.
>
> Plain JS object uses to record & react user events
>
> Each Class-based component has its own state object 
>
> Whenever a component state is changed, the component immediately re-renders as well as its children

```react
// Wrong
this.state.comment = 'Hello';

// Correct
this.setState({comment: 'Hello'});
```





```
ReactDOM.render (
	JSX,
	document.getElementById()
);
```





### Handling Events

> - React events are named using camelCase, rather than lowercase
> - With JSX you pass a function as the event handler, rather than a string

```react
<button onclick="activateLasers()">	//HTML
  Activate Lasers
</button>

<button onClick={activateLasers}>	//React
  Activate Lasers
</button>
```



### this

> JavaScript works quite surprisingly here. Because **in JavaScript function context is defined while calling the function, not while defining it**! This is what can surprise many when coming to JS from different fields. Such late binding is a powerful mechanism which allows us to re-use loosely coupled functions in variety of contexts.



### [Inline If with Logical && Operator](https://facebook.github.io/react/docs/conditional-rendering.html#inline-if-with-logical--operator)

```
function Mailbox(props) {
  const unreadMessages = props.unreadMessages;
  return (
    <div>
      <h1>Hello!</h1>
      {unreadMessages.length > 0 &&
        <h2>
          You have {unreadMessages.length} unread messages.
        </h2>
      }
    </div>
  );
}
```



### Inline If-Else with Conditional [Operator](https://facebook.github.io/react/docs/conditional-rendering.html#inline-if-else-with-conditional-operator)

`condition ? true : false`



### [Preventing Component from Rendering](https://facebook.github.io/react/docs/conditional-rendering.html#preventing-component-from-rendering)

> In rare cases you might want a component to hide itself even though it was rendered by another component. To do this return `null` instead of its render output.

> Returning `null` from a component's `render` method does not affect the firing of the component's lifecycle methods. For instance, `componentWillUpdate` and `componentDidUpdate` will still be called.



### Maps

```react
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map((number) => number * 2);
console.log(doubled);
```



#### Rendering Multiple Components

Loop through the `numbers` array using the JavaScript [`map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) function. We return an `<li>` element for each item

```react
const numbers = [1, 2, 3, 4, 5];
const listItems = numbers.map((number) =>
  <li>{number}</li>
);

ReactDOM.render(
  <ul>{listItems}</ul>,
  document.getElementById('root')
);
```





## Shortcuts

```react
const DefaultPage = function () {
    return (<div style={props.style}> {props.text} </div>)
};

//SHORTCUT
const DefaultPage = (props) => {
    return (<div style={props.style}> {props.text} </div>)
};
```



```react
import React from 'react';
const Component = React.Component;

//SHORTCUT
import React, {Component} from 'react';
```



```react
class SearchBar extends Component {
    render() {
        return <input onChange={this.onInputChange} />;
    }

    onInputChange(event) {
        console.log(event.target.value);
    }
}

//SHORTCUT
class SearchBar extends Component {
    render() {
        return <input onChange={(event) =>  console.log(event.target.value)} />;
    }
}
```



```react
const App = () => {
    return (
        <div>
            <SearchBar/>
        </div>
    );
}

class App extends Component {
    render() {
        return (
            <div>
                <SearchBar/>
            </div>
        );
    }
}
```



```react
        this.state = { videos: [] };
        YTSearch({key: API_KEY, term: 'surfboards'}, (data) => {
            this.setState({ videos: data });
        });
        
        
        this.state = { videos: [] };
        YTSearch({key: API_KEY, term: 'surfboards'}, (videos) => {
            this.setState({ videos });
        });
```



## Others (to be elaborated)

`this.state.term`

One component per file



All the code in separate files is **siloed**; can’t make reference to any variables in that other file unless explicitly access to code

> For instance, some file accessing **App **variable -> No access unless
> explicitly access to app inside of this other file



`Import React from ‘react’;`

> Find the library called **react** installed in my applicationdependency which is installed in the node modules folder. Go and find thatlibrary and assign it to the variable **React**



**ReactDOM**

> a separate library that takes a component and insert/render into the DOM

```react
Import ReactDOM from ‘react-dom’;
ReactDOM.render(<App />,document.querySelector(‘.container’))
```



**Component Class** `const App = function()`

**Component Instance** `<App></App>`  OR `<App />`



Class-based component has states, not function-based

Constructor is called immediately whenever a new instance of a class is created in JSX

Initialize variable in Constructor

`this.setState`: update state

`value={this.state.term}`: To get value, value = state, add property/controlled components: 

`this.`: use in class for variables. Not function.

Use class if involved user interaction

`props`: Function arguments

`{this.state.videos}`: Passing from parents to child videos

`{video.etag}`: Key property: render selectively instead of all key:

Always try to render when start

`return ( )`: for multiple line

SilviyaSafonova19994@bk.ru



# Typechecking With PropTypes



# New

> Hi Kai, looks better but if we don’t return anything from the map’a callback then it’s semantically better to use Array.prototype.forEach as map return a value but we don;t use it. So it our case .map returns [undfined, undfined, undfined, ….] 

```
Object.keys(parsedFilter).forEach(key => {
+                if (this.filters[key]) {
+                    this.applyFilter(key, {
+                        active: !!parsedFilter[key],
+                        value: parsedFilter[key]
+                    });
+                    this.filters[key].active = true;
+                    this.filters[key].value = parsedFilter[key];
+                }
+            });
```

