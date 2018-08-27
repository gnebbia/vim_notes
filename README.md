# VIM Notes

## Intro to Vim
Vim is without doubts one of the most powerful text editors
out there. Anyway people who is starting with it can find it quite
confusing and not very intuitive this is due to many reasons. 
Some of the main reasons are:

* vim is a modal text editor
* common shortcuts which are commmonly accepted among 
  many applications (e.g., Ctrl+c, Ctrl+v, Ctrl+z) do not 
  work in vim as expected.
* the most used alternative is command line
* too many "cryptic" commands to learn

If we just consider these points, we know from User Interface and 
more in general Human Computer Interaction theory modal tools
are unnecessarily complicated and non intuitive, and also when
designing a tool we should always make it more intuitive and user-friendly
as possible.
Indeed Jef Raskin -- a Human Commputer Intercation expert -- once said:
*"Modes are a significant source of errors, confusion, unnecessary 
restrictions, and complexity in interfaces."*
Anyway vim beats this, because User Interface theory generally
develops fundamental concepts aiming at spending less time
as possible learning an interface. 
Anyway vim users know that in order to have a more proficient text editor
users should have a desire to learn, and this is a necessary 
prerequisite in general to be a vim user.
So to sum up, UI experts don't take into account our ability
or desire to learn.

## Learning Vim

We can start by executing:

```sh
vimtutor
```

## Survival Basic Commands

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
* yy: copy line
* `dd`: delete line or more precisely cut
* `p`: paste laste copied thing
* `u`: undo
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


## Motions

* `()` "move to the beginning or end of a sentence
* `{}` "move to the beginning or end of a paragraph
* `gf` "on a file name, opens the file in a new buffer
* `g;` "goes to the last place where a modification occurred (change list)
* `g,` "goes to the next place where a modification occurred (change list)
* `gg` "go to beginning of file
* `G`  "go to end of file
* `0`  "go to the beginning of line
* `$`  "go to the end of a line
* `H`  "move cursor to the top of the currently visible page
* `M`  "move cursor to the middle of the currently visible page
* `L`  "move cursor to the bottom of the currently visible page
* `c-d` "page down
* `c-u` "page up
* `c-e` "scroll down one line
* `c-y` "scroll up one line
* `t <char>` "move the cursor just before the character indicated
* `<n> t <char>` "move the cursor just before the nth occurrence of the 
                 "character indicated
* `f <char>` "move the cursor on the character indicated
* `<n> f <char>` "move the cursor on the nth occurrence of the 
                 "character indicated
* `/<string>` "move the cursor to the indicated string
* `<n>/<string>` "move the cursor to the nth occurrence of the indicated 
                 "string
* `[[` "move the cursor to the previous textual section
* `]]` "move the cursor to the next textual section


## Search and Replace


* `/mytext`   "A basic search for text 'mytext'
* `/search\c` "Search with case insensitive
* `/search\C` "Search with case sensitive

If our cursor is on a word we can search for the next
occurrence with `*` and for the previous occurrence
with `#`.
Also, if we are with our cursor on a word this word automatically 
gets in our register and we can paste it in the Ex command line with
`c-r c-w`. 
Also notice that if we used `*` or `#` we don't need to reinsert that
pattern in our search, so we could simply do:
`:%s//newcontent/gc`
and it will substitute the every occurrence of the word we used with
`*` or `#`.


### Search in multiple files

Searching with `vimgrep` will populate the quickfix list (see :help quickfix and :help 
quickfix-window in Vim) with the result of the search.

This means that we will need to use the command `:cnext` and `:cprev` to go through the 
results (instead of `n` and `N` respectively).

You can as well open the quickfix window with `:copen` and go through the results.

* `:vimgrep /pattern/ *` "search in every files of the working directory the word 'pattern'
* `:vimgrep /pattern/ a.txt b.txt c.txt` "searches the word 'pattern' in the mentioned files
* `vimgrep /pattern/ *.php` "will search 'pattern' in every php files
* `vimgrep /pattern/ **/*.php` "will search 'pattern' in every php files in every directory and
                             "subdirectory



## Info on file

* `c-g` "displays the current file name
* `:%s/^@//n` "counts how many lines start with the character @
* `g<c-g>` "shows detailed status on the current line/column/word
* `:oldf` "lists recently opened files


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


## Working with registers

We can inspect registers with:

```vim
:reg
```

In insert mode, we can paste the content of a register, simply by issuing:
```vim
`c-r register_identifier`
```

Things we yank are automatically placed in the `0` register, so this is
not overwritten by delete commands like `dd`.

Anyway let's see how to select registers and work with them.

`"<letter>` selects a register denoted with <letter>, let's say
for example we want to copy a letter to register `a`, we can do this
by doing:
`"ayiw`
and we can paste the content from this register by doing:
`"ap`
We can append content to register `a` by woking on register `A`, so
we could add another word in the content of `a` by doing:
`"Ayiw`
and pasting the content of `a` with:
`"ap`

Always remember that uppercase registers are used to append content to lowercase
registers.

