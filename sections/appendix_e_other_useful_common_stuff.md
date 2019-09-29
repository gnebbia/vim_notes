
## Writing a file with root privileges

```vim
:w !sudo tee %
```

## Opening everything in vim

We can open basically everything in vim, by piping the launch of vim and passing
as argument '-' which corresponds to the stdin.

Let's see some examples:

```sh
man printf | vim -
```

or:
```sh
./whatever.sh | vim -
```

## Renaming files with vim

We can rename files by doing something like this:
```sh
\ls | vim -
```

then let's say we want to rename all .txt files into .md files, we can do this
by typing:
```vim
:%s/.*/mv -i & &/g
```
at this point we can do:
```vim
:%s/\.txt$/.md/g
```


## Converting/Encoding Strings in a vim file

Let's say we have a list of strings ina file and we want to convert each string
into base64, we can do this in vim by doing:
```vim
:%!xargs -n1 -I{} sh -c 'echo {} | base64'
```

Of course we can also decode a list of base64 encoded string by doing:
```vim
:%!xargs -n1 -I{} sh -c 'echo {} | base64'
```




