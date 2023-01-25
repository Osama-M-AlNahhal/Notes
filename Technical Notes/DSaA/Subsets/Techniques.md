# Using binary string
*0 means element isn't in the set, 1 means element is in the set*

**Problem :** generating sets is costly, because of multiple changes to the set from one subset to another.
**Solution :** use gray code


## Binary reflected Gray Code

> 	If (n=1) {
> 		make list L of two bit strings 0 and 1
> 	} else {
> 		generate recursively list L1 of bit strings of length n-1
> 		copy list L1 in reverse order to get list L2
> 		add 0 in front of each bit string in list L1
> 		add 1 in front of each bit string in list L2
> 		append L2 to L1 to get L
> 	}
> 	return L


---



# 3 mutually-exclusive Subsets of a string
```java
int Solution(String s) {
	int a = 1;
	int b= 1;
	int c= s.length() - 2;
	int numOfWays = 0;
	
	String x, y, z;
	while (a < s.length() - 2) {
		while (b < s.length() - a - 1) {
			//if (a+b, b+c, c+a are different) then { numOfWays++ }
			//x = a+b
			x = s.substring(0,a-1).concat(s.substring(a,c-1));
			//y = b+c
			y = s.substring(a,c-1).concat(s.substring(c));
			//z = c+a
			z = s.substring(c).concat(s.substring(0,a-1));
			
			if (x.equals(y) || x.equals(z) || y.equals(z)) {
				//invalid, do nothing.
			} else {
				numOfWays++;
			}
			b++;
			c–-;
		}
		a++;
		b = 1;
		c = s.length() - a - 1;
	}
	return numOfWays++;
}
```