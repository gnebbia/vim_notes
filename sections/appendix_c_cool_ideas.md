
* Learn how to write a plugin for a specific language and have a template
* Give perl capabilities for code evaluation directly in vim buffers
* We can produce an html of the current file with `:TOhtml`
* `ga` to show the equivalent ascii code of the character under cursor
* Open command outputs in vim: `vim <(ls -la)`
* Create in our shell rc file a `vimi` function which will work as the vim
    interpreter, so that we can create general purpose scripts with vimL, e.g.:
```sh
vimi(){
    if [ -z "$1" ]
      then
        echo "No valid vim script supplied"
    else
        vim -i NONE -u NORC -U NONE -V1 -nNesS $1 -c'echo""|qall!'
    fi
}
```
Notice that with a command launched like this, we will still have some
unwanted output, this is due to the verbosity `V1` set to 1, for example
if we try an input() function to take user input, we will see output
printed twice, anyway we can use a workaround eploiting the silent
command, e.g., let's say we want to make the user enter a string and
process it and print it back we can do:

```vimscript
echo "Enter your name..."
silent let name = input("")
" Do whatever processing to our string
echo "You entered " . name
```


