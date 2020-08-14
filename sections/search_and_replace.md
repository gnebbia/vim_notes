# Search for Text

* `/mytext`   "A basic search for text 'mytext'
* `/search\c` "Search with case insensitive
* `/search\C` "Search with case sensitive

If our cursor is on a word we can search for the next
occurrence with `*` and for the previous occurrence
with `#`.
Also, if we are with our cursor on a word this word automatically
gets in our register and we can paste it in the Ex command line with
`c-r c-w`.
Also notice that if we used `*` or `#` we don't need to reinsert that
pattern in our search, so we could simply do:
`:%s//newcontent/gc`
and it will substitute the every occurrence of the word we used with
`*` or `#`.


## Search in multiple files

Searching with `vimgrep` will populate the quickfix list (see :help quickfix and :help
quickfix-window in Vim) with the result of the search.

This means that we will need to use the command `:cnext` and `:cprev` to go through the
results (instead of `n` and `N` respectively).

You can as well open the quickfix window with `:copen` and go through the results.

- `:vimgrep /pattern/ *` "search in every files of the working directory the word 'pattern'
- `:vimgrep /pattern/ a.txt b.txt c.txt` "searches the word 'pattern' in the mentioned files
- `vimgrep /pattern/ *.php` "will search 'pattern' in every php files
- `vimgrep /pattern/ **/*.php` "will search 'pattern' in every php files in every directory and
                             "subdirectory


## Fast way to Search and Replace

Another cool pattern to use whenever we have to substitute a string in multiple
places is to:
- search for a string by using `/stringToSearch`;
- press `cgn` and insert the text we want;
- press . as many times as we want to substitute in places that we want;

## View all the results of search in a split frame

This is useful especially when we want to list all the functions of a file
indeed, in the case of a python file we can do:
- `:g/def /`
- `:g/def /#` this will also show line numbers
