##  **10.<br/>[Regular Expression Matching](https://leetcode.com/problems/regular-expression-matching/)<br/>[正則表達式匹配](https://leetcode.cn/problems/regular-expression-matching/)**

## **Topics**
* String
* Dynamic Programming
* Backtracking

## **Idea**

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Java](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/10_regular-expression-matching.md.md#java) | O(mn) | O(mn) | 1 ms | 40.1MB | https://drive.google.com/file/d/1RXUNwWTVlPI8cUh5MPQ_2o4RBRP_wymO/view?usp=share_link |

## Java
```Java
class Solution {
    public boolean isMatch(String s, String p) {
        boolean[][] dp = new boolean[s.length() + 1][p.length() + 1];
        dp[0][0] = true;
        for(int j = 1; j <= p.length(); j++) {
            if(p.charAt(j - 1) == '*') {
                dp[0][j] = dp[0][j - 2];
            }
        }
        for(int i = 1; i <= s.length(); i++) {
            for(int j = 1; j <= p.length(); j++) {
                if(s.charAt(i - 1) == p.charAt(j - 1) || p.charAt(j - 1) == '.') {
                    dp[i][j] = dp[i - 1][j - 1];
                } else if(p.charAt(j - 1) == '*') {
                    if(s.charAt(i - 1) != p.charAt(j - 2) && p.charAt(j - 2) != '.') {
                        dp[i][j] = dp[i][j - 2];
                    } else {
                        dp[i][j] = dp[i][j - 2] | dp[i - 1][j];
                    }
                }
            }
        }
        return dp[s.length()][p.length()];
    }
}
```
