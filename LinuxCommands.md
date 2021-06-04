# Description
This file contains the documentation for important linux/unix commands.

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