                    Directories and files
=====================

Directories in UNIX are like folders in Windows. Every user has their home directory, and at any given time they have a working directory — the directory in which they’re currently working. It’s sometimes called the current directory or current working directory.

Home and working directories
----------------------------

When you log into a UNIX system, you start out in your home directory. Your UNIX prompt will show this:

central:  $
end{v}
The verb central  is the name of the machine you are logged into, and
the verb ~  is the name of your home directory. This is just a shorthand:
if you use the verb pwd command (Print Working Directory) you'll see
the full name. In my case, this happens:
begin{v}[commandchars=\[]]
central:~ $ *[*pwd] /aber/jaf18

(I’m using italics to show the command I typed in, rather than Central’s output.)

Paths
-----

Just like folders in Windows, directories can contain files and other directories. We talk about a *path* to a file or directory in UNIX — it specifies a file by showing how to get there either from the current working directory (in which case it’s a *relative path*) or from the system’s top level directory (the *root* directory,) in which case it’s a *absolute path*.

The path is made up of directory names, separated by slashes, until you get to the file or directory you’re talking about. Each directory is inside the previous directory in the path.

As a silly example, if planet Earth were a UNIX file system, an absolute path to the tutorial room might be

/earth/gb/wales/aberystwyth/penglais/llandinam/c57a

If my “working directory” were `aberystwyth`, a relative path — which shows how to get to another directory from the working directory — might be

penglais/llandinam/c57a

More realistically, a file called `project1.tex` inside a directory called `work` in my home directory would have the absolute path

/aber/jaf18/work/project1.tex

or, using the shorthand `~` character[^1]:

 /work/project1.tex

or, if we want to look at the home directory of a different user than the one currently logged in,

 jaf18/work/project1.tex

Relative paths always start with a directory or file name, while absolute paths always start with a “/” or “ ”.

### Going up the tree

Let’s look at the silly example of the “Earth file system” again. If I were in (say) Physics Main, how could I get to C57A? In other words, what’s the *relative path* from there to C57A?

Firstly, let’s find out the absolute path to Physics Main:

/earth/gb/wales/aberystwyth/penglais/physics/physicsMain

Now we can see what we need to do:

-   go up to the `physics` directory

-   go up again to the `aberystwyth ` directory

-   go down to the `llandinam` directory

-   go down to `c57a`

We can go “up” a level inside a path by using “..” instead of a directory name:

../../llandinam/c57a

You’ll do this a lot — for example, you might do some work inside your `work/project1` directory, and then want to do some more work on Project 2 in `work/project2`. That might go something like this:

[commandchars=
$$$$] central:  $ emph[cd work/project1]
central:~/work/project1 $ ... central: /work/project1 $ emph[cd ../project2]
central:~/work/project2 $

As well as the “..” shorthand for “the directory above,” (also called the *parent* directory) we also have “.” for “the working directory.” This can be useful in move and copy commands.

The anatomy of a command
========================

Commands typically have three parts:

-   The name of the command

-   The options, which start with dashes

-   The parameters of the command

For example, the `ls` command lists files. It has a lot of options, a couple of which are `-l` (to give a long listing) and `-a` (to include hidden files.) Any parameters it takes are the names of files and directories it should list. So

ls -l -a ../project1 ../project2

will produce a long listing, containing all the hidden files, of the contents of the directories `project1` and `project2`, both of which are inside the current directory!

A lot of the time you can join options together, so

ls -la ../project1 ../project2

will do the same thing.

Wildcards
---------

Some commands can work on many files — for example, the `ls` command above. To help, we can use so-called “wildcards” which let us specify files given only a part of their name. The “*” wildcard matches any sequence of characters, and the “?” wildcard matches any single character. So:

ls a*

means “list all the files whose names are ‘a’ followed by any sequence of characters” — in other words, all the files whose names start with “a”. Similarly,

ls *a

will list all the files whose names *end* with the letter “a”. Here’s a more complex one:

ls *.???

This will specify files which start with any sequence of characters, followed by a “.”, followed by exactly three characters.

The most important command
==========================

man *command* & get information about a command

Changing directory
==================

