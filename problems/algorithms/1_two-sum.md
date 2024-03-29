##  **1.<br/>[Two Sum](https://leetcode.com/problems/two-sum/)<br/>[兩數之和](https://leetcode-cn.com/problems/two-sum/)**

## **Topics**
* Array 
* Hash Table

## **Idea**
在迭代nums陣列並計算出與target的差值後，判斷該差值是否存在於新增的關聯陣列，是則回傳相應的兩個索引值，否則將該數字及其對應的索引值設定至關聯陣列，便於後續快速查找相符差值並取得其索引。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Java](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/1_two-sum.md#java) | O(n) | O(n) | 1 ms | 39.2MB | https://drive.google.com/file/d/13G1crITzONM18Kd78qJFdBpevTbazOJd/view?usp=sharing |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/1_two-sum.md#go) | O(n) | O(n) | 4 ms | 3.2 MB | https://drive.google.com/file/d/1E7UFUCqwUFAOhZ-HoWsx_MyLIow67S7Q/view?usp=sharing |
| [JS](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/1_two-sum.md#js) | O(n) | O(n) | 64 ms | 43.6 MB | https://drive.google.com/file/d/152wPSLe9ohP_FhPz_WlbYNBppJjxzlDq/view?usp=sharing |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/1_two-sum.md#c) | O(n) | O(n) | 236 ms | 31.9MB | https://drive.google.com/file/d/1BmMEWGtqwPl_GdKhCozHTILTbDZfvYOz/view?usp=sharing |

## Java
```Java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> diff = new HashMap<Integer, Integer>();
        for (int i = 0; i < nums.length; i++) {
            if (diff.containsKey(target - nums[i])) {
                return new int[] { diff.get(target - nums[i]), i };
            }
            diff.put(nums[i], i);
        }
        return null;
    }
}
```

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

## JS
```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    let diff = new Map();
    for (let i = 0; i < nums.length; i++) {
        if (diff.has(target - nums[i])) {
            return [diff.get(target - nums[i]), i];
        }
        diff.set(nums[i], i);
    }
    return null;
};
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
