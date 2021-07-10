##  **141.<br/>[Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)<br/>[環形鏈表](https://leetcode-cn.com/problems/linked-list-cycle/)**

## **Topics**
* Linked List
* Two Pointers

## **Idea**

要判斷鍊表是否存在封閉迴圈可藉由設置兩個快慢指針進行判斷，快指針每次走兩步，慢指針每次走一步，則每次移動後兩者的距離以一步之差累計增加，若存在封閉迴圈則快慢指針在環形鏈表的移動過程中必然會有指向同一節點的時刻。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go]() | O(n) | O(1) | 8 ms | 4.4 MB | https://drive.google.com/file/d/1Hl4wSswXZJUCDqFgTVQybxmEEpPU0l31/view?usp=sharing |
| [C#]() | O(n) | O(1) | 96 ms | 27.1 MB | https://drive.google.com/file/d/1k4Xon8iEynLbZr2vT0tfLIcLfHRSK84k/view?usp=sharing |

## **Go**
```Go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */

func hasCycle(head *ListNode) bool {
    if head == nil || head.Next == nil {
        return false
    }

    slow, fast := head, head.Next

    for slow != fast {
        if fast == nil || fast.Next == nil {
            return false
        }
        slow = slow.Next
        fast = fast.Next.Next        
    }

    return true
}
```
## **C#**
```csharp
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public int val;
 *     public ListNode next;
 *     public ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution 
{
    public bool HasCycle(ListNode head) 
    {
        if (head == null || head.next == null) return false;
        
        var slow = head;
        var fast = head.next;
        
        while (slow != fast)
        {
            if (fast == null || fast.next == null) return false;
            slow = slow.next;
            fast = fast.next.next;
        }
        
        return true;
    }
}
```