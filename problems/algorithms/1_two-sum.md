##  Two Sum 兩數之和

### **Description**
https://leetcode.com/problems/two-sum/

### **Topics**
* Array 
* Hash Table

### **Idea**
在迭代nums陣列並計算出與target的差值後，判斷該差值是否存在於新增的關聯陣列，是則回傳相應的兩個索引值，否則將該數字及其對應的索引值設定至關聯陣列，便於後續快速查找相符差值並取得其索引。

### **Solutions**

#### C#
```csharp
public class Solution 
{
    public int[] TwoSum(int[] nums, int target) 
    {    
        Hashtable diff = new Hashtable();
        for (int i = 0; i < nums.Length; i++) 
        {
            if (diff.ContainsKey(target - nums[i])) 
            {
                return new int[2] { (int)diff[target - nums[i]], i };
            }
            diff.Add(nums[i], i);
        }                
        return null;
    }
}
```

| Time Complexity | Space Complexity | Runtime | Memory Usage |
| :--: | :--: | :--: | :--: |
| O(n) | O(n) | 236 ms | 31.7 MB |

> 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。
> https://leetcode.com/submissions/detail/467726334/


#### Go

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
| Time Complexity | Space Complexity | Runtime | Memory Usage |
| :--: | :--: | :--: | :--: |
| O(n) | O(1) | 4 ms | 3.2 MB |

> 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。
> https://leetcode.com/submissions/detail/448482768/
