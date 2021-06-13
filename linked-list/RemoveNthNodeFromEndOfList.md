# Remove Nth Node From End of List
`Easy`
### Problem
Given the head of a linked list, remove the nth node from the end of the list and return its head.

```
Example 1:
Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]

Example 2:
Input: head = [1], n = 1
Output: []

Example 3:
Input: head = [1,2], n = 1
Output: [1]
```

#### Constraints:

The number of nodes in the list is sz.
- 1 <= sz <= 30
- 0 <= Node.val <= 100
- 1 <= n <= sz

### Solution

Time O(n) | Space O(1)
```
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
class RemoveNthNodeFromEndOfList {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode backwardPointer = dummy;
        ListNode forwardPointer = dummy;
        
        int i = 1;
        while(i <= n+1){
            forwardPointer = forwardPointer.next;
            i++;
        }
        
        while(forwardPointer != null){
            backwardPointer = backwardPointer.next;
            forwardPointer = forwardPointer.next;
        }
        
        
        backwardPointer.next = backwardPointer.next.next;
        
        
        return dummy.next;
        
    }
}
```
