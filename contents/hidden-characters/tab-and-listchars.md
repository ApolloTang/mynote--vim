# Displaying tab characters in vim



Tab is a hidden characters, and by default vim does not display hidden characters.  You can turn on the display of hidden characters with the option  `list` setting.

``` 
:set list
```

(Note: to turn it off use `:set list!`).  

Then you can configure what character you want to display for `tab` with the `listchars` option: 

```
set listchars=tab:\>\-\|
```

To show this in effect you can  insert a tab character `\t` . To do this,  you type `[control-v]` follow with the `[tab]` key.  This will insert a tab character `\t` manually.  

Manually inserting tab ( `[control-v]` follow with the `[tab]` key) is only necessary if you have configured vim to use spaces in place of tab key (when you type the `[tab]` key, Vim replace `\t` with spaces behind the scene).  You can revert this behaviour with the following: 

```
:set tabstop=2      " To match the sample file
:set noexpandtab    " Use tabs, not spaces
:%retab!            " Retabulate the whole file
```

Helpful: you can examine hidden characters in your file with octal dump:

```
od -c <filename>
```







## Things to be aware of when setting `listchars`

#### 1. Displayed characters must be escape:

You have to escape the characters for the value of  `tab` argument in `listchars` option, for example:

```
set listchars=tab:\>\-\|
```

The following will not work:

```set listchars=tab:\>\ |
set listchars=tab:> |
```

Note in above that the values is `\>\ \|`  not `> |`



#### 2. Argument must be either 2 or 3 characters

Also note that the value of `tab` argument must be either **two** or **three** characters, or else you get an error message, for example:

```
:set listchars=tab:\>
```

Error message:

```
E474: Invalid argument: listchars=tab:\>
```

The following will works without error:

```
:set listchars=tab:\>\ 
```

The above works because there are two characters in the arguments, namely: `\>` and `\[space]`

When the argument is **two** characters:  the first one is displayed in the begining of tab width. The second is filled all the way to the end.

When the argument is **three** characters:  the last one is displayed in the end of the tab width.  



## Reference:

 [Vim documentation: options#list](https://vimhelp.org/options.txt.html#%27list%27) 

 [Vim documentation: options#listchars](https://vimhelp.org/options.txt.html#%27listchars%27) 

 [Display hidden characters - VimTricks](https://vimtricks.com/p/display-hidden-characters/) 

 [Vim: show line feeds & carriage-return - Super User](https://superuser.com/questions/97692/vim-show-line-feeds-carriage-return) 

 [How can I convert leading spaces to tabs in Vim or Linux? - Stack Overflow](https://stackoverflow.com/questions/9104706/how-can-i-convert-leading-spaces-to-tabs-in-vim-or-linux)   

 [configuration - How can I insert a real tab character in Vim? - Stack Overflow](https://stackoverflow.com/questions/6951672/how-can-i-insert-a-real-tab-character-in-vim) 

 [whitespace - How can I display tabs as characters? - Vi and Vim Stack Exchange](https://vi.stackexchange.com/questions/422/how-can-i-display-tabs-as-characters) 