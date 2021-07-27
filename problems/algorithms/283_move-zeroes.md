##  **283.<br/>[Move Zeroes](https://leetcode.com/problems/move-zeroes/)<br/>[移動零](https://leetcode-cn.com/problems/move-zeroes/)**
  
## **Topics**
* Array
* Two Pointers

## **Idea**
設置左右指針並比照快速排序法的概念，以分區交換方式進行移動，以右指針為主線，左指針定位在所有零元素的最左邊，遇到非零元素就互換左右指針的值，互換後左指針往右移一位，以此模式迭代結束後即可。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go]() | O(n) | O(1) | 4 ms | 3.8 MB | https://drive.google.com/file/d/1Qsu8n8SN6F40RLCdXutoyFHiIKQd8PJI/view?usp=sharing |
| [C#]() | O(n) | O(1) | 220 ms | 32.4 MB | https://drive.google.com/file/d/1hanS0LMgT184gYv9zQTT6dZG7kMZKSLs/view?usp=sharing |

## **Go**
```Go
func moveZeroes(nums []int)  {
    left := 0  
    
    for right, num := range nums {
        if num != 0 {
            nums[left], nums[right] = num, nums[left]
            left ++
        }
    }
}
```

## **C#**
```csharp
public class Solution 
{
    public void MoveZeroes(int[] nums) 
    {
        int left = 0, tmp = 0;
        
        for (int right = 0; right < nums.Length; right ++)
        {
            if (nums[right] != 0)
            {
                tmp = nums[left];
                nums[left] = nums[right];
                nums[right] = tmp;
                left ++;
            }
        }
    }
}
```