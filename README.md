# HTML-Assignment1
Exercise 1.1
  # When a user enters an URL in the browser, how does the browser fetch the desired result ?
  When you type “http://server.com ” into browser, starting it will matches the Domain Name Server (DNS) of “server.com ” to an IP address. Next browser sends an (HTTP) request to server, now server send back an HTTP response. The browser renders the HTML on page also requesting any additional resources such as CSS, JavaScript, images, etc. Each request completes a request/response cycle and is rendered in turn by the browser. The URL looks for webpage in hard disk, it returns the webpage.
  
  ![1648221687547](https://user-images.githubusercontent.com/52990768/160440451-e4a41857-bdc4-42ee-8f6c-4b82cf41ab2a.jpg)


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
The rendering engine, as the name suggests is responsible for rendering the requested web page on the browser screen. The rendering engine interprets the HTML, XML documents and images that are formatted using CSS and generates the layout that is displayed in the User Interface.

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

   Rendering, that is display of the requested contents on the browser screen.The networking layer will start sending the contents of the requested documents to the rendering engine in chunks of 8KBs.

By default the rendering engine can display HTML and XML documents and images. 

It can display other types of data via plug-ins or extension; for example, displaying PDF documents using a PDF viewer plug-in. However, in this chapter we will focus on the main use case: displaying HTML and images that are formatted using CSS.

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
 
# Script Processors..The order of execution of scripts. 
  Executable objects go through four execution stages. The second one is the generation stage. Scripts are generated during this stage. The time at which the script is generated depends on object attributes. The order in which scripts are processed in an object depends on which Process pages the scripts are on.

This page includes the following:

Execution Stages
Time of Processing
Order of Processing
Processing In Scripts
Execution Stages

To configure the object attributes correctly so that the script elements behave as you expect, you must understand the stages of execution that a task goes through. The task is activated, generated, processed (that is, executed on the target computer) and finally completed.

The following topics describe the execution stages and the individual steps that take place in each stage. Read them before starting with the Automation Engine scripting language:

Execution Stages

Activation

Generation

Processing

Completion

Time of Processing

The time at which the script is generated depends on the Generate Task at attribute that you define on the object Attributes page. You have two options:

Generate Task at: Activation time

The script is generated at the beginning of the generation stage.

Generate Task at: Runtime

The script is generated much later in the generation stage

Example

The following script uses a function to set the value of a variable to the current date and time:

:SET &CURRENTTIME# = SYS_TIME()

The actual date and time that the script returns depend on the point in time at which the task is generated. Assume that you have two tasks that are configured differently:

Task A is configured to be generated at activation time. The value of the variable is set immediately upon activation.

Task B is configured to be generated at runtime. The task is in a workflow that has several preceding tasks before Task B. Task B is generated when the preceding tasks have finished. The value of the variable is set to the actual time when the task is generated.

For more information about object attributes that concern generation, see Attributes Page. Read also Generating at Activation or at Runtime, where the implications of choosing either option are described in detail.

Important! If you exit the AWI after starting an object that is configured to be generated at activation, script generation may not have finished. If the script includes elements that require action, such as a :READ statement, you may not get the desired results.

Order of Processing

Depending on the type of object, the task may have more than one Process page on which you can write scripts. The scripts in the Process pages are processed in the following order:

Pre-Process page and Process page
Child Post Process page
Post Process page
For more information, see Process Pages.

Processing In Scripts

The Automation Engine processes scripts line by line. The results of executed script elements (such as the value of a variable that has been set) are regularly written to the AE database. This process is referred to as a commit. Other scripts can only access these new or modified values after the values have been committed.

When scripts run for longer times, the Automation Engine automatically makes a commit every 5 seconds. In addition, some script elements that require processes to complete also result in commits.

Examples

Some script elements start or stop tasks, and wait for the RunID of the task to be returned, therefore resulting in a commit. The following functions are examples of such script elements:

ACTIVATE_UC_OBJECT
CANCEL_UC_OBJECT
RESTART_UC_OBJECT
Some script statements require user interaction. The system waits for the user to react, so script statements such as the following also result in a commit:

:BEGINREAD... :ENDREAD
  
:READ
  
The :WAIT script statement instructs the system to wait for a specific length of time, and also results in a commit.
  -------------------
Scripts
The model of the web is synchronous. Authors expect scripts to be parsed and executed immediately when the parser reaches a <script> tag. The parsing of the document halts until the script has been executed. If the script is external then the resource must first be fetched from the network–this is also done synchronously, and parsing halts until the resource is fetched. This was the model for many years and is also specified in HTML4 and 5 specifications. Authors can add the "defer" attribute to a script, in which case it will not halt document parsing and will execute after the document is parsed. HTML5 adds an option to mark the script as asynchronous so it will be parsed and executed by a different thread.

Speculative parsing
While executing scripts, another thread parses the rest of the document and finds out what other resources need to be loaded from the network and loads them. In this way, resources can be loaded on parallel connections and overall speed is improved. Note: the speculative parser only parses references to external resources like external scripts, style sheets and images: it doesn't modify the DOM tree–that is left to the main parser.

Style sheets
Style sheets on the other hand have a different model. Conceptually it seems that since style sheets don't change the DOM tree, there is no reason to wait for them and stop the document parsing. There is an issue, though, of scripts asking for style information during the document parsing stage. If the style is not loaded and parsed yet, the script will get wrong answers and apparently this caused lots of problems. It seems to be an edge case but is quite common. Firefox blocks all scripts when there is a style sheet that is still being loaded and parsed. WebKit blocks scripts only when they try to access certain style properties that may be affected by unloaded style sheets.
  
  # Tree Construction
  
  While the DOM tree is being constructed, the browser constructs another tree, the render tree. This tree is of visual elements in the order in which they will be displayed. It is the visual representation of the document. The purpose of this tree is to enable painting the contents in their correct order.

Firefox calls the elements in the render tree "frames". WebKit uses the term renderer or render object.
A renderer knows how to lay out and paint itself and its children.
WebKit's RenderObject class, the base class of the renderers, has the following definition:

class RenderObject{
  virtual void layout();
  virtual void paint(PaintInfo);
  virtual void rect repaintRect();
  Node* node;  //the DOM node
  RenderStyle* style;  // the computed style
  RenderLayer* containgLayer; //the containing z-index layer
}
Each renderer represents a rectangular area usually corresponding to a node's CSS box, as described by the CSS2 spec. It includes geometric information like width, height and position.
The box type is affected by the "display" value of the style attribute that is relevant to the node (see the style computation section). Here is WebKit code for deciding what type of renderer should be created for a DOM node, according to the display attribute:

RenderObject* RenderObject::createObject(Node* node, RenderStyle* style)
{
    Document* doc = node->document();
    RenderArena* arena = doc->renderArena();
    ...
    RenderObject* o = 0;

    switch (style->display()) {
        case NONE:
            break;
        case INLINE:
            o = new (arena) RenderInline(node);
            break;
        case BLOCK:
            o = new (arena) RenderBlock(node);
            break;
        case INLINE_BLOCK:
            o = new (arena) RenderBlock(node);
            break;
        case LIST_ITEM:
            o = new (arena) RenderListItem(node);
            break;
       ...
    }

    return o;
}The element type is also considered: for example, form controls and tables have special frames.
In WebKit if an element wants to create a special renderer, it will override the createRenderer() method. The renderers point to style objects that contains non geometric information.
The render tree relation to the DOM tree
The renderers correspond to DOM elements, but the relation is not one to one. Non-visual DOM elements will not be inserted in the render tree. An example is the "head" element. Also elements whose display value was assigned to "none" will not appear in the tree (whereas elements with "hidden" visibility will appear in the tree).
There are DOM elements which correspond to several visual objects. These are usually elements with complex structure that cannot be described by a single rectangle. For example, the "select" element has three renderers: one for the display area, one for the drop down list box and one for the button. Also when text is broken into multiple lines because the width is not sufficient for one line, the new lines will be added as extra renderers.
Another example of multiple renderers is broken HTML. According to the CSS spec an inline element must contain either only block elements or only inline elements. In the case of mixed content, anonymous block renderers will be created to wrap the inline elements.

Some render objects correspond to a DOM node but not in the same place in the tree. Floats and absolutely positioned elements are out of flow, placed in a different part of the tree, and mapped to the real frame. A placeholder frame is where they should have been.

 ![image025 (1)](https://user-images.githubusercontent.com/52990768/160433390-69ce8722-568c-41dc-9d64-c7f5a49788c4.png)

Figure : The render tree and the corresponding DOM tree (3.1). The "Viewport" is the initial containing block. In WebKit it will be the "RenderView" object
  The flow of constructing the tree
In Firefox, the presentation is registered as a listener for DOM updates. The presentation delegates frame creation to the FrameConstructor and the constructor resolves style (see style computation) and creates a frame.

In WebKit the process of resolving the style and creating a renderer is called "attachment". Every DOM node has an "attach" method. Attachment is synchronous, node insertion to the DOM tree calls the new node "attach" method.

Processing the html and body tags results in the construction of the render tree root. The root render object corresponds to what the CSS spec calls the containing block: the top most block that contains all other blocks. Its dimensions are the viewport: the browser window display area dimensions. Firefox calls it ViewPortFrame and WebKit calls it RenderView. This is the render object that the document points to. The rest of the tree is constructed as a DOM nodes insertion.

See the CSS2 spec on the processing model.

Style Computation
Building the render tree requires calculating the visual properties of each render object. This is done by calculating the style properties of each element.

The style includes style sheets of various origins, inline style elements and visual properties in the HTML (like the "bgcolor" property).The later is translated to matching CSS style properties.

The origins of style sheets are the browser's default style sheets, the style sheets provided by the page author and user style sheets–these are style sheets provided by the browser user (browsers let you define your favorite styles. In Firefox, for instance, this is done by placing a style sheet in the "Firefox Profile" folder).

Style computation brings up a few difficulties:

Style data is a very large construct, holding the numerous style properties, this can cause memory problems.
Finding the matching rules for each element can cause performance issues if it's not optimized. Traversing the entire rule list for each element to find matches is a heavy task. Selectors can have complex structure that can cause the matching process to start on a seemingly promising path that is proven to be futile and another path has to be tried.

For example–this compound selector:

div div div div{
  ...
}Means the rules apply to a <div> who is the descendant of 3 divs. Suppose you want to check if the rule applies for a given <div> element. You choose a certain path up the tree for checking. You may need to traverse the node tree up just to find out there are only two divs and the rule does not apply. You then need to try other paths in the tree.
Applying the rules involves quite complex cascade rules that define the hierarchy of the rules.
Let's see how the browsers face these issues:
Sharing style data
WebKit nodes references style objects (RenderStyle). These objects can be shared by nodes in some conditions. The nodes are siblings or cousins and:

The elements must be in the same mouse state (e.g., one can't be in :hover while the other isn't)
Neither element should have an id
The tag names should match
The class attributes should match
The set of mapped attributes must be identical
The link states must match
The focus states must match
Neither element should be affected by attribute selectors, where affected is defined as having any selector match that uses an attribute selector in any position within the selector at all
There must be no inline style attribute on the elements
There must be no sibling selectors in use at all. WebCore simply throws a global switch when any sibling selector is encountered and disables style sharing for the entire document when they are present. This includes the + selector and selectors like :first-child and :last-child.
Firefox rule tree
Firefox has two extra trees for easier style computation: the rule tree and style context tree. WebKit also has style objects but they are not stored in a tree like the style context tree, only the DOM node points to its relevant style.
  
![image035](https://user-images.githubusercontent.com/52990768/160435672-bc8a32a1-a419-48e7-b050-2e8e0ca423f2.png)

Figure : Firefox style context tree
  
The style contexts contain end values. The values are computed by applying all the matching rules in the correct order and performing manipulations that transform them from logical to concrete values. For example, if the logical value is a percentage of the screen it will be calculated and transformed to absolute units. The rule tree idea is really clever. It enables sharing these values between nodes to avoid computing them again. This also saves space.

All the matched rules are stored in a tree. The bottom nodes in a path have higher priority. The tree contains all the paths for rule matches that were found. Storing the rules is done lazily. The tree isn't calculated at the beginning for every node, but whenever a node style needs to be computed the computed paths are added to the tree.

  ![tree](https://user-images.githubusercontent.com/52990768/160435776-797d7d0a-8443-4f18-be09-8379699a15e9.png)

The idea is to see the tree paths as words in a lexicon. Lets say we already computed this rule tree:


Suppose we need to match rules for another element in the content tree, and find out the matched rules (in the correct order) are B-E-I. We already have this path in the tree because we already computed path A-B-E-I-L. We will now have less work to do.

  # Layouts
  When the renderer is created and added to the tree, it does not have a position and size. Calculating these values is called layout or reflow.

HTML uses a flow based layout model, meaning that most of the time it is possible to compute the geometry in a single pass. Elements later ``in the flow'' typically do not affect the geometry of elements that are earlier ``in the flow'', so layout can proceed left-to-right, top-to-bottom through the document. There are exceptions: for example, HTML tables may require more than one pass (3.5).

The coordinate system is relative to the root frame. Top and left coordinates are used.

Layout is a recursive process. It begins at the root renderer, which corresponds to the <html> element of the HTML document. Layout continues recursively through some or all of the frame hierarchy, computing geometric information for each renderer that requires it.

The position of the root renderer is 0,0 and its dimensions are the viewport–the visible part of the browser window.
All renderers have a "layout" or "reflow" method, each renderer invokes the layout method of its children that need layout.

Dirty bit system
In order not to do a full layout for every small change, browsers use a "dirty bit" system. A renderer that is changed or added marks itself and its children as "dirty": needing layout.

There are two flags: "dirty", and "children are dirty" which means that although the renderer itself may be OK, it has at least one child that needs a layout.

Global and incremental layout
Layout can be triggered on the entire render tree–this is "global" layout. This can happen as a result of:

A global style change that affects all renderers, like a font size change.
As a result of a screen being resized
Layout can be incremental, only the dirty renderers will be laid out (this can cause some damage which will require extra layouts).
Incremental layout is triggered (asynchronously) when renderers are dirty. For example when new renderers are appended to the render tree after extra content came from the network and was added to the DOM tree.

  ![reflow](https://user-images.githubusercontent.com/52990768/160413138-cf8378db-5774-4880-8d8c-e0b07b3819a6.png)

Figure : Incremental layout–only dirty renderers and their children are laid out
  
Asynchronous and Synchronous layout:
  
Incremental layout is done asynchronously. Firefox queues "reflow commands" for incremental layouts and a scheduler triggers batch execution of these commands. WebKit also has a timer that executes an incremental layout–the tree is traversed and "dirty" renderers are layout out.
Scripts asking for style information, like "offsetHeight" can trigger incremental layout synchronously.
Global layout will usually be triggered synchronously.
Sometimes layout is triggered as a callback after an initial layout because some attributes, like the scrolling position changed.
Optimizations
When a layout is triggered by a "resize" or a change in the renderer position(and not size), the renders sizes are taken from a cache and not recalculated..
In some cases only a sub tree is modified and layout does not start from the root. This can happen in cases where the change is local and does not affect its surroundings–like text inserted into text fields (otherwise every keystroke would trigger a layout starting from the root).
The layout process
The layout usually has the following pattern:

1)Parent renderer determines its own width.
2)Parent goes over children and:
    1)Place the child renderer (sets its x and y).
    2)Calls child layout if needed–they are dirty or we are in a global layout, or for some other reason–which calculates the child's height.
3)Parent uses children's accumulative heights and the heights of margins and padding to set its own height–this will be used by the parent renderer's parent.
4)Sets its dirty bit to false.
  
