##  **136.<br/>[Single Number](https://leetcode.com/problems/single-number/)<br/>[只出現一次的數字](https://leetcode-cn.com/problems/single-number/)**

## **Topics**
* Hash Table
* Bit Manipulation

## **Idea**

基於只需保留單一存在的數值，借用位元運算子XOR同質抵銷，異質保留的特性，便可僅用一變數重複XOR運算直到迴圈結束，即可得數列中沒有重複出現的數值。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/136_single-number.md#go) | O(n) | O(1) | 12 ms | 6.2 MB | https://drive.google.com/file/d/17v8988VG_y6dAGkzwx7kloHZCWMMy-W4/view?usp=sharing |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/136_single-number.md#c) | O(n) | O(1) | 104 ms | 30.2 MB | https://drive.google.com/file/d/1TAxemf_iS_srC9U-yt-3IyxBjcYIQpQY/view?usp=sharing |

## **Go**
```Go
func singleNumber(nums []int) int {
    sn := 0
    for _, num := range nums {
        sn ^= num
    }
    return sn
}
```
## **C#**
```csharp
public class Solution 
{
    public int SingleNumber(int[] nums) 
    {
        int sn = 0;        
        foreach (int num in nums)
        {
            sn ^= num;
        }
        return sn;
    }
}
```