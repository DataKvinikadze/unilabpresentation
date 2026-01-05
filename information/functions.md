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

## 3. Parameters

We can pass arbitrary data to functions using parameters.

In the example below, the function has two parameters: from and text.

```javascript
function showMessage(from, text) {
  // parameters: from, text
  alert(from + ": " + text);
}

showMessage("Ann", "Hello!"); // Ann: Hello! (*)
showMessage("Ann", "What's up?"); // Ann: What's up? (**)
```

When the function is called in lines `(*)` and `(**)`, the given values are copied to local variables `from` and text. Then the function uses them.

Here’s one more example: we have a variable from and pass it to the function. Please note: the function changes from, but the change is not seen outside, because a function always gets a copy of the value:

```javascript
function showMessage(from, text) {
  from = "*" + from + "*"; // make "from" look nicer

  alert(from + ": " + text);
}

let from = "Ann";

showMessage(from, "Hello"); // *Ann*: Hello

// the value of "from" is the same, the function modified a local copy
alert(from); // Ann
```

When a value is passed as a function parameter, it’s also called an argument.

In other words, to put these terms straight:

- A parameter is the variable listed inside the parentheses in the function declaration (it’s a declaration time term).
- An argument is the value that is passed to the function when it is called (it’s a call time term).
  We declare functions listing their parameters, then call them passing arguments.

In the example above, one might say: “the function `showMessage` is declared with two parameters, then called with two arguments: `from` and `"Hello"`”.

### Default Values

If a function is called, but an argument is not provided, then the corresponding value becomes undefined.

For instance, the aforementioned function showMessage(from, text) can be called with a single argument:
`showMessage("Ann");`

That’s not an error. Such a call would output `"_Ann_: undefined"`. As the value for `text` isn’t passed, it becomes `undefined`.

We can specify the so-called “default” (to use if omitted) value for a parameter in the function declaration, using `=`:

```javascript
function showMessage(from, text = "no text given") {
  alert(from + ": " + text);
}

showMessage("Ann"); // Ann: no text given
```

Now if the text parameter is not passed, it will get the value "no text given".

## Returning a Value

A function can return a value back into the calling code as the result.

The simplest example would be a function that sums two values:

```javascript
function sum(a, b) {
  return a + b;
}

let result = sum(1, 2);
alert(result); // 3
```

he directive return can be in any place of the function. When the execution reaches it, the function stops, and the value is returned to the calling code (assigned to result above).

There may be many occurrences of return in a single function. For instance:

```javascript
function checkAge(age) {
  if (age >= 18) {
    return true;
  } else {
    return confirm("Do you have permission from your parents?");
  }
}

let age = prompt("How old are you?", 18);

if (checkAge(age)) {
  alert("Access granted");
} else {
  alert("Access denied");
}
```
