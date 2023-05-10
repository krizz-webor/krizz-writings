# Linux Editor commands
## Nano Editor
The main syntax to open Nano and to edit a certain file is:

`nano filename`

Let’s say we want to open a file named demo.txt. The command would look like:

`nano demo.txt`

You can open various file types, like .txt, .php, .html, and so on. Just keep in mind that if you want to open a specific file, you will need to be in the directory where the file is located.

However, if you are in another folder, and you want to open a file (demo.txt) in /path/to/directory, you can enter this line instead:

`nano /path/to/directory/demo.txt`

If you enter a file name and that file is not present in the directory, Nano will create a new file. Meanwhile, if you only execute the nano command without specifying the file name, the Nano text editor will create an empty untitled file and ask for a name when you exit the editor.

After running the nano command, a new window will pop up where you can freely edit the file. Just use the arrow keys on your keyboard to move the cursor around the text.

At the bottom of the window, you can find some shortcuts to use with the Nano editor. The “^” (caret) means that you must press CTRL (Windows) or control (macOS) to use the chosen command. Here are a few examples.

Press `CTRL + O` to save the changes made in the file and continue editing.
To exit from the editor, press `CTRL + X`. If there are changes, it will ask you whether to save them or not. Input Y for Yes, or N for No, then press Enter. But if there are no changes, you will exit the editor right away.

## Basic Nano Text Editor Commands
Command    Explanation
CTRL + A    Lets you jump to the beginning of the line.
CTRL + E    Lets you to jump to the end of the line.
CTRL + Y    Scrolls page down.
CTRL + V    Scrolls page up.
CTRL + G    A Help window will pop out and show you all the available commands.
CTRL + O    To save the file. Nano will ask you to edit or verify the desired file name.
CTRL + W    Search for a specified phrase in your text. Press ALT + W to search for the same phrase again.
CTRL + K    It cuts the entire selected line to the cut buffer (similar to clipboard).
CTRL + U    To paste the text from the cut buffer into the selected line.
CTRL + J    Justifies the current paragraph.
CTRL + C    Shows the current cursor position in the text (line/column/character).
CTRL + R    Opens a file and inserts it at the current cursor position.
CTRL + X    To exit Nano text editor. It prompts a save request if you made any changes to the file.
CTRL + \    Replaces string or a regular expression.
CTRL + T    Invokes the spell checker, if available.
CTRL + _    Lets you go to the specified line and column number.
ALT + A    To select text. You can combine this command with CTRL + K to cut a specific part of the text to the cut buffer.

## Vim command

To open a file in vim editor just write the file name after the vim command in the terminal as follows:

`vim filename.txt`

Then the file will be opened.

* Write into file 

In the previous step we have opened the file now, Let’s write some content in to write data we need to go in insert mode. To go into write mode type **i**.  As follows:

`i`

After going into insert mode you will see INSERT in the status bar. After that, we can write any data in it.

* Save and Exit:

We have written the data into a file now the task is to save and close the file to do that first exit from insert mode by pressing the **Esc key**. To write a command first type semicolon  (  :  )  and then type the command **wq!**  or **x!** (both do the same thing) And then hit ENTER.

`:wq! or :wq`

* Exit without saving the file:

To exit from the file without saving the file just use the command q! As follows

`:q!`

Vim also comes with its own tutorial. You can see this tutorial by command vimtutor into the terminal .

`vimtutor`