Client-side JavaScript exists to turn static HTML documents into interactive web applications. Scripting the content of web pages is the central purpose of JavaScript.

Every Window object has a document property that refers to a Document object. The Document object represents the content of the window. The Document object does not stand alone. It is the central object in a larger API, known as the Document Object Model, or DOM, for representing and manipulating document content.

# 15.1 Overview of the DOM
It is the central object in a larger API, known as the Document Object Model, or DOM, for representing and manipulating document content. The nested elements of an HTML or XML document are represented in the DOM as a tree of objects.

![[DOM_Table_2.png]]
The tree representation of an HTML document

Each box is a node of the document and is represented by a Node object. Root of the tree is the Document node. HTML elements are Element nodes, text are Text nodes. Document, Element, and Text are subclasses of Node.

There is a formal distinction between the generic Document and Element types, and the
HTMLDocument and HTMLElement types. In this book, we often use the generic class names Document and Element, even when referring to HTML documents.

![[DOM_Hierarchy_Nodes.png]]
A partial class hierarchy of document nodes

Comment nodes. CharacterData, the common ancestor of both Text and Comment. The Attr node type represents an XML or HTML attribute, but it is almost never used. The DOM also defines infrequently used types to represent things like doctype declarations and XML processing instructions.

# 15.2 Selecting Document Elements
When these programs start, they can use the global variable
document to refer to the Document object. Needs to *select* the Element objects that refer to those document elements. Number of ways to select elements:
- with a specified id attribute;
- with a specified name attribute;
- with the specified tag name;
- with the specified CSS class or classes; or
- matching the specified CSS selector

## 15.2.1 Selecting Elements By ID
No two elements in the same document can have the same ID. 
```js

var section1 = document.getElementById("section1");

```

```js

if (elt == null)									// If not defined,
	throw new Error("No element with id: " + id);	// throw an error

```

## 15.2.2 Selecting Elements by Name
Name attribute was originally intended to assign names to form elements, the value of this attribute is used when form data is submitted to a server. Name attribute does not have to be unique. Only valid on a handful of HTML elements.

```js

var radiobuttons = document.getElementsByName("favorite_color");

```

Defined by the HTMLDocument class, only available for HTML documents, it returns a
NodeList object (read-only array of Element objects).

Setting the name attribute of a `<form>`, `<img>`, `<iframe>`, `<applet>`, `<embed>`, or `<object>` element creates a property of the Document object whose name is the value of the attribute.

If there is more than one element, then the value of the property is a NodeList object that acts as an array of elements.

## 15.2.3 Selecting Elements by Type (tag)
Type (or tag name). To obtain a read-only array-like object containing the Element objects for all `<span>` elements:
```js

var spans = document.getElementsByTagName("span");

```

The elements of the returned NodeList are in document order.

HTML tags are case-insensitive.

Get all elements in a document by passing the argument `*` to `getElementsByTagName()`.

Element Class selects elementes that are descendants.
```js

var firstpara = document.getElementsByTagName("p")[0];
var firstParaSpans = firstpara.getElementsByTagName("span");

```

For historical reasons, the HTMLDocument class defines shortcut properties to access
certain kinds of nodes. The images, forms, and links properties, behave like read-only arrays of, `<img>`, `<form>`, and `<a>` elements (only that have an href). HTMLCollection objects can additionally be indexed by element ID or name:
```js

document.shipping_address

```

`document.forms` property, more specifically:
```js

document.forms.shipping_address

```

The HTMLDocument object also defines synonymous **embeds and plugins properties** that are HTMLCollections of `<embed>` elements. The **anchors** property is nonstandard but refers to **`<a>` elements that have a name attribute** rather than an href attribute. The **`<scripts>` property is standardized by HTML5 to be an HTMLCollection of `<script>` elements**, but it is not, at the time of this writing, universally implemented.

HTMLDocument defines two properties that refers to special single elements.
- document.body is the `<body>`
- document.head is the `<head>`. Always defined.
The browser creates them implicitly

### NodeLists and HTMLCollections
NodeList objects, HTMLCollection objects, read-only array-like objects.

You cannot invoke Array methods on NodeLists and HTMLCollections directly, but you can do so indirectly:

```js

var content =
	Array.prototype.map.call(
		document.getElementsByTagName("p"),
		function(e) { return e.innerHTML; }
	);

```

For historical reasons, both NodeList and HTMLCollection objects can also be treated as functions. Use of this quirk is discouraged.

Both define an item() method. It expects an integer and returns the element at that index.

They are not static snapshots of a historical document state but are generally *live* and the list of elements they contain can vary as the document changes.

## 15.2.4 Selecting Elements by CSS Class
`class` attribute, a space-separated list of zero or more identifiers. Define sets of related document elements. `class` is a reserved word in JavaScript, `className` property.

`getElementsByClassName()` can be invoked on both HTML documents and HTML elements, live `NodeList`, descendants. Takes single string argument, but may specify multiple space-separated identifiers. Returns elements that include all of the specified identifiers. The order of the identifiers does not matter.

“quirks mode” or “standards mode” depending on how strict the `<!DOCTYPE>`. Quirks mode exists for backward compatibility, class identifiers in the class attribute and in CSS stylesheets are case-insensitive. Otherwise, the comparison is case sensitive.

`getElementsByClassName()` is implemented by all current browsers except `IE8` and earlier. IE8 does support `querySelectorAll()`, described in the next section, and `getElementsByClassName()` can be implemented on top of that method.

## 15.2.5 Selecting Elements with CSS Selectors
Selectors
```
#nav
.warning
```
Attribute values:
```
p[lang="fr"]
*[name="x"]
```

```
span.fatal.error
```

Document structure:
```
div, #log	// All <div> elements plus the element with id="log"
```

“Selectors API” defines JavaScript methods. Document method `querySelectorAll()`, single string argument containing a CSS selector and returns a NodeList, not live. If the selector string is invalid, `querySelectorAll()` throws an exception.

`querySelector()`, returns only the first (in document order) matching element or `null`.

Also defined on Elements. When invoked on an element, matched against the entire document, and then the result is filtered so that it only includes descendants of the specified element.

> Many browsers will refuse to return matches for the :link and :visited pseudoclasses.

The specification of these methods does not require support for CSS3 selectors:

`querySelectorAll()`, very powerful technique. The jQuery library uses this kind of CSS selector-based query as its central programming paradigm. Web applications based on jQuery use a portable, cross-browser equivalent to `querySelectorAll()` named `$()`.

## 15.2.6 `document.all[]`
Before the DOM was standardized, IE4 introduced the `document.all[]` collection all elements (but not Text nodes). Now obsolete and should not be used.