Firefox uses a "state" object(nsHTMLReflowState) as a parameter to layout (termed "reflow"). Among others the state includes the parents width.
The output of the Firefox layout is a "metrics" object(nsHTMLReflowMetrics). It will contain the renderer computed height.

Width calculation:
The renderer's width is calculated using the container block's width, the renderer's style "width" property, the margins and borders.
For example the width of the following div:

                                    <div style="width: 30%"/>
  Would be calculated by WebKit as the following(class RenderBox method calcWidth):
The container width is the maximum of the containers availableWidth and 0. The availableWidth in this case is the contentWidth which is calculated as:
                                     clientWidth() - paddingLeft() - paddingRight()
  clientWidth and clientHeight represent the interior of an object excluding border and scrollbar.
The elements width is the "width" style attribute. It will be calculated as an absolute value by computing the percentage of the container width.
The horizontal borders and paddings are now added.
So far this was the calculation of the "preferred width". Now the minimum and maximum widths will be calculated.
If the preferred width is greater then the maximum width, the maximum width is used. If it is less then the minimum width (the smallest unbreakable unit) then the minimum width is used.
The values are cached in case a layout is needed, but the width does not change.

Line Breaking
When a renderer in the middle of a layout decides that it needs to break, the renderer stops and propagates to the layout's parent that it needs to be broken. The parent creates the extra renderers and calls layout on them.
  
  # Painting
  
  In the painting stage, the render tree is traversed and the renderer's "paint()" method is called to display content on the screen. Painting uses the UI infrastructure component.

