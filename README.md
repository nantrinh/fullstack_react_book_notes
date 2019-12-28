# React Concepts
1. What is JSX?

<details><summary><b>Answer</b></summary>
<p>

JavaScript eXtension syntax, a syntax extension for JavaScript written by Facebook. Using JSX enables us to write the markup for component views in an HTML-like syntax. In the end, the JSX code comiples to JavaScript.

</p>
</details>

---

2. How do you instruct the browser that you want to use Babel to compile and run JavaScript code? 

<details><summary><b>Answer</b></summary>
<p>

In `index.html`:

Import Babel in the `head` tags.
```
<head>
<!-- ... -->
<script src="vendor/babel-standalone.js"></script>
<!-- ... -->
</head>
```

Add two attributes to the script tag that loads `./js/app.js`.
```
<script
  type="text/babel"
  data-plugins="transform-class-properties"
  src="./js/app.js"
></script>
```

The attribute type="text/babel" indicates to Babel that we would like it to handle the loading of this script.
The attribute data-plugins specifies a special Babel plugin we use in this book.

</p>
</details>

---

3. True or False: JSX components return the actual HTML that gets rendered.  

<details><summary><b>Answer</b></summary>
<p>
False. They return the representation that we want React to render in the DOM.
</p>
</details>

---

4. What does braces signify in JSX? 

<details><summary><b>Answer</b></summary>
<p>
What resides between the braces is a JavaScript expression.
</p>
</details>

---

5. JSX attribute values MUST be delimited by either \____ or \_____. 

<details><summary><b>Answer</b></summary>
<p>
braces, quotes
</p>
</details>

---

6. Do keys need to be globally unique? 

<details><summary><b>Answer</b></summary>
<p>
No, they only need to be unique between components and their siblings.
</p>
</details>

---

7. Does a child component own its own props? 

<details><summary><b>Answer</b></summary>
<p>
No. Parent components own the props of child components.
React favors the idea of one-way data flow: data changes come from the "top" of the app and are propagated "downwards" through its various components.
</p>
</details>

---

8. What is the canonical manner in which children communicate events with their parent components? 

<details><summary><b>Answer</b></summary>
<p>
The parent gives the child a function to call when a particular event occurs.
</p>
</details>

---

9. How do you bind `this` to the component when we define our own custom component methods? 

<details><summary><b>Answer</b></summary>
<p>
Use a pattern like the following:
```
class Product extends React.Component {
  constructor(props) {
    super(props);

    this.handleUpVote = this.handleUpVote.bind(this)
  }
   
  // ...
} 
```
</p>
</details>

---

10. Does a child component own its own state? 

<details><summary><b>Answer</b></summary>
<p>
Yes. 
</p>
</details>

---

11. Every React component is rendered as a function of \______ and \________.

<details><summary><b>Answer</b></summary>
<p>
Its `this.props` and `this.state`. Every time either of those is updated, the component will re-render itself.
</p>
</details>

---

12. Is the rendering of a React component deterministic? 

<details><summary><b>Answer</b></summary>
<p>
Yes. Given a set of props and a set of state, a React component will always render a single way. This approach makes for a powerful UI consistency guarantee.
</p>
</details>

---

13. What is the lifecycle method that is invoked after our component has mounted to the page? 

<details><summary><b>Answer</b></summary>
<p>
`componentDidMount()`
</p>
</details>

---

14. How do you modify the state after setting the initial state? 

<details><summary><b>Answer</b></summary>
<p>
You have to use `this.setState()` (as opposed to setting it directly `this.state = // some code` in `constructor()`).
This method triggers the React component to re-render, among other things.

NEVER modify state outside of `this.setState()`. This function has important hooks around state modification.
</p>
</details>

---

15. True or False: It is best practice to treat the state object as immutable. 

<details><summary><b>Answer</b></summary>
<p>
True
</p>
</details>

---

16. What is a preset in Babel? 

<details><summary><b>Answer</b></summary>
<p>
A set of plugins used to support particular language features.
</p>
</details>

---

17. You use \______ to specify string literals as attributes in JSX, and \________________ to embed a JavaScript expression in an attribute.

<details><summary><b>Answer</b></summary>
<p>
quotes; curly braces

Examples:
```
const element1 = <div tabIndex="0"></div>;
const element2 = <img src={user.avatarUrl}></img>;
```
</p>
</details>

---

18. What naming convention does React DOM use for attribute names in JSX? 

<details><summary><b>Answer</b></summary>
<p>
camelCase (e.g., className instead of class, tabIndex instead of tabindex)
</p>
</details>

---

19. Is it safe to embed user input in JSX? For example:
```
const title = response.potentiallyMaliciousInput;
const element = <h1>{title}</h1>;
```

<details><summary><b>Answer</b></summary>
<p>
Yes. By default, React DOM escapes any values embedded in JSX before rendering them. 
</p>
</details>

---

20. What does JSX compile to? 

<details><summary><b>Answer</b></summary>
<p>
React.createElement() calls.

These two examples are identical:
```
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);
```

```
const element = React.createElement(
  'h1',
  {className: 'greeting'},
  'Hello, world!'
);
```
</p>
</details>

---

21. What is the smallest building block of React apps? 

<details><summary><b>Answer</b></summary>
<p>
Elements. An element describes what you want to see on the screen (e.g., `const element = <h1>Hello, world</h1>;`).
</p>
</details>

---

22. True or False: React elements are immutable. Once you create an element, you can’t change its children or attributes. 

<details><summary><b>Answer</b></summary>
<p>
True. The only way to update the UI is to create a new element and pass it to ReactDOM.render().
</p>
</details>

---

23. How are components like JavaScript functions? 

<details><summary><b>Answer</b></summary>
<p>
They accept arbitrary inputs (called "props") and return React elements describing what should appear on the screen.
</p>
</details>

---

24. What is a function component? 

<details><summary><b>Answer</b></summary>
<p>
A function that accepts a single object argument with data and returns a React element.

Example:
```
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```
</p>
</details>

---

25. How do you use an ES6 class to define a component equivalent to the following?
```
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

<details><summary><b>Answer</b></summary>
<p>
```
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1> 
  }
}
```
</p>
</details>

---

26. True or False: You can start component names with a lowercase or capital letter. 

<details><summary><b>Answer</b></summary>
<p>
False. Always start component names with a capital letter.

React treats components starting with lowercase letters as DOM tags. For example, <div /> represents an HTML div tag, but <Welcome /> represents a component and requires Welcome to be in scope.
</p>
</details>

---

27. What is the single strict rule of React? 

<details><summary><b>Answer</b></summary>
<p>
All React components must act like pure functions with respect to their props. They must never modify their props.
</p>
</details>

---

n. 

<details><summary><b>Answer</b></summary>
<p>
</p>
</details>

---

n. 

<details><summary><b>Answer</b></summary>
<p>
</p>
</details>

---

n. 

<details><summary><b>Answer</b></summary>
<p>
</p>
</details>

---

n. 

<details><summary><b>Answer</b></summary>
<p>
</p>
</details>

---

n. 

<details><summary><b>Answer</b></summary>
<p>
</p>
</details>

---

n. 

<details><summary><b>Answer</b></summary>
<p>
</p>
</details>

---
