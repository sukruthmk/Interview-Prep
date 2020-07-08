# Remove Duplicates from Sorted List

Given a sorted linked list, delete all duplicates such that each element appear only *once*.

**Example 1:**

```
Input: 1->1->2
Output: 1->2
```

**Example 2:**

```
Input: 1->1->2->3->3
Output: 1->2->3
```



### Leetcode

https://leetcode.com/problems/remove-duplicates-from-sorted-list/



### Optimal Solution

#### Approach 1 - Hashmap

Time Complexity: O(n)

Space Complexity: O(n)

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
var deleteDuplicates = function(head) {
    const set = new Set();
    let curr = head;
    let prev = null;
    
    while(curr != null) {
        const val = curr.val;
        
        // delete the node if the value is already in the set
        // since the list is sorted it should be in one order
        if(set.has(val)) {
            deleteNode(curr, prev);
        } else {
            prev = curr;
        }
        
        set.add(val);
        curr = curr.next;
    }
    
    return head;
};

const deleteNode = (head, prev) => {
    const next = head.next;
    prev.next = next;
}
```



#### Approach 2 - Straight forward

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
var deleteDuplicates = function(head) {
    let curr = head;
    
    while(curr != null && curr.next != null) {
        if(curr.val === curr.next.val) {
            curr.next = curr.next.next;
        } else {
            curr = curr.next;
        }
    }
    
    return head;
};
```

