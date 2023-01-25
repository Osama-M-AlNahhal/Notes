## Data Types:

### Primative Types:

#### Numbers

```
- JavaScript uses 8-byte (64-bit) floating point format for all numbers.
- array indexing and bit-wise operations use 4-byte (32-bit) integers.
- Number Systems:  
  Hexadecimal: 0x.. or 0X..
  Octal: 0.. (but not very supported therefor shouldn't be used).
```

```
Operations are defined as functions of the `Math` object.
```

**Overflow, Underflow and Division by zero:**
| Type        | info         | return                       |
| ----------- | ------------ | ---------------------------- |
| Overflow    | NOT an error | Infinity or -Infinity        |
| Underflow   | NOT an error | 0 or -0 (0 === -0)           |
| Divide by 0 |              | x/0 => Infinity or -Infinity |
|      Divide by 0       |              | 0/0 => NaN                             |

```
Math.sqr(-x), Math.exp(object) => NaN
```

Checking for NaN:
```
 var == NaN [wrong]
 var != var [correct: unique property, NaN != NaN]
 isNaN(var) [correct]
```

Rounding errors:

```javascript
0.3 - 0.2 !== 0.2 - 0.1
```
```
Solution: Round up the values and use integers (ex: 12.34 seconds = 1234 milliseconds)
```

---

#### Strings

```
- Strings are Immutable, ordered sequence of 2-byte (16-bit) characters.
- String's length = number of 16-bit values inside it.
- Javascript doesn't have a character class (Character = String w/ length=1).
- Javascript uses UTF-16 encoding
- some characters like `PI` use two 16-bit values to be represented (string.length == 2, but only 1 character inside it).
- strings are treated as Read-only arrays  
  "abc"[0] == "a"
  string[string.length - 1] //last char
```

---

#### boolean

|               |                                 |
| ------------- | ------------------------------- |
| Falsy values  | undefined, null, 0, -0, NaN, "" |
| Truthy values | everything else                 |

---

#### null

```
null = special object representing absence of value
```

```javascript
typeof null //returns `object`
```

#### undefined

```
undefined = predefined global variable.
```

```javascript
typeof undefined //returns `undefined`
```


```javascript
null == undefined //True
null === undefined //false

null[] //TypeError
undefined[] //TypeError

null.function //TypeError
undefined.function //TypeError
```

---

## Object Types

### Objects

### arrays

### functions

### dates

```javascript
let now = new Date(); //current time in milliseconds
now.toString();
now.getMonth();
now.getDay();
```

### RegExp

