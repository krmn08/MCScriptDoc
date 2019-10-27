# Define
In MCScript, processing similar to C language define is possible by editing YAML.
Describe the definition in define.yml in the same position as config.yml.
```yaml
CON: "CONSTANT"
```
Defining a key and value replaces the string that matches the key in the script before execution.
```
Println("CON") # CONSTANT
```
In order to rewrite only the matching part of the script, it is necessary to enclose it with double quotations.
If you want to treat it like a constant:
```yaml
CON: "\"CONSTANT\""
```
```
Println(CON) # CONSTANT
```
You can also take an argument and embed it in a string.
```
INCREMENT(A): "A += 1"
CONCAT(S1, S2): "\"S1 S2\""
```
```
i = 0
Println(INCREMENT(i)) # 1
Println(CONCAT(hello, world)) # hello world
```
Spaces to the left and right of the argument are ignored.
```
Println(CONCAT( This is , my book.  )) # this is my book.
```