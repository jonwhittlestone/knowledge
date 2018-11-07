# Vim Cheatsheet

Random keystrokes I've picked up from here and there

	:e!		                    Revert to last save
    :verbose imap <tab>         See what key is assigned to
    Ctrl + U                    Scroll up a bit
    Ctrl + D                    Scroll down a bit
    =                           Reindents everything nicely / beautify
    
Editing

    viw                         Visually select inner word
    ciw                         Change (insert mode) inner word
    d $                         delete everything from current cursor to EOL
    ysiw`                       (surround-vim)     Wrap the text object in backticks
    ds"                         (surround-vim)      Delete double quote delimiters
    selection S )               (surround-vim)  Wrap parentheses (without whitespace surrounding inner)
    :%s/,/Ctrl vReturn/g        Turns 1 line of comma delimited strings into each string on a separate line.
                                The CtrlV Return keystroke will display as ^M
    
Navigation
    
    CTRL + O                    Go to previous cursor position
    CTRL + I                    Go to next cursor position
    number + SHIFT+G            Go to Line number
    gd                          Go to func definition
    
Closing buffers
    :Bonly                      keeps open just buffer that is viewed      
    :bw                         deletes the current buffer, errors if there are unwritten changes
    :bw!                        deletes the current buffer, no error if unwritten changes
    :bufdo bw                   deletes all buffers, stops at first error (unwritten changes)
    :bufdo! bw                  deletes all buffers except those with unwritten changes
    :bufdo! bw!                 deletes all buffers, no error on any unwritten changes
    bd16                        deletes buffer 16

Here are a few other useful buffer commands:
   
   <C-x>                        in CtrlP, press Ctrl + X to open listing in a [split](split) 
    s                           in NERDTree, opens a file in a vertical split 
    :ls                         list open buffers
    :b N                        open buffer number N (as shown in ls)
    :tabe +Nbuf                 open buffer number N in new tab
    :bnext                      go to the next buffer (:bn also)
    :bprevious                  go to the previous buffer (:bp also)
    
Fold workflow
    
    Toggle between pairing braces   %
    Fold the brace up               zf
    Remove the fold                 zd
    Recursively open all folds      zA

Editing

    Delete and put into insert mode     , + c
