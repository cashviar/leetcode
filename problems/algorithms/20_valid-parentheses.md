## Valid Parentheses  有效的括號

### **Description**
https://leetcode.com/problems/valid-parentheses/

### **Topics**
* String
* Stack

### **Idea**

使用關聯陣列Map設置相應括號鍵值對，接著在迭代s字串時，碰到左括號一律存入stack陣列，以LIFO後進先出的stack資料結構進行後續判斷。

若stack陣列長度不為零且碰到右括號，則從關聯陣列映射找出對應左括號後跟stack陣列的最末值進行比較，相符則從stack陣列去除該元素，不相符或字串首位就是右括號則直接回傳false。

最後在for迴圈跑完時回傳stack陣列長度是否等於零，即可代表輸入字串是否皆為有效括號。

### **Solutions**

#### Go 

```Go
func isValid(s string) bool {
    parentheses := map[rune]rune{
        ')': '(', 
        ']': '[', 
        '}': '{',
    }
    var stack []rune
    
    for _, char := range s {
        if char == '(' || char == '[' || char == '{' {
            stack = append(stack, char)
        } else if len(stack) > 0 && stack[len(stack) - 1] == parentheses[char] {
            stack = stack[:len(stack) - 1]
        } else {
            return false
        }
    }
    
    return len(stack) == 0
}
```
| Time Complexity | Space Complexity | Runtime | Memory Usage |
| :--: | :--: | :--: | :--: |
| O(n) | O(1) | 0 ms | 2 MB |

> 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。
> https://leetcode.com/submissions/detail/450652287/