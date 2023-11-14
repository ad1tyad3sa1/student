---
comments: false
layout: post
title: Testing Errors
description: Tester function with if / else and try / catch (except) statements. 
type: hacks 
courses: { csp: {week: 4}}
---

Types of Errors:

Logic: The program lacks sufficient amount of logic in the code outputting something that may not make sense.

Syntax: Code  is not written in an understandable way for the computer, preventing it from running.

Run Time: While running a program, there is a error preventing the error from running. (For example invalid input which is why we should have an else statement that urges the user to enter a valid input)

Overflow: Output value is outside the defined outputs which results in the program crashing. (Calculator with only 4 decimal values can't calculate 100*100)

Here is my tester function:

```python
import subprocess

def run_program_and_validate(program_path, input_data, expected_output):
    try:
        # Run the program and capture its output
        process = subprocess.Popen(
            program_path,
            stdin=subprocess.PIPE,
            stdout=subprocess.PIPE,
            stderr=subprocess.PIPE,
            text=True
        )
        stdout, stderr = process.communicate(input_data)

        # Check if the program returned successfully (exit code 0)
        if process.returncode != 0:
            return False, f"Program exited with code {process.returncode}\n{stderr}"

        # Compare the actual output with the expected output
        if stdout.strip() == expected_output.strip():
            return True, "Test passed!"
        else:
            return False, "Test failed. Output did not match the expected result."

    except Exception as e:
        return False, f"An error occurred: {str(e)}"


# Example usage:
if __name__ == "__main__":
    program_path = "your_program.py"
    input_data = "input_data_here"
    expected_output = "expected_output_here"

    result, message = run_program_and_validate(program_path, input_data, expected_output)

    if result:
        print("Test passed!")
    else:
        print("Test failed:", message)

```

We could use try catch statements to debug code as shown below:

In python catch statements are written as expect

```python 
try:
    # Code that may raise an exception
    result = 10 / 0
    print(result)
except ZeroDivisionError as e:
    # Handle the specific exception
    print("Error:", e)
except Exception as e:
    # Handle other exceptions
    print("An error occurred:", e)
else:
    # Code that runs if there are no exceptions
    print("No errors occurred.")
finally:
    # Optional: Code that runs regardless of whether there was an error or not
    cleanup_resources()

```

Below is a simple odd/even number identifier which shows comments and code logic that reduces errors in code with if / else statements:

# Example: Checking if a number is even or odd

```python

try:
    # Get user input
    user_input = input("Enter a number: ")
    
    # Convert input to an integer
    number = int(user_input)
    
    # Check if the number is even or odd
    if number % 2 == 0:
        print("The number is even.")
    else:
        print("The number is odd.")
    
except ValueError:
    # Handle the case where the user doesn't enter a valid number
    print("Invalid input. Please enter a valid number.")
except Exception as e:
    # Handle other exceptions gracefully
    print("An error occurred:", e)

```

Specifics:

Try Block: This is where you put the code that may raise an exception. In this case, it's user input and conversion to an integer.

If-Else Statements: These are used to make a decision based on the condition. We're checking if the number is even or odd.

Except Blocks: These blocks handle exceptions. In the first except block, we handle the specific exception ValueError that occurs if the user doesn't enter a valid number. In the second except block, we handle other exceptions gracefully.

