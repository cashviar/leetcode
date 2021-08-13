## **53.<br/>[Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)<br/>[最大子序和](https://leetcode-cn.com/problems/maximum-subarray/)**

## **Topics**
* Array
* Divide and Conquer
* Dynamic Programming

## **Idea**
設置兩個變數分別代表當前累計和跟最大和，兩者皆以參數的首位數字作初始值，接著在迭代時採用貪心算法 。

從迭代的現值跟當前累計和計算出最大值後更新當前累計和，再從當前累計和跟最大和比較後更新最大和，待迭代結束後便可得到最大子序和。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/53_maximum-subarray.md#go) | O(n) | O(1) | 4 ms | 3.3 MB | https://drive.google.com/file/d/1MJ7_ZABpIabiCopQYaO2o_Sd0GdPoFXl/view?usp=sharing |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/53_maximum-subarray.md#c) | O(n) | O(1) | 84 ms | 25.7 MB | https://drive.google.com/file/d/1UW67IoL5D6OF904E7VgPq1IprjlunPEo/view?usp=sharing |

## Go 
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
## C#
```csharp
public class Solution 
{
    public int MaxSubArray(int[] nums) 
    {
        int currentSum = nums[0], maxSum = nums[0];
        
        // Greedy algorithm
        foreach (int num in nums.Skip(1))
        {
            currentSum = Math.Max(num, currentSum + num);
            maxSum = Math.Max(currentSum, maxSum);
        }
        
        return maxSum;
    }
}
```