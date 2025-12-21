---
date: "2025-07-17T08:13:58.199+02:00"
title: "GDB"
description: "Debug C Programs with the GNU Debugger"
dg-publish: true
---

## Help

| Option                         | Description                                                        |
| :----------------------------- | :----------------------------------------------------------------- |
| `help`                         | List gdb command topics.                                           |
| `help topic-classes`           | List gdb command within class.                                     |
| `help `command                 | Command description. <br>eg `help show` to list the show commands  |
| `apropos` search-word          | Search for commands and command topics containing ` search-word `. |
| `info args` <br> `i args`      | List program command line arguments                                |
| `info breakpoints`             | List breakpoints                                                   |
| `info break`                   | List breakpoint numbers.                                           |
| `info break` breakpoint-number | List info about specific breakpoint.                               |
| `info watchpoints`             | List breakpoints                                                   |
| `info registers`               | List registers in use                                              |
| `info threads`                 | List threads in use                                                |
| `info set`                     | List set-able option                                               |

## Break and Watch

| Option                                                                             | Description                                                                                                                         |
| ---------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| `break `funtion-name <br> `break `line-number <br> `break `ClassName::functionName | Suspend program at specified function of line number.                                                                               |
| `break +`offset <br> `break -`offset                                               | Set a breakpoint specified number of lines forward or back from the position at which execution stopped.                            |
| `break `filename`:`function                                                        | Don't specify path, just the file name and function name.                                                                           |
| `break `filename`:`line-number                                                     | Don't specify path, just the file name and line number.<br>`break `Directory/Path/filename`.cpp:62`                                 |
| `break *`address                                                                   | Suspend processing at an instruction address. Used when you do not have source.                                                     |
| `break `line-number`⠀if `condition                                                 | Where condition is an expression. i.e. `x > 5` <br> Suspend when boolean expression is true.                                        |
| `break `line`⠀thread `thread-number                                                | Break in thread at specified line number. Use `info threads` to display thread numbers.                                             |
| `tbreak`                                                                           | Temporary break. Break once only. Break is then removed. See "break" above for options.                                             |
| `watch `condition                                                                  | Suspend processing when condition is met. i.e. `x > 5`                                                                              |
| `clear` <br> `clear `function <br> `clear `line-number                             | Delete breakpoints as identified by command option.<br>Delete all breakpoints in `function` <br> Delete breakpoints at a given line |
| `delete` <br> `d`                                                                  | Delete all breakpoints, watchpoints, or catchpoints.                                                                                |
| `delete `breakpoint-number <br> `delete `range                                     | Delete the breakpoints, watchpoints, or catchpoints of the breakpoint ranges specified as arguments.                                |
| `disable `breakpoint-number-or-range <br> `enable `breakpoint-number-or-range      | Does not delete breakpoints. Just enables/disables them.<br>Show breakpoints: `info break` <br> i.e. `disable 2-9`                  |
| `enable `breakpoint-number` once`                                                  | Enables once                                                                                                                        |
| `continue` <br> `c`                                                                | Continue executing until next break point/watchpoint.                                                                               |
| `continue `number                                                                  | Continue but ignore current breakpoint `number` times. <br> Useful for breakpoints within a loop.                                   |
| `finish`                                                                           | Continue to end of function.                                                                                                        |

## Line Execution

| Option                                                             | Description                                                                                                                               |
| ------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
| `step` <br> `s` <br> `step `number-of-steps-to-perform             | Step to next line of code. Will step into a function.                                                                                     |
| `next` <br> `n` <br> `next `number                                 | Execute next line of code. Will not enter functions.                                                                                      |
| `until` <br> `until `line-number                                   | Continue processing until you reach a specified line number. <br>Also: function name, address, filename:function or filename:line-number. |
| `info signals` <br> `info handle` <br> `handle `SIGNAL-NAME option | Perform the following option when signal received: nostop, stop, print, noprint, pass/noignore or nopass/ignore                           |
| `where`                                                            | Shows current line number and which function you are in.                                                                                  |

## Stack

| Option                                                                                               | Description                                                                                                                                 |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| `backtrace` <br> `bt` <br> `bt `inner-function-nesting-depth <br> `bt -`outer-function-nesting-depth | Show trace of where you are currently. Which functions you are in. Prints stack backtrace.                                                  |
| `backtrace full`                                                                                     | Print values of local variables.                                                                                                            |
| `frame` <br> `frame `number <br> `f `number                                                          | Show current stack frame (function where you are stopped)<br>Select frame number. (can also user up/down to navigate frames)                |
| `up` <br> `down` <br> `up `number <br> `down `number                                                 | Move up a single frame (element in the call stack)<br>Move down a single frame<br>Move up/down the specified number of frames in the stack. |
| `info frame`                                                                                         | List address, language, address of arguments/local variables and which registers were saved in frame.                                       |
| `info args` <br> `info locals` <br> `info catch`                                                     | Info arguments of selected frame, local variables and exception handlers.                                                                   |

