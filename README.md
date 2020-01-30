# Box Walker

**Table of Contents**
- [Setup](#setup)
- [Game Description](#game-description)
- [Learning Objectives](#learning-objectives)
- [TODOs](#todos)
  - [TODO 0: Understand the Template (no coding)](#todo-0-understand-the-template-no-coding)
  - [TODO 1: Register Keyboard Inputs](#todo-1-register-keyboard-inputs)
  - [TODO 2: React to Specific Keycodes](#todo-2-react-to-specific-keycodes)
  - [TODO 3: Declare `gameItem` Variables](#todo-3-declare-gameitem-variables)
  - [TODO 4: Declare `moveGameItem` Function](#todo-4-declare-movegameitem-function)
  - [TODO 5: Update `speedX` and `speedY` with the Keyboard](#todo-5-update-speedX-and-speedY-with-the-keyboard)
  - [TODO 6: Reset `speedX` and `speedY` on `"keyup"`](#todo-6-reset-speedx-and-speedy-on-keyup)
  - [Challenge Ideas](#challenge-ideas)

# Setup

To install this project, first clone the [template](https://github.com/benspector3/asd-template/) repository by entering these commands into your bash terminal:

```bash
git clone https://github.com/benspector3/asd-template.git
rm -rf asd-template/.git
```

Then, rename the folder to `box-walker`

# Game Description

In this project we will be building a simple program that allows us to control the movement of a box with the arrow keys.

# Learning Objectives
- Become familiar with the template repository
- Learn a method for handling key events
- Write code that will be useful for pong

# TODOs

## TODO 0: Understand the Template (no coding)

Before we begin coding, open the `index.html` file and press **Preview** to see what we're starting with. It looks like the beginning of bouncing box, right?

<img src="img/preview-index.png">

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

**Add a `border-radius` property to the `#gameItem`. To make it a perfect circle, set the `border-radius` to the same value as the `width` and `height`.**

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

## TODO 1: Register Keyboard Inputs

Open the `index.js` file and find the EVENT HANDLERS section. 

Our first task is to make our game register `"keydown"` events and respond to them. We'll keep the response simple for now until we know that our code is working.

Now, do the following:
1. Find the event handler function `handleEvent` and change its name to `handleKeyDown`. Then, add a `console.log()` statement to its `{code block}` that prints the keycode of the key pressed:

```js
function handleKeyDown(event) {
  var keycode = ???;
  console.log("key pressed: " + keycode);
}
```

**HINT:** How do you know _which_ key was pressed when given the `event` object?

2. Modify the `turnOnEvents` function such that your new event handler listens for the `"keydown"` event:

```js
$(document).on("keydown", handleKeyDown);
```

3. Save your code and refresh your game. Open the running application in a new window (see below)

<img src='img/pop-into-window.png' height=400>

4. Open the console, then press keys to make sure that the events are properly being registered.

<img src='img/keycode-console.png'>

## TODO 2: React to Specific Keycodes

Now that we know our `"keydown"` events are being handled, let's figure out exactly _which_ keys are being pressed. Do the following:

1. Declare a new _constant variable_ `KEY` in the INITALIZATION section and assign an Object to it. The object should map the keycodes for the following keys: `"LEFT"`, `"UP"`, `"RIGHT"`, `"DOWN"`.

Example: 

```js
var KEY = {
  "ENTER": 13,
}
```

2. Modify your `handleKeyDown` function such that it can print out `"left pressed"` when the left arrow is pressed. Do the same for the other arrow keys.

3. Save your code and refresh your application in the other window. Test it to make sure that the right messages are being printed to the console.

## TODO 3: Declare `gameItem` Variables

Now that we can determine which keys are being pressed, we can move on to the problem of moving the `gameItem`. 

This is actually a problem we've already solved in **Bouncing Box**. To move the box, we needed the following data:

```js
var positionX = 0; // the x-coordinate location for the box
var speedX = 0; // the speed for the box along the x-axis
```

For this project, we want to be able to move along the x-axis _AND_ the y-axis.

Declare 4 variables for the `gameItem` such that we can monitor and control the following information:
- the x-coordinate location
- the y-coordinate location
- the speed along the x-axis
- the speed along the y-axis

**Initialize each variable to hold the value `0`**

## TODO 4: Declare `moveGameItem` Function

Now that we have our data tracking in place, we need to use that data to actually move the `gameItem` on each `update`. Again, this is a problem solved in Bouncing Box:

```js
function moveBox() {
  positionX += speedX;
  $box.css("left", positionX);
}
```

1. In the HELPER FUNCTIONS section, declare a new function called `moveGameItem()`.
2. Reference the above code to write the code for `moveGameItem` to make the `gameItem` move along the x-axis AND the y-axis. 
2. Call the function on each `update`.

**HINT:** Use the `"top"` CSS property to adjust the y-coordinate location of the box.

Save your code and refresh the game. If you try pressing keys you'll notice that the box isn't moving. 

**Question: why doesn't the box move yet? Try using the debugger to figure out why.**

## TODO 5: Update `speedX` and `speedY` with the Keyboard

The box isn't moving yet because we initialized `speedX` and `speedY` to `0` and, so far, have no way of changing those values.

As long as `speedX` is `0`, the `gameItem` will not move along the x-axis. Same goes for `speedY` and the y-axis.

Whenever we press a key, we want the `gameItem` to move in that direction. So, modify your `handleKeyDown` function such that when the `KEY.LEFT` key is pressed, the `speedX` is set to `-5`:

```js
if (keycode === KEY.LEFT) {
  speedX = -5;
}
```

Do the same for the other 3 arrow keys.

**Question: Why does the box only move diagonally after your press the keys?**

## TODO 6: Reset `speedX` and `speedY` on `"keyup"`

We now have motion! However, the `gameItem` doesn't stop moving once we set it off. We need some way to stop it from moving. 

Ideally, the `gameItem` would stop moving once we release the arrow key. This `"keyup"` event can be listened for in the same way that the `"keydown"` event can be listened for.

**Using the code that you've already written, set up your program to listen for `"keyup"` events and set the `speedX` and `speedY` variables to `0` whenever the arrow keys are released**

# Challenge Ideas:

## Prevent the box from leaving the bounds of the board.

## Make the box rotate whenever the space bar is pressed

## Make the box change to a random color whenever the enter button is pressed

