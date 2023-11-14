---
title: Fancy JS Calculator
comments: false
hide: true
layout: post
description: Here is the code of an improved calculator I found and customized by changing the button colors to blue to better fit my theme. 
courses: {csp: {week: 2} }
type: hacks
---

<div id="calculator">
    <input type="text" id="display" readonly>
    <div id="buttons">
        <button onclick="appendToDisplay('1')">1</button>
        <button onclick="appendToDisplay('2')">2</button>
        <button onclick="appendToDisplay('3')">3</button>
        <button onclick="appendToDisplay('+')">+</button>
        <button onclick="appendToDisplay('4')">4</button>
        <button onclick="appendToDisplay('5')">5</button>
        <button onclick="appendToDisplay('6')">6</button>
        <button onclick="appendToDisplay('-')">-</button>
        <button onclick="appendToDisplay('7')">7</button>
        <button onclick="appendToDisplay('8')">8</button>
        <button onclick="appendToDisplay('9')">9</button>
        <button onclick="appendToDisplay('*')">*</button>
        <button onclick="clearDisplay()">C</button>
        <button onclick="appendToDisplay('0')">0</button>
        <button onclick="calculate()">=</button>
        <button onclick="appendToDisplay('/')">/</button>
    </div>
</div>
<style>
/* Calculator Container */
#calculator {
    width: 300px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    background-color: #F7F7F7;
    text-align: center;
}
/* Calculator Display */
#display {
    width: 100%;
    height: 40px;
    margin-bottom: 10px;
    font-size: 18px;
    text-align: right;
    padding: 5px;
    background-color: #fff;
    border: 1px solid #ccc;
    border-radius: 3px;
    box-shadow: inset 0 0 5px rgba(0, 0, 0, 0.2);
}
/* Calculator Buttons */
#buttons button {
    width: 50px;
    height: 50px;
    font-size: 18px;
    margin: 5px;
    cursor: pointer;
    border: 1px solid #ccc;
    border-radius: 3px;
    background-color: #E0E8F9; /* Light blue background */
    color: #333;
}
/* Calculator Buttons (Operator Buttons) */
#buttons button:nth-child(4n-3),
#buttons button:nth-child(4n-2),
#buttons button:nth-child(4n-1),
#buttons button:last-child {
    background-color: #4285F4; /* Dark blue background for operators */
    color: #fff;
    border: 1px solid #4285F4;
}
/* Calculator Buttons (Clear and Equals) */
#buttons button:nth-child(13),
#buttons button:nth-child(16) {
    background-color: #FF3333;
    color: #fff;
    border: 1px solid #FF3333;
}
</style>
<script>
function appendToDisplay(value) {
    document.getElementById('display').value += value;
}
function clearDisplay() {
    document.getElementById('display').value = '';
}
function calculate() {
    try {
        document.getElementById('display').value = eval(document.getElementById('display').value);
    } catch (error) {
        document.getElementById('display').value = 'Error';
    }
}
</script>