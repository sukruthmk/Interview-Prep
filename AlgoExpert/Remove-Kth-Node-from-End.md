# Remove Kth Node from End

Given a linked list, remove the *n*-th node from the end of list and return its head.

**Example:**

```
Given linked list: 1->2->3->4->5, and n = 2.

After removing the second node from the end, the linked list becomes 1->2->3->5.
```

**Note:**

Given *n* will always be valid.

**Follow up:**

Could you do this in one pass?



### Leetcode

https://leetcode.com/problems/remove-nth-node-from-end-of-list/



### Optimal Solution

**Two pass approach**

Time Complexity : O(n)

Space Complexity: O(1)

```js
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @param {number} n
 * @return {ListNode}
 */
var removeNthFromEnd = function(head, n) {
    let length = 0;
    let node = head;
    let dummy = new ListNode(0);
    dummy.next = head;
    
    // find the size/length of the linked list
    while(node != null) {
        length++;
        node = node.next;
    }
    
    // calculate the position of node to delete
    let diff = length - n;
    node = dummy;
    
    while(diff > 0) {
        diff--;
        node = node.next;
    }
    // remove the link from the node
    node.next = node.next.next;
    
    return dummy.next;
};
```

