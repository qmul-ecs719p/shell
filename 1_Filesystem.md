# Directory Structure and Filesystem

The part of the operating system responsible for managing files and directories is called the **filesystem**. It organizes our data into files, which hold information, and directories (also called “folders”), which hold files or other directories.

First let’s find out where we are by running a command called `pwd` (which stands for “print working directory”). Directories are like places - at any time while we are using the shell we are in exactly one place, called our current working directory. Commands mostly read and write files in the current working directory, i.e. “here”, so knowing where you are before running a command is important:

```
$ pwd
$ /Users/USERNAME
```

The computer’s response is USERNAME’s home directory.

Folders and subfolders are separated by `/` symbol in UNIX (for Windows it's `\`).

To see the files and directories under the current folder, we can type:

```
$ ls
```

To list files in the root folder, we can do:

```
$ ls /
```

Full paths from the root folder are absolute paths, e.g. `/Users/USERNAME/qmul-ecs719p/shell/1_Filesystem.md`. 

Paths from current working directory are relative paths, e.g. `./qmul-ecs719p/shell/1_Filesystem.md`.

Generally relative paths are useful within work whereas absolute paths are handy for referring to standard files.

Directory abbreviations:

- Current directory: `.`

- Parent directory: `..`

- Home directory: `~`

Now let's create a new folder named `demofolder`:

```
$ mkdir demofolder
```

If we list what we have in the newly created folder by `$ ls demofolder`, nothing will be returned.

We can navigate to the new folder using command `cd` followed by a directory name to change our working directory. `cd` stands for “change directory”, which is a bit misleading: the command doesn’t change the directory, it changes the shell’s idea of what directory we are in.

```
$ cd demofolder
```

If you use `pwd` to check the current working directory, it will return `/Users/USERNAME/qmul-ecs719p/shell/demofolder`.

We have known that `mkdir` can create a new folder. To create a text file, let's say `demofile.txt`, we can run a text editor called Nano using:

```
$ nano demofile.txt
```

Let’s type the following lines into the text:

```
Andrew, 0207623512
Bob, 02089462713
Chris, 0201234567
Dave, 0207654321
Ed, 02089012345
```

We can press `Ctrl+O` (press the `Ctrl` or `Control` key and, while holding it down, press the `O` key) to write our data to disk (we’ll be asked what file we want to save this to: press Return to accept the suggested default of `demofile.txt`). Once our file is saved, we can use `Ctrl-X` to quit the editor and return to the shell.

There are many choices of text editors:

- `nano` is easy to use if not particularly powerful

- `vi` and `emacs` for power users

- or launch your favourite GUI editor, such as SublimeText, TextWrangler, etc.

We can use command `cat` (concatenate a file) to display `demofile.txt` in terminal:

```
$ cat demofile.txt
```

Display only the first or last 2 lines can be done by `$ head -n 2 demofile.txt` or `$ taiil -n 2 demofile.txt`.

To rename `demofile.txt` into `demofile1.txt`:

```
$ mv demofile.txt demofile1.txt
```

The above command `mv` actually moves one or more files or directories from one place to another. If both filenames are on the same directory, this results in a simple file rename; otherwise the file content is copied to the new location and the old file is removed.

To duplicate `demofile1.txt` and name the new file as `demofile2.txt`:

```
$ cp demofile1.txt demofile2.txt
```

To remove a file:

```
$ cp demofile.txt
```

This will return `rm: demofile.txt: No such file or directory`, since we have already renamed it into `demofile1.txt`.

Likewise, to move/copy/remove a directory and all its contents, we just need to use the recursive flag `-r`. For example, let's go back to the parent directory and back up `demofolder`:

```
$ cd ..
$ cp -r demofolder demofolder_backup
```

We can check the result by listing the contents of both directories:

```
$ ls demofolder demofolder_backup
```

To remove the directory `demofolder_backup` and all its contents:

```
$ rm -r demofolder_backup
```

**Given that there is no way to retrieve files deleted using the shell, `rm -r` should be used with great caution (you might consider adding the interactive flag `rm -r -i`).**