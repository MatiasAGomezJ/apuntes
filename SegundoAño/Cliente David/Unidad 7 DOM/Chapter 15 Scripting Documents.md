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

# 15.3 Document Structure and Traversal

## 15.3.1 Documents As Trees of Nodes
Document object, its Element objects, and the Text objects are all Node Objects. Properties:
- `parentNode`
- `childNodes`: A read-only array-like object (a NodeList) that is a live representation of a Node’s child nodes.
- `firstChild`, `lastChild`
- `nextSibling`, `previousSibling`
- `nodeType`. Document > 9. Element > 1. Text > 3. Comments > 8. Documents-fragments > 11 
- `nodeName`. The tag name of an Element, uppercase.

# 15.4 Attributes
The attribute values of HTML elements are available as properties of the HTMLElement objects.

## 15.4.1 HTML Attributes As Element Properties
Read/write properties that mirror the HTML attributes of the elements.

HTML attributes are not case sensitive, but JavaScript property names are. To convert
an attribute name to the JavaScript property, write it in lowercase. Put the first letter of each word after the first in uppercase: `defaultChecked`.

Some HTML attribute names are reserved words in JavaScript. Prefix the property name with “html”. Prefix the property name with “html”.

Event handler attributes always have Function objects (or null) as their val-
ues.

## 15.4.2 Getting and Setting Non-HTML Attributes
HTMLElement

Element defines getAttribute() and setAttribute().

```js

var image = document.images[0];
var width = parseInt(image.getAttribute("WIDTH"));
image.setAttribute("class", "thumbnail");

```

Attribute values are all treated as strings. getAttribute() never returns a number, boolean, or object.

Element also defines two related methods, hasAttribute() and removeAttribute().

# 15.5 Element Content

## 15.5.1 Element Content As HTML
`innerHTML` property of an Element returns the content of that element as a string of markup.

HTML5 also standardizes a property named outerHTML. When you query outerHTML,
the string of HTML or XML markup that is returned includes the opening and closing
tags of the element

## 15.5.2 Element Content As Plain Text
`textContent` property of Node:

```js

var para = document.getElementsByTagName("p")[0]; // First <p> in the document
var text = para.textContent;
// Text is "This is a simple document."
para.textContent = "Hello World!"; // Alter paragraph content

```

# 15.9 HTML Forms
Date from the very beginning of the Web and predate JavaScript itself. Mechanism behind the first generation of web applications, required no JavaScript at all. User input is gathered in form elements; form submission sends that input to the server; generates a new HTML
page.

With server-side programs, a form isn’t useful unless it has a Submit button. Server-side programs are based on form submissions. Client-side programs are event based, they respond to events on individual form elements.

Forms are composed of HTML elements. Form elements were the first ones to be made scriptable, support some APIs that predate the DOM.

Quick reference to the most commonly used form elements.

| HTML element                                        | Type property     | Event handler | Description and events                                                             |
| --------------------------------------------------- | ----------------- | ------------- | ---------------------------------------------------------------------------------- |
| `<input type="button">` or `<button type="button">` | “button”          | onclick       | A push button                                                                      |
| `<input type="checkbox">`                           | "checkbox"        | onchange      | -                                                                                  |
| `<input type="file">`                               | “file”            | onchange      | An input field for entering the name of a file to upload to the web server;        |
| `<input type="hidden">`                             | “hidden”          | none          | Data submitted with the form but not visible to the user                           |
| `<option>`                                          | none              | none          | Event handlers are on the Select object, not on individual Option objects          |
| `<input type="password">`                           | “password”        | onchange      | Typed characters are not visible                                                   |
| `<input type="radio">`                              | “radio”           | onchange      | Radio button                                                                       |
| `<input type="reset">` or `<button type="reset">`   | “reset”           | onclick       | Resets a form                                                                      |
| `<select>`                                          | “select-one”      | onchange      | A list or drop-down menu from which one item may be selected (also see `<option>`) |
| `<select multiple>`                                 | “select-multiple” | onchange      | A list from which multiple items may be selected (also see `<option>`)             |
| `<input type="submit">` or `<button type="submit">` | “submit”          | onclick       | Submits a form                                                                     |
| `<input type="text">`                               | “text”            | onchange      | -                                                                                  |
| `<textarea>`                                        | “textarea”        | onchange      | A multiline text entry field                                                                                   |
