##  **160.<br/>[Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/)<br/>[相交链表](https://leetcode-cn.com/problems/intersection-of-two-linked-lists/)**

## **Topics**
* Linked List

## **Idea**

 要判斷兩條鏈表是否於某一節點交匯後集結，在鏈表節點數相同的前提下，僅需藉由對應指針是否在遍歷途中有同時指向某一節點即可，若鏈表節點數不同，則需把對應的指針可以走的總節點數拉到同一水平，也就是當Ａ指針和B指針在路徑切換後，若鏈表有交匯點，在遍歷途中必會同時指向某一節點，若無交匯點，則在全部節點遍歷完後，會同時指向空節點。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/160_intersection-of-two-linked-lists.md#go) | O(n) | O(1) | 24 ms | 7.8 MB | https://drive.google.com/file/d/1xzm1lQVi-rDOh3m13gYGEcGmM-UBnqZz/view?usp=sharing |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/160_intersection-of-two-linked-lists.md#c) | O(n) | O(1) | 116 ms | 36.1 MB | https://drive.google.com/file/d/130p99qTxd_61B0DW47od8h80cbbT7DyE/view?usp=sharing |

## **Go**
```Go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func getIntersectionNode(headA, headB *ListNode) *ListNode {
    if headA == nil || headB == nil {
        return nil
    }
    
    pA, pB := headA, headB
    
    for pA != pB {
        if pA != nil {
            pA = pA.Next
        } else {
            pA = headB
        }
        if pB != nil {
            pB = pB.Next
        } else {
            pB = headA
        }
    }
    
    return pA
}
```

## **C#**
```csharp
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public int val;
 *     public ListNode next;
 *     public ListNode(int x) { val = x; }
 * }
 */
public class Solution 
{
    public ListNode GetIntersectionNode(ListNode headA, ListNode headB) 
    {
        if (headA == null || headB == null) return null;
        
        ListNode pA = headA, pB = headB;
        
        while (pA != pB)
        {
            pA = pA != null ? pA.next : headB;
            pB = pB != null ? pB.next : headA;
        }
        
        return pA;
    }
}
```