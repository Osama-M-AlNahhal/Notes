# Linear Search
*time complexity: o(n), space complexity: o(1)*

```java
int linearSearch(int[] list, int key) {
	for (int i = 0; i < list.length; i++) {
		if (key == list[i])
		return i;
	}
	return -1;
}
```


---

# Binary Search
*time complexity: o(log(n)), space complexity: o(1)*

- Array must already be sorted.

```java
int binarySearch(int[] list, int key) {
	int low = 0;
	int high = list.length - 1;
	int mid = low + (high - low) / 2;

	while (low <= high) {
		if (list[mid] == key) {
			return mid;
		} else if (list[mid] > key) {
			high = mid - 1;
			continue;
		} else {
			low = mid + 1;
		}
	}
	//insertion point
	return -(low + 1) ;
}
```

```java
java.util.Arrays.binarySearch(list, key); //returns address or (- insertion_point )
```

---

