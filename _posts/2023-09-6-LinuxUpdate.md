---
comments: False
layout: post
title: Linux Interaction with VScode
description: Improving my previous bash script... 
type: hacks
courses: {'csp': {'week': 3}}
---

Here was the bash script I showed to you on the first peer review:

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

Although this script worked fine, it lacked practical use. Here are some things I added to improve it:

- Modularization (I split my program to check for components individually). This adds functionality incase the user doesn't want to run through the whole process. It also organizes the code better.

- User input and output were used in order to ask the user what specific components they wanted checked.

- Information processed will be logged so that a user can check it in order to make sure they have all the required software. In a small scale script like this it doesn't make much of a difference. But in a real working environment it would help. 

# Modularization:

```bash

#!/bin/bash

check_installed() {
    command -v "$1" &>/dev/null
    if [ $? -eq 0 ]; then
        echo "$1 is installed."
    else
        echo "$1 is not installed."
    fi
}

# Check for Visual Studio Code
check_installed "code"

# Check for Jupyter Notebook
check_installed "jupyter"

# Check for Python
check_installed "python"

```

# User Inputs and Options

```bash

#!/bin/bash

while getopts ":cjp" opt; do
    case $opt in
        c)
            check_installed "code"
            ;;
        j)
            check_installed "jupyter"
            ;;
        p)
            check_installed "python"
            ;;
        \?)
            echo "Invalid option: -$OPTARG"
            ;;
    esac
done

```

Note: You can specify things individually if you just want to check if you have one of these programs installed and working. Run the script with options like:

- -c for Visual Studio Code 
- -j for Jupyter Notebook
- -p for Python.

```bash

./check_requirements.sh -c
./check_requirements.sh -j
./check_requirements.sh -p

```

# Logging:

```bash

#!/bin/bash

log_file="check_requirements.log"

check_installed() {
    command -v "$1" &>/dev/null
    if [ $? -eq 0 ]; then
        echo "$1 is installed."
        echo "$1 is installed." >> "$log_file"
    else
        echo "$1 is not installed."
        echo "$1 is not installed." >> "$log_file"
    fi
}

# Check for Visual Studio Code
check_installed "code"

# Check for Jupyter Notebook
check_installed "jupyter"

# Check for Python
check_installed "python"

```

The results of this script will be logged in in a file named check_requirements.log

By implementing these enhancements I made my script more user friendly and versatile.

- Users can be decide what elements of the script they want checked

- Users can check logs for future reference