# Emacs

GNU Emacs is an extensible, customizable text editor—and more.

Open from Application menu as all the other programs or from the teminal. 

In terminal
```bash
$ emacs
```

will open a new window

```bash
$ emacs -nw
```
will open emacs on the terminal

Emacs contains a menu bar, the frame (the editor), a status bar and a command prompt at the bottom.

You run a command using a combination of modifiers and keystrokes.
for example Ctrl+x Ctrl+f will ask you to type a filename. Usage of TAB
is available when you start type a command or navigate throughout the directories
and files.

## Terminology

* Buffer - 
Emacs reads the file into a buffer in memory. While you're editing the buffer and working with the data nothing is changed on disk
* Windows - 
A window in Emacs is an area of the screen in which a buffer is displayed
* Frame - 
a frame is a separate X window in which an Emacs buffer is displayed

## Commands Modifiers

* ```Ctrl as C```

This usually is the abbreviation of a function
ex. C-x C-s

* ```Alt/Esc as M```

This calls the function
ex. M-x save-buffer

# Files

* ```C-x C-f```         Open a file or create a new one if not exist.
                        You can tab to display the directory 's contexts
* ```C-x C-s```         Save file
* ```C-x C-w```         Save as
* ```C-x b```           Iterate through buffers(open files)
* ```C-x C-b```         List all open buffers
* ```C-x k```           Kill the current buffer
* ```M->```             Move cursor to the end of buffer(file)

Usage: Alt + Shift + ">"
* ```M-<```             Move cursor at the beginning of buffer(file)

Usage: Alt + Shift + "<"

if you want to select the whole text in the file:
```
$ M-< #to go at the beginning
$ C-space
$ M-> #to go at the end
```
to cancel an action
```
esc esc esc
```

# windows

* ```C-x 1```           One window. if you have open more this return into a single one
* ```C-x 2```           Split window which the cursor is on vertically with the same buffer
* ```C-x 3```           Split window which the cursor is on horizontally with the same buffer

Each window is splitting each time as many times as you want. To bring it back in a single
window run C-x 1.

# Edit

* ```M-w```             copy
* ```C-w```             cut
* ```C-y```             paste
* ```C-s```             search
* ```C-d```             delete(forward)
* ```DEL```             delete(backward)
* ```C-/```             undo

# Miscellaneous

* ```C-g```            Cancel command. Similar if you type ESC button three times.
* ```C-h k```          Documentation. There are many help file actually. This is a general one.