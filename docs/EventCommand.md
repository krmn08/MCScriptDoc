# Event, Command, Scheduling
When developing a plugin, registering event handlers, implementing commands, and scheduling processing are essential.
In MCScript, the above process can be described concisely using a special syntax.

## Event
Registering event handlers is very easy.
Simply write the event name after the @ mark (Event is omitted) and write the processing in the block.
Inside the block, the event object is passed to the `event` constant.
```
@PlayerInteract {
    event.player.sendMessage("interact")
}
```
When specifying EventPriority, write it in parentheses after the event name.
```
@PlayerInteract(LOWEST) {
    event.player.sendMessage("lowest")
}
```
## Command
The command implementation is almost the same as the function declaration.
The function name is described as the command name, and the subsequent character string is assigned to the argument.
When the command is executed, it is executed only if the number of arguments matches.
Inside the function, CommandSender is passed to the `sender` constant.
```
command test(arg1, arg2) {
    sender.sendMessage(arg1 + ":" + arg2)
}
```
```
/test arg1 arg2 # arg1:arg2
/test arg1 # nothing
```
As with functions, default arguments are available.
```
command test(arg1, arg2: "arg2") {
    sender.sendMessage(arg1 + ":" + arg2)
}
```
```
/test arg1 arg2 # arg1:arg2
/test arg1 # arg1:arg2
```
If you want to receive command arguments as an array, prefix the function name with ~.
In this case, it is always executed regardless of the number of arguments.
```
command ~test(args) {
    for arg in args {
        sender.sendMessage(arg)
    }
}
```
```
/test 1 2 3 4 5
/*
1
2
3
4
5
*/
```
## Scheduling
Use runnable expression to schedule processing.
```
r = runnable {
    Println("test")
}

r.run() # runTask(PLUGIN)
r.run(5) # runTaskLater(PLUGIN, 5)
r.run(0, 1) # runTaskTimer(PLUGIN, 0, 1)
```
The runnable expression can specify the maximum number of executions.
```
runnable(5) {
    Println(getCount())
}.run(0, 1)
/*
5
4
3
2
1
*/
```
The following methods are available in the runnable expression block:
* cancel()
* isCancelled()
* getTaskId()
* setCount(int)
* getCount()