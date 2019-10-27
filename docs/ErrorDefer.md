# Error Handling, Deferred Execution

## Error Handling
In MCScript, errors in the script and Java exceptions are collectively handled as ScriptError.
```
1 / 0 # line:1 / by zero
```
```
Integer.parseInt("a") # line:1 java.lang.NumberFormatException: For input string: "a"
```

### throw
If you want to generate an error intentionally, use the throw statement.
```
throw "error"
```
ScriptError has no information other than the line number and error message.

### try-catch
Errors thrown like Java can be handled using try-catch.
```
fun err() {
    throw "error"
}

try {
    err()
} catch e {
    e.print()
}
```
In this case, ErrorObject wrapped with ScriptError is passed to `e`.
In addition to the `lineNumber` and `message` properties, ErrorObject has a `print` method that outputs the contents.
## Deferred Execution
You can register the process in advance using the defer statement, and finally execute it with LIFO ordering.
```
defer Println("third")
Println("first")
defer Println("second")
/*
first
second
third
*/
```
If a defer statement is described in a function, it will be processed when the function is exited.
```
fun print() {
    defer Println("second")
    Println("first")
}

print()
defer Println("third")
/*
first
second
third
*/
```
The process is executed even if it is interrupted by an error.
```
fun err() {
    defer Println("first")
    throw "error"
}

try {
    defer Println("third")
    throw "error"
} catch e {
    defer Println("second")
    err()
}
/*
first
second
third
line:3 error
*/
```
Describes the process that should be executed last when the defer statement is called.
```
import java.io.FileInputStream;
import java.io.FileOutputStream;

fun copy(from, to) {
    try {
        input = FileInputStream(from)
        defer input.close()

        output = FileOutputStream(to)
        defer output.close()

        while (c = input.read()) != -1 {
            output.write(c)
        }

        output.flush()
    } catch e {
        e.print()
    }
}
```