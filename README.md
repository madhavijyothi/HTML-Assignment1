# HTML-Assignment1
Exercise 1.1
  # When a user enters an URL in the browser, how does the browser fetch the desired result ?
  When you type “https://google.com ” into browser, starting it will matches the Domain Name Server (DNS) of “google.com ” to an IP address. Next browser sends an (HTTP) request to server, now server send back an HTTP response. The browser renders the HTML on page also requesting any additional resources such as CSS, JavaScript, images, etc. Each request completes a request/response cycle and is rendered in turn by the browser. The URL looks for webpage in hard disk, it returns the webpage.

# What is main functionality of browser
Browser user interfaces have a lot in common with each other. Among the common user interface elements are:

Address bar for inserting a URI
Back and forward buttons
Bookmarking options
Refresh and stop buttons for refreshing or stopping the loading of current documents
Home button that takes you to your home page
Strangely enough, the browser's user interface is not specified in any formal specification, it just comes from good practices shaped over years of experience and by browsers imitating each other. 
Interpret HTML.
Provide a way for users to access and navigate
Display Webpages efficciently
Provide access to internet service(FTP and mail),Technology to enable multimedia
Helps to perform authentication and encryption funtions
Displaying and printing Web contents on the Intenet and saving a file on the Internet.
  
# High Level Components of a browser. 

![what-is-browser](https://user-images.githubusercontent.com/52990768/160400778-eb58bb92-42ce-47a8-a9d3-ded8bab57cc1.png)

1)The User Interface: 
The user interface is the space where User interacts with the browser. It includes the address bar, back and next buttons, home button, refresh and stop, bookmark option, etc. Every other part, except the window where requested web page is displayed, comes under it.
2)The Browser Engine: 
The browser engine works as a bridge between the User interface and the rendering engine. According to the inputs from various user interfaces, it queries and manipulates the rendering engine.
3)The Rendering Engine: 
The rendering engine, as the name suggests is responsible for rendering the requested web page on the browser screen. The rendering engine interprets the HTML, XML documents and images that are formatted using CSS and generates the layout that is displayed in the User Interface.\
However, using plugins or extensions, it can display other types data also. Different browsers user different rendering engines:
->Internet Explorer: Trident,->Firefox & other Mozilla browsers: Gecko,->Chrome & Opera 15+: Blink,->Chrome (iPhone) & Safari: Webkit
4)Networking: 
Component of the browser which retrieves the URLs using the common internet protocols of HTTP or FTP. The networking component handles all aspects of Internet communication and security. The network component may implement a cache of retrieved documents in order to reduce network traffic.
5)JavaScript Interpreter: 
It is the component of the browser which interprets and executes the javascript code embedded in a website. The interpreted results are sent to the rendering engine for display. If the script is external then first the resource is fetched from the network. Parser keeps on hold until the script is executed.
6)UI Backend: 
UI backend is used for drawing basic widgets like combo boxes and windows. This backend exposes a generic interface that is not platform specific. It underneath uses operating system user interface methods.
7)Data Persistence/Storage: 
This is a persistence layer. Browsers support storage mechanisms such as localStorage, IndexedDB, WebSQL and FileSystem. It is a small database created on the local drive of the computer where the browser is installed. It manages user data such as cache, cookies, bookmarks and preferences.

# Rendering engine and its Use. 

   Rendering, that is display of the requested contents on the browser screen.
The networking layer will start sending the contents of the requested documents to the rendering engine in chunks of 8KBs.
By default the rendering engine can display HTML and XML documents and images. It can display other types of data via plug-ins or extension; for example, displaying PDF documents using a PDF viewer plug-in. However, in this chapter we will focus on the main use case: displaying HTML and images that are formatted using CSS.

![1_cfQpu6Xvb7e9IiH4CCuiCg](https://user-images.githubusercontent.com/52990768/160402091-3f01a559-69b5-4bc8-a3c3-e9bd299f1c43.png)

The rendering engine parses the chunks of HTML document and convert the elements to DOM nodes in a tree called the “content tree” or the “DOM tree”. It also parses both the external CSS files as well in style elements.
While the DOM tree is being constructed, the browser constructs another tree, the render tree. This tree is of visual elements in the order in which they will be displayed. It is the visual representation of the document. The purpose of this tree is to enable painting the contents in their correct order. Firefox calls the elements in the render tree “frames”. WebKit uses the term renderer or render object.
After the construction of the render tree, it goes through a “layout process” of the render tree. When the renderer is created and added to the tree, it does not have a position and size. The process of calculating these values is called layout or reflow. This means giving each node the exact coordinates where it should appear on the screen. The position of the root renderer is 0,0 and its dimensions are the viewport–the visible part of the browser window. All renderers have a “layout” or “reflow” method, each renderer invokes the layout method of its children that need layout.
The next stage is painting. In the painting stage, the render tree is traversed and the renderer’s “paint()” method is called to display content on the screen. Painting uses the UI backend layer.
The rendering engine always tries to display the contents on the screen as soon as possible for better user experience. It does not wait for the HTML parsing to complete before starting to build and layout the render tree. It parses and displays the content it has received from the network, while rest of the contents stills keeps coming from the network.

![webkitflow](https://user-images.githubusercontent.com/52990768/160404134-48ea3cfa-c243-4a50-8a54-7e5591b786f2.png)


# Parsers (HTML, CSS, etc) How parser works and its importance

  A parser is a compiler or interpreter component that breaks data into smaller elements for easy translation into another language. A parser takes input in the form of a sequence of tokens, interactive commands, or program instructions and breaks them up into parts that can be used by other components in programming.
  
  ![slide_1](https://user-images.githubusercontent.com/52990768/160405344-ee46c30c-2170-4e99-9d5f-712e4143fcb1.jpg)

Total process of parsing involves three stages:

Lexical Analysis: A lexical analyzer is used to produce tokens from a stream of input string characters, which are broken into small components to form meaningful expressions. A token is the smallest unit in a programming language that possesses some meaning (such as +, -, *, “function”, or “new” in JavaScript).

Syntactic Analysis: Checks whether the generated tokens form a meaningful expression. This makes use of a context-free grammar that defines algorithmic procedures for components. These work to form an expression and define the particular order in which tokens must be placed.

Semantic Parsing: The final parsing stage in which the meaning and implications of the validated expression are determined and necessary actions are taken.
Working:
The parser obtains a string of tokens from the lexical analyzer and verifies that the string can be the grammar for the source language. It detects and reports any syntax errors and produces a parse tree from which intermediate code can be generated. 

              ---------------------------------------------------------------------------------------
              
 Importance:
Syntactic parsing, the process of obtaining the internal structure of sentences in natural languages, is a crucial task for artificial intelligence applications that need to extract meaning from natural language text or speech.
HTML parsing involves tokenization and tree construction. HTML tokens include start and end tags, as well as attribute names and values. If the document is well-formed, parsing it is straightforward and faster. The parser parses tokenized input into the document, building up the document tree.

When the HTML parser finds non-blocking resources, such as an image, the browser will request those resources and continue parsing. Parsing can continue when a CSS file is encountered, but <script> tags—particularly those without an async or defer attribute—blocks rendering, and pauses parsing of HTML.

When the browser encounters CSS styles, it parses the text into the CSS Object Model (or CSSOM), a data structure it then uses for styling layouts and painting. The browser then creates a render tree from both these structures to be able to paint the content to the screen. JavaScript is also downloaded, parsed, and then executed.
  


 
