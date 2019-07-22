### Index

- [Grepping (search)](#grepping-search)
- [Quickfix navigation](#quickfix-navigation)
- [Editing files](#editing-files)
- [Browsing through buffers](#browsing-through-buffers)
- [Window navigation](#window-navigation)
- [Window reposition](#window-reposition)
- [Window resizing](#window-resizing)
- [All Commands](#all-commands)
- [Useful config](#useful-config)


#### Grepping (search)

`:vimgrep/foobar/ *` search for foobar in current working directory


#### Quickfix navigation

`:cope` open

`:ccl` close

`:cn` go to next result in the list

`:cp` go to previous result in the list

`:cdo {cmd}` run command on every item in the list

`:cc` echo the current item

`:cc {nr}` jump to item number and echo it


#### Editing files

`:o foobar.txt` open a specific file

`:saveas foobar.txt` save file as

`:.write bar.txt` write the current line to **bar.txt**

`:n **/*.txt` open all files that end with .txt in the current working directory (project folder)

`:wn` write current file and go to the next one


#### Browsing through buffers

`:n` open next buffer

`:prev` open previous buffer

`:ls` list all buffers

`:ls!` list all buffers (including unlisted buffers)

`:b#` switch to previous edited buffer

`:b3` switch to buffer 3

`3 CTRL-^` switch to buffer 3 in NORMAL mode

`:b fil[ename.txt]` use **TAB** to autocomplete filenames

`CTRL-D` list all the possible autocomplete filenames when tabbing through buffers
	
	
#### Window navigation

`:clo`, `:close`, `Ctrl-W c` close the current window

`:q` quit the current window, if it is the last window also exit vim

`:helpc` close on help window, if there is one


#### Window reposition

`Ctrl+W` enter "window command mode"

`Ctrl+W R` rotate windows up/left

`Ctrl+W r` rotate windows down/right

`Ctrl+W L` move window to the far right

`Ctrl+W H` move window to the far left

`Ctrl+W J` move window to the very bottom

`Ctrl+W K` move window to the very top

`Ctrl W x` OR `Ctrl W + Ctrl x` swap current window with closest window to the right


#### Window resizing

`Ctrl+w +` increase height e.g **20 CTRL-w +**

`Ctrl+w -` decrease height e.g **20 CTRL-w -**

`Ctrl+w >` increase width e.g **20 CTRL-w >**

`Ctrl+w <` decrease width e.g **20 CTRL-w <**

`Ctrl+w _` change height to maximum possible

`Ctrl+w |` change width of current window e.g **50 CTRL-w |**

`Ctrl+w =` share same width and height for all windows (equalize)



### All Commands:

```
# Basics
vi                  # open the editor
:h                  # open help page/documentation
tutor               # start vim tutorial
tutor fr            # start vim tutorial in French (if available)
:q                  # quit the current window, if it is the last window also exit vim
:q!                 # quit without writing, also when the current buffer has changes
:e!                 # reloads the original version of the file (unsaved changes will be lost)
:qa                 # exit vim, unless there are some buffers which have been changed
:qa                 # exit vim, any changes to buffers are lost
:wq                 # write the current file and quit
:x		    # like `:wq` but write only when changes have been made
ZZ                  # write the current file and quit

# Navigating the help page
CTRL-]              # jump to a tag/subject
CTRL-T              # pop tag, takes you back to the preceding position (repeat to go furth back)
:h [command]        # get specific help about NORMAL mode command
:h v_[command]      # get specific help about VISUAL mode command
:h i_[command]      # get specific help about INSERT mode command
:h :[command]       # get specific help about COMMAND-line command
:h -[argument]      # get specific help about Vim command argument
:h '[option]'       # get specific help about an Option e.g :h 'textwidth'
:h /                # get specific help about regular expression e.g :h /[
:h [word] [CTRL-D]  # see matching help entries for "word" e.g: :h word CTRL-D
:h wor[TAB]         # get possible results with autocomplete
:h helphelp         # get more information on how to use the help
:helpgrep [word]    # search in all help pages (including installed plugins)
:helpc              # close on help window, if there is one

# Creating, Splitting & Resizing Windows
:clo, :close, CTRL-W_c  # close the current window
Ctrl+w +: 	    	# increase height e.g `20 CTRL-w +`
Ctrl+w -: 	    	# decrease height e.g `20 CTRL-w -`
Ctrl+w >:	 	# increase width e.g `20 CTRL-w >`
Ctrl+w <: 		# decrease width e.g `20 CTRL-w <`
Ctrl+w _: 		# change height to maximum possible
Ctrl+w |: 		# change width of current window e.g `50 CTRL-w |`
Ctrl+w =:		# share same width and height for all windows (equalize)

# Recovering from a crash
vim -r filename.txt		# read the swap file (and maybe bits and pieces of the original file)
vim -r ""			# in case you were editing without a file name (you must be in the correct directory though)
:write filename.txt.recovered	# to be on the safe side, write this file under another file name
:write #
:diffsp filename.txt 		# use vimdiff to compare the two file to see if everything looks alright

# Using an external program
:r !ls (Unix)		# read the contents of the current directory into the file
:r !dir (MS-Windows)	# " "
:0read !date -u		# inserts the current time and date in UTC format at the top of the file
:write !wc		# counts word in the current file, output is in LINES - WORDS - CHARACTERS
CTRL-L			# redraw the screen (in case external program produced an error message)


# Recording and playback commands (Macro's)
q[a-z]		    # start recording a macro e.g `qa`
q		    # end recording of a macro e.g `qa`, `^i# include<Esc>j`, `q`
@a		    # execute a macro
3@a		    # execute a macro 3 times
@@	 	    # execute tha last macro that was executed

# Editing a typo in created macro's (register)
G + o + "ap 	    # go to end of file + create new line + paste/put the contents of the `a` register
0 + "ay$	    # got to the first character of a line + yank it till the end into the register `a` 

# Appending to an existing macro
"ap		    # paste/put the current macro (to see what it currently is doing)
qA		    # to append to the `a` register use the uppercase letter `A`
"aY		    # creates a register `a` with the current line yanked
"AY		    # appends to the existing register `a` and appends the current line to it with yank line command

# Find & Replace accross many files (recursively)
vim			# open up vim
:n **/*.txt		# open all the files that you require (this opens all files in current working directory)
qq			# start recording into the `q` register
:%s/foo/bar/ge		# do the replacements in the first file, `e` flag is recommended (doesn't return an error if no match was found)
:wn			# write this file and move to the next one
q			# stop recording
@q			# execute the register (verify it doesn't produce any errors)
999@q			# execute 999 times

# Find & Replace (substitution)
:%s/foo/bar/gc	    		# most used replace method
:%s/\<foo\>/bar/gc	    	# explicit start with and end with `foo`
:s/foo/bar	    		# replace string `foo` with `bar` on a single line for first occurance only
:s/foo/bar/g	    		# replace strings `foo` with `bar` on a single line for all occurances
:1-3s/foo/bar	    		# replace strings `foo` with `bar` on lines 1 to 3
:%s/foo/bar	    		# replace string `foo` with `bar` on all lines for first occurance only
:%s/foo/bar/g	    		# replace strings `foo` with `bar` on all lines for all occurances
:%s/foo/bar/c	    		# confirm before replacing string on all lines for first occurance only
:%s/foo/bar/gc	    		# confirm before replacing strings on all lines for all occurances
				# prompt commands: [y]=Yes, [n]=No, [a]=All, [q]=Quit, [l]=Last; make this change and then quit, 
				# [CTRL-E]=Scroll up, [CTRL-Y]=Scroll down (just to view more code really)
:s/^foo/bar/			# replace string `foo` with `bar` when `foo` is at the start of a line
:s/foo$/bar/			# replace string `foo` with `bar` when `foo` is at the end of a line
:s/d.com\/1/d.com\/2		# replace slashes by prepending a backslash
:1,5s/foo/bar/g			# replace string `foo` with `bar` on line 1 to 5 for the first occurances only
:45s/foo/bar			# replace string `foo` with `bar` on line 45 for the first occurance only
:.,$s/foo/bar			# replace string `foo` with `bar` on the current line `.` till the last line of the file `$`
:10,$s/foo/bar			# replace string `foo` with `bar` from line 10 till the last line of the file
:?^<h2>?,/^<h1>/s/foo/bar/g 	# replace `foo` with `bar` between the headings `h2` and `h1`
:?^<h2>?+1,/^<h1>/-1s/foo/bar/g # replace `foo` with `bar` between the headings with offset lines (1 line below h2 and 1 line above h1)
:.+3,$-5s/foo/bar/g		# range with an offset of 3 lines below current line and 5 above the last line of the file
:`t,`bs/foo/bar/g		# range with an offset from the mark `t` (top) and mark `b` (bottom)
SHIFT-v + :s/foo/bar/g		# replace string `foo` with `bar` within the selected block 
5:				# this will result in `:.,.+4` which allows you to execute the command on the current line and 4 below
:g+^//+s/foo/bar/g		# replace `foo` with `bar` in all comments (lines that start with `//` characters)

# Opening, closing, writing files
:o [file.txt]           # open a specific file
:saveas [file.txt]      # save file as
:.write otherfile	# write the current line to `otherfile`
:n **/*.txt		# open all files that end with .txt in the current working directory (project folder)
:wn			# write current file and go to the next one
:n[ext]			# open next buffer
:prev			# open previous buffer
:ls			# list all buffers
:ls!			# list all buffers (including unlisted buffers)
:b#			# switch to previous edited buffer
:b3			# switch to buffer 3
3 CTRL-^		# switch to buffer 3 in NORMAL mode
:b fil[ename.txt]	# use <TAB> to autocomplete filenames
CTRL-D			# list all the possible autocomplete filenames when tabbing through buffers

# Moving around (positioning the cursor at the correct place in the file)
w           # move cursor to the start of the next word
W	    # move cursor to the start of the next word (including non-word characters)
b           # move cursor to the start of the previous word
B	    # move cursor to the start of the previous word (including non-word characters)
e           # move cursor to the end of the next word
E	    # move cursor to the end of the next word (including non-word characters)
ge          # move cursor to the end of the previous word
gE	    # move cursor to the end of the previous word (including non-word characters)
$ 	    # move cursor to the end of a line
5$	    # move cursor to the end of the 4th line below the current line we are on
^	    # move cursor to the first non-blank character of the line
0 	    # move cursor to the very first character of the line
f[a-z]	    # single-character search forward
3fx	    # single-character search forward for letter `x` 3 times
F	    # single-character search backwards
3Fx	    # single-character search backwards for letter `x` 3 times
tx	    # single-character search forward up to letter `x` (stops one character before the searched character) 
Tx	    # single-character search backwards up to letter `x` (stops one character before the searched character) 
;	    # single-character search repeat forward
,	    # single-character search repeate backward
%	    # when cursor is on a `(` this will move to the matching `)` e.g from `(` to `)`, `[` to `]`, `{` to `}`
gg	    # move to the first line of a file (go to top of file)
G	    # move to the last line of a file (go to bottom of file)
7G	    # move to a specific line number, e.g move to line 7 with `7G`
``	    # go back to previous `mark` (jump back to previous cursor position after a jump was made)
CTRL-O	    # this command does the same as ```` with the exception it can jump to older positions
CTRL-I	    # oposite of `CTRL-O` (jump to newer positions)
<Tab>	    # same as `CTRL-I` (however I and O are next to eachother on the keyboard which is much quicker)
:jumps	    # gives you a list of `marks` to jump to
m[a-z]	    # create mark, `ma` creates mark as `a` which you can then jump to with "`a"
	    # a rule of thumb would be create a mark "s" (start) and a mark "e" (end)
:marks	    # get a list of marks
50%	    # move halfway the file e.g: move to 1/4 of a file with 25%
H	    # move to the first line within the viewport (stands for `Home`)
M	    # move to the mid line within the viewport (stands for `Middle`)
L	    # move to the last line within the viewport (stands for `Last`)
zz	    # position context below cursor at middle of viewport
zt	    # position context below cursor at top of viewport
zb	    # position context below cursor at bottom of viewport
CTRL-U	    # scroll viewport UP by 50%
CTRL-D	    # scroll viewport DOW by 50%
CTRL-E	    # one-line scroll DOWN (show `Extra` line)
CTRL-Y	    # one-line scroll UP
CTRL-F	    # scroll `Forward` by a whole viewport (except for two lines)
CTRL-B	    # scroll `Backward` by a whole viewport (except for two lines)

# Making small changes (operator-motion, VISUAL mode and TEXT objects)
d$ [D]	  # deletes from the cursor to the end of the line (including the last character of the line)
c$ [C]	  # change to end of line
y$	  # yank to the end of the line
dl [x]	  # delete character under the cursor
cl [s]	  # change one character 
dh [X]	  # delete character left of the cursor
cc [S]	  # change a whole line
yy [Y] 	  # yank the current line
d4w	  # deletes up to the position where the motion takes the cursor
d4e	  # deletes up to the position where the motion takes the cursor including that last character 
c2w	  # deletes a word and puts you in INSERT mode
dd	  # deletes a line
y	  # yank (copy) something
"*yy	 "# copy a line to the clipboard
yw	  # yank a word (including the white space after a word)
ye	  # yank a word (excluding the white space after a word)
y2w	  # yank 2 words
r	  # replace on character
4r<Enter> # replaces four characters with one line break
.	  # repeat last change (works for all changes you make, except for the `u` (undo), `CTRL-R` (redo) and commands that start with a colon `:`
p	  # paste/put back text that was previously deleted with for instance commands like: `d` or `x`
P	  # same as `p` but puts the text before the cursor
"*p	 "# paste/put text from the clipboard back into the text
xp	  # swap 2 characters around e.g: `teh` becomes `the` when cursor is on `e`
daw	  # deletes a word (Delete A Word)
cis	  # change a whole sentence (Change Inner Sentence)
cas	  # same as `cis` but includes the white space after the sentence
!5Gsort	  # sort lines 1 to 5
!!data	  # print current timestamp to a file

# Visual mode (making big changes)
V	  # starts VISUAL mode and selects the whole line
CTRL-V	  # starts VISUAL mode in "vertical" mannar (block selection)
v_o	  # position cursor at the opposite location of the selection vertically (top/bottom)
v_O	  # position cursor at the opposite location of the selection horizontally (left/right) (on the same line)
v_I	  # insert text left of the block selection
v_A	  # append text right of the block selection
v_$A	  # append text at the end of each line within the block selection (including short lines)
v_c	  # change the text within the block selection (puts you in INSERT mode)
v_C	  # delete the text within the block selection till the end of the line and puts you in INSERT mode
v_~	  # toggle text case lowercase/UPPERCASE e.g `foo` would convert to `FOO` and `FOO` to `foo`
v_U	  # change text to UPPERCASE e.g `Foo` would convert to `FOO`
v_u	  # change text to lowercase e.g `Foo` would convert to `foo`
v_r	  # replace all characters with a different e.g `rx` would convert `foo` to `xxx`
v_>	  # shift/TAB selected text to the right one shift amount `:set shiftwidth=4` (4 spaces)
v_<	  # shift/TAB selected text to the left one shift amount `:set shiftwidth=4` (4 spaces)
v_J	  # join all selected lines together and keep the white space
v_gJ	  # join all selected lines together but remove the white space
v_!5Gsort # sort selected block

# Searching and search patterns
/	    # search for a specific word `.*[]^%/\?~$` have special meanings, if you want to use them in a search prepend them with a `\`
	    # use `:set ignorecase` to ignore case, and use `:set noignorecase` to include case
*	    # grab word under the cursor and use it as the search string (forward whole word searching)
g*	    # to only match partial words (forward partial word searching)
#	    # grab word under the cursor and use it as the search string (backward whole word searching)
g#	    # to only match partial words (backward partial word searching)
n	    # to find the next occurrence of the same string use the "n" command
3n	    # to find the third match
N	    # to find the previous occurrence
?	    # works like `/` but searches backwards (not that `n` and `N` will do the opposite for backwards searches)
/bar\>	    # search for words that end with `bar`
/\<foo	    # search for words that start with `foo`
/\<foobar\> # search for whole words that are exactly `foobar`
	    # NOTE: both `*` and `#` search for whole words only
/^foobar     # matches the word `foobar` only if it is at the beginning of a line
/foobar$     # matches the word `foobar` only if it is at the end of a line
/^foobar$    # matches a single line consisting of `foobar` with nothing else at the start nor end of the line.
/fo..ar	    # matches a string whose first 2 characters are `fo` whose next 2 characters can be anything and last 2 ar `ar`

# Text manipulation
i         # inserts a character before the character under the cursor
a         # append a character after the character under the cursor
x         # delete a character
dd        # delete a line
cc	  # change a line
o         # create a new empty line below the cursor and puts vim in INSERT mode
O         # create a new empty line above the cursor and puts vim in INSERT mode
J         # remove line break at end of current line (join 2 lines together)
u         # undo last change
U         # undo line (undoes all the changes made on the last line that was editied)
gUw	  # convert word to UPPERCASE
guw	  # convert word to lowercase
guu	  # convert line to lowercase
gUU	  # convert line to uppercase
g~~	  # toggle line to lowercase/UPPERCASE
CTRL-R    # redo last change

# Reading and writing part of a file
:r[ead] filename.txt	# insert the text of the file one line below the cursor
:$r filename.txt	# insert the text of the file at the end of the file
:0r filename.txt	# insert the text of the file at the top of the file
:.,$w filename.txt	# writes the lines from the cursor until the end of the document into the file
:.write filename.txt	# write the current line to a new file
:.write >>filename.txt	# append the current line to the end of an existing file
```

#### Useful config

`set nocp` 'compatible' is not set

`set nocompatible wildmenu`

`filetype plugin on` enable plugins (for netrw)

`set path+=**` allow vim to search within current working directory by default

`set wildmenu` allow **TAB** autocompletion

`set wildmode=full`

`set wildignorecase`

`set wildignore=.git` skip .git folder

`set tags=./tags,tags;$HOME` when using ctags define where to look for the tags

`set number` display a line number in front of every line

`set scrolloff=20` keeps a few lines of context around the cursor top/bottom

`set hls` enable search highlighting

`:nohls` temporarily disable highlighting for current search (this will not disable it for next searches)

`set incsearch` display the search match while still typing

`set shiftwidth=4` set shift amount to 4 spaces

`set autowrite` automatically save any changes made to the buffer before it is hidden 

`set autoread` autmoatically update content in vim if file was changes elsewhere

`set t_Co=256` use 256 bit colors

`set termguicolors`

`syntax on` enable syntax

`let mapleader = ","` set leader key to **,**

`nnoremap <leader>f :find *` fuzzy find files by name

`nnoremap <leader>s :sfind *` fuzzy find files by name open in horizontal split window

`nnoremap <leader>v :vert sfind *` fuzzy find files by name open is vertical split window

`:nmap <C-B> :ls<CR>:silent :b<Space>` map Ctrl-b to open buffer listG
