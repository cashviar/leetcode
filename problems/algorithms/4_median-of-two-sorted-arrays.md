##  **4.<br/>[Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/)<br/>[寻找两个正序数组的中位数](https://leetcode-cn.com/problems/median-of-two-sorted-arrays/)**

## **Topics**
* Array 
* Binary Search
* Divide and Conquer

## **Idea**
要計算兩個數組的中位數，相當於先找到第K位數，此時的K等於數組總和的中間值，再用K值二分查找比大小，數值較小的指針往右移```K/2```並重新計算K值後傳入遞迴函數反覆運算，直到返回計算中位數的數值為止。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Java](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/1_two-sum.md#java) | O(log n) | O(1) | 1 ms | 43.3 MB | https://drive.google.com/file/d/16rIBqPhJlUKU1YStebb56e6xcRzY1bZw/view?usp=sharing |
| [JS](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/1_two-sum.md#js) | O(log n) | O(1) | 96 ms | 46.2 MB | https://drive.google.com/file/d/1A18WrNLkpnMH_5UbXBTJwFpv-tARRHW6/view?usp=sharing |

## Java
```Java
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int tot = nums1.length + nums2.length;
        
        double m1 = getKth(nums1, 0, nums2, 0, (tot+1)/2);
        double m2 = getKth(nums1, 0, nums2, 0, (tot+2)/2);        
        
        return (m1+m2)/2;
    }
    
    private double getKth(int[] nums1, int p1, int[] nums2, int p2, int k) {
        if (p1 >= nums1.length) return nums2[p2+k-1];
        if (p2 >= nums2.length) return nums1[p1+k-1];
        if (k == 1) return Math.min(nums1[p1], nums2[p2]);
        
        int n1 = p1+k/2-1 < nums1.length ? nums1[p1+k/2-1] : Integer.MAX_VALUE;
        int n2 = p2+k/2-1 < nums2.length ? nums2[p2+k/2-1] : Integer.MAX_VALUE;
        
        return n1 < n2 ? getKth(nums1, p1+k/2, nums2, p2, k-k/2) : getKth(nums1, p1, nums2, p2+k/2, k-k/2);
    }
}
```

## JS
```js
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number}
 */
var findMedianSortedArrays = function(nums1, nums2) {
    const tot = nums1.length + nums2.length;
    
    let m1 = getKth(nums1, 0, nums2, 0, Math.floor((tot+1)/2));
    let m2 = getKth(nums1, 0, nums2, 0, Math.floor((tot+2)/2));
    
    return (m1+m2)/2;
    
    function getKth(nums1, p1, nums2, p2, k) {        
        if (p1 >= nums1.length) return nums2[p2+k-1];
        if (p2 >= nums2.length) return nums1[p1+k-1];
        if (k == 1) return Math.min(nums1[p1], nums2[p2]);
        
        const halfOfK = Math.floor(k/2);
        
        let n1 = p1+halfOfK-1 < nums1.length ? nums1[p1+halfOfK-1] : Number.MAX_VALUE;
        let n2 = p2+halfOfK-1 < nums2.length ? nums2[p2+halfOfK-1] : Number.MAX_VALUE;
        
        return n1 < n2 ? getKth(nums1, p1+halfOfK, nums2, p2, k-halfOfK) : getKth(nums1, p1, nums2, p2+halfOfK, k-halfOfK);
    }
};
```
