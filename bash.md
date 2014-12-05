Bash
====

Basic Commands
--------------

 * `man <command>` - view the manual page for a command.
 * `<command> --help` - show the usage information for a command.
 * `history` - show recently executed commands.

### Navigation

 * `pwd` - print the path of the current directory.
 * `ls <directory>` - list contents of a directory.
 * `cd <directory>` - change the current directory.
 * `cd -` - move back to the directory you were last in.
 * `find -name <filename>` - find a file with a given name.

### File manipulation

 * `touch <name>` - create an empty file, or update the timestamp on an existing file.
 * `cat <file>` - print the contents of a file.
 * `head [-n 10] <file>` - print the first 10 lines of a file.
 * `tail [-n 10] <file>` - print the last 10 lines of a file.
 * `cp <file> <destination>` - copy a file.
 * `mv <file> <destination>` - move or rename a file.
 * `ln -s <source> <destination>` - create a link to a file or directory.
 * `rm <file>` - remove file.
 * `chmod <permissions> <file>` - change permissions of a file.

### Directory manipulation

 * `mkdir <name>` - create a directory 
 * `cp -r <directory> <destination>` - copy a directory and it's contents.
 * `rm -r <directory>` - remove a directory and it's contents.
 * `chmod -r <permissions> <file>` - change permissions of a directory and it's contents.

### Filter, sort and count data

 * `grep <text> <file>` - search a file for a piece of text
 * `grep -R <text> <directory>` - recursively search the files in a directory for a piece of text
 * `sort <file>` - sort the contents of a file
 * `wc [-l] [-w] <file>` - print a word count for a file
   * `-l` for lines, `-w` for words

Shortcuts
---------

 * `tab` - attempt to autocomplete the current buffer.
 * `ctrl-r` - search command history.
 * `ctrl-z` - suspend a running command.
 * `ctrl-d` - exit the shell.

Managing processes
------------------

A running process can be suspended with the `ctrl-z` shortcut, which will assign the process a 'job id' and allow you to continue using the shell. The `fg` command will resume the process in the foreground (the same way a process runs normally), and the `bg` command will resume the process in the background (it continues running but does not stop you using the shell at the same time). This is usually referred to as _job control_.

If you are running a command that will take a long time to finish on a server (or any machine where you might lose your connection), it's often useful to open a shell using [screen](http://www.gnu.org/software/screen/) or [tmux](http://tmux.sourceforge.net/) and run the command inside that. When you disconnect, the shell within screen or tmux will remain running, and when you next connect you can start using the same shell session again with `screen -R` or `tmux --attach`. 

Syntax
------

### History Expansions

 * `!!` - previous command. Useful for:

```bash
$ rm path/to/thing
Permission denied
$ sudo !!
sudo rm path/to/thing
```

 * `!$` - last argument of the previous command. Useful for:

```bash
$ mkdir path/to/thing
$ cd !$
$ cd path/to/thing
```

 * `!<string>` - most recent command starting with `<string>`
 * `!<number>` - run command with number as given by `history` command.

### Argument Expansions

 * `{old,new}` syntax. For commands that take multiple, similar arguments. E.g.:

```bash
$ mv app/src/foo.c app/src/foobar.c
```

which can be turned into:

```bash
$ mv app/src/{foo,foobar}.c
```

or even:

```bash
$ mv app/src/foo{,bar}.c
```
