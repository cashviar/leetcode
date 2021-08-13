##  **206.<br/>[Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)<br/>[反轉鏈表](https://leetcode-cn.com/problems/reverse-linked-list/)**
  
## **Topics**
* Linked List

## **Idea**
借由在原鏈表移動當前指針作為反轉移動的主線，並設一個變數暫存當前節點的下一個節點，然後將此下一個節點設定為反轉鏈表的前一個節點，至於當前節點則代表反轉鏈表的下一個節點，最後將當前指針指向暫存的節點，相當於在原鏈表移動到下一個節點，重複此節點設定循環，直到當前指針指向空節點，即可得反轉後的鏈表。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/206_reverse-linked-list.md#go) | O(n) | O(1) | 0 ms | 2.6 MB | https://drive.google.com/file/d/1-PYzZqjvgGgy5DSEMFw17wZaFCcaWSy9/view?usp=sharing |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/206_reverse-linked-list.md#c) | O(n) | O(1) | 88 ms | 25.1 MB | https://drive.google.com/file/d/1Oe7l5nu_hQR10MxVKH9rADa9BRgAeCKN/view?usp=sharing |

## **Go**
```Go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func reverseList(head *ListNode) *ListNode {
    var prev *ListNode
    current, tmp := head, head

    for current != nil {
        tmp = current.Next
        current.Next = prev
        prev = current
        current = tmp
    }
    
    return prev
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
    public ListNode ReverseList(ListNode head) 
    {
        ListNode prev = null, current = head, tmp = head;
        
        while (current != null)
        {
            tmp = current.next;
            current.next = prev;
            prev = current;
            current = tmp;
        }
        
        return prev;
    }
}
```