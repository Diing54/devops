 
2025-02-15 15:14

Level : #baby

Tags : [[linux]]

# Bash Scripting

# Intro
A bash script is a file containing lines of code either simple commands or complex ones that can either navigate directories or create other stuff ; in simple words they can do a series of actions. Basically they can run bash commands eg ls , mkdir, ps, grep ,touch ,rm etc. A bash script can be executed and the lines of code inside it will be run line by line.


# Advantages of bash scripting 
1. Automation - Shell scripts allow a user to automate repetitive tasks hence saving on time and minimizing the risk of human error
2. Portability -  Can run on various OS including windows through VM's
3. HIghly flexible as they can be customized easily
4. Easy to write as they require any special software
5. Integration - Shell scripts can be integrated with other tools and applications and cloud services allowing for more complex automation and system management tasks
6. Debugging - They are easy to debug and most of them have built-in debugging and error-reporting tools
- NOTE : Shell is a program responsible for displaying of an interface for interacting the OS(CLI- Command Line Interface). Bash is a type of shell
## Creating and executing bash scripts
- Bash scripts end with .sh
- A bash script starts with a shebang. This is the first line which must be present in a script which specifies the interpreter that will be used when executing the script. This allows users to leverage the power of different interpreters. Shebang tells the shell to execute it via bash shell
- When saving a script file, its is good practice to place commonly used scripts in the ~/bin/ directory
- The script files also need to have the execute permission to allow them to run
- An example of a shebang statement (#!/bin/bash)
- ![image](https://github.com/user-attachments/assets/9569a3c0-9d0a-4b2a-9eb8-dcd8af079d8c)





- The read command reads the input and stores it in the variable path
- The ls -al command takes the variable with the stored path and displays the details of the path
- We can then run the script using the following commands :
1. sh hello.sh
2. bash hello.sh - These commands(sh hello.sh) must be specified with the directory of the bash script if not in the bash script directory
3. ./hello.sh - ./ tells the bash to execute hello.sh in the current working directory. We can use hello.sh to execute the bash script while on any directory of the terminal if the path of the script file is added to the $PATH variable
4. . hello.sh 
     When a script is executed using either the bash command or the dot (.) command, you do not have to set executable
permissions on script but read permissions need to be set.
## Variables and data types 
- Variables store data which can be read, accessed and manipulated eg : name=John
- We can also set a variable to a path of a particular directory as shown below
     path=/etc
- $ is required to access the variable's content
- The naming conventions of a variable are :
1. Variable names should start with a letter or an underscore (`_`).
2. Variable names can contain letters, numbers, and underscores (_).
3. Variable names are case-sensitive.
4. Variable names should not contain spaces or special characters.
## Command line Arguments
- Command line arguments allow users to pass data to a bash script at runtime, These arguments are accessible inside the script using special variables.
- The command line arguments are stored in special variables:
     - $0  = The name of the script
     - $1, $2, $3, ....... = First, second, third argument respectively etc
     - $# - Total number of arguments passed to the bash script
     - $@ - All the arguments supplied to the bash script
     - $ $ - The process ID of the current script
     - $USER - The username of the user running the script
     - $HOSTNAME - The hostname of the machine the script is running on.
- Example showcasing command line arguments:
  ![image](https://github.com/user-attachments/assets/f7eed79e-a831-4839-b5fb-fd7b392a16b1)

  ![image](https://github.com/user-attachments/assets/c78722de-96a5-4b14-82c3-723f6fa77d19)

  ![image](https://github.com/user-attachments/assets/335dda0c-1c25-4217-8a55-29e7fc022d26)

  

     
     
## Quotes
- We use quotes to enclose the values being assigned to a variable if we are working with complex values or values with spaces between. If we dont use quotes eg var=Hello World, there will be an error because by default, bash uses space for separate items.
- Commands work in the same way in the command line as they work in a script so we can just work in the command line for easier demonstration.
- We enclose content in quotes so bash can consider it as a single item. We can use single quotes or double quotes
- Single quotes will treat every character literally while double quotes may allow us to include other variables as part of the value as shown below :
  
  ![image](https://github.com/user-attachments/assets/4cbf654a-9657-4b6f-96b9-36526118e35a)

## Command Substitution
This allows us to take the output of a command or program and save it as a value of a variable 
![Screenshot_2025-04-14_18-23-51](https://github.com/user-attachments/assets/a589920f-453b-4ce9-8c92-368e836fb924)

## Exporting Variables
When you run a shell script e.g. bash hello.sh, it starts a new  process that is separate from the shell you are currently in. Its like opening a new mini terminal behind the scenes to run that script.
Each process in Linux has its own memory - and variables live in memory - so a variable in your current shell won't automatically be visible to that new process.
"Variables are limited to the process they were created in".
### Example
##### script1.sh
myname="Chiman"
bash script2.sh
##### script2.sh
echo "Hello $myname"
When you run `script1.sh`, it starts a new process (`script2.sh`). But unless `myname` is **exported**, `script2.sh` will print nothing because it doesn't know `myname` exists.
To solve this problem we need to export the variable; 
export myname="Chiman"
bash script2.sh

## Input
The read command takes user input and saves it into a variable.
![Screenshot From 2025-04-18 20-16-46](https://github.com/user-attachments/assets/ba466b7c-6b83-45dc-a551-388af24c59af)

You can use the -p option which allows you to specify the kind of input the user should enter and also -s which makes the input silent, e.g. prompting a user their username and password
1. read -p 'Username: ' uservar
2. read -sp 'Password: ' passvar
## STDIN / STDOUT / STDERR

(Will comeback to this when learning pipes)

## Arithmetic
Bash supports several ways to do arithmetic.
1. let
2. expr
3. Double parentheses (( ))
4. Length of a variable ${#var} - useful for strings
### Let - A basic built-in command 
let a=5+4         # No spaces allowed unless in quotes
echo $a           # 9

let "a = 5 + 4"   # You can use quotes to allow spaces
echo $a           # 9

let a++           # Increment a by 1
echo $a           # 10

let "a = 4 * 5"   # Multiplication
echo $a           # 20

let "a = $1 + 30" # Use a command-line argument

| Operator | Meaning                             |
| -------- | ----------------------------------- |
| `+`      | Addition                            |
| `-`      | Subtraction                         |
| `*`      | Multiplication (use `\*` in `expr`) |
| `/`      | Division                            |
| `%`      | Modulus (remainder)                 |
| `var++`  | Increment by 1                      |
| `var--`  | Decrement by 1                      |
### expr - Print results and does not store

expr item1 operator item2

expr 5 + 4        # Outputs: 9
expr "5 + 4"      # Wrong: Just prints the string
expr 5+4          # Wrong: No spaces = no evaluation
expr 5 \ * 4       # Right: Use \ * to escape the multiplication symbol
expr 11 % 2       # Outputs: 1

a=$(expr 10 - 3)  # Store result into variable a
echo $a           # 7

### ((  )) - Recommended way to do arithmetic

variable=$((expression))

(( expression ))  # For in-place operations like incrementing

a=$((4 + 5))      # 9
echo $a

a=$((3+5))        # 8
b=$((a + 3))      # 11
b=$(( $a + 4 ))   # 12

(( b++ ))         # Increment b by 1 => 13
(( b += 3 ))      # b = b + 3 => 16
a=$(( 4 * 5 ))    # 20

### `${#variable}` – Get String Length

a="Hello World"
echo ${#a}   # 11

b=4953
echo ${#b}   # 4

## If Statements
If statements help the script to make decisions ;
if [ <some test> ]
then
    <commands>
fi

#!/bin/bash
# Basic if statement
if [ $1 -gt 100 ]
then
    echo Hey that\'s a large number.
    pwd
fi
date

- `$1` is the **first command-line argument**.
    
- `-gt` means **greater than**.
    
- If `$1` is greater than 100:
    
    - It prints a message.
        
    - Shows current directory (`pwd`).
        
- `fi` marks the **end** of the if statement.
    
- `date` runs no matter what.

./if_example.sh 15     # Only date will be printed
./if_example.sh 150    # Message, directory, and date will be printed


In `[ $1 -gt 100 ]`, the square brackets `[` `]` are a way to call the `test` command.
Common test operators;
! EXPRESSION | Not true
-n STRING | String is not empty
-z STRING | String is empty
STRING1 = STRING2 | Strings are equal
STRING1 != STRING2 | Strings are not equal
INT1 -eq INT2 | Equal numbers
INT1 -gt INT2 | Greater than
-e FILE | File exists
-s FILE | File exists and is not empty
-x FILE | File exists and is executable



## References
 Bash scripting by freecodecamp (https://www.freecodecamp.org/news/bash-scripting-tutorial-linux-shell-script-and-command-line-for-beginners/)

  https://ryanstutorials.net/bash-scripting-tutorial/
