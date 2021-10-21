# 合并K个升序链表

给你一个链表数组，每个链表都已经按升序排列。
请你将所有链表合并到一个升序链表中，返回合并后的链表。

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode[]} lists
 * @return {ListNode}
 */
var mergeKLists = function(lists) {
    let header = new ListNode();
    getNext(header, lists);
    return header.next;
    function getNext(header, arr) {
        arr = arr.filter(item => item)
        if (!arr.length) {
            return;
        }
        let resNode = arr[0], flag = 0;
        arr.forEach((item, index) => {
            if(item.val < resNode.val) {
                resNode = item;
                flag = index;
            }
        });
        header.next=resNode;
        arr[flag] = arr[flag].next;
        getNext(resNode, arr);
    }
};
// 哈哈，未通过
// 下方可行
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode[]} lists
 * @return {ListNode}
 */
var mergeKLists = function(lists) {
    if (!lists.length) {
        return null
    }
    if (lists.length < 2) {
        return lists[0]
    }
    let res = lists.pop();
    while (lists.length) {
        res = mergeTwo(res, lists.pop())
    }
    return res;
    function mergeTwo(header1, header2) {
        let newHeader = new ListNode(), curHeader = new ListNode();
        newHeader.next = curHeader;
        while(header1 && header2){
            if (header2.val > header1.val) {
                curHeader.next = header1;
                curHeader = curHeader.next;
                header1 = header1.next;
            } else {
                curHeader.next = header2;
                curHeader = curHeader.next;
                header2 = header2.next;
            }
        }
        if (header1) {
            curHeader.next = header1;
        }
        if (header2) {
            curHeader.next = header2;
        }
        return newHeader.next.next;
    }
};
```
## 2021-10-21