cd *path* & change the working directory to a specified directory. Some examples follow.
cd   & change to your home directory
cd & shorthand way to change to your home directory
cd .. & change to the directory within which your current directory is contained (the *parent* directory)
cd / & change to the root directory of the whole system
cd . & change the current working directory to the current working directory! (Yes, it’s pointless.)
pwd & print the absolute path of the current working directory

Listing directories
===================

ls & get a short listing of the contents of the current working directory
ls *path* & get a short listing of the contents of a named directory
ls .. & get a short listing of the contents of the parent directory
ls -l & get a detailed listing of the contents of the current working directory
ls -ld & get a detailed description of the current working directory itself
ls -l *path* & get a detailed listing of the contents of a named directory
ls -la *path* & get a detailed listing of the contents of a named directory, including those files which are usually hidden.
ls -la *path*|more & as above, but split into pages (see Pipes, below)

Copying files
=============

cp *file1* *file2* & makes a new copy of *file1* called *file2*, keeping the old one. If there’s already a file called *file2* it will be overwritten.
cp *file* *directory* & makes a new copy of *file* inside *directory*, but with the same name (so it’ll be *directory/file* . If there’s already a file of that name inside *directory* it will be overwritten.
cp *file1* *directory/file2* & makes a new copy of *file1* inside *directory*, called *file2* (so it’ll be *directory/file2* . If there’s already a file of that name inside *directory* it will be overwritten.
cp *list-of-files* *directory* & copy all the files in the list into a directory.

### Examples

l|p2in

cp foo bar & make a copy of the file *foo* called *bar*, overwriting any file of that name which may already exist.
cp foo .. & copy the file *foo* into the parent directory.
cp ../foo . & copy the file *foo*, which is in the parent directory, into the current working directory

Moving files
------------

The `mv` command works almost exactly the same way as `cp`, but it removes the original file!

mv *file1* *file2* & changes the name of *file1* to *file2*, keeping the old one. If there’s already a file called *file2* it will be overwritten.
mv *file* *directory* & moves *file* into *directory*, so it’ll now be *directory/file* . If there’s already a file of that name inside *directory* it will be overwritten.
mv *file1* *directory/file2* & moves *file1* into *directory*, and changes the name to *file2* (so it’ll be *directory/file2* . If there’s already a file of that name inside *directory* it will be overwritten.
mv *list-of-files* *directory* & move all the files in the list into a directory.

Managing directories and deleting stuff
---------------------------------------

mkdir *path* & will make a new directory with that path
rmdir *path* & will remove the directory with that path
rm *list-of-files* & will remove some files
rm -r *list-of-paths* & will remove the named files and directories *recursively* — that is, it will also remove the files and directories any directories contain. **Use with extreme caution.**
rm -rf *list-of-paths* & will remove the named files and directories *recursively* — that is, it will also remove the files and directories any directories contain *and not ask you to confirm!* **Use with even more extreme caution. You WILL do this wrong one day.**
rm -rf * & **never use this** — it will silently destroy everything in the current working directory. I shouldn’t even be telling you about it.

Pipes and redirection
---------------------

Usually, input for a command comes from the keyboard and output goes to the screen. Sometimes it’s useful to change this — to get input from a file and output to a file. To do this, use the “<” character to get input from a file (think of the arrow as pointing towards the command name) and “>” to send output to a file.

For example, we an put a long listing of our home directory into a file:

ls -l >big~l~isting

We can also send the output of one command into the input of another using a *pipe.* For example, the `more` command takes its input and splits it up into pages. If we have a big directory, we can list it page by page using:

ls -l | more

This takes the output of `ls` and pipes it into `more`, which splits it into pages. Another example:

ps ax | grep MyJavaProgram

This gets a list of all the running programs on the system, and searches through that list for lines containing the string “MyJavaProgram”. Useful when a program goes out of control and you need to kill it!

A fun example:

ps ax | cut -c 28- | sort | uniq | wc -l

This

-   list all processes

-   cuts out the first 27 characters from each line, so we only get the program names

-   sorts them alphabetically

-   removes duplicate adjacent lines

-   counts the number of lines

So we get a count of all the uniquely named processes running on the system.

Showing the contents of files
-----------------------------

cat *list-of-files* & just joins all the files together and outputs them
more *list-of-files* & shows the files page by page
more & splits the input into pages (input comes from the keyboard by default, but you’ll typically redirect it from another command using a pipe)

Permissions
-----------

Each UNIX file has a set of permissions describing who can do what to it. There are three types of permission:

-   read permission — if you have this, you can see the contents of the file or directory;

-   write permission — if you have this, you can write to the file or add new files (or delete or move) in the directory;

-   execute permission — if you have this permission on a program file or script you can run it; if you have it on a directory you can `cd` into it (make it your working directory.)

The permissions can be set differently for three different types of person:

-   the owner of the file — whoever originally created it

-   the group ID of the file — a rather crude way of setting things up so groups of people can have special access to a file; I won’t worry about it too much

-   everyone else

### The output of ls

These permissions are listed by `ls -l` in a very terse way:

[commandchars=
$$$$] central:  $ emph[ls -l sheet.pdf]
-rw-rw-r--. 1 jaf18 jaf18 70273 Nov  8 14:05 sheet.pdf
end{v}
The elements in order are:
begin{itemize}
item permissions block verb+-rw-rw-r--.+ 
item the ``inode count'' (which is typically 1 for a file)
item the owner's user ID
item the group's user ID
item the size in bytes
item last modified date and time
item name
end{itemize}
Looking at the permissions block we can see that it's split into
elements:

begin{tabular}{l p{2in}}
verb+-+ & the type of the file: ``d'' would be a directory\
verb+rw-+ & permissions for the user themselves\
verb+rw-+ & permissions for the group\
verb+r--+ & permissions for other users
end{tabular}

So we can see that I (and anyone in my group, which is only me) am allowed to 
read and write the file, and other people can read it.

If I look at my home directory, things are different:
begin{v}[commandchars=\[]]
central:~ $ *[*ls -ld  ] drwx——. 85 jaf18 jaf18 4096 Nov 8 13:23 /aber/jaf18

Note that I’m using the `-d` option to look at the actual directory: if I’d not used it, I’d get the contents of the directory!

Here, the “inode count” shows the number of files in the directory, but what we’re really interested in is the permissions:

l p2in

`d` & indicates this is a directory
`rwx` & permissions for the user themselves
`---` & permissions for the group
`---` & permissions for anyone else

So I can read, write and `cd` into the directory and no-one else can do anything at all. Which is appropriate.

### Changing permissions the “easy” way

chmod o+x *list-of-paths* & add execute permissions for other users to some files or directories
chmod o-x *list-of-paths* & remove execute permissions for other users from some files or directories
chmod a+rw *list-of-paths* & add read and write permissions for all users (that’s user, group and other)
chmod o-rwx *list-of-paths* & remove all permissions for other users
chmod u+rx *list-of-paths* & add execute and read permissions for myself
chmod g-x *list-of-paths* & remove execute permissions for the group

You should get the idea: the first letter is “u” for the user, “g” for the group and “o” for others; the second character is “+” to add permissions and “-” to remove them; and the final set of characters is the permissions to add or remove. There’s more it can do — run `man chmod` to get the full info.

### Changing permissions the hard way

This involves encoding the `rwxrwxrwx` block — which divides into user, group and other — as an octal number!


chmod 755 *list-of-paths* & set the permissions to: user can read, write and execute; group and read and execute; others can read and execute.

You might want to read up on this yourself, or stick with the other technique. I tend to use both.

Other useful commands (and keys)
================================

logout & logs you out of the computer
touch *file* & creates an empty file, or updates the last-modified date on an existing file
grep *pattern* *files* & look for a “pattern” inside files — you’ll be covering these patterns (called *regular expressions*) later on, but it will also work on simple strings
sort & sorts input into alphabetical order and outputs it
du -H . & shows disk usage in current directory (find out what the H does!)
w & tells you who’s logged in and what they’re up to
*(up arrow)* & shows previous commands
*(tab key)* & autocomplete

[^1]: called a “tilde”
                    
