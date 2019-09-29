
You can use in your vimrc those commands:

`set ignorecase` - All your searches will be case insensitive
`set smartcase`  - Your search will be case sensitive if it contains an
                   uppercase letter.
                   Notice that we need to set ignorecase if you want to use what
                   smartcase provides.
`syntax on` - this enables syntax highlighting
`filetype plugin` -  indent on "enables indenting depending on the kind of file
`set history=200` - stores 200 ex commands instead of 20 which is the default
`set textwidth=80` - sets the maximum characters per line at 80, we can format
                    it by using gq format lines to 'textwidth' length



to see which key code my terminal is sending to vim we have two ways:
1. sed -n l "and then press the character we want
2. from vim press c-v and then the character

