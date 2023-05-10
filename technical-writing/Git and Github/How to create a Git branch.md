## How to create a Git branch
**List all Branches**

List all of the branches in your repository. This is synonymous with git branch --list.
`git branch`

**Create a New Branch**

Create a new branch called ＜branch＞. This does not check out the new branch.
`git branch <branch>`

**Deleting a Specified Branch**

Delete the specified branch. This is a “safe” operation in that Git prevents you from deleting the branch if it has unmerged changes.
`git branch -d <branch>`

**Force deleting a specified Branch**

Force delete the specified branch, even if it has unmerged changes. This is the command to use if you want to permanently throw away all of the commits associated with a particular line of development.
`git branch -D <branch>`

**Renaming Current Branch**

Rename the current branch to ＜branch＞.
`git branch -m <branch>`

**List all remote Branches**

List all remote branches. 
`git branch -a`
