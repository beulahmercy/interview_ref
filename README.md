# Interview Reference on Questions and Programs
Take a glance at these links and content for Java / spring / hibernate interview preparations


### Merge Two Linked List

##### Iterative and recursive

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        
// recursive approach
//         if(list1 == null)
//             return list2;
//         if(list2 == null)
//             return list1;
        
//         if(list1.val < list2.val){
//             list1.next = mergeTwoLists(list1.next, list2);
//             return list1;
//         } else {
//             list2.next = mergeTwoLists(list1, list2.next);
//             return list2;
//         }

// iterative approach
        if(list1 == null)
            return list2;
        if(list2 == null)
            return list1;
        
        if(list1.val < list2.val)
            return mergeUtil(list1, list2);
        else 
            return mergeUtil(list2, list1);
        
    }
    
    static ListNode mergeUtil(ListNode h1, ListNode h2) {
        if(h1.next == null){
            h1.next = h2;
            return h1;
        }
        
        ListNode curr1 = h1;
        ListNode next1 = h1.next;
        ListNode curr2 = h2;
        ListNode next2 = h2.next;
        
        while(next1 != null && curr2 != null) {
            if(curr2.val >= curr1.val && curr2.val <= next1.val){
                next2 = curr2.next;
                curr1.next = curr2;
                curr2.next = next1;
                
                curr1 = curr2;
                curr2 = next2;
                
            } else {
                if(next1.next != null) {
                
                next1 = next1.next;
                curr1 = curr1.next;
                } else {
                                next1.next = curr2;
                                return h1;
                            }
                   }
        }
        return h1;
    }
}
```


#### Reverse Linked List

```java
public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode current = head;
        ListNode next = null;
        while (current != null) {
            next = current.next;
            current.next = prev;
            prev = current;
            current = next;
        }
        head = prev;
        return head;
    }
```
	
#### Find Loop in linked list

```java
	void detectLoop()
    {
        Node slow_p = head, fast_p = head;
        int flag = 0;
        while (slow_p != null && fast_p != null
               && fast_p.next != null) {
            slow_p = slow_p.next;
            fast_p = fast_p.next.next;
            if (slow_p == fast_p) {
                flag = 1;
                break;
            }
        }
        if (flag == 1)
            System.out.println("Loop found");
        else
            System.out.println("Loop not found");
    }
```

	
#### Delete mid of linked list (Floyd’s Cycle-Finding Algorithm)

```java
	static Node deleteMid(Node head)
    {
        // Base cases
        if (head == null)
            return null;
        if (head.next == null) {
            return null;
        }
 
        // Initialize slow and fast pointers
        // to reach middle of linked list
        Node slow_ptr = head;
        Node fast_ptr = head;
 
        // Find the middle and previous of middle.
        Node prev = null;
 
        // To store previous of slow_ptr
        while (fast_ptr != null
&& fast_ptr.next != null) {
            fast_ptr = fast_ptr.next.next;
            prev = slow_ptr;
            slow_ptr = slow_ptr.next;
        }
        // Delete the middle node
        prev.next = slow_ptr.next;
 
        return head;
    }
```

#### Find no of occurances of a char in string methods
https://java2blog.com/count-number-occurrences-character-string-java/

#### Implement LRU cache
https://takeuforward.org/data-structure/implement-lru-cache/

#### Dead lock in java
https://www.youtube.com/watch?v=82IYrX0qdWs

#### Advanced Java, Spring, hibernate
https://jobs4times.com/

#### Algorithms

1. Kadane’s Algorithm : Maximum Subarray Sum or Product in an Array
2. Floyd’s Cycle-Finding Algorithm for finding loop and mid element in the linked list
