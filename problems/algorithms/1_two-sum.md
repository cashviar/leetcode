##  **1.<br/>[Two Sum](https://leetcode.com/problems/two-sum/)<br/>[兩數之和](https://leetcode-cn.com/problems/two-sum/)**

## **Topics**
* Array 
* Hash Table

## **Idea**
在迭代nums陣列並計算出與target的差值後，判斷該差值是否存在於新增的關聯陣列，是則回傳相應的兩個索引值，否則將該數字及其對應的索引值設定至關聯陣列，便於後續快速查找相符差值並取得其索引。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/20_valid-parentheses.md#go) | O(n) | O(n) | 4 ms | 3.2 MB | https://leetcode.com/submissions/detail/448482768/ |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/1_two-sum.md#c) | O(n) | O(n) | 236 ms | 31.9MB | https://leetcode.com/submissions/detail/475437949/ |

## Go
```Go
func twoSum(nums []int, target int) []int {
    diff := make(map[int]int)
    for i1, num := range nums {
        if i2, ok := diff[target-num]; ok {
            return []int{i2, i1}
        }
        diff[num] = i1
    }
    return nil
}
```

## C#
```csharp
public class Solution 
{
    public int[] TwoSum(int[] nums, int target) 
    {    
        Dictionary<int, int> diff = new Dictionary<int, int>();
        for (int i = 0; i < nums.Length; i++) 
        {
            if (diff.ContainsKey(target - nums[i])) 
            {
                return new int[2] { diff[target - nums[i]], i };            
            }
            diff.Add(nums[i], i);
        }                
        return null;
    }
}
```