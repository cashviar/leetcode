##  **5.<br/>[Longest Palindromic Substring](https://leetcode.com/problems/two-sum/)<br/>[最長回文子串](https://leetcode-cn.com/problems/two-sum/)**

## **Topics**
* String
* Dynamic Programming

## **Idea**

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Java](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/1_two-sum.md#java) | O(n^2) | O(1) | 14 ms | 41.2MB | https://drive.google.com/file/d/1udnzxgIWV69oK2la95rj36KRCHB8JTk4/view?usp=share_link |

## Java
```Java
class Solution {
    //使用双指针法
    int maxLen=0, begin=0;
    private void extend(String s,int i,int j,int n) {
        while(i>=0&&j<n&&s.charAt(i)==s.charAt(j)) {
            if(j-i+1>maxLen) {
                maxLen=j-i+1;
                begin=i;
            }
            --i;
            ++j;
        }
    }    
    public String longestPalindrome(String s) {
        int len = s.length();
        for(int i=0;i<len;i++) {
            extend(s,i,i,len);//以一个元素向两端扩散
            extend(s,i,i+1,len);//以两个元素为中心向两端扩散
        }
        return s.substring(begin, Math.min(begin+maxLen,len));                    
    }
}
```
