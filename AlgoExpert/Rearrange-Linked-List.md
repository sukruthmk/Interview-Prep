# Rearrange Linked List

Given a singly linked list *L*: *L*0→*L*1→…→*L**n*-1→*L*n,
reorder it to: *L*0→*L**n*→*L*1→*L**n*-1→*L*2→*L**n*-2→…

You may **not** modify the values in the list's nodes, only nodes itself may be changed.

**Example 1:**

```
Given 1->2->3->4, reorder it to 1->4->2->3.
```

**Example 2:**

```
Given 1->2->3->4->5, reorder it to 1->5->2->4->3.
```



### Leetcode

https://leetcode.com/problems/reorder-list/



### Optimal Solution

Time Complexity:

Space Complexity:

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
 * @return {void} Do not return anything, modify head in-place instead.
 */
var reorderList = function(head) {
    if(head === null || head.next === null) return;
    
    let l1 = head;
    let slow = head
    let fast = head;
    let prev = null;
    
    // find the middle node and break the linked list into two parts
    while(fast != null && fast.next != null) {
        prev = slow;
        slow = slow.next;
        fast = fast.next.next;
    }
    
    prev.next = null;
    
    // reverse the second part of the linkedlist
    let l2 = reverse(slow);
    
    // merge both the lists
    merge(l1, l2);
};

const reverse = (head) => {
    let prev = null;
    
    while(head != null) {
        const next = head.next;
        head.next = prev;
        prev = head;
        head = next;
    }
    
    return prev;
}

const merge = (l1, l2) => {
    while(l1 != null) {
        const l1_next = l1.next;
        const l2_next = l2.next;
        
        l1.next = l2
        
        if(l1_next === null) break;
        
        l2.next = l1_next;
        l1 = l1_next;
        l2 = l2_next;
    }
}
```

