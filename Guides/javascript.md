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
1. [Built in Objects](#built-in-objects)

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
array.length                        // returns the number of elements in the array.
array.push(newElement)              // insert an element at the end of the array.
array.pop()                         // removes and returns the element at the end of the array.
array.unshift(newElement)           // insert an element at the beggining of the array.
array.shift()                       // removes and returns the element at the beggining of the array.
array.concat(otherArray)            // returns an array that has the elements of both array.
array.reverse()                     // returns a reversed version of the array.

// splice removes and inserts items at same time.
array.splice(startIndex, nItemsToBeRemoved, newItem1, newItem2,..., newItemN);

// slice returns a portion of the original string. The end index is optional.
const fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
const citrus = fruits.slice(1, 3);
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

const person = {
    name: 'john',
    age: 50,
}

// you can use external variables to initialize the object's properties
const name = 'john',
const age = 50,

const person = {
    name: name,
    age: age,
}

// objects methods can be chained
object.method1().method2().method3();

// delete a object property
delete object.property;   // returns true if successful
```

With ES6 it's possible to omit the value of the property if a variable of similar name alreasy exists:

```Javascript
const name = 'john',
const age = 50,

const person = {
    name,
    age,
}
```

You can set string as properties and use indexing to access it. This can be useful if you want a property to break variable naming rules, for example, if you want your property to have spaces or hypens in its name:

```Javascript
const object = {
    name: 'john',
    age: 50,
    'random-value': 'random',
}

object['john'];
object['random-value'];

// using indexing, you can access properties dinamically using variables:
let variable = 'name';
object[variable];
variable = 'age';
object[variable];
```

## The 'this' keyword

The this keyword points to the object that is right before the dot notation:

```Javascript
const Ana = {
    firstName: "Joana",
    lastName: "d'Arc",
    fullName: function(){
        return `${this.firstName} ${this.lastName}`
    },
};
```

This means that the 'this' keyword will return what is on the left of the dot. If you run it on the global scope, it will return the window object.

```Javascript
const bob = {
    const showThis: showThis,
};

const jeter = {
    const showThis: showThis,
};

function showThis(){
    console.log(this);
};

bob.showThis();    // prints bob
peter.showThis();  // prints peter
showThis();        // prints the window object
```

> Be careful! If you use the 'this' keyword in an object method callback function, it will refer to the object, but if you use it inside a function that is called inside a callback function, it will refer to the window, not the object.

## Factory Functions

Factory functions constructs the objects with the usual curly brackets notation and the returns it:

```Javascript
function createPerson (firstName, lastName){
    const person = {
        firstName: firstName,
        lastName: lastName,
        getFullName: function(){
            return this.firstName + " " + this.lastName;
        }
    }
    return person;
}

const ana = createPerson("Ana","Potter");
```

## Constructor Functions

A constructor functions returns a new object like the factory, but instead of creating the object using the usual brackets notation, you use the 'this' keyword and the assign operators directly inside the function and then omitting the return statement. To create an instance of that object, you use the 'new' keyword before calling the constructor function.

Although it is not necessary, it convention to write the constructor function name in PascalCase instead of camelCase.

```Javascript
function Person (firstName, lastName){
    this.firstName = firstName;
    this.lastName = lastName;
    this.getFullName = function(){
        return this.firstName + " " + this.lastName;
        };
}

const ana= new Person("Ana","Potter");
```

All objects in JS have access to the 'constructor' property, that is a reference to the function that created that object.

```Javascript
ana.constructor; // returns the Person function
```

By default, the object is created by the default JS object constructor, the 'Object' function.
Lists are created by the 'Array' function, and functions created by the 'Function' function.

It's possible to use the constructor of an object indirectly by using the constructor property of the already created objects:

```Javascript
const ana= new Person("Ana","Potter");
const bob = ana.constructor("Bob","Peterson");
```

## Prototype Property

By declaring a function on the constructor body, every time we use that constructor, JS will create a copy of that function in the memory. This is pretty inefficient since we are creating copies of the exact same function, instead of reusing it. To do this, every constructor function/class has a property that is shared by every instance constructor function/class, and it is called 'prototype'.

To share properties among all the instances, set the property inside the 'prototype' property.

```Javascript
function Account (name, initialBalance){
    this.fistName = name;
    this.balance = initialBalance;
}

Account.prototype.bankName = "Money Lovers";
Account.prototype.deposit = function(amount){
    this.balance += amount;
}
Account.prototype.withdraw = function(amount){
    this.balance -= amount;
}
Account.prototype.printBalance = function(){
    console.log(this.balance);
}

const account = new Account
```

## Property Lookup

If JS will look first if the child does have a property, if not JS will ask the parent for it.
So if both the instances and the prototype have the same property, by default the returned value will be the one of the instance.

## ES6 Classes

ES6 Classes are a syntatic sugar for Prototypal Inheritance, and makes the code a lot cleaner.

```Javascript
class Account {
  constructor(name, initialBalance){
    this.fistName = name;
    this.balance = initialBalance;
  }

  // Properties will still have a copy for each instance
  bankName = "Money Lovers";
  /* If you want to share a property amoung many instance, you should use the old prototype way. Another way is using the static keyword to set a Class variable instead of a instance variable.*/

  // Still functions will be shared across instances of the same class
  deposit(amount){
    this.balance += amount;
  }
  withdraw(amount){
    this.balance -= amount;
  }
  printBalance(){
    console.log(this.balance);
  }
}

const account = new Account
```

## Call, Apply and Bind

-   call - runs instantly. Arguments = list of items.
-   apply - runs instantly. Arguments = list of array.
-   bind - assign now, use it later. Arguments = list of items.

## Call

Use the call method of a function to decide what the 'this' key word should be pointing:

```Javascript
const peter = {
   firstName: 'peter',
   lastName: 'parker',
   age: 21,
   greet: function(){
      console.log(`Hello, I'm ${firstName} ${lastName}, how are you?`);
   }
}

function printFullName () {
   console.log( this.firstName + this.lastName );
}

// This won't work since the 'this' doesn't point to anything.
// JS will consider that it is pointing to the window.
// Since the windom object doesn't have firstName and lastName properties,
// It will return undefined.
printFullName();

// The following will not work too.
// Because the 'this' keyword evaluates to what is before the dot
// when the function is called, and in this case there is nothing,
// so this will evaluate to the window.
const peterGreet = peter.greet;
peterGreet();

// In these cases, use the call method of the function.
// It will tell to JS what 'this' should evaluate to.
printFullName.call(peter);
peterGreet.call(peter)
```

With this method it is possible to make the keyword 'this' inside a method of an object point to another object:

```Javascript
peter.greet.call(susan);
```

To pass arguments to the function where you are using the call method, you can pass it as a list of items right after the object argument:

```Javascript
const object = {};
function random( parameter_1, parameter_2 ){/*code*/}

random.call( object, argument_1, argument_2);
```

## Apply

Similar to call, you can use the apply method, but instead of receiving the arguments as a list of items, it receives it as an array:

```Javascript
const object = {};
function random(parameter_1, parameter_2){/*code*/}

random.apply(object, [argument_1, argument_2]);
```

## Bind

At last we have the bind method. It is similar to call and apply, but you assign it to be used later.
It accepts a list of items.

```Javascript
function random(parameter_1, parameter_2){/*code*/}

const randomReference = random.bind( object, argument_1, argument_2);

randomReference();
```

---

# Built in Objects

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
