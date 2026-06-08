# UVa 673 - Parentheses Balance

## 題目說明

給定多行字串。

字串只包含：

```text
(
)
[
]
```

以及空字串。

判斷括號是否匹配。

---

## 匹配規則

### 圓括號

```text
()
```

合法。

---

### 中括號

```text
[]
```

合法。

---

### 巢狀

```text
([])
```

合法。

---

### 錯誤情況

```text
([)]
```

不合法。

因為：

```text
(
[
)
]
```

順序錯誤。

---

## 解題思路

這是標準 Stack 題。

---

### 遇到左括號

```text
(
[
```

放入 Stack。

```cpp
st.push(c);
```

---

### 遇到右括號

若是：

```text
)
```

必須對應：

```text
(
```

若是：

```text
]
```

必須對應：

```text
[
```

---

### 檢查方法

例如：

```cpp
c == ')'
```

則：

```cpp
st.top() == '('
```

才合法。

否則：

```text
不匹配
```

---

### 最後檢查

如果：

```cpp
st.empty()
```

表示全部成功配對。

輸出：

```text
Yes
```

否則：

```text
No
```

---

## 範例分析

### 範例 1

輸入：

```text
([])
```

---

過程：

```text
(
push

[
push

]
匹配 [

)
匹配 (
```

Stack：

```text
空
```

輸出：

```text
Yes
```

---

### 範例 2

輸入：

```text
([)]
```

---

過程：

```text
(
push

[
push

)
```

此時 Stack 頂端：

```text
[
```

需要：

```text
(
```

才能匹配。

失敗。

輸出：

```text
No
```

---

### 範例 3

輸入：

```text
((
```

過程：

```text
(
push

(
push
```

最後 Stack 不為空。

表示：

```text
還有括號沒關閉
```

輸出：

```text
No
```

---

## 程式碼講解

### 建立 Stack

```cpp
stack<char> st;
```

---

### 左括號入 Stack

```cpp
if(c=='(' || c=='[')
{
    st.push(c);
}
```

---

### 處理 ')'

```cpp
if(st.empty() || st.top()!='(')
```

表示：

```text
無法匹配
```

---

### 處理 ']'

```cpp
if(st.empty() || st.top()!='[')
```

表示：

```text
無法匹配
```

---

### 最後確認

```cpp
if(!st.empty())
```

表示：

```text
仍有未配對括號
```

答案為：

```text
No
```

---

## 為什麼用 Stack？

括號配對遵守：

```text
最後開啟
最先關閉
```

例如：

```text
([ ])
```

必須先關：

```text
[
```

再關：

```text
(
```

這正是：

```text
LIFO
```

因此使用 Stack。

---

## 時間複雜度

每個字元最多：

```text
push 一次
pop 一次
```

因此：

```text
Time: O(n)
```

```text
Space: O(n)
```

---

## 測資範例

### 輸入

```text
3
([])
(([[]]))
([)]
```

### 輸出

```text
Yes
Yes
No
```

---

## 核心觀念

遇到：

```text
(
[
```

放入 Stack。

遇到：

```text
)
]
```

檢查 Stack 頂端是否匹配。

最後：

```cpp
st.empty()
```

則：

```text
Yes
```

否則：

```text
No
```

這題是 UVa 最經典的 Stack 括號匹配題之一。