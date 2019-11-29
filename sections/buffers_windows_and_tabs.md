
Vim has three ways of viewing files:

* A buffer is the in-memory text of a file, so it is a file loaded in memory
* A window is a viewport on a buffer, so on an in-memory loaded file
* A tab page is a collection of windows

The workflow in vim is different from other common GUI applications,
indeed in vim a tab is just a collection of windows, the concept of tab
is more similar to the concept of gnu/linux virtual desktops.

For example if we are working in vim on a project and suddenly something happens
and we have to work on another small thing related to another project, this may
be a use case for using a new tab.
So tabs help us organizing workspaces.

We can do `:help windows` to have more info.


## Buffers

We can open a new buffer with:
```vim
:e filename.c
```
We can inspect the list of buffers with:
```vim
:ls
" or with
:buffers
```

```vim
:b<number> "jumps to the number relative buffer
```

```vim
:b <nameoffile> "jumps to the name of the file
" this also supports tab completion
```

We can switch between buffers also with
* `c-^` this switches to the last accessed buffer
* `<count>c-^` this switches to the buffer number count

## Windows

Most of the commands related to windows start with c-w, so:

* `c-w n` "opens a new window with a new buffer below
* `c-w s` "opens a new same split horizontally; also :sp
* `c-w v` "opens a new same split vertically; also :vs
* `c-w w` "cycles through open available windows
* `c-w c` "closes the current window
* `c-w o` "close every window in the current tabview but the current one
* `c-w r` "swaps the position of windows
* `c-w T` "break out current window into a new tabview
* `c-w +` "increase size of the current window
* `c-w -` "decrease size of the current window
* `c-w |` "maximize window vertically
* `c-w _` "maximize window horizontally
* `<count>c-w |` "increase window vertically by <count> lines
* `<count>c-w _` "decrease window horizontally by <count> lines
* `c-w =` "set all window to equal size
* `c-w +` "increase size of the current window
* `c-w H,J,K,L` "move a window in the direction of h,j,k,l
* `c-w h,j,k,l` "select the next window in the direction of h,j,k,l
* `c-w c-t`     "select window on top
* `c-w c-b`     "select window on bottom
* `:ball`     "opens each existing buffer in a window
* `:only` "closes all the windows except the currently active one
* `:windo <cmd>` "executes a command for each window




## Tabs

* :tabs             "visualize the list of current tabs
* :tabnext          "or `:gt` or `tabn` switches to the next tab
* :tabnext <count>  "or `:gt <count>` switches to the tab with id <count>
* :tabprevious      "or `:gT` or `tabp` switches to the previous tab
* :tabnew           "creates a new tab
* :tabclose         "or `tabc` closes the current tab with all its windows
* :tabedit          "or `tabe` closes the current tab with all its windows
* :tabonly          "or `tabo` closes all the tabs but the current one
* :tabmove          "or `tabm` changes the position of a tab, so with `:tabmove 0`
                    "move the current tab at the beginning of the list on the left
* `c-w t`           "break out current window into a new tabview
* `:tab sp`         "splits the current window in a new tab, this is useful
                    "everytime we are in a multi window environment and want
                    "to full screen on a specific window, then we can exit
                    "with `:wq`
* `:tabdo <cmd>`    "executes a command for each tab
* `:tab ball`       "opens one tab per buffer


this is a sentence of words and parenthesis ().
Make this clear to everyone

