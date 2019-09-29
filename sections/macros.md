
We can start recording a macro with `q<register>`, generally if we just need
a fast macro we will use the `q` register, so we can do that with
`qq`.

We can look at the register as it was just another register so
with `:regs` or in insert mode with `c-r <register>` or again
with `echo @<register>`.

In order to apply a macro we simply do `@<register>`.

In order ot apply a macro in visual mode, we can simply do:

1. select the visual area with whichever visual mode we prefer
2. press `:`
3. type `normal @q` if the macro is recorded in q, or whatever register

if we want to just apply a macro like 100 times we can do:
`100@<register>`


We can repeat the last executed macro with `@@`.

