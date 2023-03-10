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

## Window and Document Objects

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

## Selecting Elements in the Document

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

## Navigating the DOM

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

## Getting and Setting the Text Content

The text of an element will be value of its first child.  
For easy access you can just use the textContent property.

```Javascript
element.childNodes[0].nodeValue;
element.firstChild.nodeValue;
element.textContent;
element.textContent = 'new text';
```

---

## Getting and Setting Attributes

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

## Creating, Appending, Replacing and Removing Elements

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

## Editing Text

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

## Changing CSS styling

Each element has an style property that can be used to get or set CSS styles

```Javascript
element.style; //gets all the stylesheet for the element
element.style.color;
element.style.color = 'red';
```

> Actually, instead of setting styles line by line, is better to do the styling with a class or id selector inside the CSS file and then add or remove the class or id to/from the element.

---

## Events

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
