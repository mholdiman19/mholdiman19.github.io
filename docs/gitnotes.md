# GitHub Notes #

## SSH Keys ##

* To generate a SSH key => `ssh-keygen -t rsa -b 4096 -C "emailaddress"`
* Default file location => `/user/mholdiman/.ssh/id_rsa`
* To search for newly generated key => `ls | grep <filename>`
* To see your public key => `cat <filename>.pub`
* You can copy from the terminal and paste into GitHub, or you can do `pbcopy < ~/<filename>.pub`

### Adding you SSH key to the ssh-agent ###

1. Start the ssh-agent in the background => `eval "$(ssh-agent -s)"`
2. Add your SSH private key to the ssh-agent and store your passphrase in the keychain.  If you created your key with a different name, or if you are adding an existing key that has a different name, replace _id_rsa_ in the command with the name of your private key file => `ssh-add -K ~/.ssh/id_rsa`

## Git Push ##

* `git push origin master`
  * Tells git to push the changes you made locally (origin) to the GitHub branch (master)

### What if you start a repo locally? ###

* Open folder in Visual Studio Code
* If not a git repo, then do `git init`
* To push this live, you would do `git push origin master`
* However, if the repo is not on GitHub, then you will need to create a new repo on GitHub
* Copy 
* Do `git remote add origin <paste SSH Link from GitHub>`
* Then do `git remote -v` to verify
* Now, you should be able to do `git push origin master`
  * In the future, you could just type in `git push`, but you need to set an _upstream_ first.  Shortcut => `git push -u origin master`

  **GitHub Workflow** => Write Code > Commit Changes

  * If it is not our code, then we can do what is called a pull request.  GitHub Workflow would then be Write Code > Commit Changes > Make a Pull Request

  **Local Git Workflow** => Write Code > Stage Changes `git add` > Commit Changes `git commit` > Push Changes `git push` > Make a Pull Request

## Git Branching ##

* **Master Branch** => default branch in GitHub.
* We can also create a **Feature Branch**
* Each individual branch does not know about changes to any other branches.
* Why is this useful?  When rolling out new features, you can test it here.  It is a sandboxed environment.
* `git branch` => shows what branch you are currently in 
* results => `*master (END)`
* To create a new branch => `git checkout`
* To create a new branch and name the branch => `git checkout -b <new branch name>`
* To see differences between files => `git diff <branch name of the one that you want to compare it to>`
* Instead of doing a `git merge`, it is more common to push the changes to GitHub in the repo you are in, and then `merge` in GitHub.

## Pull Requests aka PRs ##

* What is a pull request?

  * Get your code pulled into another branch
  * You make a PR from feature branch to the master branch
  * Once it is merged, you remove the branch
  * You do the pull request in GitHub and then do another pull request to update your local system => `git pull origin master`
  * Now that your branch has been merged with the master, you can delete the branch => `git branch -d <branch name>`