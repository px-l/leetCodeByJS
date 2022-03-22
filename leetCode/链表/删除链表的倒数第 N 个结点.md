# 19. 删除链表的倒数第 N 个结点
给你一个链表，删除链表的倒数第 n 个结点，并且返回链表的头结点。
```javascript
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
 //快慢指针
var removeNthFromEnd = function(head, n) {
    let localHeader = new ListNode();
    localHeader.next = head;
    cur = localHeader;
    let fast = cur,slow=cur,i=0;
    while(i<n){
        fast = fast.next;
        i++;
    }
    while(fast.next){
        fast = fast.next;
        slow = slow.next;
    }
    slow.next = slow.next.next;
    return localHeader.next;
};
```
## 2022-3-22
