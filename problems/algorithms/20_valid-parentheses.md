## **20.<br/>[Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)<br/>[有效的括號](https://leetcode-cn.com/problems/valid-parentheses/)**

## **Topics**
* String
* Stack

## **Idea**
使用關聯陣列設置相應括號鍵值對及一個stack變數，在迭代字串時碰到左括號一律存入stack，以FILO先進後出的資料結構進行後續判斷。

若stack長度不為零且碰到右括號，則從關聯陣列查找對應左括號後跟stack的最末值進行比較，相符則從stack去除該元素，不相符則直接回傳false。

假如一直跑到迴圈結束都未有不相符，則回傳stack長度是否等於零，即可代表輸入字串是否皆為有效括號。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/20_valid-parentheses.md#go) | O(n) | O(1) | 0 ms | 2 MB | https://drive.google.com/file/d/1e7-AaHuvnCoMJV-rIjYZ6c1_cwpGMr_i/view?usp=sharing |
| [JS](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/20_valid-parentheses.md#js) | O(n) | O(1) | 60 ms | 42.4 MB | https://drive.google.com/file/d/10aP7bP1cIs9y0BEkBNjoLd3gZcSQsE9X/view?usp=sharing |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/20_valid-parentheses.md#c) | O(n) | O(1) | 72 ms | 23.1 MB | https://drive.google.com/file/d/150YrcwA6PU5jXpJ1TAbdXFsKBbde8hqc/view?usp=sharing |

## Go
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

## JS
```js
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    const parentheses = {
        ')': '(', 
        ']': '[', 
        '}': '{',
    };
    let stack = [];
    
    for (let char of s) {
        if (char == '(' || char == '[' || char == '{') {
            stack.push(char);
        } else if (stack.length > 0 && stack[stack.length-1] == parentheses[char]) {
            stack.pop();
        } else {
            return false;
        }
    }
    
    return stack.length == 0;
};
```
## C#
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
