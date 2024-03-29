##  **3.<br/>[Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)<br/>[無重複字符的最長子串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)**
  
## **Topics**
* Hash Table
* Two Pointers
* String
* Sliding Window

## **Idea**
藉由滑動窗口算法用双指針動態移動無重複字符串的起始與結束邊界，首先新增一個由字符對應到原始陣列索引值的關聯表，在迭代時檢查當前字符是否存在於該關聯表中，若已存在則更新起始邊界及該字符對應索引值，否則將該字符與其對應索引值存入，最後更新無重複字符串的長度，依此流程反覆進行至迭代程序終止即可。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/3_longest-substring-without-repeating-characters.md#go) | O(n) | O(n) | 4 ms | 3.1 MB | https://drive.google.com/file/d/1QPoov8W0IglW0KX6YYn30N1BEfpDDxqZ/view?usp=sharing |
| [Java](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/3_longest-substring-without-repeating-characters.md#java) | O(n) | O(n) | 4 ms | 42.3 MB | https://drive.google.com/file/d/1oSFd31dpR9xV8tcJfNJ9jNEHP0-Zel93/view?usp=sharing |
| [JS](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/3_longest-substring-without-repeating-characters.md#js) | O(n) | O(n) | 72 ms | 45.2 MB | https://drive.google.com/file/d/1YNvkpfjOf7XkilpBbtnmw7IphzPoy_F8/view?usp=sharing |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/3_longest-substring-without-repeating-characters.md#c) | O(n) | O(n) | 76 ms | 26.4 MB | https://drive.google.com/file/d/10TEGYCpL29ZsT0B4dI6p_0HrTY17e5Hh/view?usp=sharing |

## **Go**
```Go
func lengthOfLongestSubstring(s string) int {
    note := make(map[byte]int)
    length := 0

    for start, end := 0, 0; end < len(s); end ++ {
        if v, ok := note[s[end]]; ok {
            start = max(start, v+1)
        }      
        
        note[s[end]] = end        
        length = max(length, end-start+1)
    }

    return length
}

func max(a int, b int) int {
    if a > b {
        return a
    }
    return b
}
```

## Java
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        Map<Character, Integer> note = new HashMap<Character, Integer>();
        int length = 0;
        
        for (int start = 0, end = 0; end < s.length(); end ++) {
            if (note.containsKey(s.charAt(end))) {
                start = Math.max(start, note.get(s.charAt(end))+1);
            }
            
            note.put(s.charAt(end), end);
            length = Math.max(length, end-start+1);
        }
        
        return length;
    }
}
```

## JS
```js
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    const note = new Map();
    let length = 0;
    
    for (let start = 0, end = 0; end < s.length; end++) {
        if (note.has(s[end])) {
            start = Math.max(start, note.get(s[end])+1);
        }
        
        note.set(s[end], end);
        length = Math.max(length, end-start+1);
    }
    
    return length;
};
```

## **C#**
```csharp
public class Solution 
{
    public int LengthOfLongestSubstring(string s) 
    {
        Dictionary<char, int> note = new Dictionary<char, int>();
        int length = 0;
        
        for (int start = 0, end = 0; end < s.Length; end ++)
        {
            if (note.Keys.Contains(s[end]))
            {
                start = Math.Max(start, note[s[end]]+1);
            }
            
            note[s[end]] = end;            
            length = Math.Max(length, end-start+1);
        }
        
        return length;
    }
}
```
