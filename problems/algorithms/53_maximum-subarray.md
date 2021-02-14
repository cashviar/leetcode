## Maximum Subarray 最大子序和

### **Description**

https://leetcode.com/problems/maximum-subarray/

### **Topics**

* Array
* Divide and Conquer
* Dynamic Programming

### **Idea**

設置兩個變數分別代表當前累計和跟最大和，兩者皆以輸入陣列的首位數字作初始值，接著在迭代時採用貪心算法，先從迭代的現值跟當前累計和計算最大值後更新當前累計和，再從當前累計和跟最大和比較後更新最大和，
待迭代結束後便可得到最大子序和。

### **Solutions**

#### Go 
```Go
func maxSubArray(nums []int) int {
    currentSum, maxSum := nums[0], nums[0]
    
    // Greedy algorithm
    for _, num := range nums[1:] {
        currentSum = max(num, currentSum + num)
        maxSum = max(currentSum, maxSum)
    }

    return maxSum
}

func max(x, y int) int {
    if x > y {
        return x
    }

    return y
}
```

| Time Complexity | Space Complexity | Runtime | Memory Usage |
| :--: | :--: | :--: | :--: |
| O(n) | O(1) | 4 ms | 3.3 MB |
> 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。
> https://leetcode.com/submissions/detail/455543489/