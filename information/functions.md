# Function

a set of statements that performs a task or calculates a value, but for a procedure to qualify as a function, it should take some input and return an output where there is some obvious relationship between the input and the output. To use a function, you must define it somewhere in the scope from which you wish to call it.

Functions are the main “building blocks” of the program. They allow the code to be called many times without repetition.

##### Built it Function Examples:

- alert(message)
- prompt(message, default)
- confirm(question)

## Function Declaration

To create a function we can use a function declaration.

It looks like this:

`function showMessage() {
  alert( 'Hello everyone!' );
}`Here is the refined content, formatted in clean Markdown so you can copy and paste it directly into your `.md` file. I’ve improved the hierarchy, added syntax highlighting, and clarified the concept of **Shadowing**.

---

# Functions in JavaScript

A **function** is a reusable block of code designed to perform a particular task. They are the primary "building blocks" of a program, allowing you to execute logic multiple times without repetition.

To qualify as a function, a procedure should take **input** and return an **output** where there is an obvious relationship between the two.

### Built-in Function Examples

JavaScript provides several built-in functions for browser interaction:

- `alert(message)` – Shows a message.
- `prompt(message, default)` – Shows a message asking the user to input text.
- `confirm(question)` – Shows a message and waits for the user to press “OK” or “Cancel”.

---

## 1. Function Declaration

To create a function, we use a **function declaration**.

### Syntax

```javascript
function name(parameter1, parameter2, ...parameterN) {
  // function body
}
```

- **`function` keyword**: Placed first to declare the function.
- **Name**: The name of the function (usually a verb describing what it does).
- **Parameters**: A list of inputs between parentheses (comma-separated).
- **Body**: The code to be executed, wrapped in curly braces `{}`.

### Calling a Function

To execute the code inside a function, you must "call" (invoke) it by its name followed by parentheses.

```javascript
function showMessage() {
  alert("Hello everyone!");
}

showMessage(); // Invokes the code inside the function
```

---

## 2. Variable Scope

### Local Variables

A variable declared inside a function is **local** to that function. It is only visible and accessible within that function's body.

```javascript
function showMessage() {
  let message = "Hello, I'm JavaScript!"; // local variable
  alert(message);
}

showMessage();
alert(message); // Error! The variable is not defined outside the function.
```

### Outer (Global) Variables

A function can access and modify variables declared outside of it. Variables declared outside of any function are called **Global Variables**.

```javascript
let userName = "John"; // Global variable

function showMessage() {
  userName = "Bob"; // Modifies the outer variable
  let message = "Hello, " + userName;
  alert(message);
}

alert(userName); // John (before call)
showMessage(); // Hello, Bob
alert(userName); // Bob (value was modified by the function)
```

### Variable Shadowing

If a function declares a local variable with the **same name** as an outer variable, the local one "shadows" the outer one. The function will ignore the outer variable and use its own local version.

```javascript
let userName = "John";

function showMessage() {
  let userName = "Bob"; // Local variable, does not affect the global one
  alert(userName);
}

showMessage(); // Bob
alert(userName); // John (The global variable remains unchanged)
```

---

> **Best Practice:** Minimize the use of global variables. Modern code relies on functions that handle their own data. Use globals only for project-level data that must be accessible everywhere.

**Would you like me to explain how "Parameters" and "Return Values" work next?**

### How to create a function

The function keyword goes first, then goes the name of the function, then a list of parameters between the parentheses (comma-separated, empty in the example above, we’ll see examples later) and finally the code of the function, also named “the function body”, between curly braces.

`function name(parameter1, parameter2, ... parameterN) {
 // body
}`

### How to Call a function

Our new function can be called by its name: showMessage().

For instance:

```javascript
function showMessage() {
  alert("Hello everyone!");
}

showMessage();
```

## Local Variables

A variable declared inside a function is only visible inside that function.

For example:

```javascript
function showMessage() {
  let message = "Hello, I'm JavaScript!"; // local variable

  alert(message);
}

showMessage(); // Hello, I'm JavaScript!

alert(message); // <-- Error! The variable is local to the function
```

## Outer variables

A function can access an outer variable as well, for example:

```javascript
let userName = "John";

function showMessage() {
  let message = "Hello, " + userName;
  alert(message);
}

showMessage(); // Hello, John
```

The function has full access to the outer variable. It can modify it as well.

For Instance:

```javascript
let userName = "John";

function showMessage() {
  userName = "Bob"; // (1) changed the outer variable

  let message = "Hello, " + userName;
  alert(message);
}

alert(userName); // John before the function call

showMessage();

alert(userName); // Bob, the value was modified by the function
```

The outer variable is only used if there’s no local one.

** If a same-named variable is declared inside the function then it shadows the outer one. For instance, in the code below the function uses the local userName. The outer one is ignored. **

! Global variables
Variables declared outside of any function, such as the outer userName in the code above, are called global.

Global variables are visible from any function (unless shadowed by locals).

It’s a good practice to minimize the use of global variables. Modern code has few or no globals. Most variables reside in their functions. Sometimes though, they can be useful to store project-level data.

```

```
