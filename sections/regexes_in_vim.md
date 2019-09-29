
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
so you can search and replace with `%sno/regex/new_text/g`. Alternatively, you might find it helpful
to refine your regular expression by searching with /\v first, then you can insert your regular
expression by typing:

`:s/<c-r>/`

Remember that the Ctrl-r combination in insert mode allows us to insert the
content of a register and the register `/` contains the last searched string.

Notice that many times we will use the very magic mode `\v` in order to have a
behaviour similar to POSIX Extended Regular Expressions (ERE) or *egrep*, or
the very non magic mode `\V` to have a behaviour similar to `fgrep`, with the
ability to use regex capabilities only by escaping every character.



* `/regex/{n}` Makes the motion go to the nth line below the match, or above if
   n is negative. It also has the side effect of making the motion linewise.
   So you want to delete to the first line matching regex and include that line,
   you can do d/regex//0.


Let's see some examples of useful regexes.

When working with files organized in columns or tables, it's generally a good
idea to use anchors, let's see an example:

If we have a three columns file like this:

```text
0-1 1188 1.00
1-2 883 0.70
2-3 4674 3.90
3-4 4220 3.50
4-5 25998 21.90
5-6 22924 19.30
6-7 16193 13.60
7-8 26463 22.20
8-9 527 0.40
9-10 15876 13.30
```
We can substitute everything by just the second column like this:
```vim
:%s/^\S\+\s\+\(\S\+\)\s\+.*/\1/g
```

We can also move columns around by doing something like:
```vim
:%s/^\(\S\+\)\s\+\(\S\+\)\s\+.*/\2 \1/g
```

Another trick, is when we want to join more lines with a specific character,
this indeed can be done by selecting all the block we want to join except the
last line of the block and then press:
```vim
:s/\n/+/g
"in this case we join the lines with a +
```

Or another trick is to just select all the lines of the block and press "J" in
order to join them on space, and then substitute the space with another
character.


