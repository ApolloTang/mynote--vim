user defined variable can have same name as option.

to assign value to variable and options, you use the keywoard `let` and `set`. `let` target user defined variabvle and `set` target the options. 

To use the value stored in an option you prepend `&` in front of option name:

``` 
let textwidth='foo'
echo textwidth  " foo
echo &textwidth " 80  
```

Ref: 

 [Variables / Learn Vimscript the Hard Way](https://learnvimscriptthehardway.stevelosh.com/chapters/19.html#:~:text=Options%20as%20Variables,-You%20can%20read&text=Using%20an%20ampersand%20in%20front,to%20have%20the%20same%20name.&text=This%20time%20Vim%20displays%201,integer%201%20as%20%22true%22.) 

 [Vim: What's the difference between let and set? - Stack Overflow](https://stackoverflow.com/questions/9990219/vim-whats-the-difference-between-let-and-set) 

 [vimrc - What's the difference between let and set? - Vi and Vim Stack Exchange](https://vi.stackexchange.com/questions/2076/whats-the-difference-between-let-and-set) 