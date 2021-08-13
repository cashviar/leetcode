##  **543.<br/>[Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)<br/>[二元樹的直徑](https://leetcode-cn.com/problems/diameter-of-binary-tree/)**
  
## **Topics**
* Tree

## **Idea**
設計一遞迴函數以當前節點為根節點出發，分成左右路徑在遞迴時選擇累計值較大的一方進行遞增，並且每次以當前根節點的最大左右路徑相加總和跟當前直徑比較，取較大值的一方更新當前直徑，待所有路徑皆訪問至空節點時結束遞迴，即可得最大直徑。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/543_diameter-of-binary-tree.md#go) | O(n) | O(n) | 4 ms | 4.4 MB | https://drive.google.com/file/d/13n0kVm4kYbWW34byQHPTntOrvF8_7QA7/view?usp=sharing |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/543_diameter-of-binary-tree.md#c) | O(n) | O(n) | 80 ms | 26.6 MB | https://drive.google.com/file/d/1bEDEtE_NTD_FeHjY1IA4ava4Lml_5ltX/view?usp=sharing |

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
var diameter int

func diameterOfBinaryTree(root *TreeNode) int { 
    diameter = 0
    
    getDiameter(root)    
    return diameter
}

func getDiameter(node *TreeNode) int {
    if node == nil {
        return 0
    }
    
    l, r := getDiameter(node.Left), getDiameter(node.Right)    
    
    diameter = max(diameter, l+r)    
    return max(l, r)+1
}

func max(l, r int) int {
    if l > r {
        return l
    }
    return r
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
    private int diameter;
    
    public int DiameterOfBinaryTree(TreeNode root) 
    {        
        GetDiameter(root);
        return diameter;
    }
        
    private int GetDiameter(TreeNode node)
    {
        if (node == null) return 0;
        
        var l = GetDiameter(node.left);
        var r = GetDiameter(node.right);        
        
        diameter = Math.Max(diameter, l+r);              
        return Math.Max(l, r)+1;
    }
}
```