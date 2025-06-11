# tmux
TMux Cheat Sheet

* list  
tmux ls 
* attach to the first one  
tmux attach  
* attach to window #1
tmux attach-session -t 1  
* kill current window
C-b &  
* Hierarchy:
    Session > Windows > Pane  
* Control mode: C-b  
    : command line  
    [ or PgUp: copy mode  
        scroll up/down  
        Use vi command for search  
    ": split horizontally  
    %: split vertically  
    x: kill pane/window/session  
    c: new window  
    n: next window  
    p: previous window  
    0-9: go to numbered window  
    d: detach pane/session  
    s: list sessions  
    q: identify panes  
    w: window mode  
    D: exit to parent  
    new: new session  
* copy/paste using ctrl-c/v ctrl-shift-c/v
select by hold shift and mouse; shift-right-click to use menu, or  
copy/paste as usual  
* turning off tmux mouse support enables system behavior; use in tmux command or in ~/.tmux.conf
set -g mouse off  
* capture screen
C-b, :  
* copies 3000 lines into a buffer
capture-pane -S -3000
* save to file
C-b, :
save-buffer filename.txt
>>>>>>>>>>>> multiplexing
// create a horizontal split bar
C-b followed by "
// create a vertical split bar
C-b followed by %
// updated tmux.conf
# override split 
unbind %    # split-window -h
unbind '"'  # split-window
bind | split-window -h -c "#{pane_current_path}"
bind _ split-window -v -c "#{pane_current_path}"
// sync control
setw synchronize-panes on
setw synchronize-panes off
// or toggle
setw synchronize-panes
// resize split panes
C-b Esc Arrow
// auto resize
C-b z: zoom current 
C-b <Space>: Cycle through
C-b Alt+1: Even horizontal splits
C-b Alt+2: Even vertical splits
C-b Alt+3: Horizontal span for the main pane, vertical splits for lesser panes
C-b Alt+3: Vertical span for the main pane, horizontal splits for lesser panes
C-b Alt+1: Side-by-side
C-b Alt+5: Tiled layout
// moving panes
C-b {          move the current pane to the previous position
C-b }          move the current pane to the next position
C-b C-o        rotate window ‘up’ (i.e. move all panes)
C-b M-o        rotate window ‘down’
C-b !          move the current pane into a new separate
               window (‘break pane’)
// navigate
C-b O (order)
C-b arrow
// reload config
C-b :
source-file ~/.tmux.conf
