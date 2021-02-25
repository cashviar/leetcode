##  Symmetric Tree 對稱二元樹

### **Description**

https://leetcode.com/problems/symmetric-tree/

### **Topics**

* Tree
* Depth-first Search
* Breadth-first Search

### **Idea**

若以中央對切為基準的每一個最小單位的二元樹皆為鏡像對稱，則可代表最終組合而成的二元樹為鏡像對稱。如此便可設計一個遞迴函數同步移動左右指針來遍歷二元樹是否為鏡像對稱，依序比較當前根節點的值以及雙指針反向移動後的值是否相同，反向移動意即判斷指針分別對應的兩個二元樹的左右節點是否互為相反值。



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

| Time Complexity | Space Complexity | Runtime | Memory Usage |
| :--: | :--: | :--: | :--: |
| O(n) | O(n) | 0 ms | 2.9 MB |
> 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。
> https://leetcode.com/submissions/detail/460073264/