If vim is compiled with *clipboard* extension option we can work with graphical
clipboards, specifically with registers `+` (the one we commonly work with
copy/paste or ctrl-c, ctrl-v) and `*` (we can paste content from `*` by using
the middle mouse button).


## Visual Modes

There are three main visual modes:

* `v` character-wise selection mode
* `V` line-wise selection mode
* `c-v` block-wise selection mode

We can flexibly switch between these selection modes, and go
from one extremity of selection to the other by using `o`.
We can change a block of text by doing:

`c-v` "then we select the text we are interested in c text we want to insert <esc>

instead of pressing `c` after the selection we could also have typed:
* I "to insert before text
* A "to insert after text, useful for adding ; in c-style programming languages
    instructions
* c "changes text selected

This is a good way to change text within a block.
There are other interesting things about visual selections,
for exaample:

* `gv`, reselects the last selected visual block
* `\`>`, after a selection moves the cursor at the end of the last selection
* `\`<`, after a selection moves the cursor at the beginning of the last selection

Notice that we can combine registers and visual mode selections to
perform complex yanking and pasting operations.

For example let's say that we have a sequence of numbered lines from 1 to 10,
like a sequence of lines generated with the bash shell command `seq 10`

```text
1
2
3
4
5
6
7
8
9
10
```
Now we can create a register which will contain lines from 2 to 5 and from 7 to
9. We can do this by issuing:

`gg` "goes to the beginning of file
`/2<CR>` goes on line 2
`V` enters in line-wise visual mode
`/5<CR>` goes to line with 5
`"ay` pastes the content in register a
`/7<CR>` goes on line 7
`V` enters in line-wise visual mode
`/9<CR>` goes to line with 5
`"Ay` appends the content in register a

Now we can paste text with a simple `"ap`.


## Ex Commands

* `q/` "opens the command line window with history of searches
* `q:` "opens the command line window with history of Ex commands
* `c-f` "swtich from command line mode to the command line window

Let's see now some examples of Ex commmands, for someone
who is already used to sed it will be easy to memorize or use
vim Ex commands.

`:12`                     "moces cursor to line number 12
`:p`                      "prints the current line, the one the cursor is on
`:10,22p`                 "prints lines from 10 to 22
`:10,22w filename.txt`    "saves lines from 10 to 22 to a file called *filename.txt*
`:d`                      "deletes the current line, the one the cursor is on
`:1,7d`                   "deletes lines from 1 to 7
`:/match1/,/match2/p`     "prints lines between lines who match match1 and match2
`:$`                      "moves cursor to last line
`:12,$p`                  "prints lines from 12 to end of file
`:/BEGIN/,/END/p`         "prints in a window the content between BEGIN and END
                          "lines including the lines which match BEGIN or END
`:g/BEGIN/,/END/p`        "prints in a window the content between BEGIN and END
                          "lines including the lines which match BEGIN or END
                          "it does that for all the occurrences and not only
                          "for the next one as with th previous Ex command
`:s/pattern1/pattern2/`   "performs a substitution on current line once
`:%s/pattern1/pattern2/`  "performs a substitution on current buffer once per line

`:s/pattern1/pattern2/g`  "performs a substitution on current line for all occurrences
`:%s/pattern1/pattern2/g` "performs a substitution on current buffer for all occurrences


We can also use offsets:

`:/BEGIN/+1,/END/-1p`     "prints in a window the content between BEGIN and END
                          "lines excluding the lines which match BEGIN or END
`:g/BEGIN/+1,/END/-1p`    "prints in a window the content between BEGIN and END
                          "lines excluding the lines which match BEGIN or END
                          "it does that for all the occurrences and not only
                          "for the next one as with th previous Ex command

We can also use marks -- this is interesting -- so mark a line with `ma`
then mark another line with `mb` and then for example save that into another
file with:
`:'a,'bw newfile.txt` 

Of course this may also be more comfortable by using visual selection.



## Inserting text from files or commands

We can insert text from files by doing:

```vim
:r filename.txt
```

this can be useful also for templates.

We can also print the output of a command into our current buffer with:
```vim
:r! command
```

Another way to print the output from a command is:
```vim
:r !command -flag1 --option1
```


## Buffers, Windows and Tabs

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


### Buffers

