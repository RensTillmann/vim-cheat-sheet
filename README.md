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

# Misc
:o [file.txt]                   # open a specific file
:saveas [file.txt]              # save file as
:clo, :close, CTRL-W_c          # close the current window

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

# Text manipulation
i         # inserts a character before the character under the cursor
a         # append a character after the character under the cursor
x         # delete a character
dd        # delete a line
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
```
