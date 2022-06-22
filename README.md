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

# Connect with SSH
Using the SSH protocol, you can connect and authenticate to remote servers and services. With SSH keys, you can connect to GitHub without supplying your username and personal access token at each visit.

# Checking for existing SSH keys
Before you generate an SSH key, you can check to see if you have any existing SSH keys.

1. Open Terminal.
2. Enter ls -al ~/.ssh to see if existing SSH keys are present.
```
$ ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
```

```
3. Check the directory listing to see if you already have a public SSH key. By default, the filenames of supported public keys for GitHub are one of the following.
id_rsa.pub
id_ecdsa.pub
id_ed25519.pub
```

4. Either generate a new SSH key or upload an existing key.
If you don't have a supported public and private key pair, or don't wish to use any that are available, generate a new SSH key.
If you see an existing public and private key pair listed (for example, id_rsa.pub and id_rsa) that you would like to use to connect to GitHub, you can add the key to the ssh-agent.

# Generating a new SSH key and adding it to the ssh-agent
After you've checked for existing SSH keys, you can generate a new SSH key to use for authentication, then add it to the ssh-agent.
1. Open Terminal.
2. Paste the text below, substituting in your GitHub email address.

```
$ ssh-keygen -t ed25519 -C "your_email@example.com"
```
When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.
> Enter a file in which to save the key (/Users/you/.ssh/id_algorithm): [Press enter]
At the prompt, type a secure passphrase.

```
> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
```

When adding your SSH key to the agent, use the default macOS ssh-add command, and not an application installed by macports, homebrew, or some other external source.

1. Start the ssh-agent in the background.
```
$ eval "$(ssh-agent -s)"
> Agent pid 59566
```
Depending on your environment, you may need to use a different command. For example, you may need to use root access by running sudo -s -H before starting the ssh-agent, or you may need to use exec ssh-agent bash or exec ssh-agent zsh to run the ssh-agent.

2. If you're using macOS Sierra 10.12.2 or later, you will need to modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain.
. First, check to see if your ~/.ssh/config file exists in the default location.
```
$ open ~/.ssh/config
> The file /Users/you/.ssh/config does not exist.
```
. If the file doesn't exist, create the file.
```
$ touch ~/.ssh/config
```
. Open your ~/.ssh/config file, then modify the file to contain the following lines. If your SSH key file has a different name or path than the example code, modify the filename or path to match your current setup.
```
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519
  
```
3. Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_ed25519 in the command with the name of your private key file.
```
$ ssh-add -K ~/.ssh/id_ed25519
```
4. Add the SSH key to your account on GitHub.

Copy the SSH public key to your clipboard.
If your SSH public key file has a different name than the example code, modify the filename to match your current setup. When copying your key, don't add any newlines or whitespace.
```
$ pbcopy < ~/.ssh/id_ed25519.pub
# Copies the contents of the id_ed25519.pub file to your clipboard
```
2. In the upper-right corner of any page, click your profile photo, then click Settings.
3. In the "Access" section of the sidebar, click  SSH and GPG keys.
4. Click New SSH key or Add SSH key.
5. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal Mac, you might call this key "Personal MacBook Air".
6. Paste your key into the "Key" field.
7. Click Add SSH key.
8. If prompted, confirm your GitHub password.

# Testing your SSH connection

Open Terminal.
Enter the following:
```
$ ssh -T git@github.com
# Attempts to ssh to GitHub
```
You may see a warning like this:
```
> The authenticity of host 'github.com (IP ADDRESS)' can't be established.
> RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
> Are you sure you want to continue connecting (yes/no)?
```
3. Verify that the fingerprint in the message you see matches GitHub's public key fingerprint. If it does, then type yes:
```
> Hi username! You've successfully authenticated, but GitHub does not
> provide shell access.
```
4. Verify that the resulting message contains your username.






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

# GitHub CLI

