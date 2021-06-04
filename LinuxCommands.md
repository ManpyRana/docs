# Description
This file contains the documentation for important linux/unix commands.

### Table of Contents
#### File Commands

 * [cat](#cat)
 * [head](#head---tail)
 * [tail](#head---tail)
 * [more](#more--less)
 * [less](#more--less)
## cat
To display the contents of a file.
```
cat filename.txt
```
To create a new file with content. 
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
`cat` displays the full content of file. If the file is too big you can use some commands like `head`, `tail`, `more`, `less` to improve readability. 

## head  / tail
| head | tail |
| ---- | ---- |
| `head filename.txt` | `tail filename.txt` |
| By default it displays top 10 lines of file. To display specific no. of lines, use `-n` with head command. | By default it displays bottom 10 lines of file. To display specific no. of lines, use `-n` with tail command. |
| `head -n 5 filename.txt` | `tail -n 5 filename.txt` |

## more / less
| more | less |
| --- | --- |
|moves in forward direction only| moves in both directions |
| `more filename.txt` | `less filename.txt` |
| N/A | use *up arrow key* |

To display page by page, press *spacebar*.  
To display line by line, press *enter*.  
To exit from file, press *q*.