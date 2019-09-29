
We can apply operations on multiple files, like searches, substitutions
and deletions or macros by using the arg commands.

Let's see some examples:


* `:arg *.html`      "Empty the buffer and populate the arglist
                    with all html file in the current working directory
* `:argadd *.twig`   "Add twig files to the arglist
* `:argdo %s/pattern/replace/ge | update` "Replace the occurence pattern by
                                         replace in every files of the arglist
* `argdo %s/foo/bar/gc` "performs all the substitutions in every file of the
                         arglist
* `bufdo bd`            "closes all the buffers except the current one

The e flag in a substution warns if the pattern is not found.

