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
}`

### How to create a function

The function keyword goes first, then goes the name of the function, then a list of parameters between the parentheses (comma-separated, empty in the example above, we’ll see examples later) and finally the code of the function, also named “the function body”, between curly braces.

`function name(parameter1, parameter2, ... parameterN) {
 // body
}`

### How to Call a function

Our new function can be called by its name: showMessage().

For instance:

`
function showMessage() {
alert( 'Hello everyone!' );
}

showMessage();
`

## Local Variables

A variable declared inside a function is only visible inside that function.

For example:

`
function showMessage() {
let message = "Hello, I'm JavaScript!"; // local variable

alert( message );
}

showMessage(); // Hello, I'm JavaScript!

alert( message ); // <-- Error! The variable is local to the function
`

## Outer variables

A function can access an outer variable as well, for example:

`
let userName = 'John';

function showMessage() {
let message = 'Hello, ' + userName;
alert(message);
}

showMessage(); // Hello, John
`

The function has full access to the outer variable. It can modify it as well.

For Instance:

`
let userName = 'John';

function showMessage() {
userName = "Bob"; // (1) changed the outer variable

let message = 'Hello, ' + userName;
alert(message);
}

alert( userName ); // John before the function call

showMessage();

alert( userName ); // Bob, the value was modified by the function
`

The outer variable is only used if there’s no local one.

** If a same-named variable is declared inside the function then it shadows the outer one. For instance, in the code below the function uses the local userName. The outer one is ignored. **

! Global variables
Variables declared outside of any function, such as the outer userName in the code above, are called global.

Global variables are visible from any function (unless shadowed by locals).

It’s a good practice to minimize the use of global variables. Modern code has few or no globals. Most variables reside in their functions. Sometimes though, they can be useful to store project-level data.
