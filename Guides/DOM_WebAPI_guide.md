# DOM - Document Object Model API

## Summary

1. [Window and Document Objects](#window-and-document-objects)
1. [Selecting Elements in the Document](#selecting-elements-in-the-document)
1. [Navigating the DOM](#navigating-the-dom)
1. [Getting and Setting the Text Content](#getting-and-setting-the-text-content)
1. [Getting and Setting Attributes](#getting-and-setting-attributes)
1. [Creating, Appending, Replacing and Removing Elements](#creating-appending-replacing-and-removing-elements)
1. [Editing Text](#editing-text)
1. [Changing CSS styling](#changing-css-styling)
1. [Events](#events)

---

# Window and Document Objects

The window object is a reference for the browser tab.  
The document object is a child of window object. It is the HTML document itself.

```Javascript
window;
window.console.log();
window.alert();
window.prompt();
window.document;
window.document.head;
window.document.body;
```

If Javascript can't find a property, it will search it in the window object. This is why we can use methods like alert and log without writing window.alert or window.console.log.

```Javascript
console.log();
alert();
document;
document.head;
document.body;
```

To print the value of something in the console, use the log method of the console object.  
If you want to print the properties of an object, you can use the dir method of the console.

```Javascript
console.log(document)
console.dir(document)
```

---

# Selecting Elements in the Document

Selecting id will always return one object, since ids are not reusable.

```Javascript
document.getElementById( 'id' );
```

The following method returns a HTMLCollection, an array like object.  
You can't use array methods like foreach in these, unless you convert them.

```Javascript
document.getElementsByTagName( 'tagName' );
document.getElementsByClassName( 'className' );
```

Query Selector accepts CSS selectors as an argument, which makes it a very useful method.

```Javascript
document.querySelector( 'any css selector' );
document.querySelectorAll( 'any css selector' );
```

---

# Navigating the DOM

## Get the Child Nodes

To get all the children of an element, you can use the property childNodes.  
ChildNodes is not so useful because it retuns all the children, INCLUDING all the text/whitespace inside the elements.

```Javascript
element.childNodes;
```

The children property is more useful, it returns the children but not the whitespace

```Javascript
element.childrenNodes;
```

You can get the first and the last child, but will returns the text/whitespace, so not so useful.

```Javascript
firstChild;
lastChild;
```

## Get the Parent

To get the parent of an element is simple:

```Javascript
document.parentElement
```

You can chain it, for example, to get the grand parent.  
Be careful that eventually you will run out of nodes, and it will return null.

```Javascript
document.parentElement.parentElement
```

## Get siblings

The following properties will return an element, INCLUDING the text/white space.

```Javascript
element.nextSibling;
element.previousSibling;
```

The following properties will return an element, IGNORING the text/white space.

```Javascript
element.previousElementSibling;
element.nextElementSibling;
```

---

# Getting and Setting the Text Content

The text of an element will be value of its first child.  
For easy access you can just use the textContent property.

```Javascript
element.childNodes[0].nodeValue;
element.firstChild.nodeValue;
element.textContent;
element.textContent = 'new text';
```

---

# Getting and Setting Attributes

You can get the attributes of an element, for example the 'id', the 'class' or the 'href'.

```Javascript
element.getAttribute( 'html-attribute' );
element.setAttribute( 'html-attribute', 'new-value' );
```

You can set/get the class as an string, like in the HTML:

```Javascript
element.className;
element.className = 'first-class second-class';
```

Or can set/get the list of classes of an element.  
The adevantage is that you can use .add(), .remove() and contains() methods.  
If you use the assignment operator, it will overwrite the existing classes.

```Javascript
element.classList;
element.classList.add('new-class');
element.classList.remove('old-class');
element.classList.contains('old-class');
```

---

# Creating, Appending, Replacing and Removing Elements

The document object has methods for creating elements and text nodes.

## Creating Elements

```Javascript
let newElement = document.createElement( 'tagName' );
let newTextNode = document.createTextNode( 'text content' );
```

## Appending Elements

Remember that you must append the new text or element to the page.  
For new text nodes you must append it to an element.  
For new elements you should append to the document, normally in the body.

Append will insert the element to the end of another element.

```Javascript
newElement.appendChild( newTextNode );
document.body.appendChild( newElement );
element.appendChild( newElement );
```

And prepend will insert the element to the start of another element.

```Javascript
element.prepend(newElement);
```

Or you can insert before a specific element.
This needs two arguments, and existing element and the element to be inserted before the first one.

```Javascript
document.body.insertBefore(existingElement, elementToBeInsertedBefore)
```

## Replacing Elements

```Javascript
document.body.replaceChild('newChild','oldChild');
```

## Element Removal

```Javascript
element.remove();
element.removeChild( childNode);
```

---

# Editing Text

Instead of creating a new text node and appending it to an element, of can access the text of the element using its innerText property or the textContent:

```Javascript
element.innerText = 'new text';
element.textContent;
```

Using the innerHTML propery, you can get or set the entire HTML inside an element, not only the text:

```Javascript
element.innerHTML;
element.innerHTML = '<h1>First Heading</h1>';
element.innerHTML += '<h2>Second Heading</h2>'
```

---

# Changing CSS styling

Each element has an style property that can be used to get or set CSS styles

```Javascript
element.style; //gets all the stylesheet for the element
element.style.color;
element.style.color = 'red';
```

> Actually, instead of setting styles line by line, is better to do the styling with a class or id selector inside the CSS file and then add or remove the class or id to/from the element.

---

# Events

Some examples of events are mouse clicks, window scroll and forms submission.

## Mouse Events

Mouse click events:

```Javascript
element.addEventListener('mousedown', callbackFunction);
element.addEventListener('mouseup', callbackFunction);
element.addEventListener('click', callbackFunction); // called  after mouse down and mouse up events
```

Mouse hover events:

```Javascript
element.addEventListener('mouseenter', callbackFunction); // called the cursor hovers over the element
element.addEventListener('mouseleave', callbackFunction); // called the cursor stopes hovering over the element
```

## Key Events

Key press events:

```Javascript
element.addEventListener('keydown', callbackFunction)
element.addEventListener('keyup', callbackFunction)
element.addEventListener('keypress', callbackFunction)
```

At each key pressed, the key value will be added to the value property of the element:

```Javascript
element.value;
```

## Key Object

You can pass the event itself to the callback function.  
This way you can attach the same function to many events but still reference different targets:

```Javascript
element.addEventListener('click', function(event){
    console.log(eventObjectName);
    event.currentTarget; //returns the HTML element that the event is targeting
    event.currentTarget.classList.Add('new-class');
    event.currentTarget === this; // in some situations currentTarget returns the same value as the this keyword
});
```

You can prevent the default behavior of an element.  
One use of this is to prevent the instant scroll of an anchor tag to then implement a smooth scroll.  
Other example is that you might want to prevent the page refresh when the user submits a form.

```Javascript
event.preventDefault();
```

You can access compount elements separately using the event target.
This way, you can target the children of the element to which the event handler was attached to.

```Javascript
event.currentTarget; // always refers to the element to which the event handler was attached to
event.target; // indentifies the element on which the event occured
```

## Event Propagation, Bubbling and Capturing

When a elements fires an event, this event climbs up the hierarchy ('bubbles up') until it reaches the element where the event listener is attached.
Consider the following HTML hierarchy:

```HTML
<body>
    <div class="container">
        <ul class="list">
            <li class="list-items"><a>Button 1</a></li>
            <li class="list-items"><a>Button 2</a></li>
            <li class="list-items"><a>Button 3</a></li>
        </ul>
    </div>
</body>
```

If you add the following Javascript code, when you click one of the buttons, the clicked button will fire the event, and then it bubbles up and then it will reach the list first, then the container and then the body. So in this case, it will fire the the three functions, but not in the order that is declared in the code, but in the order that the event reach the listeners.

```Javascript
window.addEventListener('click', function (){console.log("window click function")});
document.addEventListener('click', function (){console.log("document click function")});
body.addEventListener('click', function (){console.log("body click function")});
container.addEventListener('click', function (){console.log("container click function")});
list.addEventListener('click', function (){console.log("list click function")});
list-item.addEventListener('click', function (){console.log("list-item click function")});
```

Output:

> "list-item click function"  
> "list click function"  
> "container click function"  
> "body click function"
> "document click function"  
> "window click function"

You may want for example that when you click on a link, you may want that the click event bubbles just until it reaches the list-item. In this case you can prevent the event to bubble up.
In this case the others functions will only be called when you fire a click event that is not from the anchor elements.

```Javascript
event.stopPropagation();
```

If you want to invert the direction of the bubbling, you should pass a third argument to the 'addEventListener' function. That argument is passed in a form of object with the key capture equals to true. In this way, instead of bubbling up, the event will bubble down.

```Javascript
window.addEventListener('click', function (){console.log("window click function")}, {capture: true});
document.addEventListener('click', function (){console.log("document click function")}, {capture: true});
body.addEventListener('click', function (){console.log("body click function")}, {capture: true});
container.addEventListener('click', function (){console.log("container click function")}, {capture: true});
list.addEventListener('click', function (){console.log("list click function")}, {capture: true});
list-item.addEventListener('click', function (){console.log("list-item click function")}, {capture: true});
```

Output:

> "window click function"  
> "document click function"  
> "body click function"
> "container click function"  
> "list click function"  
> "list-item click function"

## The Forms Submit Event

Consider the HTML code below:

```HTML
<form action="" id="form">
    <input type="text" id="name"></input>
    <input type="password" id="password"></input>
    <input type="submit" value="submit"></input>
</form>
```

The event fired when the submit button is pressed is called 'submit'.  
When submited, a form by default fires an action (the parameter inside the tag) that sends the information to some play and then refreshes the page.
In the example below, a message is logged to the console, but since the action reloads the page, the console will be cleared and the message will disapear extremely fast.
If you want don't want the page to be reloaded, use the event method 'preventDefault' discussed before.

```Javascript
form.addEventListener('submit', function(event){
    event.preventDefault();
    console.log("message");
    // do something with form
})
```

Remember that this way, the action will not be executed and the information won't be sent by it. You will have to handle the form information in your Javascript code.

---

# Local Storage

The Web Storage API is provided by the browser. It provides mechanisms by which browsers can store key/value pairs, in a much more intuitive fashion than using cookies. It has session storage and local storage.
Each webpage has it own storage.

```Javascript
localStorage.setItem('name','john');
localStorage.getItem('name'); // if the key doesn't exist in the local storage, it returns null
localStorage.removeItem('name');
localStorage.clear();

sessionStorage.setItem('name','john');
sessionStorage.getItem('name'); // if the key doesn't exist in the session storage, it returns null
sessionStorage.removeItem('name');
sessionStorage.clear();
```

## Local storage with multiple values

Sometimes you will want to store a value that is more complex than a string. A example would be an array or other type of object.
Javascript provides us functions to transform a complex data type into a JSON (Javascript Object Notation) string, or transform it back to an object.

```Javascript
const names = ['Peter Parker','Tony Stark','Clark Kent'];
//Incorrect way of storing an object
localStorage.setItem('friends', names); // this line actually stores all the values into one string with the values separated by commas.
//The correct way of storing an object
localStorage.setItem('friends', JSON.stringify(names)); // to transform the object into an string, use this method JSON.stringify()
const retrievedNames = JSON.parse(localStorage.getItem('friends')); // to transform the JSON string into an object, use JSON.parse()
```

---

# Timed functions

Timed functions are functions that runs based on time passed.
You can set function to run just after a specific time using setTimeout:

```Javascript
let uniqueIdentifier = window.setTimeout(callbackFunction, duration); // duration is in miliseconds, the default is 0
setTimeout(callbackFunction, duration);
setTimeout(function(){console.log("hello world")}, 2000);
```

At last you can set a function to run repeatedly at specific intervals with setInterval:

```Javascript
let uniqueIdentifier = setInterval(callbackFunction, duration);
setInterval(callbackFunction, duration);
```

Use clearTimeout to cancel a timed function using the id number:

```Javascript
window.clearTimeout(uniqueIdentifier);
clearTimeout(uniqueIdentifier);
```

```Javascript

```

```Javascript

```

```Javascript

```

```Javascript

```

```Javascript

```

```Javascript

```

```Javascript

```

```Javascript

```

```Javascript

```

```Javascript

```

```Javascript

```

```Javascript

```
