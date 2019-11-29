
By default vim ships with netrw, which is a file manager with many
features. This is also useful to edit files remotely via different
protocols.

Let's see how to let vim navigate through an ssh server:
```sh
vim scp://remoteuser@server.tld//absolute/path/
```

We can open netrw in different ways:

* :E
* :Sex  "opens netrw in a horizontal split
* :Vex! "opens netrw in a vertical split on the right
* :Vex  "opens netrw in a vertical split on the left
* :Sex  "opens netrw in a horizontal split
* :Hex  "opens netrw in a horizontal split below
* :Hex! "opens netrw in a horizontal split above
* :Tex  "opens netrw in a new tab
* :Lex  "opens netrw vertically full height on the left (only new vims)
* :Lex! "opens netrw vertically full height on the right (only new vims)

Inside netrw we can:

* create a new file with `%`
* create a new directory with `d`
* rename a file `R`
* remove a file with `D`
* go to parent directory with `-`
* go to previous directory inn history `u`
* go to next directory in history `U`
* open a file with Enter `<CR>`
* exit netrw and go back to the file we were editing `<C-^>`
* open a file in a new horizontal split `o`
* open a file in a new vertical split `v`
* open a file in a new tab `t`
* open a file with an external program with `x`
* change sorting with `s`
* reverse sorting order `r`
* cycle between view modes `i`
* refresh file list `c-l`
* gives info on a file `qf`
* toggles showing hidden files`gh`
* toggle hidden files `a`
* preview a file (this is useful because opens the file in another window) `p`
* close the preview window `C-W z`
* Toggle netrw banner `I`


## Useful Options for netrw

In order to disable netrw automatic banner we can set:
```vim
let g:netrw_banner=0
```

