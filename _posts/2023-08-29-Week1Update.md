---
comments: false
layout: post
title: Week1 Update
description: What I have accomplished after Week1
type: hacks
courses: { csp: {week: 1}}
---

# Week1 Update

## Bash and Linux Hacks

Important Linux commands:

- ls - The most frequently used command in Linux to list directories
- pwd - Print working directory command in Linux
- cd - Linux command to navigate through directories
- mkdir - Command used to create directories in Linux
- rm - Delete files or directories
- cat - Display file contents on the terminal
- clear - Clear the terminal display
- echo - Print any text that follows the command
- man - Access manual pages for all Linux commands
- whoami - Get the active username
- tar - Command to extract and compress files in Linux
- grep - Search for a string within an output
- sudo - super user

My Bash Script to make sure I have required software:

```bash

#!/bin/bash

# Check if Visual Studio Code is installed
if command -v code &>/dev/null; then
    echo "Visual Studio Code is installed."
else
    echo "Visual Studio Code is not installed."
fi

# Check if Jupyter Notebook is installed
if command -v jupyter &>/dev/null; then
    echo "Jupyter Notebook is installed."
else
    echo "Jupyter Notebook is not installed."
fi

# Check if Python is installed
if command -v python &>/dev/null; then
    echo "Python is installed."
else
    echo "Python is not installed."
fi

- chmod +x check_requirements.sh
# This gives an executable permission so that I can run the script**

- ./check_requirements.sh
# This runs the script
```

Here are commands I learned for updating a repository using the git command line:

- git add --all

- git status (optional)

- git commit -m 'type any message here'

- git push

-git pull 

# Javascript

## Hacks completed Pseudo Code vs Python vs JavaScript

This was a hack which helped me understand Javascript better when comparing it to simpler languages like python helping me better understand the syntax:

```Javascript

%%js%%

let a = 1;
let b = 1;
if (a === b) {
    //Establishes variables and criteria
    console.log("A equals B");
}

//console.log stores the information and outputs it, unlike print which just outputs static text

//Program using iteration (Repeat N Times/Sum all numbers/Print result)

let sum = 0;
for (let i = 1; i <= 100; i++) {
// Structure of javascript for loop: for(initialize; condition; iteration)
    sum += i;
//Uses sum module which initiates code given the criteria. 
}

console.log("Sum of numbers from 1 to 100:", sum);
//Outputs and stores sum

```

<html>
<head>
    <title>Calculator</title>
    <style>
        #calculator {
            width: 300px;
            margin: 50px auto;
            border: 1px solid #ccc;
            padding: 10px;
            text-align: center;
        }
    </style>
</head>
<body>
    <div id="calculator">
        <input type="text" id="display" readonly>
        <br>
        <button onclick="appendToDisplay('7')">7</button>
        <button onclick="appendToDisplay('8')">8</button>
        <button onclick="appendToDisplay('9')">9</button>
        <button onclick="appendToDisplay('+')">+</button>
        <br>
        <button onclick="appendToDisplay('4')">4</button>
        <button onclick="appendToDisplay('5')">5</button>
        <button onclick="appendToDisplay('6')">6</button>
        <button onclick="appendToDisplay('-')">-</button>
        <br>
        <button onclick="appendToDisplay('1')">1</button>
        <button onclick="appendToDisplay('2')">2</button>
        <button onclick="appendToDisplay('3')">3</button>
        <button onclick="appendToDisplay('*')">*</button>
        <br>
        <button onclick="appendToDisplay('0')">0</button>
        <button onclick="appendToDisplay('.')">.</button>
        <button onclick="calculateResult()">=</button>
        <button onclick="appendToDisplay('/')">/</button>
        <br>
        <button onclick="clearDisplay()">C</button>
    </div>
    
    <script>
        let currentInput = '';

        function appendToDisplay(value) {
            currentInput += value;
            updateDisplay();
        }

        function updateDisplay() {
            document.getElementById('display').value = currentInput;
        }

        function clearDisplay() {
            currentInput = '';
            updateDisplay();
        }

        function calculateResult() {
            try {
                currentInput = eval(currentInput).toString();
                updateDisplay();
            } catch (error) {
                currentInput = 'Error';
                updateDisplay();
            }
        }
    </script>
</body>
</html>

Here is my raw Javascript code for this calculator:

```Javascript 

// calculator.
let currentInput = '';
// Defining user input
function appendToDisplay(value) {
    currentInput += value;
    updateDisplay();
}

function updateDisplay() {
    document.getElementById('display').value = currentInput;
}

function clearDisplay() {
    currentInput = '';
    updateDisplay();
}

function calculateResult() {
    try {
        currentInput = eval(currentInput).toString();
        updateDisplay();
    } catch (error) {
        currentInput = 'Error';
        updateDisplay();
    }
}

```