# Special Cases:
1. empty list : new node becomes *head* and *tail*.
2. 


---

# Walking

**Finding 2nd to last element (penultimate)**
```java
public Node<E> penultimate( ) {
   Node<E> walk = head;
   while (walk.next != tail) {
	   walk = walk.next;
	}
   return walk;
}
```


---

# Reversing
*using recursion*

```java
Node reverse(Node head) {
	//special case : linked list is empty
	if(head == null){return head;}
	
	//base case
	if(head.next == null) {
		return head;
	}
	
	Node newHeadNode = reverse(head.next);
	
	// change references for middle chain
	head.next.next = head;
	head.next = null;
	
	// send back new head node in every recursion
	return newHeadNode;	
}

void reverse(SinglyLinkedList L) {
	//special case : empty list / only 1 element
	if(L.getSize() < 2) {return;}
	
	Node temp = L.removeFirst();
	reverse(L);
	L.addLast(temp);
}
```