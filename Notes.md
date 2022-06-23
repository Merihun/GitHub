
# What is Git Upstream Branch?

When you want to checkout a branch in git from a remote repository such as GitHub or Bitbucket, the “Upstream Branch” is the remote branch hosted on Github or Bitbucket. It’s the branch you fetch/pull from whenever you issue a plain git fetch/git pull basically without arguments.

# How to Set Upstream Branches in Git

Using the Git Push command with the “-u” option for the upstream branch.

# Set Upstream Branch using Git Push command

Create a new branch with the name ” and switch to the current branch using the -b option

git checkout -b <branch name>
  
 Now, you need to set the upstream branch using the Git push command with the -u option.  Replace <branch name> with your branch name.
 ```
 git push -u origin <branch name>
  ```
  Alternatively, you can use the ‘–set-upstream’ command as well to set the Upstream branch
  ```
  git push --set-upstream origin <branch name>
  
  ````
  
 # How to Change Upstream Branches in Git

Now, you need to track a new upstream branch than the one you just setup running:

git branch -u <remote/branch name>
For example:

git branch main -u <origin/new_branch>
git branch main -u <origin/main>
  
  # How to check which Git Branches are tracking which Upstream Branches
  
  Now, you can list all your branches that are tracking upstream branches using “Git branch” with the -vv option:
```
git branch -vv
  
```