GitHub CLI is an open source tool for using GitHub from your computer's command line. When you're working from the command line, you can use the GitHub CLI to save time and avoid switching context.

GitHub CLI includes GitHub features such as:

- View, create, clone, and fork repositories
- Create, close, edit, and view issues and pull requests
- Review, diff, and merge pull requests
- Run, view, and list workflows
- Create, list, view, and delete releases
- Create, edit, list, view, and delete gists
- List, create, delete, and connect to a codespace

```gh``` is GitHub on the command line. It brings pull requests, issues, and other GitHub concepts to the terminal next to where you are already working with ```git``` and your code.

1. Install GitHub CLI on macOS, Windows, or Linux.
2. In the command line, authenticate to GitHub.
``` gh auth login ```
3. Start working with GitHub in the command line. 

For example, 
- find an issue to work on with ```gh issue status``` or ```gh issue list --assignee @me```. 
- Create a pull request with ```gh pr create```. 
- Review a pull request with ```gh pr checkout```, ```gh pr diff and gh pr review```.

# Create a Repository
1. In the command line, navigate to the directory where you would like to create a local clone of your new project.
2. To create a repository for your project, use the ```gh repo create``` subcommand. When prompted, select Create a new repository on GitHub from scratch and enter the name of your new project. If you want your project to belong to an organization instead of to your personal account, specify the organization name and project name with organization-name/project-name.
3. Follow the interactive prompts. To clone the repository locally, confirm yes when asked if you would like to clone the remote project directory.
4. Alternatively, to skip the prompts supply the repository name and a visibility flag (--public, --private, or --internal). 

For example, ```gh repo create project-name --public```. To clone the repository locally, pass the --clone flag.
```
# create a repository interactively
gh repo create

# create a new remote repository and clone it locally
gh repo create my-project --public --clone

# create a remote repository from the current directory
gh repo create my-project --private --source=. --remote=upstream
```

```
# Create a repository for the current directory.
~/Projects/my-project$ gh repo create
✓ Created repository user/my-project on GitHub
✓ Added remote https://github.com/user/my-project.git
~/Projects/my-project$
```
# How to Switch Git Branch

## Switch Branch using git checkout

The easiest way to switch branch on Git is to use the “git checkout” command and specify the name of the branch you want to switch to.

If the destination branch does not exist, you have to append the “-b” option, otherwise you won’t be able to switch to that branch.
```
$ git checkout <existing_branch>

$ git checkout -b <new_branch>
```
As an example, let’s say that you want to switch to the master branch to another branch named “feature” in your repository.

First, make sure that the target branch exists by running the “git branch” command.

``` $ git branch ```

## Switch branch using git switch

A quick way of switching branch on Git is to use the “git switch” command and specify the name of the branch you want to switch to.

If the destination branch does not exist, you have to specify the “-c” option (for “create branch“), otherwise you will get an error message when switching to that branch.

$ git switch <existing_branch>

$ git switch -c <non_existing_branch>

Again, as an example, let’s say that you want to switch to the “feature” branch from the “master” branch.

In order to switch from the “master” branch to the “feature” branch, use the “git switch” command and specify the destination branch (which is “feature” in this case)

``` $ git switch feature ```

## Checkout Remote Branch on Git

In some cases, you may be interested in checking out remote branches from your distant repository.

In order to switch to a remote branch, make sure to fetch your remote branch with “git fetch” first. You can then switch to it by executing “git checkout” with the “-t” option and the name of the branch.
```
$ git fetch

$ git checkout -t <remote_name>/<branch_name>

```

The “-t” option in checkout stands for “track” and it is used to create your branch and setting up the upstream branch automatically to the remote branch.

## Checkout New Branch from Specific Commit

In some cases, you may need to switch to a new branch, but you want it to start from a specific commit on the branch.

In order to checkout a new branch from a specific start point, you have to execute the “git checkout” command and specify the “-B” option, as well as the branch and its start point.
```
$ git checkout -B <branch> <start_point>

```
In order to checkout to a specific start point, you will have to list the commits done in you repository using the “git log” command.

