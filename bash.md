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
