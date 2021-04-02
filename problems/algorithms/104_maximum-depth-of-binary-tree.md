##  **104.<br/>[Maximum Depth of Binary Tree](https://leetcode.com/problems/symmetric-tree/)<br/>[二元樹的最大深度](https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/)**

## **Topics**
* Tree
* Depth-first Search
* Recursion

## **Idea**
設計一遞迴函數從根結點出發，若該節點為空回傳0，否則回傳1疊加一層。

在遞迴時擇取左右指針分別訪問的節點回傳值較大的一方進行遞增，待左右路線皆訪問至空節點時結束遞迴，回傳疊加值較大的路徑。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/8305822ad5cc2307a66e15c0896c89f640bf08bd/problems/algorithms/104_maximum-depth-of-binary-tree.md#go) | O(n) | O(n) | 4 ms | 4.4 MB | https://leetcode.com/submissions/detail/461137920/ |

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