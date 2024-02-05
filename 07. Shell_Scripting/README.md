# Shell Scripting

Shell scritpting helps automate repititive task. Bash scripts are essentially a series of commands and instructions that are executed sequentially in a shell. You can create a shell script by saving collection of commands in a text file with a .sh extension. These scripts can be executed directly from the command line or called from other scripts. 

## Shell Scripting Syntax Elements 

### 1. Variables 
Bash allows you to define and work with variables. Variables can store data of various types such as numbers, strings, and arrays. You can assign values to variables using the = operator, and access their values using the variable name preceded by a $ sign. 

### Assigning value to a variable 

`name="John"` 

### Retrieving value from a variable 

`echo $name`

### 2. Control Flow

Bash provides control flow statements like if-else, for loops, while loops, and case statements to control the flow of execution in your scripts. These statements allow you to make decisions, iterate over list, and execute different commands based on conditions.

Uisng if-else to execute script based on a conditions

`#!/bin/bash`
`Example script to check if a number is positive, negative, or zero`

`read -p "Enter a number" num`

`if [ $num -gt 0]; then`
    `echo "The number is positive"`
`elif [$num -1t 0 ]; then`
    `echo "The number is negative"`
`else`
    `echo "The number is zero"`
`fi`

![control_flow](./images/control_flow_sample_script.PNG)

The piece of code prompts you to type a number and prints a statement stating the number is positive or negative. 

### Iterating through a list using a for loop

`#!/bin/bash`
# Example script to print numbers from 1 to 5 using a for loop¬

`for (( i=1; i<=5; i++ ))`
`do`
    `echo $i`

`done`

![sample_for_loop](./images/sample_for_loop.PNG)

