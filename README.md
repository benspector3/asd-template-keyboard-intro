# Box Walker

# Setup

To install this project, first clone the [template](https://github.com/benspector3/asd-template/) repository by entering these commands into your bash terminal:

```bash
git clone https://github.com/benspector3/asd-template.git
rm -rf asd-template/.git
```

Then, rename the folder to `box-walker`

# Learning Objectives
- Become familiar with the template repository
- Practice modeling data with Objects
- Learn a method for handling key events
- Write code that will be useful for pong

# TODOs

## TODO 0: Run the template program and understand the basic structure (no coding)

Before we begin coding, open the `index.html` file and press **Preview** to see what we're starting with. It looks like the beginning of bouncing box, right?



Take 10 minutes to look at the code in each of the three files to get a sense of how this template is laid out. 

Pay attention to the following:

### The `index.html` file

The body only has 2 elements: the `#board` and a single `#gameItem`. It should look like this:

```html
<body>
  <div id='board'>
    <div id='gameItem'></div>
  </div>
</body>
```

Each game we create this semester will have a board of some sort with various game items. Often, you will have many more game items that you'll either create manually, or dynamically added to the board later using jQuery.

Remember that these two elements have unique `id` attributes, which means that we can select them using the following CSS selectors:
- `#board`
- `#gameItem`

### The `index.css` file

The games we will build this semester will all use 2D graphics since we are limiting ourselves to HTML and CSS. Most of the shapes can be easily drawn as rectangles using the `width` and `height` properties. 

Rectangles can be made into circles by adding a `border-radius` property.

**Go ahead and add a `border-radius` property to the `#gameItem`. To make it a perfect circle, set the `border-radius` to the same value as the `width` and `height`.

Also, pay attention to the value for the `position` properties set for the `#board` and the `#gameItem`. 

Notice that the parent element (`#board`) has the `position: relative` property while the child element (`#gameItem`) has the `position: absolute` property. This combo means that the child element can be placed anywhere inside the parent element by manipulating the `left` and `top` properties. 
- `left` is the x-coordinate, or distance from the left
- `top` is the y-coordinate, or distance from the top

_Note: There are also `right` and `bottom` properties but we'll stick with `top` and `left` for consistency._

### The `index.js` file

Look at the code written under each header. Remember:
- Initialization: variable declarations, any one-off statements needed to start the program
- Core Logic: The main logic driving the program. Should delegate work to helper functions.
- Helper Functions: functions that implement the core logic.
- Event Handlers: functions that directly respond to events. Depending on the program, these can serve as the "Core Logic"

## TODO 1: register keyboard inputs

Open the `index.js` file and find the function `turnOnEvents()` in the HELPER FUNCTIONS section. 

Now, do the following:
1. Modify the code such that it registers the event handler for the `"keydown"` event.
2. Find the event handler function and add a `console.log("key pressed")` statement to its `{code block}`
3. Save your code and refresh your game. Open the running application in a new window (see below) and open the console. 
4. Press keys to make sure that the events are properly being registered.


