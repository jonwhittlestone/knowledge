# Getting Started with Tmux

Packt Pub book

----

### 01 Naming the session and basics

| Operation | Keystroke | Comment 
|--- |--- |---
| Start tmux | `tmux` |
| Detaching tmux | `CTRL` + `B` + `d` | Keeps it running in background
| Kill Pane, Window or Tmux | `exit` | we no longer need 

### 02 Configuring

| Operation | Keystroke | Comment
|--- |--- |---
|View Current Key bindings | `CTRL+B` + `?` |
| Change the status bar in [`~/.tmux.conf`](https://github.com/jonwhittlestone/dotfiles/blob/jons-dotfiles-repo/.tmux.conf) | `set-option -g status-bg blue` | |
| Re-source tmux conf | `tmux source-file ~/.tmux.conf` | |


### 03 Sessions, windows and panes

| Operation | Keystroke | Comment
|--- |--- |--- |
| Start a new session called 'work' | `tmux new-session -s work` | |
| Create a vertical split | `CTRL + B` + `%` |
