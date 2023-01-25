# Variable-sized input to function
```java
int method1(int... inputs) {
	//do something
	return 1;
}
```

---

# Integer to Binary
*int -> binary string -> char array*

```java
int a = 5;
String b = Integer.toBinaryString(a); //"101"
char[] c = b.toCharArray(); //'1','0','1'
int digit1 = Integer.parseInt(String.valueOf(c[0]));
```


---

# Get type of object
```java
something.getClass().getSimpleName(); //returns Integer, String, etc (as a string);
```
