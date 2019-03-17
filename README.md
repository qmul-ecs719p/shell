# Shell

This repo guides you through the basics of file systems and the shell in a MacOS system. 

We are all familiar with graphical user interfaces (GUI). They are easy to learn and suitable for “do the thing I want” by “click”. If you wish to do complex and purpose-specific things, you can use shell to express your instructions to the computer. Shell provides a simple language and a command-line interface to use it through.

The heart of a command-line interface is a read-evaluate-print loop (REPL). When you type a command and press `Return` or `Enter`, the shell reads your command, evaluates (or “executes”) it, prints the output of your command, loops back and waits for you to enter another command.

To learn how to use the shell, first we need to start a terminal session:

in **Finder**, open the **Application** -> **Utilities** folder, double-click **Terminal**.

You will see the hostname, followed by your current path and your name.
```
Last login: DDD MMM XX HH:MM:SS on ttysXXX 
HOSTNAME:PATH USER$
```

The `$` sign is a **prompt**, indicating you that the shell is waiting for commands. Your shell may use different text for the prompt. Most importantly: when typing commands, do not type the prompt, only the commands that follow it.

### In this repo, we will introduce some commands on - 

* [Directory Structure and Filesystem](./1_Filesystem.md): How can I move around on my computer and list files and directories? How can I create, copy, and delete files and directories? 

* [Text Wrangling](./2_Text.md): How can I edit files? How can I count the number of lines and sort contents of the files?

* [Job Controls](./3_Job.md): How can I start a command in background and detach process in terminal?

* [Working on EECS Servers](./4_Server.md): How can I run commands on EECS servers?

---

There are a couple of tools that are going to be handy:s

**1. TAB key**

You probably want to type precise commands. For that you can use the embedded auto completion with your `TAB_KEY`.

For example,
```
HOSTNAME:PATH USER$ cd De[TAB_KEY]
HOSTNAME:PATH USER$ cd Desktop
```

**2. Use history**

It's good to know how to go back on your steps to take a look of what you have done.

- You can use the `history` command:
```
HOSTNAME:PATH USER$ his[TAB_KEY] 
HOSTNAME:PATH USER$ history
```

- Or you can go through your history using the `UP_KEY`:
```
HOSTNAME:PATH USER$ [UP_KEY]
HOSTNAME:PATH USER$ history
```

**3.Read the manual**

Unix has an embedded manual. Just type `man` followed by the name of the command and you will get the manual for it. Use key for navigating throughout it and after that press `q` to quit.

Generally, commands take the form:  `<command> <options> <parameters>`

`<options>` usually being of the form `-x` or `--extract`, `<parameters>` being based on their position.

**4.Keyboard shortcuts**

a. Control Process

* `Ctrl` + `C` Kill whatever you are running 

* `Ctrl` + `Z` Puts whatever you are running into a suspended background process. `fg` restores it.

b. Control your entry

* `Ctrl` + `D` Exit the current shell

* `Ctrl` + `L` Clears the Screen, similar to the clear command

* `Ctrl` + `U` Clears the line before the cursor position. If you are at the end of the line, clears the entire line.

* `Ctrl` + `A` Go to the beginning of the line you are currently typing on

* `Ctrl` + `E` Go to the end of the line you are currently typing on

* `Ctrl` + `W` Delete the word before the cursor

* `Ctrl` + `K` Clear the line after the cursor

* `Ctrl` + `R` Let’s you search through previously used commands

* `TAB` Auto-complete files and folder names

c. Control your terminal

* `Cmd` + `N` Create a new terminal window

* `Cmd` + `RIGHT` and `Cmd` + `LEFT` Jump between windows

* `Cmd` + `shift` + `w` close Terminal windows

* `Cmd` + `t` Create a new terminal tab

* `Cmd` + `Shift` + `right`/`left` Jump between tabs

* `Cmd` + `w` Close Tab

* `Cmd` + `up` line up

* `Cmd` + `down` line down