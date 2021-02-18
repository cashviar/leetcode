##  Climbing Stairs 爬樓梯

### **Description**

https://leetcode.com/problems/climbing-stairs/

### **Topics**

* Dynamic Programming

### **Idea**

基於一次只能爬一階或二階，使用動態規劃可將此問題拆解成費氏數列格式，意即爬到第 i 階的方法數等於爬到第 i-1 階加上第 i-2 階的方法數，且因為只需回傳爬到最後一階的總方法數，
故使用滾動數組形式儲存迭代當下的變量即可。

#### Go 
```Go
func climbStairs(n int) int {
    p1, p2, p0 := 0, 0, 1
    for i := 1; i <= n; i++ {
        p1 = p2
        p2 = p0
        p0 = p1 + p2
    }
    return p0
}
```

| Time Complexity | Space Complexity | Runtime | Memory Usage |
| :--: | :--: | :--: | :--: |
| O(n) | O(1) | 0 ms | 1.9 MB |
> 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。
> https://leetcode.com/submissions/detail/456404061/