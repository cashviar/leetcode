##  **234.<br/>[Palindrome Linked List](https://leetcode.com/problems/invert-binary-tree/)<br/>[回文鏈表](https://leetcode-cn.com/problems/reverse-linked-list/)**
  
## **Topics**
* Linked List
* Two Pointers

## **Idea**
首先使用兩倍速的快慢指針切出原鏈表的後半段，然後反轉此後半段鏈表的節點（詳見：[206.反轉鏈表](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/206_reverse-linked-list.md#206reverse-linked-list%E5%8F%8D%E8%BD%89%E9%8F%88%E8%A1%A8)），再來以反轉後的後半段鏈表為主線，對照跟前半段的節點是否皆相同，即可判斷是否為回文鏈表。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/234_palindrome-linked-list.md#go) | O(n) | O(1) | 140 ms | 11.4 MB | https://drive.google.com/file/d/1x_4u8dwIQ_5iHmjCuv3ad-4vEz3UEmoF/view?usp=sharing |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/234_palindrome-linked-list.md#c) | O(n) | O(1) | 256 ms | 46.2 MB | https://drive.google.com/file/d/1lePkKOWUU_fL7fAo27XXt41XW6YhQMZn/view?usp=sharing |

## **Go**
```Go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func isPalindrome(head *ListNode) bool {
    if head == nil {
        return true
    }
    
    reversedSecondHalf := reverseList(getSecondHalf(head))
    
    for reversedSecondHalf != nil {
        if head.Val != reversedSecondHalf.Val {
            return false
        }
        head = head.Next
        reversedSecondHalf = reversedSecondHalf.Next
    }    
    
    return true
}

func getSecondHalf (head *ListNode) *ListNode {
    fast, slow := head, head
    
    for fast.Next != nil && fast.Next.Next != nil {
        fast = fast.Next.Next
        slow = slow.Next
    }
    
    return slow.Next
}

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
    public bool IsPalindrome(ListNode head) 
    {
        if (head == null) return true;
        
        ListNode reversedSecondHalf = ReverseList(GetSecondHalf(head));
        
        while (reversedSecondHalf != null)
        {
            if (head.val != reversedSecondHalf.val) return false;
            head = head.next;
            reversedSecondHalf = reversedSecondHalf.next;            
        }
        
        return true;
    }
    
    private ListNode GetSecondHalf(ListNode head)
    {
        ListNode fast = head, slow = head;
        
        while (fast.next != null && fast.next.next != null)
        {
            fast = fast.next.next;
            slow = slow.next;            
        }
        
        return slow.next;
    }
    
    private ListNode ReverseList(ListNode head) 
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