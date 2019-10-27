# Tutorial

This chapter explains the basics of MCScript.

MCScript syntax is based on Java and incorporates the latest language elements.
Some plug-in development syntax has been added, but it is basically a simplified Java syntax

Java requires a semicolon at the end of the sentence, but MCScript does not need it because it is automatically inserted at the end of the line.
Due to the above specifications, some restrictions may apply to the script format. We try not to lower the readability at the minimum, but please follow the format of this document  because there are cases where the description method that can be done in Java is not possible.

Example
```
if condition
{
    # error
}

if condition {
    # pass
}

sb = StringBuilder()

# error
sb.append("a")
    .append("b")
    .append("c")

# pass
sb.append("a")\
    .append("b")\
    .append("c")

sb.append("a").
    append("b").
    append("c")

sb.append(
    "a"
).append(
    "b"
).append("c")

# error
a = "a"
    + "b"

# pass
a = "a" +
    "b"
```

Keywords
```
runnable    const       import      null        instanceof
is          isnot       in          notin       fun
command     true        false       while       for
break       continue    switch      default     if
elif        else        return      vararg      throw
try         catch       defer       boolean     char
byte        short       int         long        float
double
```