
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