Global and Incremental
  
Like layout, painting can also be global–the entire tree is painted–or incremental. In incremental painting, some of the renderers change in a way that does not affect the entire tree. The changed renderer invalidates its rectangle on the screen. This causes the OS to see it as a "dirty region" and generate a "paint" event. The OS does it cleverly and coalesces several regions into one. In Chrome it is more complicated because the renderer is in a different process then the main process. Chrome simulates the OS behavior to some extent. The presentation listens to these events and delegates the message to the render root. The tree is traversed until the relevant renderer is reached. It will repaint itself (and usually its children).
  
The painting order
  
This is actually the order in which the elements are stacked in the stacking contexts. This order affects painting since the stacks are painted from back to front. The stacking order of a block renderer is:
1)background color
2)background image
3)border
4)children
5)outline
  
Firefox display list
  
Firefox goes over the render tree and builds a display list for the painted rectangular. It contains the renderers relevant for the rectangular, in the right painting order (backgrounds of the renderers, then borders etc). That way the tree needs to be traversed only once for a repaint instead of several times–painting all backgrounds, then all images, then all borders etc.
Firefox optimizes the process by not adding elements that will be hidden, like elements completely beneath other opaque elements.

WebKit rectangle storage
  
Before repainting, WebKit saves the old rectangle as a bitmap. It then paints only the delta between the new and old rectangles.
  
