## Git Commands
**What is Git?**

Git is a widely used modern version control system for tracking changes in computer files. The term version control system suggests a system that records all the changes made to a file or set of data, so a specific version can be considered whenever needed. This feature makes the process of collaboration so feasible with all team members, making it considerably more comfortable to work over a big project.  

Git makes it possible for several people involved in the project to work together and track each other's progress over time. In software development, the tool helps in Source Code Management. Git favors not only programmers but also non-technical users by keeping track of their project files.

While working on Git, we actively use two repositories. 

* Local repository: The local repository is present on our computer and consists of all the files and folders. This Repository is used to make changes locally, review history, and commit when offline.
* Remote repository: The remote repository refers to the server repository that may be present anywhere. This repository is used by all the team members to exchange the changes made.

Both repositories have their own set of commands. There are separate Git Commands that work on different types of repositories. 
## All The Git Commands You Need to Know About
**git init**

* The command git init is used to create an empty Git repository. 
* After the git init command is used, a .git folder is created in the directory with some subdirectories. Once the repository is initialized, the process of creating other files begins.
`git init`

**git add**
* Add command is used after checking the status of the files, to add those files to the staging area.
* Before running the commit command, "git add" is used to add any new or modified files.

      git add .
      or
      git add -A

**git commit**
* The commit command makes sure that the changes are saved to the local repository.
* The command "git commit –m <message>" allows you to describe everyone and help them understand what has happened.
`git commit -m “commit message”`

**git status**
* The git status command tells the current state of the repository.
* The command provides the current working branch. If the files are in the staging area, but not committed, it will be shown by the git status. Also, if there are no changes, it will show the message no changes to commit, working directory clean.
`git status`

**git config**

* The git config command is used initially to configure the user.name and user.email. This specifies what email id and username will be used from a local repository.
* When git config is used with --global flag, it writes the settings to all repositories on the computer.

      git config --global user.name “any user name”
      git config --global user.email <email id>

**git branch**
A branch represents an independent line of development. Branches serve as an abstraction for the edit/stage/commit process. You can think of them as a way to request a brand new working directory, staging area, and project history.
* The git branch command is used to determine what branch the local repository is on.
* The command enables adding and deleting a branch.

      Create a new branch
        git branch <branch_name>
      
      List all remote or local branches
        git branch -a
      
      Delete a branch
        git branch -d <branch_name>

**git checkout**
* The git checkout command is used to switch branches, whenever the work is to be started on a different branch.
* The command works on three separate entities: files, commits, and branches.

      Checkout an existing branch
        git checkout <branch_name>
      
      Checkout and create a new branch with that name
        git checkout -b <new_branch>

        Forcefully delete a specific branch even if it has unmerged changes
        git branch -D <branch>

**git merge**
* The git merge command is used to integrate the branches together. The command combines the changes from one branch to another branch.

We have the emergency fix ready, and so let's merge the master and emergency-fix branches.

First, we need to change to the master branch:

    git checkout master
    Switched to branch 'master'
Now we merge the current branch (master) with emergency-fix:

    git merge emergency-fix
    Updating 09f4acd..dfa79db
    Fast-forward
     index.html | 2 +-
     1 file changed, 1 insertion(+), 1 deletion(-)

* It is used to merge the changes in the staging branch to the stable branch.
 ` git merge <branch_name>`

## Git Commands: Working With Remote Repositories
**git remote** 
* The git remote command is used to create, view, and delete connections to other repositories. 
* The connections here are not like direct links into other repositories, but as bookmarks that serve as convenient names to be used as a reference.
`git remote add origin <address>`

To check the remote URL present in the code/repository, use

      git remote -v

**git clone**
* The git clone command is used to create a local working copy of an existing remote repository.
* The command downloads the remote repository to the computer. It is equivalent to the Git init command when working with a remote repository.
`git clone <remote_URL>`

**git pull** 
* The git pull command is used to fetch and merge changes from the remote repository to the local repository.
* The command "git pull origin master" copies all the files from the master branch of the remote repository to the local repository.
`git pull <branch_name> <remote URL>`

**git push**
* The command git push is used to transfer the commits or pushing the content from the local repository to the remote repository.
* The command is used after a local repository has been modified, and the modifications are to be shared with the remote team members.
`git push -u origin master`

## Some Advanced Git Commands
**git stash**
* The git stash command takes your modified tracked files and saves it on a pile of incomplete changes that you can reapply at any time. To go back to work, you can use the stash pop.
* The git stash command will help a developer switch branches to work on something else without committing to incomplete work.

      Store current work with untracked files
        git stash -u
        
      Bring stashed work back to the working directory
        git stash pop

**git log**
* The git log command shows the order of the commit history for a repository.
* The command helps in understanding the state of the current branch by showing the commits that lead to this state.
`git log`
* To show the log of a particular branch, we use:
`git log <name>/branch`

