##  **448.<br/>[Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)<br/>[找到所有陣列中消失的數字](https://leetcode-cn.com/problems/find-all-numbers-disappeared-in-an-array/)**
  
## **Topics**
* Array

## **Idea**
基於題目已假定在n個元素的陣列中其數值皆介於[1, n]之間，故可借由陣列索引及變更其元素的正負值來判斷數字是否有斷層。首先跑第一次迴圈時，以「元素值-1」為索引，若對應的元素值大於零,則將其乘上-1，負數表示該「索引+1」的值已存在，接著在跑第二次迴圈時，若陣列元素值大於零，則代表該「索引+1」的值不存在，將其附加到待返回陣列即可。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go]() | O(n) | O(1) | 44 ms | 7.9 MB | https://drive.google.com/file/d/1dE1BZDIiH_KS-8_iasC2i_pFdaJVTfKM/view?usp=sharing |
| [C#]() | O(n) | O(1) | 292 ms | 44.1 MB | https://drive.google.com/file/d/1tRcxphRmXGGI5ELqVLiCzezczvm7Ptc4/view?usp=sharing |

## **Go**
```Go
func findDisappearedNumbers(nums []int) []int {
    var dn []int
    absVal := 0
    
    for _, num := range nums {
        if num < 0 {
            num *= -1
        }
        absVal = num-1
        if nums[absVal] > 0 {
            nums[absVal] *= -1
        }
    }
    
    for i, _ := range nums {
        if nums[i] > 0 {
            dn = append(dn, i+1)
        }
    }
    
    return dn
}
```

## **C#**
```csharp
public class Solution 
{
    public IList<int> FindDisappearedNumbers(int[] nums) 
    {
        List<int> dn = new List<int>();
        int absVal = 0;
        
        foreach (int num in nums)
        {
            absVal = Math.Abs(num)-1;
            if (nums[absVal] > 0) nums[absVal] *= -1;
        }
        
        for (int i = 0; i < nums.Length; i ++)
        {
            if (nums[i] > 0) dn.Add(i+1);
        }
        
        return dn;
    }
}
```