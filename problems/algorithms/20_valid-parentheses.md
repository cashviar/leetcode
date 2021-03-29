## Valid Parentheses  有效的括號

### **Description**
https://leetcode.com/problems/valid-parentheses/

### **Topics**
* String
* Stack

### **Idea**

使用關聯陣列設置相應括號鍵值對及一個stack變數，在迭代字串時碰到左括號一律存入stack，以FILO先進後出的資料結構進行後續判斷。

若stack長度不為零且碰到右括號，則從關聯陣列查找對應左括號後跟stack的最末值進行比較，相符則從stack去除該元素，不相符則直接回傳false。

假如一直跑到迴圈結束都未有不相符，則回傳stack長度是否等於零，即可代表輸入字串是否皆為有效括號。

### **Solutions**

#### C#

```csharp
public class Solution 
{
    public bool IsValid(string s) 
    {
        Dictionary<char, char> parentheses = new Dictionary<char, char>();
        parentheses.Add(')', '(');
        parentheses.Add('}', '{');
        parentheses.Add(']', '[');

        Stack<char> stack = new Stack<char>();

        foreach(char v in s)
        {
            if (v == '(' || v == '[' || v == '{')
            {
                stack.Push(v);
            }
            else if (stack.Count > 0 && stack.Peek() == parentheses[v])
            {
                stack.Pop();
            }
            else 
            {
                return false;
            }
        }
        
        return stack.Count == 0;
    }
}
```
| Time Complexity | Space Complexity | Runtime | Memory Usage |
| :--: | :--: | :--: | :--: |
| O(n) | O(1) | 72 ms | 23.1 MB |

> 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。
> https://leetcode.com/submissions/detail/473401073/

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