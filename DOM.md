# Useful Links

[Web Api](https://developer.mozilla.org/en-US/docs/Web/API)

# The DOM

When you request a website, no matter what backend language is powering that website, it will respond with HTML. The browser receives a stream of HTML. The bytes are run through a complicated (but fully documented) parsing process that determines the different characters (e.g. the start tag character <, an attribute like href, a closing angle bracket like >). After parsing has occurred, a process called tokenization. Tokenization takes one character at a time and builds up tokens. The tokens are:

* DOCTYPE
* start tag
* end tag
* comment
* character
* end-of-file

Let's take a break for a second. At this state, the browser has received the bytes that've been sent by a server. The browser has converted the bytes to tags and has read through the tags to create a list of tokens.

This list of tokens then goes through the tree construction stage. The output of this stage is a tree-like structure - this is the DOM!

two important quotes:

* a tree structure that captures the content and properties of the HTML and all the relationships between the nodes
* the DOM is the full, parsed representation of the HTML

So the DOM is a model (representation) of the relationships and attributes of the HTML document that was received. Remember that DOM stands for "Document Object Model". Something that I've found to be true as I've been learning is that to break something down, just read the thing backwards:

Document Object Model

...would become…

Object Model of the Document!

Remember that a JavaScript object is a tree-like structure that has properties and values. So the DOM can be accessed using a special object provided by the browser: document

The document object is provided by the browser and is a representation of the HTML document. This object is not provided by the JavaScript language. ECMAScript is the language specification that JavaScript is based on, and it only references the document object model in one place, in its "Global Object" section:

> In addition to the properties defined in this specification the global object may have additional host defined properties. This may include a property whose value is the global object itself; for example, in the HTML document object model the window property of the global object is the global object itself. (source)

Basically, this says that the document object is not part of JavaScript, but is expected to already exist and be freely accessible to JavaScript code.

The DOM is standardised by the W3C. There are a number of specifications that make up the DOM, here are few:

* Core Specification
* Events Specification
* Style Specification
* Validation Specification
* Load and Save Specification

# Interface

⚠️ **Interface vs User Interface** ⚠️
The word "interface" might be an unclear word right now, and that's ok. I do want to make sure that you're not connecting this "interface" with a user interface (UI) or a graphical user interface (GUI).

Our use of "interface" face is not related to the either a UI or a GUI. Our use of "interface" is a technical, computer science word for a list of properties and methods that are inherited.

Node (with a capital "N"!) is a blueprint that contains information about all of the properties and methods for real nodes (with a lowercase "n"!). If you're not used to them, the words "interface", "property", and "method" can be kind of cryptic at first. Just remember that:

* interface = blueprint
* properties = data
* methods = functionality

[Docs](https://developer.mozilla.org/en-US/docs/Web/API/Node)

# Select an element by id

`document.getElementById(<id-name>);`

There are a couple of important things to keep in mind about this method:

* it is called on the document object
* it returns a single item

[Docs](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById)

# Select an elements by class or tag

`document.getElementsByClassName(<class-name>);`

`document.getElementsByTagName('<tag-name>');`

Similarly to .getElementById(), if we ran the code above in the console, we wouldn't get anything, because we did not tell it the class to search for! Also just like .getElementById(), .getElementsByClassName() is expecting that we call it with a string of the class we want it to search for/return:

[Docs](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByClassName)
