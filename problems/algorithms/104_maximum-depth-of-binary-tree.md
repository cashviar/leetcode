##  Maximum Depth of Binary Tree 二元樹的最大深度

### **Description**

https://leetcode.com/problems/symmetric-tree/

### **Topics**

* Tree
* Depth-first Search
* Recursion

### **Idea**

設計一遞迴函數從根結點出發，若該節點為空回傳0，否則回傳1。接著遞迴擇取左右指針分別訪問的節點回傳值較大的一方進行遞增，待左右路線皆訪問至空節點時結束遞迴。

#### Go 
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

| Time Complexity | Space Complexity | Runtime | Memory Usage |
| :--: | :--: | :--: | :--: |
| O(n) | O(n) | 4 ms | 4.4 MB |
> 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。
> https://leetcode.com/submissions/detail/461137920/