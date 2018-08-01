# VIM

## Learning Vim

We can start by executing:

```sh
vimtutor
```

## Survival Basic Commands

Here we want to inspect the very basic survival commands:

Basic movements:
* h,j,k,l: which is left, down, up, right
    it is easier to remember if we think that 'j' seems an arrow going down
* `:q`: quit
* `:q!`: quit without saving
* `:w`: save file
* `:wq`: save file and quit
* i: go to insert mode
* <esc>: go to normal mode
* yy: copy line
* dd: delete line or more precisely cut
* p: paste laste copied thing
* u: undo
* <c-r>: redo
* .: repeat last command
* n[command]: repeat command n times
* =: indent line
* s/foo/bar: replace foo with bar on the current line only once
* %s/foo/bar: replace foo with bar on the current file only once per line
* s/foo/bar/g: replace foo with bar on the current line
* %s/foo/bar/g: replace foo with bar on the current file


## Motions

    * `()` "move to the beginning or end of a sentence
    * `{}` "move to the beginning or end of a paragraph


## Keymaps

If there is something which is slowing us down in vim, we can speed it up, for
example by using a key map:

```vim
inoremap jk <esc> "this will map the combo jk to the pressure of the button esc
```

So the `i` means "insert mode" since this mapping will work in insert mode.
The `nore` means non-recursive, notice that every map is non recursive, 
since recursive mappings nowadays with all these plugins existing, 
could cause problems.

## Common Options

```vim
syntax on "this enables syntax highlighting
filetype plugiin indent on "enables indenting depending on the kind of file
```

## Working with registers

We can inspect registers with:

```vim
:reg
```

In insert mode, we can paste the content of a register, simply by issuing:

```vim
c-r register_identifier
```

## Visual Modes

There are three main visual modes:

    * v
    * V
    * c-v

we can change a block of text by doing:

    c-v "then we select the text we are interested in
    c text we want to insert
    <esc>

instead of pressing `c` after the selection we could also have typed:
    * I "to insert before text
    * A "to insert after text

This is a good way to change text within a block.


## Inserting text from files or commands

We can insert text from files by doing:

:r filename.txt

this can be useful also for templates.

We can also print the output of a command into our current buffer with:

:r! command


## Buffers, Windows and Tabs

Vim has three ways of viewing files:

* A buffer is the in-memory text of a filee
* A window is a viewport on a buffer
* A tab page is a collection of windows

We can do `:help windows` to have more info.


### Buffers

We can open a new buffer with:
```vim
:e filename.c
```
We can inspect the list of buffers with:
```vim
:ls
```

```vim
:b<number> "jumps to the number relative buffer
```

```vim
:b <nameoffile> "jumps to the name of the file
" this also supports tab completion
```

### Windows

Most of the commands related to windows start with c-w, so:

* c-w n "opens a new blank split window below
* c-w s "opens a new same split horizontally
* c-w v "opens a new same split vertically

### Tabs

:gt
:gT
:tabnew

### Appendix A: Math


On a number we can do:

* c-a to increase
* c-z to decrease it
* in insert mode c-r= and type an operation vim will give us the result

### Appendix B: Shell Tricks

We can pause the vim execution and go to a terminal with a simple:

```vim
:shell
```
then we can go back to vim with a:
```sh
exit
```
this is very useful, especially if we need the full capabilities of a terminal
for a while.


Another good trick is to save the command output to the current buffer.
This can be done in a couple of cool ways:

1. `:r! commandname` "this will print the command output to screen
2. save as mapping `nnoremap Q !!sh<CR>` " now everytime, we can type a command
    in vim buffer and then on that line just press `Q` to print the output

A cool but somewhat useless thing is to print ascii art, for example by using
programs like `figlet`.



## Appendix C: Cool Ideas

* Learn how to write a plugin for a specific language and have a template
* Give perl capabilities for code evaluation directly in vim buffers
* Create in our shell rc file a `vimi` function which will work as the vim
    interpreter, so that we can create general purpose scripts with vimL, e.g.:
```sh
vimi(){
    if [ -z "$1" ]
      then
        echo "No valid vim script supplied"
    else 
        vim -i NONE -u NORC -U NONE -V1 -nNesS $1 -c'echo""|qall!'
    fi
}
```




## Navigate in a specific file type


* `:g/^#/#` "gives a summary of sections
* `:g/def /#` "gives a list of functions in a python source


