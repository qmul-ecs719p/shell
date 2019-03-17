# Job Controls

We are finally ready to see what makes the shell such a powerful programming environment. We are going to take the commands we repeat frequently and save them in files so that we can re-run all those operations again later by typing a single command. For historical reasons, a bunch of commands saved in a file is usually called a shell script, but make no mistake: these are actually small programs.

Make sure we at at the directory of `demofolder`, and let's create a script named `getline_2to4.sh` using text editor "nano" (which runs within the shell). If the file does not exist, it will be created:

```
$ nano getline_2to4.sh
```

Simply insert the following line to the script:

```
head -n 4 "$1" | tail -n 3
```

Now we are not running it as a command just yet. We are putting the commands in a file. This command will select lines 2-4 of a file. "$1" means “the first filename (or other argument) on the command line”.

Then we save the file (`Ctrl-O` in nano), and exit the text editor (`Ctrl-X` in nano). Check that the directory `demofolder` now contains a file called `getline_2to4.sh`.

We can now run our script like this:

```
$ bash getline_2to4.sh demofile1.txt
```

When you execute a script or a command that takes a long time, you can run it as a background job.  

To execute a background job, just append an ampersand `&` to the command. For example, use the `ping` command to test the connection between your computer and google in the background, and send the outputs into a file:

```
$ ping www.google.com > ./tempfile.txt &
```

You can also send an already running foreground job to background as explained below:

- Press `CTRL`+`Z` which will suspend the current foreground job.

- Execute `bg` to make that command to execute in background.

Using the same `ping` example:

```
$ ping www.google.com > ./tempfile.txt
[CTRL+Z]
[1]+  Stopped                 ping www.google.com > ./tempfile.txt
$ bg
[1]+ ping www.google.com > ./tempfile.txt &
```

You can list out the background jobs with the command `jobs`. For example:
```
$ jobs
[1]+  Running                 ping www.google.com > ./tempfile.txt &
```

The numbers in `[ ]`  are the job numbers that `bg` (background), `fg` (foreground), and `kill` can use.

A background job can be brought to the foreground with the command `fg`. For example:

```
fg %1
```

To kill a background job, we can use `kill %JOB_NUMBER`. 

This capability of sending jobs to background or foreground it's really handy, but if you are logging on and off all the time it gets difficult. If you close the terminal, jobs will be terminated too.

That's why there is a very powerful application it will take you in a completely new different level. It's call `screen` and is more complex. Please [check this article](https://www.ibm.com/developerworks/aix/library/au-gnu_screen/index.html) for further reading on `screen`.