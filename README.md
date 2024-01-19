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
5. Now we want to create the buttons for our calculator in the div tag right after the 'output' class. The first button will be the AC or all-clear button. This button will be huge and to set it up we need a class for it. To set it up we need `<button class="span-two">AC</button>`. For the rest of the buttons we only need `<button>data-fill</button>`, 'fill' being number for the number buttons and operation for the arithmetic operation numbers. The last button will be the '=' sign and it will take up two spaces.
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
5. Now to create the grid for our calculator, select the `calculator-grid` class we created.
```
.calculator-grid {

}
```
6. Next we want to edit the layout for the calculator we need to input these items: `display`, `justify-content`, `align-items`, `min-height`, `grid-template-columns`, `grid-template-rows`.
7. Set `display` to grid, `justify-content` to center, `align-content` to center, `min-height` to 100vh, `grid-template-columns` to repeat(4, 100px),  `grid-template-columns` to minmax(120xpx, auto) repeat(5, 100px).
8. Notice the calculator buttons are lacking color and the numbers look really small? We can customize this by selecting the `.calculator-grid > button` class. Set `cursor:` to pointer, `font-size:` to 2rem, `border:` to 1px solid white, `outline:` to none, and `background-color:` to rgba(55, 255, 255, .75).
```
  .calculator-grid > button {

  }
```
9. Now we want to make it when the cursor hovers over the button it changes color. To do so create another function just like we did in the previous step but instead put `.calculator-grid > button:hover` and set the `background-color:` to `rgba(255, 255, 255, .9)`

10. You've probably noticed that the buttons now are in the right places but the 'AC' button and '=' button aren't taking up two spaces. To fix that we need to call the class `.span-two` and inside the class set `grid-column: span 2`.
11. Now the output looks like it's a button but we want it to have its own screen above the rest of our buttons. We call the output class and set its column to 1 / -1. Next, set its `background-color:` to black with 75 transparency.
```
.output {
    grid-column: 1 / -1;
    background-color: rgba(0, 0, 0, .75);
}
```
11. We then want to format the current and previous operands in our output screen. To do so we need to add the following: `display: flex;`, `align-items: flex-end;`, `justify-content: space-around;`, `flex-direction: column;`, `padding: 10px;`, `word-wrap: break-word;`, and `word-break: break-all;`.
12. Now the text sizes are not filling up the screen too well so we can call the classes for both the previous and current operand to fix that.
```
.output .previous-operand {
  color: rgba(255, 255, 255, .75);
  font-size: 1.5rem;
}

.output .current-operand {
  color: white;
  font-size: 2.5rem;
}
```
# Part 3 JS
1. We want to select our buttons and to do so we need to create the variables for them.
```
const numberButtons = document.querySelectorAll('[data-number]')
const operationButtons = document.querySelectorAll('[data-operation]')
const equalsButton = document.querySelector('[data-equals]')
const deleteButton = document.querySelector('[data-delete]')
const allClearButton = document.querySelector('[data-all-clear]')
const previousOperandTextElement = document.querySelector('[data-previous-operand]')
const currentOperandTextElement = document.querySelector('[data-current-operand]')
```
2. Now we want to make a `calculator class` to store all the information so that our calculator can function properly. Place it atop the variables we just created. We then want to create a constructor method to store all the inputs and functions for our calculator. The constructor method will take on two arguments `perviousOperandTextElement` and `currentOperandTextElement`. Then add the following to the method: `this.previousOperandTextElement = previousOperandTextElement`, `this.currentOperandTextElement = currentOperandTextElement`, `this.clear()`.
3. Next we need to create the following functions:
```
 clear() {
    this.currentOperand = ''
    this.previousOperand = ''
    this.operation = undefined
  }

  delete() {
    this.currentOperand = this.currentOperand.toString().slice(0, -1)
  }

  appendNumber(number) {
    if (number === '.' && this.currentOperand.includes('.')) return
    this.currentOperand = this.currentOperand.toString() + number.toString()
  }

  chooseOperation(operation) {
    if (this.currentOperand === '') return
    if (this.previousOperand !== '') {
      this.compute()
    }
    this.operation = operation
    this.previousOperand = this.currentOperand
    this.currentOperand = ''
  }

  compute() {
    let computation
    const prev = parseFloat(this.previousOperand)
    const current = parseFloat(this.currentOperand)
    if (isNaN(prev) || isNaN(current)) return
    switch (this.operation) {
      case '+':
        computation = prev + current
        break
      case '-':
        computation = prev - current
        break
      case '*':
        computation = prev * current
        break
      case '÷':
        computation = prev / current
        break
      default:
        return
    }
    this.currentOperand = computation
    this.operation = undefined
    this.previousOperand = ''
  }

  getDisplayNumber(number) {
    const stringNumber = number.toString()
    const integerDigits = parseFloat(stringNumber.split('.')[0])
    const decimalDigits = stringNumber.split('.')[1]
    let integerDisplay
    if (isNaN(integerDigits)) {
      integerDisplay = ''
    } else {
      integerDisplay = integerDigits.toLocaleString('en', { maximumFractionDigits: 0 })
    }
    if (decimalDigits != null) {
      return `${integerDisplay}.${decimalDigits}`
    } else {
      return integerDisplay
    }
  }

  updateDisplay() {
    this.currentOperandTextElement.innerText =
      this.getDisplayNumber(this.currentOperand)
    if (this.operation != null) {
      this.previousOperandTextElement.innerText =
        `${this.getDisplayNumber(this.previousOperand)} ${this.operation}`
    } else {
      this.previousOperandTextElement.innerText = ''
    }
  }
```
These functions all carry out the operations of our calculator. When a function is called the actions in the function are carried out. Some functions take on arguments, these functions take the given input and deliver an output. When a function that takes arguments is called but with no given input or argument a default output will be returned.

The `clear function` is pretty straightforward, it sets the screen blank when it is called. The `delete()` function deletes the current number every time it is called. The `appendNumber()` function adds numbers to the screen. The `chooseOperation()` function deals with whenever the user clicks an operation. The `comp[ut()` function returns the results of the operation(s). The last function is the `updateDisplay()` function updates the values inside of the output screen.
4. After creating all the functions we then need to set up the variables we previously created to operate on our calculator. To do so we need to create a calculator object.
```
const calculator = new Calculator(previousOperandTextElement, currentOperandTextElement)
```
5. We then want to create a listener for our number buttons. Then we want it to append the numbers when number buttons are pressed.
```
numberButtons.forEach(button => {
  button.addEventListener('click', () => {
    calculator.appendNumber(button.innerText)
    calculator.updateDisplay()
  })
})
```
6. For the next functions they all follow the same steps where we create a function for the type of button and create a listener. These functions carry out the ability of the calculator to carry out the operations of our calculator by listening for inputs and giving an output.
```
operationButtons.forEach(button => {
  button.addEventListener('click', () => {
    calculator.chooseOperation(button.innerText)
    calculator.updateDisplay()
  })
})

equalsButton.addEventListener('click', button => {
  calculator.compute()
  calculator.updateDisplay()
})

allClearButton.addEventListener('click', button => {
  calculator.clear()
  calculator.updateDisplay()
})

deleteButton.addEventListener('click', button => {
  calculator.delete()
  calculator.updateDisplay()
})
```









