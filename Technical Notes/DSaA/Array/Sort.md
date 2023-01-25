# Selection Sort
*Time complexity: o(n^2), Space complexity: o(1), not stable*

```java
void selectionSort(int[] list) {
	for (int i = 0; i < list.length; i++) {
		int currentMin = i;
		int currentMinIndex = i;
		
		for (int j = i + 1 ; j < list.length ; j++j++) {
			if (currentMin > list[j]) {
				currentMin = list[j];
				currentMinIndex = j;
			}		
		}

		if (currentMinIndex != i ) {
			list[currentMinIndex] = list[i];
			list[i] = currentMin;
		}
	}
}
```

```java
java.util.Arrays.sort(list);
```

```java
java.util.Arrays.parallelSort(list);
```


---

