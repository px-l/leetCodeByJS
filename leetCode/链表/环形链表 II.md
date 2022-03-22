# 142. 环形链表 II

给定一个链表的头节点  head ，返回链表开始入环的第一个节点。 如果链表无环，则返回 null。

如果链表中有某个节点，可以通过连续跟踪 next 指针再次到达，则链表中存在环。 为了表示给定链表中的环，评测系统内部使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。如果 pos 是 -1，则在该链表中没有环。注意：pos 不作为参数进行传递，仅仅是为了标识链表的实际情况。

不允许修改 链表。

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */

/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var detectCycle = function(head) {
    // 快慢指针，当快指针追上满指针时，一定位于环内；假设环外长度为p，环起点到相交位置为n1，剩余长度为n2;
    //此时快指针跑了p+n圈+n1，慢指针跑了p+n1
    // 快指针与慢指针之间差一步。此时继续往后走，慢指针前进一步，快指针前进两步，两者相遇。
    // 快指针与慢指针之间差两步。此时唏嘘往后走，慢指针前进一步，快指针前进两步，两者之间相差一步，转化为第一种情况。
    // 快指针与慢指针之间差N步。此时继续往后走，慢指针前进一步，快指针前进两步，两者之间相差(N+1-2)-> N-1步。
    // 在环内最多相差n步，在慢指针走完n之前一定会相遇；
    // p = n圈-n1，所以当相遇时，慢指针回到起点，快指针从n1出发，同时以+1的步长前进，相遇的地方及环的起点；
    let slow = head, fast = head, isR = false;
    while(fast && fast.next && fast.next.next){
        fast = fast.next.next;
        slow = slow.next;
        if (slow === fast) {
            fast = null;
            isR = true;
        }
    }
    if (isR) {
        fast = slow;
        slow = head;
        while (fast !== slow) {
            fast = fast.next;
            slow = slow.next;
        }
        return fast;
    } else {
        return null;
    }
};
```
## 2022-3-22
