## **21.<br/>[Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)<br/>[合併兩個有序鏈表](https://leetcode-cn.com/problems/merge-two-sorted-lists/)**

## **Topics**
* Linked List
* Recursion

## **Idea**
若參數l1或l2其一為空，則直接返回不為空的鏈表參數。

假如參數l1和l2皆不為空，則判斷何者當前的節點較小，將擁有較小節點的鏈表參數其指針往後移一位作為遞迴參數，並返回其值指定給待返回鏈表的下一個節點，直到其中一個鏈表參數其指針位移後指向空節點，即可得合併後的有序鍊表。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/21_merge-two-sorted-lists.md#go) | O(n) | O(n) | 0 ms | 2.6 MB | https://drive.google.com/file/d/1LqRXr65NValtpNOcd2Nirt2RbbYNAv-u/view?usp=sharing |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/21_merge-two-sorted-lists.md#c) | O(n) | O(n) | 92 ms | 26.6 MB | https://drive.google.com/file/d/1ZNCDwmmrwopEwh9JHob-V1NJirx1YcCd/view?usp=sharing |

## **Go** 
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
## **C#**
```csharp
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public int val;
 *     public ListNode next;
 *     public ListNode(int val=0, ListNode next=null) {
 *         this.val = val;
 *         this.next = next;
 *     }
 * }
 */
public class Solution 
{
    public ListNode MergeTwoLists(ListNode l1, ListNode l2) 
    {
        if (l1 == null) 
        {
            return l2;
        }
        if (l2 == null)
        {
            return l1;
        }
        
        if (l1.val < l2.val)
        {
            l1.next = MergeTwoLists(l1.next, l2);
            return l1;
        } 
        else
        {
            l2.next = MergeTwoLists(l1, l2.next);
            return l2;
        }
    }
}
```