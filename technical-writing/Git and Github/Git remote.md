## Git remote

The git remote command lets you create, view, and delete connections to other repositories. Remote connections are more like bookmarks rather than direct links into other repositories. Instead of providing real-time access to another repository, they serve as convenient names that can be used to reference a not-so-convenient URL.

## Git remote usage overview

The git remote command is essentially an interface for managing a list of remote entries that are stored in the repository's ./.git/config file. The following commands are used to view the current state of the remote list.
## Viewing git remote configurations 

`git remote`

List the remote connections you have to other repositories.

`git remote -v`

Same as the above command, but include the URL of each connection.

## Creating and modifying git remote configurations

The git remote command is also a convenience or 'helper' method for modifying a repo's ./.git/config file. The commands presented below let you manage connections with other repositories. The following commands will modify the repo's /.git/config file. The result of the following commands can also be achieved by directly editing the ./.git/config file with a text editor.

`git remote add <name> <url>`

Create a new connection to a remote repository. After adding a remote, you’ll be able to use ＜name＞ as a convenient shortcut for ＜url＞ in other Git commands.

`git remote rm <name>`

Remove the connection to the remote repository called ＜name＞.

`git remote rename <old-name> <new-name>`

Rename a remote connection from ＜old-name＞ to ＜new-name＞.