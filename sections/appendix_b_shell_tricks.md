
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



