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