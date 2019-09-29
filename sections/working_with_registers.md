
We can inspect registers with:

```vim
:reg
```
or with:
```vim
:di
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


We can append to other registers, e.g., the clipboard register with let:
```vim
You have to use

:let @+ .= your_expression
```
TO REORGANIZE THE FOLLOWING PARAGRAPH
see stackoverflow. The problem, as you have understood, is that you cannot
capitalise the + character.

For example, to add a line in your buffer to the clipboard, place the cursor on
the line and yank it with yy. Then type
:let @+ .= @0
to run (:) the command let
to append (.=) register (@) 0, which always holds the last yank, to register +
which is a representation of the clipboard.

For example, to add the string "abc" to the clipboard, type :let @+ .= 'abc'.

(To change the X11 selection instead of the clipboard register + use register `*)`.

vim has a huge set of commands. If you plan to adopt it as your favourite editor
it is worth putting some effort into knowing, at least superficially, some of
them. Most vim users probably only use about a dozen commands and are not
interested it its true potential. It's a pity, as such tools could significantly
reduce their workload.


