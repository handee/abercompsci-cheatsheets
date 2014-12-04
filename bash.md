Bash
====

Basic Commands
---------------

 * `man` - view the manual page for a command.
 * `ls` - list contents of a directory.
 * `cd` - change the current directory.
 * `rm` - remove file.
 * `touch` - create file.
 * `mv` - move/rename file.
 * `cp` - copy file.
 * `chmod`- change permissions of a file.
 * `pwd` - show present working directory.
 * `ln` - create a link.
 * `history` - show recently executed commands.
 * `mkdir` - create a directory 

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
cd path/to/thing
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

`$ mv app/src/foo{,bar}.c`
