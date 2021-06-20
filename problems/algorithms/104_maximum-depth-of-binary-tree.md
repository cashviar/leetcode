##  **104.<br/>[Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)<br/>[二元樹的最大深度](https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/)**

## **Topics**
* Tree
* Depth-first Search
* Recursion

## **Idea**
設計一遞迴函數從根結點出發，分成左右路徑在遞迴時選擇累計值較大的一方進行遞增，若訪問至空節點回傳0，否則回傳1，待左右指針皆訪問至空節點時結束遞迴，即可得最大深度。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/104_maximum-depth-of-binary-tree.md#go) | O(n) | O(n) | 4 ms | 4.4 MB | https://drive.google.com/file/d/1Z1FrlTDJQIs9jnx9KD5Ji_svvsOCSPRj/view?usp=sharing |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/104_maximum-depth-of-binary-tree.md#c) | O(n) | O(n) | 88 ms | 25.9 MB | https://drive.google.com/file/d/1t05-Ff14eTewyVKHa2bI8ubVDEhTuMZh/view?usp=sharing |

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
func maxDepth(root *TreeNode) int {
    if root == nil {
        return 0
    }
    return 1 + max(maxDepth(root.Left), maxDepth(root.Right))
}

func max(l, r int) int {
    if l > r {
        return l 
    }
    return r 
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
    public int MaxDepth(TreeNode root) 
    {
        if (root == null) return 0;
            
        return 1 + Math.Max(MaxDepth(root.left), MaxDepth(root.right));
            
    }
}
```