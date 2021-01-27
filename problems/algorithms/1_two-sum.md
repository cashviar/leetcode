##  Two Sum 兩數之和

### **Description**
https://leetcode.com/problems/two-sum/

### **Topics**
* Array 
* Hash Table

### **Idea**
在迭代nums陣列並計算出與target的差值後，判斷該差值是否存在於新增的關聯陣列，是則回傳相應的兩個索引值，否則將該數字及其對應的索引值設定至Map，便於後續快速查找相符差值並取得其索引。

### **Solutions**
> #### Go
| Time Complexity | Space Complexity | Runtime / beats | Memory Usage / beats |
| :--: | :--: | :--: | :--: |
| O(n) | O(1) | 4 ms / 92.25% | 3.2 MB / 99.88% |

_Runtime 和 Memory Usage 及 beats 比例皆來自LeetCode提交後的回傳值，僅供參考。_

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
