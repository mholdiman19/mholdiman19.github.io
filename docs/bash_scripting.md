# Bash Scripting

Resource: [you need to learn BASH Scripting RIGHT NOW!! // EP1](https://youtu.be/SPwyp2NG-bE)

## Episode 1

* `which $SHELL` => `/bin/bash`
* `echo "Hi Mom"` => `Hi Mom`
* To automate the above command, open a text editor, such as `nano`.
* `nano himom.sh`
* Create script

```bash

#!/bin/bash
echo "Hi Mom"

```
* save script in nano
* do `ls` to confirm your file is saved
* To run the script, you can do:
    - `bash himom.sh` or 
    - you can change the permissions via `chmod +x himom.sh` and then do `./himom.sh`
    - To see the permissions of the file, do `ls -al`
* Bash scripts are just commands.

## Episode 2

__Beginning Quick Challenge__

1. Create a script
2. Name it bestdayever.sh
3. Be sure to include the following 3 lines: 
    - Good Morning Michelle!!
    - You're looking good today Michelle!!
    - You have the best eyes I've ever seen Michelle!!

* What if you wanted to change the name for your friend Monica?
* Add a __variable__, which can change
* To do this add, do `name="Monica"`
* Then, change remove Michelle in the script 
* Replace with `$name`

Script:

```bash
                               
#!/bin/bash

name="Monica"

# Greeting

echo "Good Morning $name!!"

sleep 3

# Compliment 1

echo "You're looking good today $name!!"

sleep 3

# Compliment 2

echo "You have the best eyes I've ever seen $name!!"
```

Results:
```text
Good Morning Monica!!
You're looking good today Monica!!
You have the best eyes I've ever seen Monica!!
```


* However, we want to be more lazy and not have to go in and change the name each time.
* So, we need to make some changes.

Script:

```bash
#!/bin/bash

echo "What is your name?"

read name

# Greeting

echo "Good Morning $name!!"

sleep 3

# Compliment 1

echo "You're looking good today $name!!"

sleep 3

# Compliment 2

echo "You have the best eyes I've ever seen $name!!"
```

Results:

```text
What is your name?
Ben
Good Morning Ben!!
You're looking good today Ben!!
You have the best eyes I've ever seen Ben!!
```

### Positional Parameters (A.K.A Argument) Example

Script:

```bash
#!/bin/bash

# Positional Parameter (aka Argument)

name=$1

# Greeting

echo "Good Morning $name!!"

sleep 3

# Compliment 1

echo "You're looking good today $name!!"

sleep 3

# Compliment 2

echo "You have the best eyes I've ever seen $name!!"
```

* To run the script, you would need to do, `./bestdayever2.sh Brian`
* `Brian` is the __positional parameter__

Results:

```text
Good Morning Brian!!
You're looking good today Brian!!
You have the best eyes I've ever seen Brian!!
```

__Challenge__

* Change the `eyes` variable to something for everyone
* Essentially, we are adding an additional __positional parameter or argument__

Script:

```bash
#!/bin/bash

# Positional Parameter (aka Argument)

name=$1
feature=$2

# Greeting

echo "Good Morning $name!!"

sleep 3

# Compliment 1

echo "You're looking good today $name!!"

sleep 3

# Compliment 2

echo "You have the best $feature I've ever seen $name!!"
```

* Again to run the script, I had to input the __argument__
* So, I did `./bestdayever2.sh Kim hair

Results:

```text
Good Morning Kim!!
You're looking good today Kim!!
You have the best hair I've ever seen Kim!!
```

* Now, lets try to use the output of a command in our script.
* Commands to use: `whoami`, `pwd` and `date`

Script:

```bash
#!/bin/bash

# Positional Parameter (aka Argument)

name=$1
feature=$2

user=$(whoami)
location=$(pwd)
date=$(date)

# Greeting

echo "Good Morning $name!!"

sleep 3

# Compliment 1

echo "You're looking good today $name!!"

sleep 3

# Compliment 2

echo "You have the best $feature I've ever seen $name!!"

sleep 2

echo "You are currently logged in as $user and you are in the directory $location. Also, today is: $date"
```

* To run script, do `./bestdayever2.sh Kim hair`

Results:

```text
Good Morning Kim!!
You're looking good today Kim!!
You have the best hair I've ever seen Kim!!
You are currently logged in as manhands and you are in the directory /home/manhands/scripts. Also, today is: Thu 30 Jun 2022 03:48:51 PM CDT
```

## Here Documents

__Resource Used__ => Hak5 

* All __heredocs__ include the following:
  - command << token
  - script
  - token

__Example1__

```bash
cat << _EOF_
echo "Hello World"
_EOF_
```
## Bash Scripting on Linux (The Complete Guide)

### Class 02 - Hello World

__Resource__ => [Bash Scripting on Linux (The Complete Guide) Class 02 - Hello World](https://youtu.be/boqC9QenshY)

* To see what bash you are using => `echo $SHELL`
    * Result => `/bin/bash`

### Class 03 - Variables

#### How to create a variable in Bash

* Need to name the variable => Ex: `name` is the variable.
* Add an `=` sign
* Inside `""` define the variable.
* Example is below.

```bash
#!/bin/bash

name="Michelle"

echo $name
```
* Result is `Michelle`

```bash
#!/bin/bash
myname="Michelle"
myage="42"
echo "Hello, my name is $myname."
echo "I am $myage years old."
```
* Result:

```txt
Hello, my name is Michelle.
I am 43 years old.
```

* Clearly, you wouldn't create a script to do these funcions.
* What are some of the reasons you would create a script?
    + Less typing
    + Less duplication of typing
    + Saves time
* Another example would be the following:
```bash
#!/bin/bash
word="awesome"
echo "Linux is $word!"
echo "Videogames are $word!"
echo "Sunny days are $word!"
```
* Results:
```text
Linux is awesome!
Videogames are awesome!
Sunny days are awesome!
```
* You can also utilize the output of commands as well.
* Example:
```bash
#!/bin/bash
files=$(ls)
echo $files
```
* Result:
```text
3_variables.sh Advanced_Bash_Scripting.pdf helloworld.sh myscript.sh script_ls.sh
```
* How to view environment variables in your Linux session
* Example => `echo $USER`  
* Result => `manhands`
* More detailed example:
```bash                             
#!/bin/bash
name="Michelle Holdiman"
now=$(date)
echo "Hello $name"
echo "The system date and time is:"
echo $now
echo "Your username is: $USER"
```
* Results:
```text
Hello Michelle Holdiman
The system date and time is:
Mon Feb 13 09:27:19 AM CST 2023
Your username is: manhands
```
* You should use lowercase letters for your variables.
* Best practice is to use uppercase letters for environment variables.
* This way whoever is reading your code will know which variables you are creating versus which variables are environment or system variables.
* How to see your environment variables => `env`
* Partial results of my `env`:
```text
LOGNAME=manhands
XDG_SESSION_DESKTOP=ubuntu
XDG_SESSION_TYPE=wayland
SYSTEMD_EXEC_PID=2286
```
* Additional examples
    + `echo $HOME`
    + `echo $USER`

### Class 04 - Basic Math

* Math is handled differently in Bash than in Python for example.
* In Bash, the __evaluate expression__ (`expr`) is used.
* Examples are below:
    + `expr 1 + 1` => 2
    + The spaces are require, or Example => `expr 1+1` => 1+1
    + `expr 1 - 1` => 0
    + `expr 1 / 1` => 1
    + Multiplication is different, since "`*`" is a wildcard in Bash.
    + Example => `expr 1 \* 1` => 1
* Mathematical expressions can also be done using variables.  Please see example below.

```bash
#!/bin/bash

mynum=19
kimnum=14

expr $mynum + $kimnum
```
* Result: `33`

### Class 05 - If Statements

```bash
#!/bin/bash

# Declaring variable
mynum=200

# Beginning of if statement
# If statement is determining whether 200 is equal to 200
if [ $mynum -eq 200 ]

# Then what are we going to do?  Echoing the text statement
then
    echo "This condition is true."
# If backwards ends the script
fi
```
* If I change the variable from 200 to 300, then the statement is no longer true so the text will not be echoed.
* To combine to "if statements" you can use `else`.
* Example is below.
```bash
#!/bin/bash

mynum=300

if [ $mynum -eq 200 ]
then
    echo "The condition is true."
else
    echo "The variable does not equal 200."
fi
```
* Result => `The variable does not equal 200.`

* A quick way to do the opposite of the "if statement" is to add an "`!`" mark before the variable in the "if statement".
* Example is below.
```bash
#!/bin/bash

mynum=300

if [ ! $mynum -eq 200 ]
then
    echo "The condition is true."
else
    echo "The variable does not equal 200."
fi
```
* Result => `The condition is true.`

* To set the above if_statement to _not equals_ is to use `-ne` instead of `-eq`.
* `-ne` => not equal
* `-eq` => equal
* Please see example below using `-ne`.
```bash
#!/bin/bash

mynum=300

if [ $mynum -ne 200 ]
then
    echo "The condition is true."
else
    echo "The variable does not equal 200."
fi
```
* Result => `The condition is true.`
* Another option is to use greater than, which is `-gt`.
* Example is below.
```bash
#!/bin/bash

mynum=300

if [ $mynum -ne 200 ]
then
    echo "The condition is true."
else
    echo "The variable does not equal 200."
fi
```
* Result => `The condition is true.`
* An example of a more useful way to use this would be to see if a file exists.
* Please see the example below.
```bash
#!/bin/bash

if [ -f ~/myfile ]
then
    echo "The file exists."
else
    echo "The file does not exist."
fi
```
* Result => `The files does not exist.`
* Why? Because I do not have a file named myfile in my home directory.

* You can also create a script to see if a program is installed, and if not, install it.
* Example is below.
```bash
#!/bin/bash

command=/usr/bin/htop

if [ -f $command ]
then 
    echo "$command is available, let's run it..."
else
    echo "$command is not available, installing it..."
    sudo apt update && sudo apt install -y htop
fi

$command
```
* Result => The above script installed `htop` on my system.
* You can also create the same script without using brackets.
* Example is below.
```bash
#!/bin/bash

command=htop

if command -v $command
then 
    echo "$command is available, let's run it..."
else
    echo "$command is not available, installing it..."
    sudo apt update && sudo apt install -y htop
fi

$command
```
* Result => `htop` started running.
* Brackets are really only needed for test command.
* `command -v` can actually be used in command prompt.
* `command` lets you know if a command is available.
* You can find out more about the __test command__ via the `man` page.
* If you type `man test` in your command prompt screen, you will see `[]` is a test.

### Class 06 - Exit Codes

* How do you know if your script was successful?
* Answer => Exit Codes
* How does Bash represent whether command/script was successful or if there was a failure?
* The variable `$?` represents whether or not the previous command was successful.
* If I typed `ls -l /etc` in a command prompt screen and then typed `echo $?`, then my result would be `0`.
* What does that mean?
    + `0` => means command was successful
    + Anything other than zero, means that command failed.
* An exit code tells us the status.
* An example of a working script:
```bash
!/bin/bash

package=htop

sudo apt install $package

echo "The exit code for the package install is: $?"
```
* Result => `The exit code for the package install is: 0`
* An example of a failed script:
```bash
#!/bin/bash

package=notexist

sudo apt install $package

echo "The exit code for the package install is: $?"
```
* Result => `The exit code for the package install is: 100`
* An example of a more useful way to utilize the `$?` exit code.
```bash
#!/bin/bash

package=htop

sudo apt install $package

if [ $? -eq 0 ]
then
    echo "The installation of the $package was successful."
    echo "The new command is available here:"
    which $package
else
    echo "$package failed to install."
fi
```
* A more realistic version of a script you may see on a real Linux system.
```bash
#!/bin/bash

package=notexist

sudo apt install $package >> package_install_results.log

if [ $? -eq 0 ]
then
    echo "The installation of the $package was successful."
    echo "The new command is available here:"
    which $package
else
    echo "$package failed to install." >> package_install_fail.log
fi
```
* Since `nonexist` is not a real package name.  I can find the results in the file __package_install_fail.log__.
* Results => `notexist failed to install.`
* You need to make sure that the exit codes are in the correct location.
* Check them at the appropriate time in the script.
* You can also control what the exit code ends up being.
```bash
#!/bin/bash

echo "Hello World"
exit 199
echo $?
```
* Result => `Hello World`
* If you do `$?`, then you get `199`.
* Remember when you type `exit`, the script will __exit__.

### Class 07 - While Loops

* A __while loop__ completes a script over and over again.
* Please see example below.

```bash
#!/bin/bash

# Setting myvar equal to 1
myvar=1

# Checking to see if myvar is less than 10
while [ $myvar -le 10 ]
do
    echo $myvar
    myvar=$(( $myvar +1 ))
    sleep 0.5
done
```

* Result:

```text
1
2
3
4
5
6
7
8
9
10
```

* Why does the script stop at 10?  Because 11 is greater than 10, meaning the script is no longer true, so it stops.
* Another example would be the following:

```bash
#!/bin/bash

myvar=1

while [ -f ~/testfile ]
do 
    echo "The test file exists."
done

echo "The file no longer exists."
```

* The system will check to see if `testfile` exists in the `~` directory.
* Result (if the file exists):

```text
The test file exists.
The test file exists.
The test file exists.
The test file exists.
The test file exists.
The test file exists.
```

* The above will continue to run until it is manually stopped or the file is removed.
* Result if the file does not exist:

```text
The file no longer exists.
```

* Another example including `sleep` would be the following:

```bash
#!/bin/bash

# myvar is not needed
myvar=1

# Does the testfile exist?
while [ -f ~/testfile ]
do 
    echo "As of $(date), the test file exists."
    sleep 5
done

# This happens if the file does not exist.
echo "As of $(date), the test file has gone missing."
```

* The above not only adds the `sleep` function, but it also adds the `date` to the script as well.  
* In the output below, you can see the script did sleep for 5 seconds prior to the loop checking again.

```text
As of Fri Feb 17 03:14:22 PM CST 2023, the test file exists.
As of Fri Feb 17 03:14:27 PM CST 2023, the test file exists.
As of Fri Feb 17 03:14:32 PM CST 2023, the test file exists.
As of Fri Feb 17 03:14:37 PM CST 2023, the test file exists.
```









