# Simple-Calculator
Tutorial on how to make a simple calculator using JS, CSS, and HTML
-------------

# Description
This project covers methods and their basic concepts. You will learn to declare and call functions and understand return statements, and optional arguments. With the use of all three languages, you can create a simple interface of a calculator, where you can do basic arithmetic operations.

# Difficulty
Intermediate

# Prerequisites
1. Familiarity with JavaScript
2. Familiarity with CSS
3. Familiarity with HTML

This project is to help you get a better idea of how functions function in JS(pun not intended at all)
Some key points to watch out for:
1. Creating a function
2. Declaring a function
3. Arguments / Optional arguments
4. Return Statements

# Setup
Create these files in Visual Studio Code:
1. index.html
2. script.js
3. style.css

# Part 1 HTML
1. Starting with the `<head>` tag, change the current title `'Document'` to `'Simple Calculator'`.
2. Next we want to link our CSS script and JS script. After the steps, your <head> tag should look like this:
```
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link href="styles.css" rel="stylesheet"
    <script src="script.js" defer></script>
</head>
```
3. We want to make the layout of our calculator. Most if not all calculators use a grid layout. To create this grid layout use the `<div>` tag. In the `<body>` tag implement the div tag with the class name 'simple calculator-grid'.
4. To create the output screen for the calculator we need 3 `<div>` tags. One div tag contains the other 2 div tags. The div tag containing the other two will have the class name 'output'. The other two class names will be 'previous' and 'current'.
```
 <div class="calculator-grid">
    <div class="output">
      <div data-previous-operand class="previous-operand"></div>
      <div data-current-operand class="current-operand"></div>
    </div>
```
5. Now we want to create the buttons for our calculator in the div tag right after the 'output' class. The first button will be the AC or all-clear button. This button will be huge and to set it up we need a class for it. To set it up we need `<button class="span-two">AC</button>`. For the rest of the buttons we only need `<button>operation</button>`, 'operation' being the numbers and arithmetic operations. The last button will be the '=' sign and it will take up two spaces.
```
 <button data-all-clear class="span-two">AC</button>
    <button data-delete>DEL</button>
    <button data-operation>÷</button>
    <button data-number>1</button>
    <button data-number>2</button>
    <button data-number>3</button>
    <button data-operation>*</button>
    <button data-number>4</button>
    <button data-number>5</button>
    <button data-number>6</button>
    <button data-operation>+</button>
    <button data-number>7</button>
    <button data-number>8</button>
    <button data-number>9</button>
    <button data-operation>-</button>
    <button data-number>.</button>
    <button data-number>0</button>
    <button data-equals class="span-two">=</button>
```
# Part 2 CSS
1. We want to select all our before and after elements.
2. Create the box size and set it to a border box.
3. Change the font to the desired font and set the font weight to normal. Font weight determines the boldness or lightness of the text. For the font family, it takes two arguments, one being the initial font and the second one being the backup font just in case the initial font is not found.
```
*, *::before, *::after {
  box-sizing: border-box;
  font-family: sans-serif, sans-serif;
  font-weight: normal;
}
```
4. Change the background color to your preference. For this example, a gradient will be used and the padding and margin will be both set to 0. The padding and margin are set to zero so our background can fill up the entire screen. To do so select the body element.
```
body {
  padding: 0;
  margin: 0;
  background: linear-gradient(to right, #00AAFF, #00FF6C);
}
```
5. Now to create the grid for our calculator, select the `calculator-grid`.
```
.calculator-grid {

}
```
6. Next we want to edit the layout for the calculator we need to input these items: `display`, `justify-content`, `align-items`, `min-height`, `grid-template-columns`, `grid-template-rows`.
7. Set `display` to grid, `justify-content` to center, `align-items` to center, `min-height` to 100vh, `grid-template-columns` to repeat(4, 100px),  `grid-template-columns` to minmax(120xpx, auto) repeat(5, 100px).