Dynamic changes
  
The browsers try to do the minimal possible actions in response to a change. So changes to an element's color will cause only repaint of the element. Changes to the element position will cause layout and repaint of the element, its children and possibly siblings. Adding a DOM node will cause layout and repaint of the node. Major changes, like increasing font size of the "html" element, will cause invalidation of caches, relayout and repaint of the entire tree.

  The rendering engine's threads
  
The rendering engine is single threaded. Almost everything, except network operations, happens in a single thread. In Firefox and Safari this is the main thread of the browser. In Chrome it's the tab process main thread.
Network operations can be performed by several parallel threads. The number of parallel connections is limited (usually 2–6 connections).

  Event loop
  
The browser main thread is an event loop. It's an infinite loop that keeps the process alive. It waits for events (like layout and paint events) and processes them. This is Firefox code for the main event loop:
  
                            while (!mExiting)
                                 NS_ProcessNextEvent(thread);
  
  # Under the hood understanding of how a browser works.
  Process Flow
The networking layer provides the rendering engine with the content of the document that is requested. The contents are generally transferred in chunks about 8kb each in size. Once that happens, the following flow occurs:

A content tree is created by the rendering engine where the HTML elements get parsed and get converted to DOM nodes. Style data in both internal and external CSS are parsed and visual information along with styling is used to create the render tree.
Rectangles with specific colors and dimensions are arranged inside the rendered tree. They are meant to be in the right order to be rendered on the screen.
Once the rendered tree is constructed, it follows the layout process where each node is given the exact coordinates, according to which they should be displayed on the screen.
The final stage is the painting. Each node in the render tree will be designed according to the code written in the backend layer of the UI. Painting usually takes place in the following order:
The background color is assigned first.
It is immediately followed by the background image.
The border is assigned.
Children are stacked.
Outline of the page is created.
All the processes that occur inside the rendering industry take place gradually. However, the job of a render engine is to display content on the screen as soon as possible for providing a better user experience. That is why, instead of parsing the HTML and building the content of the render tree in one go, it starts building a few parts of the tree while other parts get parsed and built in the backend. Let’s take a detailed look at layout, a complex part of a page’s lifecycle.

