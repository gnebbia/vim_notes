
If there is something which is slowing us down in vim, we can speed it up, for
example by using a key map:

```vim
inoremap jk <esc> "this will map the combo jk to the pressure of the button esc
```

So the `i` means "insert mode" since this mapping will work in insert mode.
The `nore` means non-recursive, notice that every map is non recursive,
since recursive mappings nowadays with all these plugins existing,
could cause problems.


