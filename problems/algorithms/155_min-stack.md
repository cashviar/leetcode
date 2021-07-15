##  **155.<br/>[Min Stack](https://leetcode.com/problems/min-stack/)<br/>[最小堆疊](https://leetcode-cn.com/problems/min-stack/)**

## **Topics**
* Stack
* Design

## **Idea**

依據題意需設計一個堆疊資料結構，可以常數級別的時間取得最小值，故借由一個專門存放每一次堆疊操作的最小值紀錄的堆疊即可達到目的。

## **Solutions**
| Language | Time Complexity | Space Complexity | Runtime | Memory Usage | 注意：Runtime和Memory Usage的數值皆來自LeetCode提供的效能測試，僅供參考。 |
| :--: | :--: | :--: | :--: | :--: | :-- |
| [Go](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/155_min-stack.md#go) | O(1) | O(n) | 12 ms | 8.5 MB | https://drive.google.com/file/d/1ECI3XJyvfd5G1SM36Sm5CnbA-MNqdKes/view?usp=sharing |
| [C#](https://github.com/cashviar/leetcode/blob/main/problems/algorithms/155_min-stack.md#c) | O(1) | O(n) | 112 ms | 35.6 MB | https://drive.google.com/file/d/1uNZABeTYMo9ngOfB5dvUykEaX_DaVw5U/view?usp=sharing |

## **Go**
```Go
type MinStack struct {
    base []int
    target []int
}


/** initialize your data structure here. */
func Constructor() MinStack {
    return MinStack{base: []int{}, target: []int{}}
}


func (this *MinStack) Push(x int)  {
    this.base = append(this.base, x)
    if len(this.target) == 0 || x <= this.GetMin() {
        this.target = append(this.target, x)
    }
}


func (this *MinStack) Pop()  {
    if this.Top() == this.GetMin() {
        this.target = this.target[:len(this.target)-1]
    }
    this.base = this.base[:len(this.base)-1]
}


func (this *MinStack) Top() int {
    return this.base[len(this.base)-1]
}


func (this *MinStack) GetMin() int {
    return this.target[len(this.target)-1]
}


/**
 * Your MinStack object will be instantiated and called as such:
 * obj := Constructor();
 * obj.Push(x);
 * obj.Pop();
 * param_3 := obj.Top();
 * param_4 := obj.GetMin();
 */
```

## **C#**
```csharp
public class MinStack 
{
    Stack<int> _base;
    Stack<int> _target;

    /** initialize your data structure here. */
    public MinStack() 
    {
        _base = new Stack<int>();
        _target = new Stack<int>();
    }
    
    public void Push(int val) 
    {
        _base.Push(val);
        if (_target.Count == 0 || val <= GetMin())
        {
            _target.Push(val);
        }
    }
    
    public void Pop() 
    {
        if (Top() == GetMin())
        {
            _target.Pop();
        }
        _base.Pop();
    }
    
    public int Top() 
    {
        return _base.Peek();
    }
    
    public int GetMin() 
    {
        return _target.Peek();
    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.Push(val);
 * obj.Pop();
 * int param_3 = obj.Top();
 * int param_4 = obj.GetMin();
 */
```