DOM and CSS Object Model Construction
In the very first step of the rendering engine, HTML documents are parsed and the parsed elements are converted into nodes in the DOM tree. Each element in the tree is represented to be a parent node, within which the child elements are contained.

While the browser is working on parsing the HTML, it faces the “link” tag which references the external CSS linked to the page. It anticipates that the link is needed to render the complete page. A request is sent immediately to parse the CSS page.

Layout
When a renderer is added to the tree after creation, it does not have any size or position. The layout is the means of calculating those values.

A flow-based layout model is used by HTML. This means that, in most cases, the layout is completed in a single pass. Elements which are placed later in the layout tree do not impact the geometry of elements that are placed earlier. So, the layout can proceed in an omnidirectional way. Although there may exist some exceptions. More than one pass is required in the tables.

All renderers consist of a layout method, which occurs recursively through the child elements in the frame hierarchy. In a default HTML page, a root renderer is placed at the (0,0) coordinate and its dimensions serve as a part of the browser window that is visible, known as the viewport.

Process flow followed by a layout:

1)The rendered Parent decides the width.
2)It goes over children and sets their horizontal and vertical coordinates.
3)The child layout is called only when needed.
4)The cumulative height, margin, and padding of a child are used by the parent to figure out its own height, which will thereby be used by the parent renderer that lies above it in the hierarchy.
5)The value of the dirty renderer is set to false.
6)If you take a look at the developer console, you will find a box-like structure containing a series of rectangular boxes, one placed inside the other. This is the CSS box model which is made of containers which represent the element in the document tree and laid out in a way according to the visual model.
7)Each box contains a content area and may or may not contain the surrounding border, padding, margin, etc.
html body

  ![mm1](https://user-images.githubusercontent.com/52990768/160416085-5a275465-ecb0-4374-b3d4-171517ea93f3.jpg)

Painting
In painting, the paint() method is called to render the UI infrastructure, custom styles, etc., on the component. Painting occurs either globally, where the whole render tree is painted at once, or in an incremental order, where the elements are stacked context wise.

When any custom style of the webpage is changed, the browser performs the minimal number of actions required, since any small change will result in the repainting of the entire element, and the layout will change its position and re-render the entire tree.

Layered Display of Elements
The z-index property of an element deducts where the element will be placed in the stack. In the stack, elements which are aligned at the back get painted first and elements with higher z-index value are arranged on the front and get painted last. These stacks usually have two types:

Containers or boxes having z-index property forms the local stack.
Viewport of the HTML forms the outer stack.
Browsers used nowadays are mostly freeware and fully functional that can render and display not only web pages but web applications as well. Some of them offer plug-ins that allow the user to get multimedia related information. Getting a clear understanding of how a browser works is highly beneficial for a web developer before using the developer console and building an interactive web application as every browser is developed differently, hence, it renders differently.

This is the main reason why a website looks different on different browsers. So, it is necessary to test any website on all browsers.
  
 
