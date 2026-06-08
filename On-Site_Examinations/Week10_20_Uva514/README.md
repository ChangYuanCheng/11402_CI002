# UVa 514 - Rails

## 題目說明

有一列火車依序進站：

```text
1 2 3 4 ... n
```

車站內有一條側軌。

側軌只能遵守：

```text
Stack (LIFO)
```

也就是：

```text
最後進去
最先出來
```

---

## 題目要求

給你一個目標排列：

```text
target
```

判斷是否能利用：

```text
一個 Stack
```

把原本：

```text
1 2 3 ... n
```

轉換成：

```text
target
```

若可以：

```text
Yes
```

否則：

```text
No
```

---

## 解題思路

直接模擬火車進站。

---

### 進站順序固定

火車只能：

```text
1 → 2 → 3 → ... → n
```

依序進站。

因此：

```cpp
cur
```

表示下一台要進站的火車。

---

### 使用 Stack

建立：

```cpp
stack<int> st;
```

模擬側軌。

---

### 火車進入側軌

```cpp
st.push(cur++);
```

表示：

```text
火車進站
```

---

### 檢查是否能出站

若：

```cpp
st.top() == target[idx]
```

代表：

```text
目前最上面的火車
正好是下一台要輸出的火車
```

可以直接出站：

```cpp
st.pop();
idx++;
```

---

### 持續輸出

```cpp
while (!st.empty() &&
       st.top() == target[idx])
```

就一直出站。

---

### 最後判斷

若：

```cpp
idx == n
```

表示：

```text
所有火車都成功輸出
```

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
5
5 4 3 2 1
```

---

進站：

```text
push 1
push 2
push 3
push 4
push 5
```

Stack：

```text
1 2 3 4 5
```

---

開始出站：

```text
pop 5
pop 4
pop 3
pop 2
pop 1
```

得到：

```text
5 4 3 2 1
```

成功。

輸出：

```text
Yes
```

---

### 範例 2

輸入：

```text
5
1 2 5 3 4
```

---

先輸出：

```text
1
2
```

成功。

---

之後：

```text
push 3
push 4
push 5
```

Stack：

```text
3 4 5
```

---

輸出：

```text
5
```

成功。

Stack：

```text
3 4
```

---

下一個需要：

```text
3
```

但頂端：

```text
4
```

無法取得。

失敗。

輸出：

```text
No
```

---

## 程式碼講解

### 建立目標排列

```cpp
vector<int> target(n);
```

儲存：

```text
目標輸出順序
```

---

### 建立 Stack

```cpp
stack<int> st;
```

模擬側軌。

---

### 下一台進站火車

```cpp
int cur = 1;
```

表示：

```text
1~n
```

依序進站。

---

### 目前比對位置

```cpp
int idx = 0;
```

表示：

```text
target[idx]
```

是下一台想要輸出的火車。

---

### 火車進站

```cpp
st.push(cur++);
```

---

### 可以出站就出站

```cpp
while(!st.empty() &&
      st.top()==target[idx])
{
    st.pop();
    idx++;
}
```

---

### 判斷結果

```cpp
if(idx==n)
```

代表：

```text
全部成功匹配
```

輸出：

```text
Yes
```

否則：

```text
No
```

---

## 輸入格式注意

### 外層

```text
n
```

若：

```text
n = 0
```

整個輸入結束。

---

### 內層

每行是一個目標排列。

若第一個數字：

```text
0
```

表示此組 n 結束。

需輸出空白行。

---

## 時間複雜度

每台火車：

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

## 核心觀念

利用 Stack 模擬側軌：

```cpp
push(1~n)
```

並持續：

```cpp
while(st.top()==target[idx])
```

就：

```cpp
pop()
```

最後：

```cpp
idx == n
```

表示可以完成目標排列。

這題是 UVa 最經典的 Stack 模擬題之一。