##  **226.<br/>[Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/)<br/>[反轉二元樹](https://leetcode-cn.com/problems/reverse-linked-list/)**
  
## **Topics**
* Tree

## **Idea**
由題目的示意圖可知反轉二元樹即代表所有的左右節點互換，因此可使用遞迴分別帶入左右指針，及設置兩個變數儲存當前的左右節點，然後覆寫其根節點並回傳，重複此流程直到指針指向空節點時結束遞迴。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/226_invert-binary-tree.md#go) | O(n) | O(n) | 0 ms | 2.1 MB | https://drive.google.com/file/d/1-udIFRALZ5eMurAHs679pnHiX_Z3yN6f/view?usp=sharing |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/226_invert-binary-tree.md#c) | O(n) | O(n) | 84 ms | 24.8 MB | https://drive.google.com/file/d/1-yazqQW8bqhktTS8e3_SLnZqGyhO9zKm/view?usp=sharing |

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
func invertTree(root *TreeNode) *TreeNode {
    if root == nil {
        return nil
    }
    
    left := invertTree(root.Left)
    right := invertTree(root.Right)
    
    root.Left = right
    root.Right = left
    
    return root
}
```

## **C#**
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
    public TreeNode InvertTree(TreeNode root) 
    {
        if (root == null) return null;
        
        TreeNode left = InvertTree(root.left);
        TreeNode right = InvertTree(root.right);
        
        root.left = right;
        root.right = left;
        
        return root;
    }
}
```