# vim-cheat-sheet
>This cheat sheet is based of the Vim :help page. I created it purely for my own personal reference.

```bash
#Basics
vi                  # open the editor
:h                  # open help page/documentation
tutor               # start vim tutorial
tutor fr            # start vim tutorial in French (if available)
:q                  # quit the current window, if it is the last window also exit vim
:q!                 # quit without writing, also when the current buffer has changes
:qa                 # exit vim, unless there are some buffers which have been changed
:qa                 # exit vim, any changes to buffers are lost
:wq                 # write the current file and quit

#Navigating the help page
CTRL-]              # jump to a subject
CTRL-T              # jump back. repeat to go further back
:h [command]        # get specific help about NORMAL mode command
:h v_[command]      # get specific help about VISUAL mode command
:h i_[command]      # get specific help about INSERT mode command
:h :[command]       # get specific help about COMMAND-line command
:h -[argument]      # get specific help about Vim command argument
:h '[option]'       # get specific help about an Option e.g :h 'textwidth'
:h /                # get specific help about regular expression e.g :h /[
:h [word] [CTRL-D]  # see matching help entries for "word" e.g: :h word CTRL-D

:o [file.txt]       # open a specific file
:saveas [file.txt]  # save file as
`:h[elp]` - *open a window and display the help file in read-only mode.*
`:h[elp] {subject}` - *additionally jump to the tag e.g: :help options*
`:helpc[lose]` - *close on help window, if there is one*
`:clo`, `:close`, `CTRL-W_c` - *close the current window*
```
