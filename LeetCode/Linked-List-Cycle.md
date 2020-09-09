# Linked List Cycle

Given a linked list, determine if it has a cycle in it.

To represent a cycle in the given linked list, we use an integer `pos` which represents the position (0-indexed) in the linked list where the tail connects to. If `pos == -1`, then there is no cycle in the linked list.

**Follow up:**

Can you solve it using *O(1)* (i.e. constant) memory?

 

**Example 1:**

![img](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)

```
Input: head = [3,2,0,-4], pos = 1
Output: true
Explanation: There is a cycle in the linked list, where tail connects to the second node.
```

**Example 2:**

![img](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png)

```
Input: head = [1,2], pos = 0
Output: true
Explanation: There is a cycle in the linked list, where tail connects to the first node.
```

**Example 3:**

![img](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test3.png)

```
Input: head = [1], pos = -1
Output: false
Explanation: There is no cycle in the linked list.
```

 

**Constraints:**

- The number of the nodes in the list is in the range `[0, 104]`.
- `-105 <= Node.val <= 105`
- `pos` is `-1` or a **valid index** in the linked-list.



### Leetcode

https://leetcode.com/problems/linked-list-cycle/



### Optimal Solution

##### Approach 1 - HashMap

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */

/**
 * @param {ListNode} head
 * @return {boolean}
 */
var hasCycle = function(head) {
  const set = new Set();
  
  let curr = head;
  while(curr != null) {
    if(set.has(curr)) return true;
    set.add(curr);
    curr = curr.next;
  }
  
  return false;
};
```



##### Approach 2 - Two pointer

Time Complexity: O(n)

Space Complexity: O(1)

```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */

/**
 * @param {ListNode} head
 * @return {boolean}
 */
var hasCycle = function(head) {
  let slow = head;
  let fast = head;
  
  while(slow != null && fast!=null && fast.next != null) {
    slow = slow.next;
    fast = fast.next.next;
    if(slow === fast) {
      return true;
    }
  }
  
  return false;
};
```

