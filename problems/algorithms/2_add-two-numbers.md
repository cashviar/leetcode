##  **2.<br/>[Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)<br/>[兩數相加](https://leetcode-cn.com/problems/add-two-numbers/)**
  
## **Topics**
* Linked List
* Math
* Recursion

## **Idea**
設計一個遞迴函數，除了原來的鏈表參數以外，新增一個計數器，若鏈表節點不為空，便將其值累加至計數器，並在新增至鏈表前以十進制轉成個位數，至於要進位的數值則當作新的遞迴參數，併到下一個節點，待所有鏈表皆訪問至空節點且計數器為零時結束遞迴。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/2_add-two-numbers.md#go) | O(n) | O(n) | 0 ms | 4.9 MB | https://drive.google.com/file/d/1RvAl3evA5NYSmVrGOdZSmNk0B2MEcUKA/view?usp=sharing |
| [Java](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/2_add-two-numbers.md#java) | O(n) | O(n) | 1 ms | 42.5 MB | https://drive.google.com/file/d/1n5TUy0QHN4ut-gEkAbgWnxygDee4iA_m/view?usp=sharing |
| [JS](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/2_add-two-numbers.md#js) | O(n) | O(n) | 80 ms | 46.6 MB | https://drive.google.com/file/d/1vUs5Umzg2I5jxPgDTnSnA739ywVB4z29/view?usp=sharing |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/2_add-two-numbers.md#c) | O(n) | O(n) | 100 ms | 28.5 MB | https://drive.google.com/file/d/1nRdFrUYRTFsKRBrY6MH5hBmBY9rLGSad/view?usp=sharing |

## **Go**
```Go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func addTwoNumbers(l1 *ListNode, l2 *ListNode) *ListNode {
    return addUp(l1, l2, 0)
}

func addUp(l1 *ListNode, l2 *ListNode, tot int) *ListNode{
    if l1 == nil && l2 == nil && tot == 0 {
        return nil
    }
    
    if l1 != nil {
        tot += l1.Val
        l1 = l1.Next
    }
    
    if l2 != nil {
        tot += l2.Val
        l2 = l2.Next
    }

    return &ListNode{tot%10, addUp(l1, l2, tot/10)}
}
```

## Java
```Java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        return addUp(l1, l2, 0);
    }
    
    private ListNode addUp(ListNode l1, ListNode l2, int tot) {
        if (l1 == null && l2 == null && tot == 0) {
            return null;
        }
        
        if (l1 != null) {
            tot += l1.val;
            l1 = l1.next;
        }
        
        if (l2 != null) {
            tot += l2.val;
            l2 = l2.next;
        }
        
        return new ListNode(tot%10, addUp(l1, l2, tot/10));
    }
}
```

## JS
```js
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var addTwoNumbers = function(l1, l2) {
    return addUp(l1, l2, 0);
    
    function addUp(l1, l2, tot) {
        if (l1 == null && l2 == null && tot == 0)  {
            return null;
        }
        
        if (l1 != null) {
            tot += l1.val;
            l1 = l1.next;
        }
        
        if (l2 != null) {
            tot += l2.val;
            l2 = l2.next;
        }
        
        return new ListNode(tot%10, addUp(l1, l2, Math.floor(tot/10)));
    };
};
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
    public ListNode AddTwoNumbers(ListNode l1, ListNode l2) 
    {
        return AddUp(l1, l2, 0);
    }
    
    private ListNode AddUp(ListNode l1, ListNode l2, int tot)
    {
        if (l1 == null && l2 == null && tot == 0) return null;
        
        if (l1 != null)
        {
            tot += l1.val;
            l1 = l1.next;
        }
        
        if (l2 != null)
        {
            tot += l2.val;
            l2 = l2.next;
        }
        
        return new ListNode(tot%10, AddUp(l1, l2, tot/10));
    }
}
```
