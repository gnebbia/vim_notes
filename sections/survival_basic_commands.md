
Here we want to inspect the very basic survival commands:

Basic movements:

* `h,j,k,l`: which is left, down, up, right
    it is easier to remember if we think that 'j' seems an arrow going down
* `:q`: quit
* `:q!`: quit without saving
* `:w`: save file
* `:wq`: save file and quit
* `:wn`: save file and switch buffer
* `ZZ`: save file and quit
* `i`: go to insert mode
* `<esc>`: go to normal mode
* `R`: go to replace mode, useful when we want to edit without moving all the text
* `yy`: copy line
* `dd`: delete line or more precisely cut
* `p`: paste laste copied thing on a newline
* `P`: paste laste copied thing here
* `u`: undo
* `U`: undoes changes on the current line
* `<c-r>`: redo
* `.`: repeat last command
* `n[command]`: repeat command n times
* `=`: indent line
* `s/foo/bar`: replace foo with bar on the current line only once
* `%s/foo/bar`: replace foo with bar on the current file only once per line
* `s/foo/bar/g`: replace foo with bar on the current line
* `%s/foo/bar/g`: replace foo with bar on the current file
* `!!`: gives me an input line for a shell command
* `J`: join lines
* `i<c-m>`: split lines
* `~`: swap case of current character under cursor
* `gu`: changes to lowercase the current word with guw and a line with guu
* `gU`: changes to uppercase the current word with gUw and a line with gUU


