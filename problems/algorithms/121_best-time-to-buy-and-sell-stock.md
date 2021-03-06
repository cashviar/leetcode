##  Best Time to Buy and Sell Stock 買賣股票的最佳時機

### **Description**

https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

### **Topics**

* Array
* Dynamic Programming

### **Idea**

基於序列順序為按照天數排定，且必須先買進才能賣出，故最大獲利值可藉由動態規劃概念拆解成如下形式：
```
prices[2] - prices[0] = prices[2] - prices[1] + prices[1] - prices[0]
```
以此形式進行迭代計算，若為負值則直接歸零，若大於當前最大值則以該值更新最大值。


#### Go 
```Go
func maxProfit(prices []int) int {
    tmp, max := 0, 0
    for i := 1; i < len(prices); i++ {
        tmp += prices[i] - prices[i-1]
        if tmp < 0 {
            tmp = 0
        }
        if tmp > max {
            max = tmp
        }
    }
    return max
}
```

| Time Complexity | Space Complexity | Runtime | Memory Usage |
| :--: | :--: | :--: | :--: |
| O(n) | O(1) | 120 ms | 8.6 MB |
> 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。
> https://leetcode.com/submissions/detail/463493719/