# Hello World

There are three ways to execute a script with MCScript.
1. Write a script in a file
2. Execute with /mcs command
3. Execute interactively with REPL

We recommend using REPL for learning in this document.

### Write a script in a file

When actually developing a plugin, write the script in a file (.mcs) and place it under ScriptPath. All script files are executed as soon as the MCScript plugin is loaded.

### Execute with /mcs command

It can be executed by writing a script after /mcs. This is useful if you want to execute a short script immediately.
```
/mcs a = 1 + 1
```
### Execute interactively with REPL

During REPL mode, all chats are interpreted as scripts. If it determines that the script is interrupted, it does not run immediately but waits for the next input.
If you want to force execution, please add ";" at the end of the script.

```
/mcs repl # toggle
/mcs repl stop # disable
/mcs repl start # enable
```
Scripts can be entered on multiple lines.
```
/mcs repl
a = 1
for (x in Range(5)) {
    a += x
}
/mcs repl
```
Hello World
```
Println("Hello World")
```