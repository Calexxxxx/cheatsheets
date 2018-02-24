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

# querySelector() & querySelectorAll()

`document.querySelector('<class>/<id>/<tag>');`

returns one element

[Docs](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)

`document.querySelectorAll('<class>/<id>/<tag>');`

returns all elements

[Docs](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll)

⚠️ **.querySelector() Returns A Single Element** ⚠️
I want to point out one potentially tricky thing - the .querySelector() method only returns one element. This makes sense if you use it to search for an element by ID. However, even though .getElementsByClassName() and .getElementsByTagName() both return a list of multiple elements, using .querySelector() with a class selector or a tag selector will still only return the first item it finds.

# DOMContentLoaded

Pretty cool, right?!? We have the JavaScript code in the <head> element, but it is now wrapped in an event listener for the DOMContentLoaded event. This will prevent the DOM-styling code from running when the browser gets to it. Then, when the DOM has been constructed, the event will fire and this code will run.

If you're looking at somebody else's code, you may see that their code listens for the load event being used instead (e.g. document.onload(...)). load fires later than DOMContentLoaded -- load waits until all of the images, stylesheets, etc. have been loaded (everything referenced by the HTML.) Many older developers use load in place of DOMContentLoaded as the latter wasn't supported by the very earliest browsers. But if you need to detect when your code can run, DOMContentLoaded is generally the better choice.

However, just because you can use the DOMContentLoaded event to write JavaScript code in the <head> that doesn't mean you should do this. Doing it this way, we have to write more code (all of the event listening stuff) and more code is usually not always the best way to do something. Instead, it would be better to move the code to the bottom of the HTML file just before the closing </body> tag.

So when would you want to use this technique? Well, JavaScript code in the <head> will run before JavaScript code in the <body>, so if you do have JavaScript code that needs to run as soon as possible, then you could put that code in the <head> and wrap it in a DOMContentLoaded event listener. This way it will run as early as possible, but not too early that the DOM isn't ready for it.
