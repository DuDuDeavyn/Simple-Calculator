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
1. Starting with the <head> tag, change the current title 'Document' to 'Simple Calculator'.
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
3. We want to make the layout of our calculator. Most if not all calculators use a grid layout. To create this grid layout use the <div> tag. In the <body> tag implement the <div> tag with the class name 'simple calculator-grid'.
4. To create the output screen for the calculator we need 3 <div> tags. One <div> tag contains the other 2 <div> tags. The <div> containing the other two will have the class name 'output'. The other two class names will be 'previous' and 'current'.
```
 <div class="calculator-grid">
    <div class="output">
      <div data-previous-operand class="previous-operand"></div>
      <div data-current-operand class="current-operand"></div>
    </div>
```

