Bash
====

Basic Commands
---------------

 * `man <command>` - view the manual page for a command.
 * `ls <directory>` - list contents of a directory.
 * `cd <directory>` - change the current directory.
   - `cd -` - move back to the directory you were last in
 * `rm <file>` - remove file.
   - `rm -r <directory>` - remove directory
 * `touch <file>` - create file.
 * `mv <file> <destination>` - move or rename a file.
 * `cp <file> <destination>` - copy a file.
   - `cp -r <directory> <destination>` - copy directory
 * `chmod <permissions> <file|directory>` - change permissions of a file.
 * `pwd` - show present working directory.
 * `ln <source> <destination>` - create a link.
 * `history` - show recently executed commands.
 * `mkdir <name>` - create a directory 

Shortcuts
---------

 * `tab` - attempt to autocomplete the current buffer.
 * `ctrl-r` - search command history.
 * `ctrl-z` - suspend a running command.
 * `ctrl-d` - exit the shell.

Managing processes
------------------

A running process can be suspended with the `ctrl-z` shortcut, which will assign the process a 'job id' and allow you to continue using the shell. The `fg` command will resume the process in the foreground (the same way a process runs normally), and the `bg` command will resume the process in the background (it continues running but does not stop you using the shell at the same time). This is usually referred to as _job control_.

IF you are running a command that will take a long time to finish on a server (or any machine where you might lose your connection), it's often useful to open a shell using [screen](http://www.gnu.org/software/screen/) or [tmux](http://tmux.sourceforge.net/) and run the command inside that. When you disconnect, the shell within screen or tmux will remain running, and when you next connect you can start using the same shell session again with `screen -R` or `tmux --attach`. 

History Expansions
-------------------

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

Argument Expansions
-------------------

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
