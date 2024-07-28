# Understanding *word* (lowercase) and *WORD* (uppercase) in vim

This article is my attempt to illustrate what the *word* (lowercase) and *WORD* (uppercase) are in vim. 

The [official definition of `word`](https://vimhelp.org/motion.txt.html#word)  is:

> A word consists of a sequence of letters, digits and underscores, or a
sequence of other non-blank characters, separated with white space (spaces,
tabs, `<EOL>`).  This can be changed with the 'iskeyword' option.  An empty line
is also considered to be a word.

To make understanding easier, I am introducing two terminologies: **keyword-group** and **non-keyword group**. 

A **keyword group** is a sequence of letters, digits, and underscores, for example:

```
s
sd_f23s
afld_saf
sfdsafdaf
```

I use the term *keyword*, similar to the term *reserved word* or *identifiers* in a programming language (see [this](https://en.wikipedia.org/wiki/Reserved_word) or [this](https://www.programiz.com/c-programming/c-keywords-identifier)). The *keyword group* is simply "a sequence of letters, digits and underscores" as defined in the vim's official definition of *word* (lowercase).

A **non-keyword group** is a sequence of special characters (non-black characters), for example:

```
#$$%^
%#@(
(
/()..)/
//"@#$/
```

The *non-keyword group* is simply "a sequence of other non-blank characters" as defined in the vim's official definition of *word* (lowercase).

Consider the following string (composed of groups of characters from the examples above):

```
    #$$%^s%#@(sd_f23s(afld_saf    /()..)/   //"@#$/sfdsafdaf
```

Let's highlight the groups with colour:

![my-understanding-of-word](./assets/explained--small-word.png)

Green boxes are the *keyword group* while red boxes are the *non-keyword group*. Finally, yellow boxes are the *sequence of white space characters*.

Within a line, the delimiter for a *word* (lowercase) is the boundaries: 
1. The *sequence of white space characters* (yellow)
2. Any boundary between the *keyword group* (green) and *non-keyword group* (red)

With these boundaries for delimiters clearly illustrated, I can easily see the beginning and the ending of a *word* (lowercase), which I marked with the `V` and `^` marks, respectively. 

Thus, pressing the word motion `w` and `e` in normal mode will move the cursor over to the next location marked by `V` and `^`, respectively.

Now that we have understood the boundary of a *word* (lowercase), we can easily explain what a *WORD* (uppercase) is. 

The [official definition of `WORD`](https://vimhelp.org/motion.txt.html#WORD) is:

> A WORD consists of a sequence of non-blank characters, separated with white
space.  An empty line is also considered to be a WORD.

Within a line, the delimiter for a *WORD* (uppercase) is the boundaries: 
1. The *sequence of white space characters* (yellow)

For a *WORD* (uppercase), the *keyword group* (green) and *non-keyword group* (red) are now treated as the same entity; there is no longer a boundary between them:
   
![my-understanding-of-word](./assets/explained--big-word.png)

The horizontal curly braces mark the *WORD* (uppercase) as a unit. There is no longer a delimiter between the *keyword group* (green) and *non-keyword group* (red). Therefore the `V` and `^` is no longer present between the *keyword group* (green) and *non-keyword group* (red). Pressing the word motion `W` and `E` in normal mode will move the cursor over to the next location marked by `V` and `^`, illustrated, respectively. 


#### References:

[stackoverflow.com/questions/22931032/vim-word-vs-word/61319054#](https://stackoverflow.com/a/61319054/3136861)



## § Use the command `viw` and `viW` to identify `word` and `WORD`

When trying to understand *word* and *WORD*, I use the command `viw` and `viW` to highlight them.

The following image illustrated the *word*s highlighted by `viw`: 

<img src="./assets/small-word.png" width=350px />

The following image illustrated the *WORD*s highlighted by `viW`: 

<img src="./assets/big-word.png" width=390px />


## Special case with change word/WORD (`cw` , `cW`) and change to end of word/WORD  (`ce` , `cE`)

> `cw` and `cW` are treated like `ce` and `cE` if the cursor is
on a non-blank.  This is because "cw" is interpreted as change-word, and a
word does not include the following white space.


### References:

[vimhelp.org/motion.txt.html#word-motions](https://vimhelp.org/motion.txt.html#word-motions)
