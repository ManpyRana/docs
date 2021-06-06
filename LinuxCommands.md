# Description
This file contains the documentation for important linux/unix commands.
## Tips and Tricks
Bonus Tips and Tricks
Use the `clear` command to clean out the terminal if it is getting cluttered with too many past commands.

Try the **TAB** button to autofill what you are typing.  
For example, if you need to type Documents, begin to type a command (let’s go with cd Docu, then hit the TAB key) and the terminal will fill in the rest, showing you cd Documents.

**Ctrl+C** and **Ctrl+Z** are used to stop any command that is currently working.  
Ctrl+C will stop and terminate the command, while Ctrl+Z will simply pause the command.

If you accidental freeze your terminal by using **Ctrl+S**, simply undo this with the unfreeze **Ctrl+Q**.

**Ctrl+A** moves you to the beginning of the line while **Ctrl+E** moves you to the end.

You can run multiple commands in one single command by using **;** to separate them.  
For example Command1; Command2; Command3. Or use && if you only want the next command to run when the first one is successful.

You can easily learn how to use Linus Commands right from Linux’s shell by using the `man` command.   
For instance, entering `man tail` will show the manual instruction of the tail command.

### Table of Contents
#### File Commands

 * [cat](#cat)
 * [head](#difference-between-head-and-tail-command-)
 * [tail](#difference-between-head-and-tail-command-)
 * [more](#difference-between-more-and-less-command-)
 * [less](#difference-between-more-and-less-command-)
 * [touch](#touch)
 * [cp](#cp)
 * [mv](#mv)
 * [rm](#rm)

#### Directory Commands
 * [rmdir](#rmdir)
 * [mkdir](#mkdir)
 * [cd](#cd)
 * [pwd](#pwd)

#### List files or Directories
 * [ls](#ls)

#### System Commands
* [who](#who)
* [whoami](#whoami)
* [hostname](#hostname)
* [uptime](#uptime)
* [cal](#cal)
* [date](#date)

#### Roles and Permissions
* [chmod](#chmod)
* [chown](#chown)
## cat
To display the contents of a file.
```
cat filename.txt
```
To create a new file with content. To create empty file use `touch` command. 
```
cat > filename.txt
your content
```
To display content from multiple files.
```
cat file1.txt file2.txt
```
To Append file.
```
cat >> filename.txt
```

## head, tail, more, less
`cat` displays the full content of file. If the file is too big you can use some commands like `head`, `tail`, `more`, `less` to improve readability. 

### Difference between head and tail command : 
| head | tail |
| ---- | ---- |
| `head filename.txt` | `tail filename.txt` |
| By default it displays top 10 lines of file. To display specific no. of lines, use `-n` with head command. | By default it displays bottom 10 lines of file. To display specific no. of lines, use `-n` with tail command. |
| `head -n 5 filename.txt` | `tail -n 5 filename.txt` |

### Difference between more and less command : 
| more | less |
| --- | --- |
|moves in forward direction only| moves in both directions |
| `more filename.txt` | `less filename.txt` |
| N/A | use *up arrow key* |

To display page by page, press *spacebar*.  
To display line by line, press *enter*.  
To exit from file, press *q*.
## touch
To create empty file.
```
touch myfile.txt
```
To create hidden file start filename with *dot*.
```
touch .myhiddenfile.txt
```
## cp
Copies files from one location to another.
```
cp srcfile destdir
```
## mv
To Rename a file.
 ```
 mv oldname newname
 ```
To move file from one directory to another directory.
```
 mv filename newdirectory
 ```
## rm
To delete a file.
```
rm myfile.txt
```
To remove a directory, even if files existed in that directory. 
```
rm -r mydir
```
## rmdir
To delete a directory. It works only if directory is empty.
```
rmdir dir
```
## mkdir
To create a new directory.
```
mkdir newdirname
```
To make directory with sub-directories.
```
mkdir -p world/countries/states
```
## cd
To change directory one level up.
> cd dirname

To change directory one level down.
> cd ..

To move to root directory.
> cd ~

## pwd
To display path of present working directory.
## ls
To list the contents of the current working directory.
| flags | use |
| --- | --- |
| `ls /` | To list the content of root directory |
| `ls ~` | To list the content of user's home diectory |
| `ls -d */` | To list only directories |
| `ls *` | To list files with its sub directories |
| `ls -R` | To list files recursively down the last file | 
| `ls -s` | To list files with their sizes |
| `ls -S` | To list files sorted by size in descending order | 
| `ls -r` | To list files in reverse order |
| `ls -t` | To list files sorted by date and time |
| `ls -l` | To list files in long format |
| `ls -a` | To list files including hidden files |
| `ls -lh` | To long list files with readable file size |

## who
 To a list of logged-in users.
## whoami
To print the user’s name from which they are currently logged-in.
## hostname
To know the name of your host/network.  
Adding a -i to the end will display the IP address of your network.

## uptime
To return information about how long your system has been running
## cal
To display current month calendar.   
To see the calendar of a whole year. `cal 2021`.  
To see the calendar of a specific month. `cal 3 2021`. 
## date
To display the current date and time.
ex o/p: `Tue Oct 10 22:55:01 PDT 2017`

## chmod
To change the read, write, and execute permissions of files and directories.

3 Types of Roles :
> Owners/Users (u)  
> Groups (g)  
> Others (o)  

3 Types of Permissions :
> Read (r) 4  
> Write (w) 2  
> Execute (e) 1

2 ways to change permissions :
> Symbolic/ Text Mode 
> > chmod u+x sample.txt  
> > chmod g-r, 0-r sample.txt

> Numeric Mode
> > chmod 000 sample.txt  
> > chmod 764 sample.txt
## chown
To change or transfer the ownership of a file to the specified username.
``` 
chown linuxuser2 file.ext
```








