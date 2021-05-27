# 动态规划之正则表达

![](../.gitbook/assets/screen-shot-2021-05-27-at-10.05.37-am.png)

## ⼀、不考虑通配符情况

第⼀步，我们暂时不管正则符号，如果是两个普通的字符串进⾏⽐较，如何 进⾏匹配？我想这个算法应该谁都会写：

```cpp
 bool isMatch(string text, string pattern) { 
        if (text.size() != pattern.size()) 
        return false; 
        for (int j = 0; j < pattern.size(); j++) { 
            if (pattern[j] != text[j]) 
            return false; 
        }
        return true; 
    }
```

稍微改造⼀下上⾯的代码，略微复杂了⼀点，但意思还是⼀样的:

```cpp
bool isMatch(string text, string pattern) { 
       int i = 0; // text 的索引位置 
       int j = 0; // pattern 的索引位置 
       while (j < pattern.size()) { 
           if (i >= text.size()) 
           return false; 
           if (pattern[j++] != text[i++]) 
           return false; 
        }// 相等则说明完成匹配 
        return j == text.size(); 
    }
}
```

如上改写，是为了将这个算法改造成递归算法（伪码）：

```python
def isMatch(text, pattern) -> bool: 
    if pattern is empty: return (text is empty?) 
    first_match = (text not empty) and pattern[0] == text[0] 
    return first_match and isMatch(text[1:], pattern[1:])
```



