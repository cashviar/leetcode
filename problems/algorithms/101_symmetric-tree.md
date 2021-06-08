##  **101.<br/>[Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)<br/>[對稱二元樹](https://leetcode-cn.com/problems/symmetric-tree/)**

## **Topics**
* Tree
* Depth-first Search
* Breadth-first Search

### **Idea**
設計一個遞迴函數同步移動左右指針來遍歷二元樹是否為鏡像對稱，依序比較當前根節點的值以及左右指針反向移動後的值是否相同，最後藉由左右指針是否同步指向空節點即可判斷是否為完全鏡像對稱。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/101_symmetric-tree.md#go) | O(n) | O(n) | 0 ms | 2.9 MB | https://leetcode.com/submissions/detail/475451684/ |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/101_symmetric-tree.md#c) | O(n) | O(n) | 88 ms | 25.6 MB | https://leetcode.com/submissions/detail/504449300/ |

## **Go**
```Go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func isSymmetric(root *TreeNode) bool {
    return check(root, root)
}

func check(left *TreeNode, right *TreeNode) bool {
    if left == nil && right == nil {
        return true
    }
    if left == nil || right == nil {
        return false
    }

    return left.Val == right.Val && check(left.Right, right.Left) && check(left.Left, right.Right)    
}
```
## C#
```csharp
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     public int val;
 *     public TreeNode left;
 *     public TreeNode right;
 *     public TreeNode(int val=0, TreeNode left=null, TreeNode right=null) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
public class Solution 
{
    public bool IsSymmetric(TreeNode root) => Check(root, root);
    
    private bool Check(TreeNode left, TreeNode right)
    {
        if (left == null && right == null) return true;
        if (left == null || right == null) return false;
        
        return left.val == right.val && Check(left.right, right.left) && Check(left.left, right.right);
    }
}
```