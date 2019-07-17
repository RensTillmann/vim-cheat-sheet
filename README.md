# vim-cheat-sheet
>This cheat sheet is based of the Vim :help page. I created it purely for my own personal reference.

```bash
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

# Find & Replace (substitution)
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
CTRL-R    # redo last change

# Useful configuration/settings for Vim
:set number 		# display a line number in front of every line
:set scrolloff=20 	# keeps a few lines of context around the cursor top/bottom
:set hlsearch		# enable search highlighting
:nohlsearch		# temporarily disable highlighting for current search (this will not disable it for next searches)
:set incsearch		# display the search match while still typing
:set shiftwidth=4	# set shift amount to 4 spaces
`
