# Linux Commands

Linux is a family of open-source Unix-like operating systems based on the Linux kernel, an operating system kernel first released on September 17, 1991, by Linus Torvalds. Linux is typically packaged in a Linux distribution.

Linux is a case-sensitive operating system. So, `file` and `File` are two different files in Linux.
All below commands are executed in Ubuntu.

## General

`pwd`
- to print current working directory

`whoami`
- to print current user

`history`
- to view all the executed commands in current session

`!<number of command>`
- to execute the command which is in the history



## Managing Packages

`apt`
- advance package tool (package manager in ubuntu)

`apt list`
- to list all the packages

`apt update`
- to update all existing packages
- always run this before going to install a new package

`apt install <package>`
- to install a package

`apt remove <package>`
- to remove an existing package



## File System

Everything in linux is a file

`cd ~`
- to go to home directory

`cd ..`
- to go to parent directory

`cd <directory>`
- to go to a directory
- can use absolute path or relative path

`cd -`
- to go to previous directory

`mkdir <directory> <...>`
- to create a directory(s)

`rmdir <directory> <...>`
- to remove a directory(s)
- only works for empty directorie(s)	

`mv <old file name/file> <new file name/directory>`
- to rename file
- to rename directory
- to move file to a directory
- to move directory to a another directory

`touch <file name> <...>`
- to create a file(s)

`rm <file name> <...>`
- to remove a file(s)

`rm -r <directory> <...>`
- to remove a directory(s) recursively

`rm -rf <directory> <...>`
- to remove a directory(s) recursively without asking confirmation

`ls`
- to list files and directories in current directory

`ls -l`
- to list files and directories in current directory with details

`ls -lh`
- to list files and directories in current directory with details and human readable format

`ls -a`
- to list all files and directories in current directory including hidden files

`ls -l <directory>`
- to list files and directories in a another directory
- can use absolute path or relative path

`ls -1`
- to list files and directories in one column



## Viewing and Editing Files

`cat <file name>`
- to view file content

`cat <file name> <...>`
- to view concatenated file content

`head <file name>`
- to view first 10 lines of file content

`head -n <number> <file name>`
- to view first <number> lines of file content

`tail <file name>`
- to view last 10 lines of file content

`tail -n <number> <file name>`
- to view last <number> lines of file content

`more <file name>`
- to view file content in interactive way
- 'up' and 'down' keys to scroll
- 'space' key for next page
- 'q' key for quit

`less <file name>`
- to view file content in interactive way (better than `more`)
- 'up' and 'down' keys to scroll
- 'space' key for next page
- 'q' key for quit

`nano`
- to open nano editor
- nano is a default text editor for linux
- if nano is not installed, install it using `apt install nano`

`nano <file name>`
- to open file in nano editor



## Redirection

`cat <file name> > <new file name>`
- to copy file content to a new file
- '>' will overwrite the content of new file

`cat <file name> <...> > <new file name>`
- to concatenate content of files to a new file
- '>' will overwrite the content of new file if it exists

`cat <file name> >> <file name>`
- to append content of file to another file

`cat <file name> <...> >> <file name>`
- to append content of files to another file

Ex: `ls -l /etc > etc-content.txt`
- get the long listing of file content in 'etc' directory and write it into file 'etc-content.txt'



## Searching for text

`grep <regular expression/test> <file name>`
- to search for regular expression or text in a file
- case sensitive search by default
- grep stands for 'global regular expression print'

`grep -i <reg ex/text> <file name>`
- to search for regular expression or text in a file in case insensitive way

`grep -r <reg ex/test> <directory>`
- to search for regular expression or text in a directory recursively
- search in sub directories as well

Ex: 
- `grep hello file1.txt`
- `grep hello file1.txt file2.txt`
- `grep hello *.txt`
- `grep "hello world" file1.txt`



## Finding Files and Directories

`find`
- to find all the files and directories in current directory recursively
- search on sub directories as well

`find <file name/directory name>`
- to find a file or directory
- can use absolute path or relative path of file or directory

`find -type d`
- to get only the directories in current directory recursively

`find -type f`
- to get only the files in current directory recursively

`find -type f -name "<file name>"`
- to find a file in current directory recursively by name

`find -type f -iname "<file name>"`
- to find a file in current directory recursively by name in case insensitive way

`find -type d -name "<directory name>"`
- to find a directory in current directory recursively by name

`find -type d -iname "<directory name>"`
- to find a directory in current directory recursively by name in case insensitive way

Ex: 
- `find / -type f -name "*.py"`
- `find / -type f -name "*.py" > python-files.txt`



## Chaining commands

Ex:

`mkdir dir1 ; cd dir1 ; echo done`
- to create a directory, go to that directory and print 'done'
- if first command fails, second command will still execute (`cd dir1` will execute even if `mkdir dir1` fails, but in this case, second command will not execute)

`mkdir dir1 && cd dir1 && echo done`
- to create a directory, go to that directory and print 'done'
- if first command fails, second command will not execute
- each command will only execute if the previous one was successful.

`mkdir dir1 || echo "directory exists"`
- to create a directory, if directory already exists, print 'directory exists'
- if first command fails, second command will execute

`ls /bin | more`
- to list files in '/bin' directory and view it in interactive way
- this is called 'piping': the output of the first command `ls /bin` is passed as input to the second command `more`

```
mkdir dir1 ;\
cd dir1 ;\
echo done
```
- break commands into several lines by using backslash (\\)



## Environment Variables

`printenv`
- to print all environment variables with values

`printenv <environment variable>`
- to print the value of an environment variable

`echo $<env variable>`
- to print the value of an environment variable (another way)

`export <env variable name>=<value>`
- to define a new environment variable
- this is only for current terminal session, once exit from the terminal session, it will be disappear

`echo DB_USER=adheesha >> .bashrc`
- save new environment variable permently
- for this, have to save it in .bashrc file
- don't use redirection operation `>`, sice this could completly rewright the '.bashrc' file
- instead of this use redirection operation `>>`
- the newly saved environment variable will be available from next terminal session onwards
- because '.bashrc' files only loads once when we start the session
- can use another command to reload the '.bashrc' file manually

`source .bashrc`
- to reload the '.bashrc' file manually

`source ~/.bashrc`
- to reload the '.bashrc' file manually, if not in the home directory
