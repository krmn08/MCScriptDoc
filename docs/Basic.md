# Basic
### Comments
In MCScript, comments can be written in two ways.
```
# line comment
/*
block comment
*/
```
* "#" Is treated as a comment until the end of the line.
* By enclosing it with "/ ** /", the entire range is treated as a comment.

### Variables
MCScript variable definition is simple.
```
a = 1
```
Variable declaration in MCScript is the same as assignment. An empty variable cannot be created.

### Constants
You can declare a constant by adding const before the variable declaration. A constant cannot be assigned a value again.
```
const a = 1
a = 0 # error
```
You can also override variables and constants in scope units using constant declarations.
```
a = 1
const b = 1
if true {
    const a = 2
    Println(a + b) # 3
    const b = 2
    Println(a + b) # 4
    const a = 3
    Println(a + b) # 5
}
Println(a + b) # 2
```
You can read a variable from another file by prefixing the variable declaration with public. This variable is treated as a constant.
```
public a = 1
```
### Multi Value
MCScript treats multiple values as multi-value by separating them with commas.
By using multi-value, you can assign to multiple variables at once.
```
a, b, c = 1, 2, 3 # 1, 2, 3
a, b, c += 1, 2, 3 # 2, 4, 6
```
If there are more left sides than right sides, the last value on the right side is assigned.
```
a, b, c = 1 # 1, 1, 1
a, b, c += 1 # 2, 2, 2
d, e, f = 1, 2 # 1, 2, 2
```
If the number on the right side is greater than the number on the left side, the value on the right side is truncated.
```
a, b = 1, 2, 3 # 1, 2
```
When ":=" is used, the right side is evaluated each time.
```
i = 0
a, b, c = i += 1 # 1, 1, 1
i = 0
d, e, f := i += 1 # 1, 2, 3
```
### Literals
MCScript basic type literals are no different from Java.
#### Integer
A numeric literal without a decimal point is treated as an Integer type, and when it ends with l or L, it is treated as a Long type. Underscores in numeric literals are ignored.
```
1 # Integer
1l # Long
```
#### Floating Point
A numeric literal with a decimal point is treated as a Double type, and if it ends with f or F, it is treated as a Float type.
In addition, it is handled as a double type by adding d or D to an integer literal.
```
1.0 # Double
1f # Float
1d # Double
```
Numeric literals also support binary, octal, and hexadecimal notation.
|Base|Notation|
|--|--|
|2|0b101|
|8|077|
|16|0xff|
#### Character
Characters are treated as Character type by enclosing them with single quotations. Escape sequences and character code input are also supported in the same way as Java.
```
'A'
'\n'
'\u0041' # A
```
#### String
Characters are handled as String type by enclosing them with double quotations. As with character literals, input with escape sequences and character codes is supported.
```
"AB"
"AB\n"
"A\u0042" # AB
```
Interpret line breaks in strings as they are.
```
"test
test"
/*
test
test
*/
```
##### String Templates
If you describe the variable name after $, you can embed the value in the string.
```
a = 1 + 1
Println("1 + 1 = $a") # 1 + 1 = 2
```
If you write an expression enclosed in {} after $, you can embed the result of the expression in the string.
```
Println("1 + 1 = ${1 + 1}") # 1 + 1 = 2
```
If \$ is followed by a variable or a character other than {, it is treated as a normal $.
```
Println("$100") # $100
```
#### List
Multiple expressions are separated by commas and enclosed in [] to be treated as a List type. There is no type restriction for MCScript lists.
```
[0, 1, "A", f()]
```
#### Map
Multiple pairs are separated by commas and enclosed in {} to be treated as Map type.
Like lists, there are no type restrictions.
```
{1:"a", b:"2", f1():f2()}
```