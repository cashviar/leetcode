##  **11.<br/>[Container With Most Water](https://leetcode.com/problems/container-with-most-water/)<br/>[盛最多水的容器](https://leetcode.cn/problems/container-with-most-water/)**

## **Topics**
* Array
* Two Pointers

## **Idea**

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Java](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/5_container-with-most-water.md#java) | O(n) | O(1) | 3 ms | 51.7 MB | https://drive.google.com/file/d/104pBQDem_qgFvyFtmdS48H4gNOvQ8mrD/view?usp=share_link |

## Java
```Java
class Solution {
    public int maxArea(int[] height) {
        int i = 0, j = height.length - 1, area = 0;
        while(i < j) {
            area = height[i] < height[j] ? 
                Math.max(area, (j - i) * height[i++]): 
                Math.max(area, (j - i) * height[j--]); 
        }
        return area;
    }
}
```
