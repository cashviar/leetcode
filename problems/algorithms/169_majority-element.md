##  **169.<br/>[Majority Element](https://leetcode.com/problems/majority-element/)<br/>[多數元素](https://leetcode-cn.com/problems/majority-element/)**

## **Topics**
* Array
* Divide and Conquer
* Bit Manipulation

## **Idea**

基於題目已假定陣列一定有過半的多數元素，因此可借用摩爾投票算法的概念來計次。

假設陣列有n個元素，遇到相同元素票數+1，反之-1，若某元素個數大於n/2，則用其餘剩下的元素將其抵銷後的個數必不等於零，所以若當前的候選元素票數計次後歸零，就會被下一個元素取代，依此模式迭代完該陣列後，即可得過半的多數元素。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/169_majority-element.md#go) | O(n) | O(1) | 16 ms | 6.1 MB | https://drive.google.com/file/d/1_hfiCruyZaNTeQu-iz-6S7_gJ72FY6yv/view?usp=sharing |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/169_majority-element.md#c) | O(n) | O(1) | 108 ms | 30.4 MB | https://drive.google.com/file/d/1kGWiZVLgEduAOlk5p9sLhv_gljoAGSLU/view?usp=sharing |

## **Go**
```Go
func majorityElement(nums []int) int {
    candidate, count := nums[0], 1
    
    for i := 1; i < len(nums); i++ {
        if count == 0 {
            candidate = nums[i]
        }
        if nums[i] == candidate {
            count += 1
        } else {
            count -= 1
        }
    }
    
    return candidate
}
```

## **C#**
```csharp
public class Solution 
{
    public int MajorityElement(int[] nums) 
    {
        int candidate = nums[0], count = 1;
        
        for (int i = 1; i < nums.Length; i++)
        {
            if (count == 0) candidate = nums[i];
            count = nums[i] == candidate ? count + 1 : count - 1;
        }
        
        return candidate;
    }
}
```