```
$ git log --oneline --graph

* 98a14be Version 2 commit (master, HEAD)
* 53a7dcf Version 1.0 commit
* 0a9e448 added files
```
The HEAD of the master branch is at 98a14be but we want to checkout to the commit just before HEAD (which is 53a7dcf).

In order to switch to the master branch, on this specific commit, we are going to execute the “git checkout” command and specify the “master” branch as well as the commit SHA.
```
$ git checkout -B master 53a7dcf 

Switched to and reset branch 'master'
* bd6903f first commit
```

In order to check that you are correctly on a specific commit, you can use the “git log” command again.

``` $ git log --oneline --graph ```

# Add All Files using Git Add

The easiest way to add all files to your Git repository is to use the “git add” command followed by the “-A” option for “all”.
```
$ git add -A                       

$ git add .                        (at the root of your project folder)
```

In this case, the new (or untracked), deleted and modified files will be added to your Git staging area. We also say that they will be staged.

## Adding deleted and modified files only

In order to add all deleted and modified files only to your staging area, you have to use the “git add” command followed by the “-u” option.
```
$ git add -u

```
## Merging branch to master

To create a new branch, we can use the ``` git branch new-branch ``` command. This will create a new branch mirroring the commits on the currently active branch:
```
$ git branch new-branch
$ git branch
* master
new-branch
```
As a brief aside, keep in mind that behind the scenes Git does not actually create a new set of commits to represent the new branch. In Git, a branch is really just a tag. It is a label that we can use to reference a particular string of commits. It would be inefficient to duplicate a set of commits behind the scenes, so Git allows us to create multiple diverging sets of commits from a single base.

At this point we have created a new branch, but are still located on the source branch. To start working on the new branch we first need to run the command git checkout new-branch. This will change the active branch to the new branch:
```
$ git checkout new-branch
Switched to branch ‘new-branch'
$ git branch
master
* new-branch
```
At this point, commits can be made on the new branch to implement the new feature. Once the feature is complete, the branch can be merged back into the main code branch.

First we run ``` git checkout master ``` to change the active branch back to the master branch. Then we run the command ``` git merge new-branch ``` to merge the new feature into the master branch.

If you're merging a new feature into the main branch, you first want to switch to the main branch and then merge into it:

# ...develop some code...

```
$ git add –A
$ git commit –m "Some commit message"
$ git checkout master
Switched to branch 'master'
$ git merge new-branch

```
## When to Delete branches
It is common for a Git repo to have different branches. They are a great way to work on different features and fixes while isolating the new code from the main codebase.

Repos often have a main branch for the main codebase and developers create other branches to work on different features.

Once work is completed on a feature, it is often recommended to delete the branch.

Deleting a branch LOCALLY
Git will not let you delete the branch you are currently on so you must make sure to checkout a branch that you are NOT deleting. For example: git checkout main

## Delete a branch with git branch -d <branch>.

For example: git branch -d fix/authentication

The -d option will delete the branch only if it has already been pushed and merged with the remote branch. Use -D instead if you want to force the branch to be deleted, even if it hasn't been pushed or merged yet.

The branch is now deleted locally.

## Deleting a branch REMOTELY
Here's the command to delete a branch remotely: git push <remote> --delete <branch>.

For example: ``` git push origin --delete fix/authentication ```

The branch is now deleted remotely.
  
You can also use this shorter command to delete a branch remotely: git push <remote> :<branch>

For example: ``` git push origin :fix/authentication ```

If you get the error below, it may mean that someone else has already deleted the branch.
  ```error: unable to push to unqualified destination: remoteBranchName The destination refspec neither matches an existing ref on the remote nor begins with refs/, and we are unable to guess a prefix based on the source ref. error: failed to push some refs to 'git@repository_name' ```
