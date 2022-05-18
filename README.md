# Git & GitHub

## What is Git?

Git is a Version Control System (VCS) that keeps track of all the changes to your project files, allowing you to work with your team on the same code while saving you a lot of confusion that tends to happen when multiple people are editing the same files. Git stores every record of every change that you or someone else makes to the project, and this makes keeping track of your progress easy. If you need to look at your old code, or if you need to see what or who modified it – the record is always there.

## What is GitHub
GitHub acts as remote storage for your Git repositories and provides a really neat and simple way for people to collaborate and contribute to development projects.

First, set your identity. Git uses that information for every commit.

git config --global user.name "Your Name"
git config --global user.email mail@example.com

Warning: Never git add, commit, or push sensitive information to a remote repository. Sensitive information can include, but is not limited to:
Passwords
SSH keys
AWS access keys
API keys
Credit card numbers
PIN numbers

## Adding a project to GitHub with GitHub CLI
GitHub CLI is an open source tool for using GitHub from your computer's command line. GitHub CLI can simplify the process of adding an existing project to GitHub using the command line. (... to add more notes to this)

# Setting your Git username for every repository on your computer

Open Terminal.
Set a Git username:
```
$ git config --global user.name "Mona Lisa"
```
Confirm that you have set the Git username correctly:
```
$ git config --global user.name
```
> Mona Lisa

Setting your Git username for a single repository

Open Terminal.
Change the current working directory to the local repository where you want to configure the name that is associated with your Git commits.
Set a Git username:
```
$ git config user.name "Mona Lisa"
```
Confirm that you have set the Git username correctly:
```
$ git config user.name
```
> Mona Lisa
