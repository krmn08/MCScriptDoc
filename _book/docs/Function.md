# Function
MCScript functions can be handled in the same way as normal objects.
Higher order functions that pass functions to functions can also be realized easily.
## Function Literal
You can create anonymous functions using function literals. MCScript functions do not need to specify an argument or return type, and a return statement is not required.
MCScript functions return the result of the last evaluated statement.
```
fun(x) {
    Println(x)
}
```
You can omit the curly braces for a single expression.
```
fun(x): Println(x)
```
#### Arguments
MCScript does not support function overloading. Instead, default arguments are available.
```
f = fun(x, y: 3) {
    x + y
}
f(1) # 4
f(1, 2) # 3
```
#### Lambda Expression
Function objects can be described with the same lambda expression as Java.
```
() -> Println("test")
(x, y: 3) -> {
    x + y
}
```
## Function definition
You can also define a named function explicitly without assigning an anonymous function to a variable.
```
fun f(x, y) {
    x + y
}
f(1, 2)
```
In a function definition, a function object is assigned to a constant.
```
const f = fun(x, y) {
    x + y
}
```
Therefore, it cannot be assigned to a variable with a function name.
```
fun f(x, y) {
    x + y
}
f = 1 # error
```
In addition, function definitions at the top level are evaluated before other statements.
```
f(1) # error
f = fun(x) {
    Println(x)
}
```
```
f(x) # pass
fun f(x) {
    Println(x)
}
```
#### Public function
When writing to a script file, function cannot be called from outside. In MCScript, you can call from outside by capitalizing the first letter of the function name.

public.mcs
```
fun Public(x) {
    Println(x)
}
```
main.mcs
```
Public("Hi")
```
Public functions are executed in an independent environment. Therefore, external variables and functions cannot be called.
```
x = 1
fun f(s) {
    Println(s)
}

fun Public() {
    a = x # error
    f(a) # error
}

Public()
```
## Function call
Define the add function.
```
fun add(x, y: 1) {
    x + y
}
```
For normal function calls, write as follows:
```
add(2, 3) # 5
```
Because there is a default argument, even one argument can be called.
```
add(2) # 3
```
You can also specify arguments by name when calling functions.
```
fun sum(a, b:1, c:2) {
    a + b + c
}
sum(1) # 4
sum(1, 2) # 5
sum(1, c: 3) # 5
sum(c: 3, b: 2, 0) # 5
```