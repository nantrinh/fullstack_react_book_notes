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

28. True or False: Class components should always call the base constructor with `props` (i.e., super(props)). 

<details><summary><b>Answer</b></summary>
<p>
True
</p>
</details>

---

29. What is mounting and unmounting? 

<details><summary><b>Answer</b></summary>
<p>
Mounting is when a component is rendered to the DOM for the first time.
Unmounting is when the DOM produced by the component is removed.
</p>
</details>

---

30. What are the two lifecycle methods and when do they run? 

<details><summary><b>Answer</b></summary>
<p>
`componentDidMount()` runs after the component output has been rendered to the DOM.
`componentWillUnmount()` runs immediately before a component is unmounted and destroyed.
</p>
</details>

---

31. What are three things to remember about state? 

<details><summary><b>Answer</b></summary>
<p>
- Do not modify state directly. Use `setState()` instead. The only place where you can assign `this.state` is the constructor.
- State updates may be asynchronous. Because this.props and this.state may be updated asynchronously, you should not rely on their values for calculating the next state.
- State updates are merged.
</p>
</details>

---

32. Why is state often called local or encapsulated? 

<details><summary><b>Answer</b></summary>
<p>
It is not accessible to any component other than the one that owns and sets it.
</p>
</details>

---

33. What is the framework used in the FullStack React book for developing a React app from scratch? 

<details><summary><b>Answer</b></summary>
<p>
- Break the app into components
- Build a static version of the app
- Determine what should be stateful
- Determine in which component each piece of state should live
- Hard-code initial states
- Add inverse data flowComponents
- Add server communication
</p>
</details>

---

34. Why are keys important? 

<details><summary><b>Answer</b></summary>
<p>
Keys help React identify which items have changed, are added, or are removed. The best way to pick a key is to use a string that uniquely identifies a list item among its siblings. Most often you would use IDs from your data as keys. If you choose not to assign an explicit key to list items then React will default to using indexes as keys.
</p>
</details>

---

35. Why might it be a bad idea to use indexes for keys? 

<details><summary><b>Answer</b></summary>
<p>
It may negatively impact performance and may cause issues with component state if the order of items changes. 
</p>
</details>

---

36. Do keys get passed to your components? 

<details><summary><b>Answer</b></summary>
<p>
No. Keys serve as a hint to React but they don’t get passed to your components. If you need the same value in your component, pass it explicitly as a prop with a different name. With the example below, the Post component can read props.id, but not props.key.

```
const content = posts.map((post) =>
  <Post
    key={post.id}
    id={post.id}
    title={post.title} />
);
```
</p>
</details>

---

37. What are three questions to ask about each piece of data to figure out if it is state? 

<details><summary><b>Answer</b></summary>
<p>
- Is it passed in from a parent via props? If so, it probably isn’t state.
- Does it remain unchanged over time? If so, it probably isn’t state.
- Can you compute it based on any other state or props in your component? If so, it isn’t state.
</p>
</details>

---

38. What steps should you follow to determine which component should own what state? 

<details><summary><b>Answer</b></summary>
<p>
For each piece of state in your application:

- Identify every component that renders something based on that state.
- Find a common owner component (a single component above all the components that need the state in the hierarchy).
- Either the common owner or another component higher up in the hierarchy should own the state.
- If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.
</p>
</details>

---
n. 

<details><summary><b>Answer</b></summary>
<p>
</p>
</details>

---
