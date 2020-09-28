# Palindrome Linked List

Given a singly linked list, determine if it is a palindrome.

**Example 1:**

```
Input: 1->2
Output: false
```

**Example 2:**

```
Input: 1->2->2->1
Output: true
```

**Follow up:**
Could you do it in O(n) time and O(1) space?



### Leetcode

https://leetcode.com/problems/palindrome-linked-list/



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
 * @return {boolean}
 */
var isPalindrome = function(head) {
    // empty value is also a palindrome
    if (head === null) return true;
    
    let fast = head;
    let slow = head;
    
    // 1. find the mid of the list using fast and slow pointers
    while(fast.next != null && fast.next.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }
    
    // 2. split the list into two parts
    let list1 = head;
    let list2 = slow.next;
    slow.next = null;
    
    // 3. reverse the second list 
    list2 = reverseList(list2, null);
    
    // 4. compare both lists and check if the values are equal
    return compareLists(list1, list2);
};

const reverseList = (head, prev) => {
    if(head === null) {
        return prev;
    }
    const next = head.next;
    head.next = prev;
    return reverseList(next, head);
}

const compareLists = (list1, list2) => {
    let curr1 = list1;
    let curr2 = list2;
    
    while(curr1 != null && curr2 != null) {
        if(curr1.val != curr2.val) {
            return false;
        }
        curr1 = curr1.next;
        curr2 = curr2.next;
    }
    
    return true;
}
```



### Explanation

https://www.youtube.com/watch?v=bOGh_3MTrdE