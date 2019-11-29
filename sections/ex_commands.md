
* `q/` "opens the command line window with history of searches
* `q?` "opens the command line window with history of searches
* `q:` "opens the command line window with history of Ex commands
* `c-f` "swtich from command line mode to the command line window
* `@:` "recall last ex command

Let's see now some examples of Ex commmands, for someone
who is already used to sed it will be easy to memorize or use
vim Ex commands.

`:12`                         "moves cursor to line number 12
`:p`                          "prints the current line, the one the cursor is on
`:10,22p`                     "prints lines from 10 to 22
`:10,22w filename.txt`        "saves lines from 10 to 22 to a file called *filename.txt*
`:d`                          "deletes the current line, the one the cursor is on
`:1,7d`                       "deletes lines from 1 to 7
`:/match1/,/match2/p`         "prints lines between lines who match match1 and match2
`:$`                          "moves cursor to last line
`:12,$p`                      "prints lines from 12 to end of file
`:.! <command>`               "is equivalent to pressing `!!` and substitutes
                              "the current line with the output of the command
`:%! <command>`               "substitutes the current entire buffer with the
                              "output of the command
`:%!grep '^C'`                "removes from the file all the lines except the
                              "ones respecting the mentioned regex
`:%!grep -v '^C'`             "removes from the file all the lines who do not
                              "respect the mentioned regex
`:sort`                       "sort all lines
`:sort!`                      "sort all lines in reverse
`:sort u`                     "sort all lines and remove duplicates
`:g/^#/y A`                   "yanks all the lines starting with the character `#` in
                              "the register `a`
`:g/pattern/z#.5|echo '=='`   "shows all the occurrences of pattern with a context
                              "of 5 lines separater by the sequence `==`
`:w !sudo tee %`              "saves the file with root privileges
`:/BEGIN/,/END/p`             "prints in a window the content between BEGIN and END
                              "lines including the lines which match BEGIN or END
`:g/BEGIN/,/END/p`            "prints in a window the content between BEGIN and END
                              "lines including the lines which match BEGIN or END
                              "it does that for all the occurrences and not only
                              "for the next one as with th previous Ex command
`:s/pattern1/pattern2/`       "performs a substitution on current line once
`:%s/pattern1/pattern2/`      "performs a substitution on current buffer once per line
`:s/pattern1/pattern2/g`      "performs a substitution on current line for all occurrences
`:%s/pattern1/pattern2/g`     "performs a substitution on current buffer for all occurrences
`:%s/\%Vpattern1/pattern2/g`  "performs a substitution on current visual selection
`:%! <command>`               "performs substitution of the entire buffer with
                              "the output of command


We can also use offsets:

`:/BEGIN/+1,/END/-1p`       "prints in a window the content between BEGIN and END
                            "lines excluding the lines which match BEGIN or END
`:g/BEGIN/+1,/END/-1p`      "prints in a window the content between BEGIN and END
                            "lines excluding the lines which match BEGIN or END
                            "it does that for all the occurrences and not only
                            "for the next one as with th previous Ex command

We can also use marks -- this is interesting -- so mark a line with `ma`
then mark another line with `mb` and then for example save that into another
file with:
`:'a,'bw newfile.txt`

Of course this may also be more comfortable by using visual selection.



