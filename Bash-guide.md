# BASH scripting syntax guide 

A quick reference for commonly used Bash syntax.

## Contents
- [BASH Overview](#bash-overview)
- [Declaring Variables](#declaring-variables)
- [Arithmetic Expressions](#arithmetic)
- [Conditional Statements](#conditional-statements)
- [Looping Constructs](#looping-constructs)
- [Exit Codes](#exit-codes)
- [Functions](#functions)
- [Arrays](#arrays)
- [Learn More](#learn-more)

## BASH Overview
__What is BASH__

Bash is a Unix shell that interprets command-line input and provides a scripting language for automating system tasks.

__What makes bash different from other programming language?__

Bash is fundamentally different from general-purpose programming languages because it is designed to orchestrate programs, not to build standalone applications.

At its core, Bash excels at gluing together existing system tools, managing processes, and automating operating-system tasks rather than implementing complex algorithms.


## Declaring Variables

```bash
# store the value "foo" in the variable var
var="foo"

# Print the content of the variable to STDOUT
echo $var
```

__Capturing the output of a command and saving as variable__

```bash
#store the output of the ls command in the ls_contents variable
ls_contents=$(ls)
echo $ls_contents
```

__Special Variables__

Special variables in BASH are predefined variables that store system or shell info, or last command status.

| Variable | Meaning / Use |
|----------|---------------|
| `$?`     | Exit status of the last command |
| `$$`     | PID of the current shell |
| `$!`     | PID of the last background process |
| `$0`     | Name of the script or shell |
| `$#`     | Number of positional parameters |
| `$*`     | All positional parameters as a single string |
| `$@`     | All positional parameters as separate strings |
| `$1, $2…` | First, second, … positional parameter |



## Arithmetic Expressions
Bash does integer-only arithmetic by default. No floating point unless you call external tools.


```bash
#Evaluate expression an expression
#You can use the standard arithmetic expression with the expr command.

expr 30 + 40

#Except for multiplication:
expr 100 \* 4
```
Another method of evaluating arithmetic operations is using 
Bash’s built-in arithmetic evaluation syntax.

```bash
#This evaluates the expression below and and returns a success/failure exit status. 
#It does not print the result to STDOUT 
((5 + 5))

#To view the result of the below arithmetic expression, you can use the echo command to view the result.
sum=$((2 * 5))
echo $sum 
```

## Conditional statements

__if statements__

```bash
#The syntax of the if command is:
if test-commands 
	then
  		consequent-commands

#The elif and else block are optional if more conditions are required

elif more-test-commands 
	then
  		more-consequents
  
else alternate-consequents

fi 
```

__Case statements__

```bash

#case will selectively execute the command-list corresponding to the first pattern that matches word, proceeding from the first pattern to the last.

case $var in
  pattern| pattern) commands ;;
  pattern2) commands ;;
  *) default ;;  
esac

# The ‘*’ charcter is used as a final pattern to define the default case, since that pattern will always match.
```

## Looping Constructs
Bash supports the following looping constructs.

__while loops__

```bash
#While loop syntax
while test-commands 
	do consequent-commands 
done

#The syntax can also be re-writen in one line as:
while test-commands; do consequent-commands; done

#Example usage:
myvar=1

while [ $myvar -le 10 ]
	do
        echo $myvar
        myvar=$(($myvar + 1))
        sleep 1.0
done
```

__for loop__

```bash
#For loop example:
for current_number in {1..10}
	do 
		echo $current_number
		sleep 1
done 
echo "This is the end of the loop"

#C-style for loop. 
#The above for loop syntax cannot be used with variables.
#It is called C-style due to its similarity to the C language for loop syntax. 

for (( INITIALIZATION ; CONDITION ; UPDATE ))
do
  commands
done


#Example: 

start=1
stop=10

for ((i=$start; i<=$stop; i++))
	do 
		echo $i
	done
#The $ symbol before the variable name can be ignored as variables are expanded in arithmetic context.

for ((i=start; i<=stop; i++))
	do 
		echo $i
	done
```

__until loop__

```bash
#The the until loop works precisely like the while loop, but with the difference: The code inside a until loop is executed as long as the particular condition is false

#Until loop syntax:
until test-commands 
	do consequent-commands 
done

#Example usage:

var="0"

until [ $var -eq 10 ]
do
  # Increase $var by 1
  ((var++))
  echo "var: $var"
done
```

__continue__ and __break__

**continue** would skip to the next iteration of a loop while **break** would exit the loop immediately.



## Exit Codes
Exit codes indicate whether a command __succeeded or failed__.

The special variable `$?` stores the exit status of the __last executed command__:

```bash
ls /tmp
echo $?   # 0 means success, any non-zero value indicates failure
```

You can also __explicitly exit a script with a specific code__ using the `exit` command:

```bash
exit 1     # exits the script with status 1 (failure)
exit 0     # exits with status 0 (success)
```

## Functions

Functions are used to execute recurring commands. it makes code easier to read and short.

There are two ways of defining functions:

```bash
function name {
	[commands]
}
```
OR
```bash
function_name() {
	[commands]
}
```
__Example usage:__

```bash
func () {	#or "function func" instead of "func ()"
	if test-command
		then
			consequent-commands
	fi
}

#calling a function
func
```

## Arrays
An array is a Bash variable that can hold multiple string values under a single name.

There are two types of arrays: __Associative__ and __Indexed__ arrays

__Indexed Arrays__

Indexed arrays use numeric indexes to store and access array values

```bash
#Indexed Arrays

arr=(a b c)        # create an array
echo "${arr[0]}"   # access the first element of the array
arr[1]="new"       # update the second element of an array
echo "${arr[@]}"   # list all elements of the array
echo "${#arr[@]}"  # length

# Loop 
for val in "${arr[@]}"; do    
  echo "$val"
done
```

__Associative Arrays__
Associative arrays use string keys to store and access array values.

```bash
# Associative arrays 

#create an associative array
declare -A colors
colors[red]="FF0000"         # create
colors[blue]="0000FF"

echo "${colors[red]}"         # access -> FF0000

colors[blue]="5111ff"        # update

echo "${!colors[@]}"           # list keys -> red blue

echo "${colors[@]}"            # list values -> FF0000 1111FF

#Loop
for key in "${!colors[@]}" 
	do
  		echo "$key -> ${colors[$key]}"
done
```

## Learn More
This document is __NOT a comprehensive introduction__ to BASH scripting; it is intended as a __quick syntax reference__ for commonly used commands and constructs.

For a more detailed introduction to Bash scripting, check out this YouTube series by [Learn Linux TV](https://www.youtube.com/@LearnLinuxTV).

Hack The Box Academy also offers an [introductory Bash scripting module](https://academy.hackthebox.com/).

For the official, in-depth documentation, refer to the [GNU Bash Reference Manual](https://www.gnu.org/software/bash/manual/bash.html).






 