## Source Code

| Option                                                                                                                               | Description                                           |
| ------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------- |
| `list` <br> `l` <br> `list `line-number <br> `list `function <br> `list -` <br> `list `start#`,`end# <br> `list `filename`:`function | List source code.                                     |
| `set listsize `count <br> `show listsize`                                                                                            | Number of lines listed when `list command` given.     |
| `directory `directory-name <br> `dir `directory-name <br> `show directories`                                                         | Add specified directory to front of source code path. |
| `directory`                                                                                                                          | Clear sourcepath when nothing specified.              |

## Machine Language

| Option                                   | Description                                                                                                                                                                                                                                                                        |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `info line` <br> `info line `number      | Displays the start and end position in object code for the current line in source.<br>Display position in object code for a specified line in source.                                                                                                                              |
| `disassemble `0xstart 0xend              | Displays machine code for positions in object code specified (can use start and end hex memory values given by the `info line` command.                                                                                                                                            |
| `stepi` <br> `si` <br> `nexti` <br> `ni` | step/next assembly/processor instruction.                                                                                                                                                                                                                                          |
| `x `0xaddress <br> `x/nfu `0xaddress     | Examine the contents of memory.<br>Examine the contents of memory and specify formatting.<ul><li>n: number of display items to print</li><li>f: specify the format for the output</li><li>u: specify the size of the data unit (eg. byte, word, ...)</li></ul>Example: `x/4dw var` |

## Examine Variables

| Option                                                                                                                 | Description                                                                                                                        |
| ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `print `variable-name <br> `p `variable-name <br> `p `file-name`::`variable-name <br> `p '`file-name`'::`variable-name | Print value stored in variable.                                                                                                    |
| `p *`array-variable`@`length                                                                                           | Print first # values of array specified by `length`. Good for pointers to dynamically allocated memory.                             |
| `p/x `variable                                                                                                         | Print as integer variable in hex.                                                                                                  |
| `p/d `variable                                                                                                         | Print variable as a signed integer.                                                                                                |
| `p/u `variable                                                                                                         | Print variable as a un-signed integer.                                                                                             |
| `p/o `variable                                                                                                         | Print variable as a octal.                                                                                                         |
| `p/t `variable <br> `x/b `address <br> `x/b &`variable                                                                 | Print as integer value in binary. (1 byte/8bits)                                                                                   |
| `p/c `variable                                                                                                         | Print integer as character.                                                                                                        |
| `p/f `variable                                                                                                         | Print variable as floating point number.                                                                                           |
| `p/a `variable                                                                                                         | Print as a hex address.                                                                                                            |
| `x/w `address <br> `x/4b &`variable                                                                                    | Print binary representation of 4 bytes (1 32 bit word) of memory pointed to by address.                                            |
| `ptype `variable <br> `ptype `data-type                                                                                | Prints type definition of the variable or declared variable type. Helpful for viewing class or struct definitions while debugging. |

## GDB Modes

| Option                                                                                          | Description                                                        |
| ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| `set `gdb-option value                                                                          | Set a GDB option                                                   |
| `set logging on` <br> `set logging off` <br> `show logging` <br> `set logging file `log-file    | Turn on/off logging. Default name of file is `gdb.txt`             |
| `set print array on` <br> `set print array off` <br> `show print array`                         | Default is off. Convient readable format for arrays turned on/off. |
| `set print array-indexes on` <br> `set print array-indexes off` <br> `show print array-indexes` | Default off. Print index of array elements.                        |
| `set print pretty on` <br> `set print pretty off` <br> `show print pretty`                      | Format printing of C structures.                                   |
| `set print union on` <br> `set print union off` <br> `show print union`                         | Default is on. Print C unions.                                     |
| `set print demangle on` <br> `set print demangle off` <br> `show print demangle`                | Default on. Controls printing of C++ names.                        |

## Start and Stop

| Option                                                                         | Description                                                                                                                                      |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| `run` <br> `r` <br> `run `command-line-arguments <br> `run <`infile`> `outfile | Start program execution from the beginning of the program. <br>The command `break main` will get you started. Also allows basic I/O redirection. |
| `continue` <br> `c`                                                            | Continue execution to next break point.                                                                                                          |
| `kill`                                                                         | Stop program execution.                                                                                                                          |
| `quit` <br> `q`                                                                | Exit GDB debugger.                                                                                                                               |



---
Sources:
- 2022-04-06 [Linux Tutorial - GNU GDB Debugger Command Cheat Sheet](http://www.yolinux.com/TUTORIALS/GDB-Commands.html)

Related:

Tags:
[Programming Languages - Communicate instructions between humans and computers](./Programming-Languages.md)