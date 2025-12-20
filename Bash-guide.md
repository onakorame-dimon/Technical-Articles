# Bash scripting syntax guide 

What is BASH
A shell, language, or command line interpreter?
What is a shell?

What makes bash different from other programming language? its similarities and limitations?
What of the other data types like arrays and co. 

## Declaring Variables

```bash
var="foo"
echo $var
```
#### Difference between using quotes and not using quotes when declaring a variable
content

Capturing the output of a command and saving as variable

ls_contents=$(ls)
echo ls_contents

Math/Arithmetic
===
Evaluate expression -- similar to python
expr 30 + 40

Except, for multiplication:
expr 100 \* 4

Conditional statements
===
If statements syntax

if [ condition ]
then 
	action 
fi 


Exit codes
===
Helps you determine if a command was successful or not

$?
If echo $? returns 0 that is success, else failure

exit [code]  -- set exit code

While loop
==========
myvar=1

while [ $myvar -le 10 ]
do
        echo $myvar
        myvar=$(($myvar + 1))
        sleep 1.0
done

__For loop__
---
```bash
for current_number in {1..10}
do 
	echo $current_number
	sleep 1
done 

echo "This is the end of the loop"
```

__Data Streams__
---
```bash
${#var}	String length
${#arr[@]}	Number of array elements
${#arr[*]}	Same as above
```
---

__PART 2__

Bash scripting syntax guide 2


BASH 2
Variables in bash
======================
In contrast to other programming languages, there is no direct differentiation and recognition between the types of variables in Bash like "strings," "integers," and "boolean." 

All contents of the variables are treated as string characters. 
What about numbers? 

Bash enables arithmetic functions depending on whether only numbers are assigned or not. It is important to note when declaring variables that they do not contain a space. Otherwise, the actual variable name will be interpreted as an internal function or a command.

special variables
=================
What are they, what do they do? 

Tabulate this
| Character     |  purpose   |
| --- | ---- |
$#   | it is used for . . .
$$   | it is used for . . .
$0..9
$@
$*

Arrays
==========
Similarity and difference between a python list, is it still a string or a data structure.

```bash
arr=(a b c)        # create
echo "${arr[0]}"   # access
arr[1]="new"       # update
echo "${arr[@]}"   # all elements
echo "${#arr[@]}"  # length
```
Examples.

functions
==========
```bash
func () {	#or function func instead of func ()
	if [ expr ]
	then
		condition
	fi
}

#calling a function
func
```
Example

Case statements
================
```bash
case $var in
  pattern1) commands ;;
  pattern2) commands ;;
  *) default ;;
esac
```
Explain how it matches.

Examples 

Flow Control
===========
What it is, its usefulness. How to introduce the list

Branches:
If-Else Conditions
Case Statements
Loops:

For Loops
While Loops
Until Loops

BASH 3
---
BASH 3
==========

Scheduling job

at command is used to run jobs

crontab -e --> edit crontab
crontab -l --> view crontab for a user

You can use journalctl or syslog to view the results of CRON jobs

command -v and which, their similarities and differences. 

rsync vs cp in backing up

Cronjobs have no output. Explain?
