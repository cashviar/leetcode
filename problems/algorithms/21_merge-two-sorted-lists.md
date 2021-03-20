## Merge Two Sorted Lists 合併兩個有序鏈表

### **Description**
https://leetcode.com/problems/merge-two-sorted-lists/

### **Topics**
* Linked List
* Recursion

### **Idea**

若l1或l2其一為空，則直接返回另一有序鏈表。若l1和l2皆不為空，則判斷何者當前的節點較小，將擁有較小節點的鏈表其指針往後移一位進行遞迴處理，並返回其值指定給待返回鏈表的下一個節點，持續遞迴直到其中一個鏈表其指針位移後指向空節點，結束遞迴。

### **Solutions**

#### Go 
```Go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func mergeTwoLists(l1 *ListNode, l2 *ListNode) *ListNode {
    if l1 == nil {
        return l2
    }
    if l2 == nil {
        return l1
    }

    if l1.Val < l2.Val {
        l1.Next = mergeTwoLists(l1.Next, l2)
	    return l1
    } else {
        l2.Next = mergeTwoLists(l1, l2.Next)
        return l2
    }
}
```
| Time Complexity | Space Complexity | Runtime | Memory Usage |
| :--: | :--: | :--: | :--: |
| O(n) | O(n) | 0 ms | 2.6 MB |

> 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。
> https://leetcode.com/submissions/detail/453626787/