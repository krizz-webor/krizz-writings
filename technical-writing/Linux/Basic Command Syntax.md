## Basic Command Syntax
This module deals exclusively with the CLI or Command Line Interface, rather than a GUI or Graphical User Interface you may be familiar with. The CLI terminal is a powerful tool that is often the primary method used to administer small low-power devices, extremely capable cloud computing servers, and everything in between. A basic understanding of the terminal is essential to diagnosing and fixing most Linux based systems. Since Linux has now become so ubiquitous, even those who plan on working primarily with systems not utilizing the Linux kernel can benefit from having a basic understanding of the terminal.

What is a command? A command is a software program that when executed on the CLI (command line interface), performs an action on the computer. When you type in a command, a process is run by the operating system that can read input, manipulate data and produce output. A command runs a process on the operating system, which then causes the computer to perform a job.

To execute a command, the first step is to type the name of the command. Click in the terminal on the right. Type `ls` (lowercase letters **L** and **S**) and hit **Enter**. The result should resemble the example below:

    sysadmin@localhost:~$ ls
    Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos

The name of the command is often based on what it does or what the developer who created the command thinks will best describe the command's function. For example, the `ls` command displays a listing of information about files. Associating the name of the command with something mnemonic for what it does may help you to remember commands more easily.

**Consider This**

Every part of the command is normally case-sensitive, so `LS` is incorrect and will fail, but `ls` is correct and will execute.

    sysadmin@localhost:~$ LS
    -bash: /usr/games/LS: Permission denied

Most commands follow a simple pattern of syntax:

    command [options…] [arguments…]

In other words, you type a command, followed by any *options* and/or *arguments* before pressing the **Enter** key. Typically *options* alter the behavior of the command and arguments are items or values for the command to act upon. Although there are some commands in Linux that aren’t entirely consistent with this syntax, most commands use this syntax or something similar.

In the example above, the `ls` command was executed without any options or arguments. When this is the case, it’s default behavior is to return a list of files contained within the current directory.

    sysadmin@localhost:~$ ls
    Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos

## Arguments

    command [options…] [arguments…]

An argument can be used to specify something for the command to act upon. The `ls` command can be given the name of a directory as an argument, and it will list the contents of that directory. In the next example, the Documents directory will be used as an argument:

    sysadmin@localhost:~$ ls Documents
    School           alpha-second.txt  food.txt     linux.txt     os.csv
    Work             alpha-third.txt   hello.sh     longfile.txt  people.csv
    adjectives.txt   alpha.txt         hidden.txt   newhome.txt   profile.txt
    alpha-first.txt  animals.txt       letters.txt  numbers.txt   red.txt
The resulting output is a list of files contained with the Documents directory.

Because Linux is open source, there are some interesting secrets that have been added by developers. For example, the `aptitude` command is a package management tool available on some Linux distributions. This command will accept moo as an argument:

    sysadmin@localhost:~$ aptitude moo  
    There are no Easter Eggs in this program.

## Options

    command [options…] [arguments…]

Options can be used to alter the behavior of a command. On the previous page, the `ls` command was used to list the contents of a directory. In the following example, the `-l` option is provided to the `ls` command, which results in a "long display" output, meaning the output gives more information about each of the files listed:

    sysadmin@localhost:~$ ls -l
    total 32
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Desktop                        
    drwx------ 4 sysadmin sysadmin 4096 Dec 20  2017 Documents                      
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Downloads                      
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Music                          
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Pictures                       
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Public                         
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Templates                      
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Videos
Note that, in the command above, -l is a lowercase letter "L".
Often the character is chosen to be mnemonic for its purpose, like choosing the letter *l* for *long* or *r* for *reverse*. By default, the `ls` command prints the results in alphabetical order, so adding the `-r` option will print the results in reverse alphabetical order.

    sysadmin@localhost:~$ ls -r
    Videos  Templates  Public  Pictures  Music  Downloads  Documents  Desktop

Multiple options can be used at once, either given as separate options as in `-l -r` or combined like `-lr`. The output of all of these examples would be the same:

    ls -l -r
    ls -rl
    ls -lr

As explained above, `-l` gives a long listing format while `-r` reverses the listing. The result of using both options is a long listing given in reverse order:

    sysadmin@localhost:~$ ls -l -r
    total 32
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Videos                         
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Templates                      
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Public                         
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Pictures                       
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Music                          
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Downloads                      
    drwx------ 4 sysadmin sysadmin 4096 Dec 20  2017 Documents                      
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Desktop   
    sysadmin@localhost:~$ ls -rl
    total 32
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Videos                         
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Templates                      
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Public                         
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Pictures                       
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Music                          
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Downloads                      
    drwx------ 4 sysadmin sysadmin 4096 Dec 20  2017 Documents                      
    drwx------ 2 sysadmin sysadmin 4096 Dec 20  2017 Desktop 

Ultimately, commands can use many combinations of options and arguments. The possibilities for each command will be unique. Remember the `aptitude` easter egg?

    sysadmin@localhost:~$ aptitude moo
    There are no Easter Eggs in this program.

It is possible to alter the behavior of this command using options. See what happens when the `-v` (verbose) option is added:

    sysadmin@localhost:~$ aptitude -v moo
    There really are no Easter Eggs in this program.

By combining multiple `-v` options, we can get a variety of responses:

    sysadmin@localhost:~$ aptitude -vv moo
    Didn't I already tell you that there are no Easter Eggs in this program?
    sysadmin@localhost:~$ aptitude -vvv moo
    Stop it!

Remember multiple options can be denoted separately or combined:

    aptitude -v -v moo
    aptitude -vv moo
Keep adding `-v` options to see how many unique responses you can get!