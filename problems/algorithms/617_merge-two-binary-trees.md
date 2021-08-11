##  **617.<br/>[Merge Two Binary Trees](https://leetcode.com/problems/merge-two-binary-trees/)<br/>[合併二元樹](https://leetcode-cn.com/problems/merge-two-binary-trees/)**
  
## **Topics**
* Tree

## **Idea**
以其中一個二元樹為基底，使用前序遍歷從根節點開始合併，接著以遞迴方式合併之後的左右節點，若其中一方訪問到空節點，則直接返回另一方當前的節點，最後返回以合併值覆蓋後的二元樹即可。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/617_merge-two-binary-trees.md#go) | O(n) | O(n) | 12 ms | 7 MB | https://drive.google.com/file/d/1_tY7mfngOqy9PZSM8YY-98YyR7NTYag1/view?usp=sharing |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/617_merge-two-binary-trees.md#c) | O(n) | O(n) | 96 ms | 28.6 MB | https://drive.google.com/file/d/14_Ci5K8p6CEM2ZYhLeBOxp1KIkNwyFbd/view?usp=sharing |

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
func mergeTrees(t1 *TreeNode, t2 *TreeNode) *TreeNode {    
    if t1 == nil {
        return t2
    }    
    if t2 == nil {
        return t1
    }    
    
    t1.Val += t2.Val
    
    t1.Left = mergeTrees(t1.Left, t2.Left)
    t1.Right = mergeTrees(t1.Right, t2.Right)
    
    return t1
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
    public TreeNode MergeTrees(TreeNode root1, TreeNode root2) 
    {
        if (root1 == null) return root2;
        if (root2 == null) return root1;
        
        root1.val += root2.val;
        
        root1.left = MergeTrees(root1.left, root2.left);
        root1.right = MergeTrees(root1.right, root2.right);
        
        return root1;
    }
}
```