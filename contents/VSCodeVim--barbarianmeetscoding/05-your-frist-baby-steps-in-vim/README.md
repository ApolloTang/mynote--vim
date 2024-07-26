## 5.0 [Your First Baby Steps in Vim | Barbarian Meets Coding](https://www.barbarianmeetscoding.com/boost-your-coding-fu-with-vscode-and-vim/baby-steps-in-vim/) 



### `<CTRL-C>` in vim

I just learned that `<CTRL-C>` also let you get back to normal mode.  That is in additional to `<ESC>` and `<CTRL-[>`

This mean you no longer able to use `<CTRL-C>` to copy inside vim on window's plateform. 



### Common window keymap that vim over written: 

|            | win original function | vim function            | replacement  of window fnction in vim |
| ---------- | --------------------- | ----------------------- | ------------------------------------- |
| `<CTRL-C>` | copy                  | to normal mode          | `y`                                   |
| `<CTRL-V>` | pastes                | to visual mode          | p                                     |
| `<CTRL-F>` | search                | scroll one page forward | /{searching-string}                   |

If you want to restore these windor control key map, set `vim.usCtrlKeys` to false. 

If you want graualr control to which control key map to enable or disable, set the key-value pair in `vim.handleKeys`

