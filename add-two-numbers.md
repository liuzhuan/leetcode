# 2. [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/#/description)

## Description

You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Input:** (2 -> 4 -> 3) + (5 -> 6 -> 4)

**Output:** 7 -> 0 -> 8

## My Solution

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var addTwoNumbers = function(l1, l2) {
    var head = null;
    var lastnode = null;
    var carry = 0;
    
    while (l1 || l2) {
        var a = l1 ? l1.val : 0;
        var b = l2 ? l2.val : 0;
        var sum = a + b + carry;
        carry = parseInt(sum / 10);
        var node = new ListNode(sum % 10);
    
        if (lastnode === null) {
            head = node;
        } else {
            lastnode.next = node;
        }
    
        lastnode = node;
      
        l1 && (l1 = l1.next);
        l2 && (l2 = l2.next);
    }
  
    if (carry > 0) {
        lastnode.next = new ListNode(carry);
    }
  
    return head;
};
```

Runtime: **195 ms**

## Sample 185 ms submission

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var addTwoNumbers = function(l1, l2) {
    if (l1 == null && l2 != null) {
        l1 = new ListNode(0);
    } else if (l2 == null && l1 != null) {
        l2 = new ListNode(0);
    }
        
    var addNum = l1.val + l2.val;
    if (addNum > 9) {
        addNum = addNum - 10;
        if (l1.next == null)
            l1.next = new ListNode(0);
        l1.next.val++;
    }
    var newNode = new ListNode(addNum);
    if (l1.next == null && l2.next == null) {
        newNode.next = null;
        return newNode;
    } else {
        newNode.next = addTwoNumbers(l1.next, l2.next);
        return newNode;
    }
};
```

> 链表问题适用于递归算法