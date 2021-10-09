# 删除链表的倒数第 N 个结点

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
var removeNthFromEnd = function(head, n) {
    let localHeader = new ListNode();
    localHeader.next = head;
    let fast = head,slow=head;
    let num = n;// 获取被删的前一个
    while(num>0){
        fast = fast.next;
        num--;
    };
    if (fast === null) {// 删除的位于首位
        localHeader.next = localHeader.next.next;
        return localHeader.next;
    }
    while(fast.next){
        fast = fast.next;
        slow = slow.next;
    }
    if (localHeader.next === slow && !fast) {// 只有一个节点
        localHeader.next = null;
        return localHeader.next;
    }
    slow.next = slow.next.next;
    return localHeader.next;
};
```
## 2021-10-9
