# Special Test Cases:
1. empty array.
2. array of 1 element.
3. duplicated elements.
4. all elements are the same.
5. array is already sorted.
6. array is reverse sorted.

---

# Testing Equality
- `list1 == list2` and `list1.equals(list2)` compare the references only.

```java
java.util.Arrays.equals(list1, list2);
```

```java
java.util.Arrays.deepEquals(list1, list2); //for nested arrays
```


---

# Cloning
***Shallow Copy***
```java
data.clone(); //copies references (bad)
```
- 