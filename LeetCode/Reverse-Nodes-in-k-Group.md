# Reverse Nodes in k-Group

Given a linked list, reverse the nodes of a linked list *k* at a time and return its modified list.

*k* is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of *k* then left-out nodes in the end should remain as it is.



**Example:**

Given this linked list: `1->2->3->4->5`

For *k* = 2, you should return: `2->1->4->3->5`

For *k* = 3, you should return: `3->2->1->4->5`

**Note:**

- Only constant extra memory is allowed.
- You may not alter the values in the list's nodes, only nodes itself may be changed.



### Leetcode

https://leetcode.com/problems/reverse-nodes-in-k-group/



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
 * @param {number} k
 * @return {ListNode}
 */
var reverseKGroup = function(head, k) {
    const tmp = new ListNode();
    tmp.next = head;
    let prev = tmp;
    let curr = head;
    let count = 1;
    while(curr != null) {
        if(count%k === 0) {
            const tail = curr;
            const next = tail.next;
            tail.next = null;
            const subLinkedListHead = prev.next;
            reverseLinkedList(subLinkedListHead, null);
            prev.next = tail;
            prev = subLinkedListHead;
            subLinkedListHead.next = next;
            curr = next;
        } else{
            curr = curr.next;
        }
        count++;
    }
    return tmp.next;
};

const reverseLinkedList = (head, prev) => {
    if(head === null) return head;
    const next = head.next;
    head.next = prev;
    return reverseLinkedList(next, head);
}
```



### Explanation

https://www.youtube.com/watch?v=acJEBQiFPoY