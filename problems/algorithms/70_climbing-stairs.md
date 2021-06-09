##  **70.<br/>[Climbing Stairs](https://leetcode.com/problems/climbing-stairs/)<br/>[爬樓梯](https://leetcode-cn.com/problems/climbing-stairs/)**

## **Topics**
* Dynamic Programming

## **Idea**
基於一次只能爬一階或二階，使用動態規劃可將此問題拆解成費氏數列格式。

爬到第 i 階的方法數等於爬到第 i-1 階加上第 i-2 階的方法數，且因為只需回傳爬到最後一階的總方法數，
故使用滾動數組形式儲存迭代當下的變量，待迭代結束回傳疊加總數即可。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/70_climbing-stairs.md#go) | O(n) | O(1) |0 ms | 1.9 MB | https://leetcode.com/submissions/detail/456404061/ |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/70_climbing-stairs.md#c) | O(n) | O(1) | 36 ms | 15.2 MB | https://leetcode.com/submissions/detail/499430153/ |

## Go 
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
## C#
```csharp
public class Solution 
{
    public int ClimbStairs(int n) 
    {
        int p1 = 0, p2 = 0, p0 = 1;         
        for (int i = 1; i <= n; i++)
        {
            p1 = p2;
            p2 = p0;
            p0 = p1 + p2;
        }        
        return p0;
    }
}
```