
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