We can open a new buffer with:
```vim
:e filename.c
```
We can inspect the list of buffers with:
```vim
* :ls
* :buffers
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

### Windows

Most of the commands related to windows start with c-w, so:

* `c-w n` "opens a new window with a new bufferbelow
* `c-w s` "opens a new same split horizontally; also :sp
* `c-w v` "opens a new same split vertically; also :vs
* `c-w w` "cycles through open available windows
* `c-w c` "closes the current window
* `c-w o` "close every window in the current tabview but the current one
* `c-w r` "swaps the position of windows
* `c-w t` "break out current window into a new tabview
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
* `:only` "closes all the windows except the currently active one



### Tabs

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


this is a sentence of words and parenthesis ().
Make this clear to everyone

## Sessions

* `:mksession filename` "saves session to filename
* `vim -S filename` "restore session from filename
* `:mks!` "saves again the session


## Spelling

* `:set spell` "turns on spell checking
* `:set spelllang=[language abbreviation]` "sets the spelling language
* `]s` "jumps to the next mistake
* `[s` "jumps to the previous mistake
* `z=` "checks for spelling suggestions
* `zg` "adds word to regular dictionary
* `zG` "adds word to the current session dictionary
* `zug` "remove word from the current session dictionary
* `zuG` "adds word from the current session dictionary


## Regexes in Vim

In vim we have 4 modes in order to deal with regexes:

* `very non magic mode`, manually specified with `\V`
* `non magic mode`, manually specified with `\M`
* `magic mode`, manually specified with  `\m` **default setting**
* `very magic mode`, manually specified with `\v`

In order to better understand how it works, I will put a piece
of documentation easily accessible with `:help /magic`.

```sh
Examples:
after:    \v       \m       \M       \V     matches 
                'magic' 'nomagic'
          $        $        $        \$    matches end-of-line
          .        .        \.       \.    matches any character
          *        *        \*       \*    any number of the previous atom
          ()      \(\)     \(\)     \(\)   grouping into an atom
          |        \|       \|       \|    separating alternatives
          \a       \a       \a       \a    alphabetic character
          \\       \\       \\       \\    literal backslash
          \.       \.       .        .     literal dot
          \{       {        {        {     literal '{'
          a        a        a        a     literal 'a'
```

notice that only Vim supports \m, \M, \v and \V.

It is recommended to always keep the 'magic' option at the default setting,
which is 'magic'.  This avoids portability problems.  To make a pattern immune
to the 'magic' option being set or not, put "\m" or "\M" at the start of the
pattern.

Se vogliamo quindi utilizzare una versione simile alle POSIX Extended
Regular Expressions (ERE) basta utilizzare la sequenza `\v`.
Esempio:

* `\v(test.*)`

Regular expressions in scripts should always specify one of \v, \m, \M, or \V, to make them 
immune to the user's 'magic' setting.

The :substitute command has the :smagic and :snomagic alternate forms (the same as \m and \M), 
so you can search and replace with %sno/regex/new_text/g. Alternatively, you might find it helpful 
to refine your regular expression by searching with /\v first, then you can insert your regular 
expression by typing:

`:s/<c-r>/` 

Remember that the Ctrl-r combination in insert mode allows us to insert the
content of a register and the register `/` contains the last searched string.


## Navigate through the docs

* :help or :h
* :helpgrep or :helpg  and then :cn or :cp to browse different matches


## Navigate in a specific file type

* `:g/^#/#` "gives a summary of sections
* `:g/def /#` "gives a list of functions in a python source
* `:g/^$/d` "deletes all blank lines, useful especially when some
            "lines are selected visually


## Working with multiple files

We can apply operations on multiple files, like searches, substitutions
and deletions or macros by using the arg commands.

Let's see some examples:


* `:arg *.html`      "Empty the buffer and populate the arglist 
                    with all html file in the current working directory
* `:argadd *.twig`   "Add twig files to the arglist
* `:argdo %s/pattern/replace/ge | update` "Replace the occurence pattern by 
                                         replace in every files of the arglist

The e flag in a substution warns if the pattern is not found.

## Miscellaneous

* `:retab` converts all tabs to spaces


Examples of regex in vim substitutions

Notice that a newline in vim is \r

:%s/\s\+/\r/gc substitute each space (at least one) with a new line



## Vim Commands Scripts

We can automate vim commands, e.g., substitutions or some other kinds of
modifications by writing a series of commands in a file, for example:

```vim
%s/ciao/hello/g
%s/\\n/\r/g
%s/\\t/    /g
quit
```

now if we save this text in a file called `myscript.vim` we can execute on
whatever file with:

```vim
vim -S myscript.vim textfile1 textfile2
```

## Autocompletion

* `c-x c-f` "autocompletion for file names


A very nice trick with autocompletion is to press c-n c-p
to havee a real-time filtering list an works with any kind
of autocompletion. This is very useful when we have a lot
of suggestions, e.g., like 20 or more suggestions and we may
be confused with all that text, so in this case we can just press
c-n c-p and type some text to filter.

For example, let's say we want to filter on some filename and we
are currently in a directory with a lot of files, we can do:
`c-x c-f c-n c-p` and this will allow us to keep the list and type
some text in order to have a better filter.


## Appendix A: Math

On a number we can do:

* c-a to increase
* c-z to decrease it
* in insert mode c-r= and type an operation vim will give us the result


## Appendix B: Shell Tricks

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
* `ga` to show the equivalent ascii code of the character under cursor
* Open command outputs in vim: `vim <(ls -la)`
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


## Appendix D: Common Options

You can use in your vimrc those commands:

`set ignorecase` - All your searches will be case insensitive
`set smartcase`  - Your search will be case sensitive if it contains an
                   uppercase letter.
                   Notice that we need to set ignorecase if you want to use what 
                   smartcase provides. 
`syntax on` - this enables syntax highlighting
`filetype plugin` -  indent on "enables indenting depending on the kind of file
`set history=200` - stores 200 ex commands instead of 20 which is the default

