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

n. What is the canonical manner in which children communicate events with their parent components? 

<details><summary><b>Answer</b></summary>
<p>
The parent gives the child a function to call when a particular event occurs.
</p>
</details>

---

n. question 

<details><summary><b>Answer</b></summary>
<p>
Answer
</p>
</details>

---
