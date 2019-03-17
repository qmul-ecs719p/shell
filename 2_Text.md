# Text Wrangling

Here we will do some text wrangling given the two files we created in [1_Filesystem](./1_Filesystem.md).

First we need to move to the working directly, which is the folder that has the two files:

```
$ cd demofolder
```

Then display the text contents in the two files:

```
$ cat demofile1.txt demofile2.txt
```

The following ten lines should be presented in the terminal:

```
Andrew, 0207623512
Bob, 02089462713
Chris, 0201234567
Dave, 0207654321
Ed, 02089012345
Andrew, 0207623512
Bob, 02089462713
Chris, 0201234567
Dave, 0207654321
Ed, 02089012345
```

We can save the above results into a new file `demofile_all.txt` using the greater than symbol, i.e. `cat demofile1.txt demofile2.txt > demofile_all.txt`. `>` tells the shell to redirect the command’s output to a file instead of printing it to the screen. (This is why there would be no screen output: everything that `cat` would have printed has gone into the file `demofile_all.txt` instead.) The shell will create the file if it doesn’t exist. If the file exists, it will be silently overwritten, which may lead to data loss and thus requires some caution. 

To get the number of lines, words, and characters in `demofile_all.txt` (from left to right, in that order):

```
$ wc demofile_all.txt
```

To sort the line in a file into order (use the `-n` flag if you prefer to specify the sort is numerical instead of alphanumerical):

```
$ sort demofile_all.txt
```

This does not change the file itself, to save the output we can redirect the output from the terminal to a file using `$ sort demofile_all.txt > demofile_allsorted.txt`

To output a file without duplicate lines, we can use:

```
$ uniq demofile_allsorted.txt
```

We can acutally make the above commands easier by running `sort` and `uniq` together:

```
$ sort demofile_all.txt | uniq > demofile_allsorted_uniq.txt 
```

The vertical bar, `|`, between the two commands is called a pipe. It tells the shell that we want to use the output of the command on the left as the input to the command on the right. The computer might create a temporary file if it needs to, or copy data from one program to the other in memory, or something else entirely; we don’t have to know or care.

To search for a text string in files, we can use `grep`, which stands for "global regular expression print," processes text line by line and prints any lines which match a specified pattern. For example, search for `Bob` in `demofile_all.txt`: 

```
$ grep Bob demofile_all.txt
```

If we have multiple files to search, we can search them all using a wildcard in our FILE name. Instead of specifying `demofile_all.txt`, we can use an asterisk `*` and the `.txt` extension. When the command is executed, the shell will expand the asterisk to the name of any file it finds (within the current directory) which ends in `.txt`.

```
$ grep Bob *.txt
```

Noted that you can use [regular expressions](https://en.wikipedia.org/wiki/Regular_expression) to perform more powerful searches!

If you want to perform the same actions on many different files, we can use **loop** to execute commands repeatedly.. Similar to wildcards and tab completion, using loops also reduces the amount of typing (and typing mistakes). Here’s a simple example that displays the first three lines of each txt file in turn:

```
$ for filename in *.txt
> do
>    head -n 3 $filename	# Indentation within the loop aids legibility
> done
```