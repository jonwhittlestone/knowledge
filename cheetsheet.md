# Tmux Cheatsheet

Lifted from the web somewhere

## Visuals

    :clear-history      clear the history

## Editing

    Copy/Paste                  CTRL+B [ to get into copy mode
                                Vim command mode to navigate around
                Space           To set mark
                Enter           To copy to clipboard
                Paste           CTRL+B ]
                
## Sessions

    :new<CR>                    new session
    s                           list sessions
    $                           name session
    kill-session -d <name>      kill the session

## Windows (tabs)

    c                           new window
    ,                           name window
    w                           list windows
    f                           find window
    &                           kill window
    .                           move window - prompted for a new number
    :movew<CR>                  move window to the next unused number
    :move-window -r             renumber windows sequentially
    swap-window -s 3 -t 1

## Panes (splits)

    %  horizontal split
    "  vertical split
    
    o  swap panes
    q  show pane numbers
    x  kill pane
    ⍽  space - toggle between layouts
    

## Pairing over ssh

1. start new session
    
    tmux new-session -s pair
    
2. show running tmux sessions

    tmux ls
    
3. attach to one of the pairs

    tmux a -t pair

4. cont. https://goo.gl/U2DELz 
