# Swap Nodes in Pairs

Given a linked list, swap every two adjacent nodes and return its head.

You may **not** modify the values in the list's nodes, only nodes itself may be changed.

 

**Example:**

```
Given 1->2->3->4, you should return the list as 2->1->4->3.
```



### Leetcode

https://leetcode.com/problems/swap-nodes-in-pairs/



### Optimal Solution

Time Complexity: O(n)

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
 * @return {ListNode}
 */
var swapPairs = function(head) {
    // create a temporary new head
    let newHead = new ListNode();
    let curr = head;
    newHead.next = curr;
    let prev = newHead;
    
    while(curr !=null && curr.next != null) {
        const next = curr.next;
        const adjacent = next.next;
        curr.next = adjacent;
        prev.next = next;
        next.next = curr;
        prev = curr;
        curr = curr.next;
    }
    
    return newHead.next;
};
```
