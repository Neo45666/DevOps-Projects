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
### Example script to print numbers from 1 to 5 using a for loop¬

`for (( i=1; i<=5; i++ ))`
`do`
    `echo $i`

`done`

![sample_for_loop](./images/sample_for_loop.PNG)


## Command Substitution
Using backtick for command substitution

`current_date = date +%Y-%m-%d`
Using `$()` syntax for command substitution

### Input and Output 
Bash provides various ways to handle input and output. You can use the read command to accept user input and ,output using operators like > (output to a file), < (input from a file), and | (pipe the output of one command as input to another)

`echo "Enter your name:"`
`read name`

### Output text to the terminal 

`echo "Hello World"`

To out the result of a command into a file:
`echo "hello world" > index.txt`

To pass the result of a command as input to another command 

`echo "hello world" | grep "pattern"`

## Functions
Bash allows you to define and use functions to group related commands together. Functions provide a way to modularize your code and make it more reusable.

![input_output](./images/input_output.PNG)

## Write a shell script
Step 1: Open a folder called shell scripting using `mkdir shell-scripting`. This would hold all the script we will write

Step 2: Create a file called "user-input.sh" using the command `touch user-input.sh`

Step 3: Paste the block of code inside 

Step 4: Save file

Step 5: Run the command `sudo chmod +x user-input.sh` this makes the file executable

Step 6: Run the script using the command `./user-input.sh`

![executable_file](./images/executable_file.PNG)

## Directory Manipulation and Navigation

Step 1: open a file named *navigating-linux-filesystem.sh*

Step 2: paste the code block into the file

Step 3: Run the command `sudo chmod +x navigating-linus-filesystem.sh` to set execute permission on the file.

Step 4: Run your script using this command  `./navigating-linux-filesystem.sh`







