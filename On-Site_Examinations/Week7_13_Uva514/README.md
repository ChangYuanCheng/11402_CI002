# UVa 514 - Rails

## 題目說明

有一列火車：

```text
1 2 3 4 5 ... n
```

依序進入車站。

車站內只有一條側軌（Stack）。

規則：

1. 火車只能依序進站
2. 可以進入側軌等待
3. 側軌遵守 Stack（後進先出）
4. 火車離開順序必須符合目標排列

要求判斷：

```text
是否能利用一個 Stack
產生指定輸出順序
```

---

## 解題思路

直接模擬 Stack。

---

### 進站順序固定

```text
1 → 2 → 3 → ... → n
```

無法改變。

因此：

```cpp
cur
```

表示下一台要進站的火車。

---

### 模擬流程

每台火車：

```cpp
st.push(cur);
```

進入側軌。

---

接著不停檢查：

```cpp
st.top()
```

是否等於：

```cpp
target[idx]
```

若相同：

```cpp
st.pop();
idx++;
```

表示成功送出。

---

### 最後判斷

若：

```cpp
idx == n
```

代表：

```text
所有車廂都成功輸出
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

### 輸入

```text
5
5 4 3 2 1
0
0
```

---

目標：

```text
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

開始輸出：

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

## 不能成功的例子

目標：

```text
1 2 5 3 4
```

---

輸出：

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

但 Stack 頂端：

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

## 為什麼用 Stack？

側軌特性：

```text
最後進去
最先出來
```

即：

```text
LIFO
```

正是 Stack。

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

## 測資格式

### 外層

```text
n
```

當：

```text
n = 0
```

結束。

---

### 內層

每行：

```text
目標排列
```

當：

```text
第一個數字 = 0
```

表示此組 n 結束。

並輸出空白行。

---

## 核心觀念

模擬：

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

則：

```text
Yes
```

否則：

```text
No
```

這題是 UVa 最經典的 Stack 模擬題之一。