# Understanding *word* (lowercase) and *WORD* (uppercase) in vim

This article is my attempt to illustrate what the *word* (lowercase) and *WORD* (uppercase) are in vim. 

The [Official definition of `word`](https://vimhelp.org/motion.txt.html#word)  is:

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

I use the term *keyword*, similar to the term *reserved word* or *identifiers* in a programing language (see [this](https://en.wikipedia.org/wiki/Reserved_word) or [this](https://www.programiz.com/c-programming/c-keywords-identifier)).

A **non-keyword group** is a sequence of special characters (non-black characters), for example:

```
#$$%^
%#@(
(
/()..)/
//"@#$/
```



Consider the following string (composed of groups of characters from the examples above):

```
    #$$%^s%#@(sd_f23s(afld_saf    /()..)/   //"@#$/sfdsafdaf
```

Let's colours highlight the groups with colour:

![my-understanding-of-word](./assets/explained--small-word.png)

Green boxes are the *keyword group* while red boxes are the *non-keyword group*. Finally, yellow boxes are the *sequence of white space characters*.

The boundary of a *word* (lowercase) is simply: 
1. *the sequence of white space characters* (yellow)
2. The boundary between any of the *keyword group* (green), *non-keyword group* (red)

With these boundaries for delimiters clearly illustrated, I can easily see the beginning and end of a *word* (lowercase), which I marked with the `V` and `^` marks, respectively. 

Thus, pressing the word motion `w` and `e` in normal mode will move the cursor over to the next location marked by `V` and `e` respectively.

 

The [Official definition of `WORD`](https://vimhelp.org/motion.txt.html#WORD)  is:

> A WORD consists of a sequence of non-blank characters, separated with white
space.  An empty line is also considered to be a WORD.

![my-understanding-of-word](./assets/explained--big-word.png)


#### References:

[stackoverflow.com/questions/22931032/vim-word-vs-word/61319054#](https://stackoverflow.com/a/61319054/3136861)



## Official definition of `word` and `WORD`




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
