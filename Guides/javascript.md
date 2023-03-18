# JavaScript

## Summary

1. [Inserting Javascript into the HTML document](#inserting-javascript-into-the-html-document)
1. [Comments](#comments)
1. [Variables](#variables)
1. [Strings](#strings)
1. [Comparison and Logical Operators](#comparison-and-logical-operators)
1. [Control Flow](#control-flow)
1. [Loops](#loops)
1. [Functions](#functions)
1. [Arrays](#arrays)
1. [Reference vs. Value](#reference-vs-value)
1. [Null vs. Undefined](#null-vs-undefined)
1. [Objects](#objects)

---

# Inserting Javascript into the HTML document

Methods to insert javascript to the page:

-   Inline.
-   Internal: code inside the script tags `<script></script>`.
-   External: insert a source in the first script tag `<script src="path"></script>`.

---

# Comments

// this is one line comment  
/_ this is a multi line comment _/

---

# Variables

Variable names can contain letters, digits, underscore and $, can't start with a digit and can't be a Javascript keyword.  
Javascript is canse sensitive. As naming scheme use camelcase or snakecase, but camelcase is recommended.

To create a variable, you have 3 options:

-   To create a value that can be changed use the keyword `let`,
-   To create a value that cannoy be changed use the keyword `const`,
-   To create a global variable use the keywrod `var`.

```Javascript
let variable_name;
const variable_name;
var variable_name;
```

Assign a value to an existing variable:

```Javascript
variable_name = value;
```

Create a variable and assign a value:

```Javascript
let variable_name = value;
```

## Data Types

-   number
-   string
-   boolean
-   null
-   undefined
-   symbol
-   object

## Checking Data Types

Check the type of something with the typeof operator:

```Javascript
typeof variable;
typeof value;
```

---

# Strings

Use the plus sign between strings

```Javascript
string_1 + string_2 + ... + string_n;
```

### Template Literals

Surround the message with backticks ( \` ) and use the `${variable}` syntax.

```Javascript
`You name is ${variable_name}, and your age is ${variable_age}`
```

Convert string to Int:

```Javascript
parseInt(intValue);
```

## String properties and methods

```Javascript
string.length // returns the numbers of characters of the string
string.toLowerCase() // returns a lower case version of the string
string.toUpperCase() // returns a upper case version of the string
string.charAt(index) // returns the character at index
string.indexOf(string) // returns the index of the first occurence of the string, if it not returns -1
string.trim() // remove the white space at the start and the end
string.startsWith(string) // returns as boolean if the string starts with the argument
string.includes(string) // returns as boolean if the string contains the argument
string.slice(startIndex, optionalEndIndex) // returns a substring. You can use negative indexing to get the end of the string
string.substring(startIndex, optionalEndIndex) // similar to slice but doesn't accept negative values, start and end can be inverted
string.substr(startIndex, length) // a legacy method that should be avoided
```

---

# Comparison and Logical Operators

Comparision Operators:

```Javascript
!=  // checks if not equal
!== // checks if not equal, independent of type
==  // checks if values are equal, independent of type
=== // checks if values are equal and same type

>   // checks if the first value is greater than the second
>=  // checks if the first value is greater or equal to the second
<   // checks if the first value is less than the second
<=  // checks if the first value is less or equal to the second
```

Logical Operators:

```Javascript
!   // NOT
&&  // AND
||  // OR
```

---

# Control Flow

## Conditionals

If and else Conditionals are the main way of branching you code exercution:

```Javascript
if (condition) {
    //code
}

if (condition) {
    //code
} else {
    //code
}

if (condition) {
    //code
} else if (condition) {
    //code
} else {
    //code
}
```

## The Ternary operator

The ternary operator allow us to make conditionals with just one line:

```Javascript
(/*condition*/) ? ( /*statement that runs if true*/) : (/*statemnet that runs if false*/)
```

## Switch

The switch statement is another way of branching the execution of the code:

```Javascript
switch (value) {
    case 1:
        //code;
        break;
    case 2:
        //code;
        break;
    case 3:
        //code;
        break;
    default:
        //code
}
```

---

# Loops

```Javascript
for(initialization; condition; increment/decrement){
    /*code*/
}

while(condition){
    /*code*/
}

do{
    /*code*/
} while(condition)
```

---

# Functions

If arguments aren't passed to the functions, the parameters will receive the value of undefined.

```Javascript
function name (parameter) {
    //code here
};
```

You can return values with the return keyword:

```Javascript
function name (parameter1, parameter2, ..., parameterN) {
    //code here
    return value;
};
```

You can set default values to the parameters:

```Javascript
function name (parameter1= defaultValue1, parameter1= defaultValue2) {};
```

Function Expressions:

```Javascript
const variableName = function functionName (parameters) {code};
```

With function expressions you can omit the name. These are called anonymous function.

```Javascript
const variableName = function (parameters) {code};
```

---

# Arrays

You can mix anything in Javascript arrays, and they can grow dinamicaly.

## Basic Array Methods

Some of the basic array properties and methods are:

```Javascript
array.length                // returns the number of elements in the array.
array.concat(otherArray)    // returns an array that has the elements of both array.
array.reverse()             // returns a reversed version of the array.
array.unshift(newElement)   // insert an element at the beggining of the array.
array.shift()               // removes and returns the element at the beggining of the array.
array.push(newElement)      // insert an element at the end of the array.
array.pop()                 // removes and returns the element at the end of the array.
array.splice(startIndex, nItems) // removes and returns n elements of the array.
```

## Advanced Array Methods

### For Each

The forEach method iterates through all elements in the array with a callback function. It doesn't return a new array.
For each using a callback function:

```Javascript
forEach(callback);
```

Using an anonymous function.

```Javascript
forEach (function (item) {} );
```

### Map

the map method iterates through all elements in the array, returning a new array of the same size.  
The callback function return will be used to construct a new array.

```Javascript
const ages = people.map( function (person) {return person.age; });
```

### Filter

Filter iterates through all elements in the array, returning a new array that isn't necessarily the same size. The callback functions should return a boolean.

```Javascript
const youngPeople = people.filter( function (person) {return person.age <= 25; });
```

### Find

Find iterates through all elements in the array until it find and returns the first element that matches the condition.

```Javascript
const wantedPerson = people.find( function (person) {return person.id === 3; });
```

### Reduce

Reduce iterates through all elements in the array reducing it to a single value.
The reduce method itslef should receive two arguments:

1. a callback function.
2. a initial value where the reduce method will sum to.

The callback function should recieve two parameters:

1. accumulator - total of all calculations, or the value will accumulate.
2. current - current iteration/value

The callback function should return the accumulator too.

```Javascript
const totalExpense = employees.reduce( function (acc, currItem ) {acc += currItem.salary; return acc;}, 0)
```

---

# Null vs. Undefined

`undefined` - when javasript can't find a value, examples:

-   Variable without a value, missing function arguments, missing object properties...
-   Can't be used on math operations.

`null` value set by the user. If used on math operations, it will mean 0.

Besides booleans, other types can be evaluated as true or false.
Empty strings, positive or negative zeroes, NaN, null and undefined will be evaluated as false.
Non empty string or non zero values will be evaluated as true.

---

# Reference vs. Value

When assigning primitive data type value to a variable any changes are made directly to that value, without affecting original value. This is called a depp copy.

When assigning non-primitive data type value to a variable is done by reference so any changes will affect all the references. This is called a shallow copy.

---

# Objects

Objects are collections of key/value pairs. Javascript objects are similar to dictionaries in languages like python and C#. Their properties can be variables or anonymous functions.

```Javascript
const objectName = {
    property_1: value_1,
    property_2: value_2,
    property_3: function () {},
    etc...
};
```

Objects methods can be chained:

```Javascript
object.method1().method2().method3();
```

## Math object

-   `Math.floor( number );` -rounds down the number
-   `Math.ceil( number );` -rounds up the number
-   `Math.round( number );` -rounds to the nearest integer
-   `Math.sqrt( number );` -square root
-   `Math.PI;` -the pi number
-   `Math.min( n1, n2, ...,nn );`
-   `Math.max( n1, n2, ...,nn );`
-   `Math.random();` -returns a random value between 0 and 1;

## Date Object

You can instantiate a date object. It will have the current date.

```Javascript
const date = new Date();
```

Or a custom date:

```Javascript
const date = new Date('21/10/2015');
```

The date object have methods to get the full date, the year, the month and so on.
Be careful since month and week day are zero index based, so January and sunday values is 0.

```Javascript
getMonth() // January is number 0.
getDay() // Day of the week. Sunday is number 0
getDate() // Day of the month
getFullYear() // Get the year
```
