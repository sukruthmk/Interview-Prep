# Sort List

Sort a linked list in *O*(*n* log *n*) time using constant space complexity.

**Example 1:**

```
Input: 4->2->1->3
Output: 1->2->3->4
```

**Example 2:**

```
Input: -1->5->3->4->0
Output: -1->0->3->4->5
```



### Leetcode

https://leetcode.com/problems/sort-list/



### Optimal Solution

The solution is based on Merge Sort

1. Recursively split the linked list into two parts. i.e left and right part using divide and conquer method.
2. Sort the left and right part
3. Merge recursively



Time Complexity: O(nlogn)

Space Complexity: O(nlogn)

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
var sortList = function(head) {
  if(head == null || head.next == null) {
    return head;
  }
  
  let leftTail = head;
  let slow = head;
  let fast = head;
  
  // find the mid point and split it
  while(fast != null && fast.next != null) {
    leftTail = slow;
    slow = slow.next;
    fast = fast.next.next;
  }
  
  leftTail.next = null;
  
  const left = sortList(head);
  const right = sortList(slow);
  
  return merge(left, right);
};

const merge = (left, right) => {
  const head = new ListNode();
  let curr = head;
  
  while(left != null && right != null) {
    if(left.val < right.val) {
      curr.next = left;
      left = left.next;
    } else {
      curr.next = right;
      right = right.next;
    }  
    curr = curr.next;
  }
  
  if(left != null) {
    curr.next = left;
  }
  
  if(right != null) {
    curr.next = right;
  }
  
  return head.next;
}
```



### Explanation

https://www.youtube.com/watch?v=pNTc1bM1z-4