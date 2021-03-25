# vim visual modes

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


We can also issue commands on the visual selected block, for example to add a character
at the end of a block of lines we can do:

    : norm A"

This will add the double quotes to the and of every line selected.
