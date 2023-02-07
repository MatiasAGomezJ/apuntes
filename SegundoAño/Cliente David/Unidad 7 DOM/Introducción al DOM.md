The Document Object Model (DOM) is the data representation of the objects that comprise the structure and content of a document on the web. DOM represents an HTML or XML document in memory.

# What is DOM?
Document Object Model (DOM) is a programming interface for HTML and XML documents. Programs can change the document structure, style, and content. Nodes and objects.

DOM is an object-oriented representation of the web page, which can be modified with a scripting language such as JavaScript.

DOM standards are implemented in most modern browsers. Many browsers extend the standard.

All the properties, methods, and events available for manipulating and creating web pages are organized into objects.

The modern DOM is built using multiple APIs that work together.

# DOM and JavaScript
It's written in JavaScript, but it uses the DOM to access the document and its elements. The DOM is not a programming language,

The page content is stored in the DOM and may be accessed and
manipulated via JavaScript,

API = DOM + JavaScript

The DOM was designed to be independent of any particular programming language, making the structural representation of the document available from a single, consistent API.

Implementations of the DOM can be built for any language,

# Accessing the DOM
Different browsers have different implementations of the DOM, and these implementations exhibit varying degrees of conformance to the actual DOM standard

using the API for the `document` or `window` elements to manipulate the document itself

```js
// run this function when the document is loaded
window.onload = function() {
	// create a couple of elements in an otherwise empty HTML page
	const heading = document.createElement("h1");
	const heading_text = document.createTextNode("Big Head!");
	heading.appendChild(heading_text);
	document.body.appendChild(heading);
}
```

# Fundamental data types
> It's common to always refer to the nodes in the DOM as **elements**, since in an HTML document, each node is an element.

| Data type <br> (Interface) | Description                                                                                                                              |
|:-------------------------- |:---------------------------------------------------------------------------------------------------------------------------------------- |
| Document                   | This object is the root document object itself                                                                                           |
| Node                       | Every object located within a document is a node of some kind. Element node but also a text node or attribute node.                      |
| Element                    | The element type is a base on node. `element` objects implement the DOM `Element` interface and also the more basic Node interface       |
| NodeList                   | A `nodelist` is an array of elements. Items in a `nodeList` are accessed by index in either of two ways: `list.item(1)` or `list[1]`.    |
| Attribute                  | Object reference that exposes a special (albeit small) interface for attributes. Attributes are nodes in the DOM just like elements are. |
| NamedNodeMap               | A `namedNodeMap` is like an array, but the items are accessed by name or index.                                                          |

# DOM interfaces
Many objects borrow from several different interfaces. Table object, specialized `HTMLTableElement` interface.

`table` implements the `Element` interface. It also implements the more basic `Node` interface, from which `Element` derives.

You routinely use all three of these interfaces interchangeably on the object, perhaps without knowing it.

The window object represents something like the browser, and the document object is the root of the document itself. Element inherits from the generic Node interface, and together these two interfaces provide many of the methods and properties you use on individual elements. These elements may also have specific interfaces for dealing with the kind of data those elements hold,

Brief list of common APIs in web and XML page scripting using the DOM.
- `document.getElementById(id)`
- `document.getElementsByTagName(name)`
- `document.createElement(name)`
- `parentNode.appendChild(node)`
- `element.innerHTML`
- `element.style.left`
- `element.setAttribute()`
- `element.getAttribute()`
- `element.addEventListener()`
- `window.content`
- `window.onload`
- `window.scrollTo()`