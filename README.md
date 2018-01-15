# vimim

Vim IMitation ~ A Vim-like text editor made in C++

Created by : Julien He & Kevin Sangbeom Park (Dec 2017)

----------
_**NOTE** : This project was a final assignment for my (Advanced) Object-Oriented Programming course, and as such, the source code is [only available upon request](mailto:hejulien22@gmail.com?Subject=vimim%20Source%20Code%20Request)._

_I have still included the Linux executable which can be run with :_ `./vimim <filename(s)...>`

----------

## About
The goal of this project was to create a Vim-like text editor with robust, maintainable code that follows the MVC design pattern. The program aimed to follow good OOP design principles such as the SOLID principles and low-coupling/high cohesion. One of the main focuses of the project was to maintain high resilience to change (open/closed principle), and the various design decisions reflect such ideals.

Vimim is not a complete replica of Vim, but it's pretty close in most of the main commands. 
Here's what is currently implemented :

 - `a` : Append text after the cursor times
 - `A` : append at end of the line (equivalent to `$a`)
- `b` : jump backwards to the start of the word
 - `cc` : change (replace) the entire line and enter insert mode (equivalent to `ddO`)
 - `S` : same as `cc`
 - `c[arrow]` :
	 - `c[left/right]` : copy left/right char and remove it, and enter insert mode
	 - `c[up]` : move cursor up, then `2cc`
	 - `c[down]` : `2cc`
 - `dd` : delete (cut) line
 - `d[arrow]` : same as `c[arrow]` with `dd`, but do NOT enter insert mode
 - `f[char]` : jump to the next char on the current line (everything to the right of cursor)
 - `F[char]` : jump to the prev char on the current line (everything to the left of cursor)
 - `h` : move cursor left
 - `j` : move cursor down
 - `k` : move cursor up
 - `l` : move cursor right
 - `i` : enter insert mode before cursor
 - `I` : enter insert mode at beginning of line (equivalent to `^i`)
 - `n` : repeat last `/` or `?` search 
 - `N` : repeat last `/` or `?` search in the opposite direction
 - `o` : enter newline at end of current line, move cursor down and enter insert mode
 - `O` : enter newline at beginning of current line, cursor goes to before the newline char and enter insert mode
 - `p` : paste clipboard after the cursor
 - `P` : paste clipboard before the cursor
 - `r[char]` : replace char at cursor with char
 - `R` : enter Replace mode
 - `s` : delete character and enter insert mode (equivalent to `c[right]`)
 - `u` : undo last command (note: not all commands are undoable, e.g. `hjkl`/other movement commands)
 - `ctrl-r` : redo
 - `w` : jump forward to start of next word (considers lines and punctuation :note based off of groups : alphanumeric + _, punctuation)
 - `x` : delete (cut) character (equivalent to delete button)
 - `X` : delete (cut) character before cursor
 - `yy` : yank (copy) a line 
 - `y[arrow]` : same as `d[arrow]` but copy instead of cut
 - `J` : join next line to the current line with a space in between (replace next newline with a space) (equivalent to `$[del]a[space]` )
 - `^` : jump to first non empty character of the line
 - `$` : jump to end of the line
 - `0` : jump to start of line (including empty chars)
 - `;` : repeats the last `f` or `F` command
 - `/[pattern]` : search forwards for next occurrence of `pattern`
 - `?[pattern]` : search backwards for next occurrence of `pattern`
 - `%` : If currently at one of `{`,`(`,`[` , jump to its corresponding closing bracket. Otherwise, find the next bracket on the current line and jump to its partner bracket.
 - `ctrl-b` : move back one screen (page-up)
 - `ctrl-f` : move forward one screen (page-down)
 - `ctrl-d` : move forward 1/2 screen
 - `ctrl-u` : move back 1/2 screen
 - `ctrl-g` : print at bottom current file name and path, file status,  cursor position.
 
 - `:w [filename]` : save file [optional filename for save as]
 - `:q` : quit file as long as not modified, fails when changes have been made
 - `:wq [filename]` : save and quit [optional filename for save as and quit]
 - `:q!` : exit without saving 
 - `:r [file=current file]` : copies file and pastes it below the current cursor
 - `:[num]` : jump to num line of file
 - `:0` : jump to beginning of file
 - `:$` : jump to end of file
 - `<esc>` : cancel the current command

Additionally, there is also :

 - Syntax highlighting for C++ files (needs to end in `.cc` or `.h`)
 - Support for multiple files
	 - Still kind of rough at the moment. Can open multiple files with `./vimim <file1> <file2> ...`, and then switch in between the different files with `:next` and `:prev`
 - Numeric Multipliers: Almost all of these commands support multipliers, as in you can add a number before to repeat the value multiple times. 
	 - For example: `3d4/abc` will find the 4th instance of `abc` after the cursor and delete everything from the cursor to `abc`, then repeat all of that again 3 times. Why you would ever use such a command is beyond me, but it's there if you ever need it

Future Things to Implement:

 - Macros (the `q` and `@` commands)
 - The `.` command
 - Regex pattern searching
 - Split screen (for multiple files)
