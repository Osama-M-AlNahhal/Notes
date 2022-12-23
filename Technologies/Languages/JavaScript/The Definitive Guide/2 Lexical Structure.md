
## Optional Semicolons:

JavaScript will treat a line break as a semicolon if it can't parse the 2nd line as a continuation of the first line.

Exceptions: 

```
Line breaks after `continue`, `return` and `break` are always interpreted as a  semicolon
```

```
x  
++  
y
```
This is interpreted as `x; ++y;` Instead of `x++; y;`
