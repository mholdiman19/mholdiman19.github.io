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
* Best practice is to use uppercase variables for environment variables.
* This way whoever is reading your code will know which variables you are creating and which variables are environment or system variables.
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