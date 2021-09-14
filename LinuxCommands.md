# Description
This file contains the documentation for important linux/unix commands.
## Tips and Tricks

Use the `clear` command to clean out the terminal if it is getting cluttered with too many past commands.

Try the **TAB** button to autofill what you are typing.  
For example, if you need to type Documents, begin to type a command (let’s go with cd Docu, then hit the TAB key) and the terminal will fill in the rest, showing you cd Documents.

**Ctrl+C** and **Ctrl+Z** are used to stop any command that is currently working.  
Ctrl+C will stop and terminate the command, while Ctrl+Z will simply pause the command.

**Ctrl+A** moves you to the beginning of the line while **Ctrl+E** moves you to the end.

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

#### Search, Sort, Filter Commands
 * [wc](#wc)
 * [sort](#sort)
 * [uniq](#uniq)
 * [grep](#grep)

#### Compare Files Commands
 * [cmp](#cmp)
 * [diff](#diff)
 * [comm](#comm)

#### Piping, tee and xargs
 * [Piping](#piping-tee-and-xargs)
 * [tee](#piping-tee-and-xargs)
 * [xargs](#piping-tee-and-xargs)

#### Process Management
 * [ps](#ps)
 * [kill](#kill)
  
#### Compress and Extract Files
 * [tar](#tar)

#### Useful tools
 * [gedit](#gedit)
 * [Putty](#putty)
 * [WinSCP](#winscp)
#### Additional Information
 * [wildcard characters](#wild-card-characters---)
 * [regular expressions](#regex)
 * [Input Redirection](#input-output-and-error-redirection)
 * [Output Redirection](#input-output-and-error-redirection)
 * [Error Redirection](#input-output-and-error-redirection)
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
> Execute (x) 1

2 ways to change permissions :
> Symbolic/ Text Mode 
> > Add execute permission to users :
> > > chmod u+x sample.txt 

> > Rewoke read permission from groups and others : 
> > > chmod g-r, o-r sample.txt

> Numeric Mode
> > Rewoke all permissions from all roles:
> > > chmod 000 sample.txt 
 
> > Add all permissions to users, read & write to groups, read to others:
> > >  chmod 764 sample.txt
## chown
To change or transfer the ownership of a file to the specified username.
``` 
chown linuxuser2 file.ext
```
## wc
To count the number of lines, words, characters, and bytes in one or multiple files or standard input or the input from pipe.
> Options:

`wc -l` --> count no. of lines  
`wc -w` --> count no. of words  
`wc -c` --> count no. of bytes  
`wc -m` --> count no. of characters

## sort
It takes text data as input and outputs sorted data.  
`sort test`   
`sort -n test` --> sorts numerically  
`sort -r test` --> sorts in reverse order

## uniq
To remove duplicates from sorted file.  
```
sort test > sortedtest
uniq sortedtest
```
> Options:  
`uniq -d` --> duplicate lines  
`uniq -u` --> unique lines  
`uniq -c` --> each entry count   
`uniq -i` --> case-insensitive  
## cmp
To compare the two files byte by byte.
```
cmp file1 file2
```

## diff
To display the differences in the files by comparing the files line by line.
```
diff file1 file2
```
> special symbol:

**<** from first file  
**>** from second file  
**c** change  
**d** delete  
**a** add  

## comm
To compare two sorted files line by line and write to standard output; the lines that are common and the lines that are unique.
```
comm file1 file2
```
The output contains three columns where first column contains lines that are unique in file1 ,second column contains lines unique in file2 and the third column contains lines common to both the files.

## Pipe(|), tee and xargs
To send output of one command to another for further processing.
> Syntax:    
```
command1 | command2 | command3
```
> example: 
```
sort filename | uniq
```

In the middle of piping if we use redirection, it will break pipe. For that we need to use **tee** with pipeline. It reads from standard input and writes simultaneously to standard output and one or many files. It’s more of a redirection command.
> example: 
```
ls -l | tee output.txt | wc -l
```
Another important utility used with pipe is **xargs**. It reads streams of data from standard input, then generates and executes command lines.
> example: 
```
cat test.txt | xargs rm
```

## grep
Global regular expression pattern.
To search for a string of characters in a specified file.
```
grep <stringtomatch> <filename>
```
| options | use |
| --- | --- |
| -i | ignore case |
| -n | show the line no. |
| -c | count no. of matches |
| -v | inverse- that do not match the search pattern |
| -w | whole words only |
| -l | prints file names |
| -x | prints entire line |

grep supports matching control option **-e** that allows us to define **multiple patterns** using different strings. Example :  
```
grep -e "Delhi" -e "Chennai" cities
```  
OR  use egrep  
```
egrep "(Delhi|Chennai)" cities
```

grep supports matching control option **-F** that instructs grep to interpret the patterns as a list of **fixed strings** (instead of regular expressions), separated by newlines. Example :   
``` 
grep -F "./
> Mumbai
> Chennai" cities
```
OR use fgrep
```
fgrep "./
> Mumbai
> chennai" cities
```

## ps
To know what all process are running. Process is an instance of running program.  
Use `ps` to get the PID of the process. To see every process on the system **-e** & do full format listing **-f** , use below command :
```
ps -fe
```
Show process hierarchy using **-H** option.
```
ps -F -H
```

## kill
To terminate the running process.  
Issue the `kill` command for the PID you want to terminate.  
To terminate multiple process use option **-9**.
```
kill <PID>
```
## tar
To compress and extract files.  
**c** - creates a new .tar archive file    
**x** - extracts archived files  
**v** - verbosely show the .tar file progress  
**f** - allows to specify filename of the archive file  

3 types of compression:   
* tar
* gunzip
* bunzip

> Compress/ Zip files   

`tar -cvf mydir.tar dirToArchive`  
`tar -cvf mydir.tar.gz dirToArchive`  
`tar -cvf mydir.tar.bz2 dirToArchive`

> Extract/ unzip files

`tar -xvf mydir.tar targetLocation`  
`tar -xvf mydir.tar.gz`  
`tar -xvf mydir.tar.bz2` 


## gedit
General purpose text editor.
```
gedit test
```
## vi
CLI mode text editor.
```
vi test
```
Important vi editor commands:  
> 2 Modes :
* command mode (**esc**)
* insert mode (**i**)

> Important commands: 
* :w! --> save
* :q! --> quit without saving
* :wq! --> save and quit

> Navigation:
* h --> left
* l --> right
* j --> down
* k --> up

> handy commands:
* dd --> delete line
* yy, p --> copy-paste
## Putty
CLI mode to access linux server files from windows.
## WinSCP
Transfer files between your window machine and remote linux server.

To connect Putty and WinSCP with the Linux server, you need to know the  ipaddress, username and password of the linux server you want to connect with from your windws machine.
## wild card characters (?, *, [])
**?** replaces single character.  
**\*** replaces multiple characters.  
**[]** replaces a range of characters.
## REGEX
some examples: 
ls [a-z]* or ls [[:lower:]]*  
ls [A-Z]* or ls [[:upper:]]*  
ls [0-9]* or ls [[:digit:]]*  
ls [[:alpha:]]*.txt  
ls [![:alnum:]]*  
ls { *.java, *.py }

## Input, Output and Error Redirection
| Input | Output | Error |
| --- | --- | --- |
| 0 | 1 | 2|
| < | > - overwrite, >> - append | 2> |
| ex: `cat 0< input.txt` | `cat 1> abc.txt` | `cal 15 2020 2> error.txt`| 
| `cat < input.txt` | `cat > abc.txt` | |
| `cat input.txt` | `cat >> abc.txt` | |
|| `date > output.txt` ||

You can also redirect output of one terimal to another.  
terminal 2-->  `tty`  
: /dev/pts/1  
terminal 1--> `ls > /dev/pts/1`






