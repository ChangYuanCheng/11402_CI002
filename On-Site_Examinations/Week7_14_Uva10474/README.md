# UVa 10474 - Where is the Marble?

## 題目說明

有 N 顆彈珠（Marbles）。

接著有 Q 次查詢。

對於每個查詢數字 x：

```text
找出 x 是否存在於彈珠中
```

如果存在：

```text
輸出第一次出現的位置
```

如果不存在：

```text
輸出 not found
```

---

## 解題思路

### Step 1：排序

題目要求找：

```text
第一次出現的位置
```

因此先排序：

```cpp
sort(marbles.begin(), marbles.end());
```

例如：

```text
5 2 1 3 2
```

排序後：

```text
1 2 2 3 5
```

---

### Step 2：使用 lower_bound

```cpp
lower_bound(begin, end, x)
```

功能：

```text
找到第一個 >= x 的位置
```

例如：

```text
1 2 2 3 5
```

查詢：

```text
x = 2
```

得到：

```text
第一個 2
```

的位置。

---

### Step 3：判斷是否找到

```cpp
if(it != marbles.end() && *it == x)
```

表示：

```text
真的存在
```

輸出：

```cpp
it - marbles.begin() + 1
```

因為題目位置從：

```text
1 開始
```

不是 0。

---

## 範例分析

### 輸入

```text
4 1
2
3
5
1
5
0 0
```

---

排序後：

```text
1 2 3 5
```

---

查詢：

```text
5
```

找到：

```text
第 4 個位置
```

輸出：

```text
5 found at 4
```

---

## lower_bound 範例

陣列：

```text
1 2 2 3 5
```

---

查詢：

```cpp
lower_bound(...,2)
```

結果：

```text
指向第一個 2
```

位置：

```text
2
```

---

查詢：

```cpp
lower_bound(...,4)
```

結果：

```text
指向 5
```

因為：

```text
5 是第一個 >=4 的數
```

但：

```cpp
*it != 4
```

所以：

```text
not found
```

---

## 為什麼用 lower_bound？

暴力搜尋：

```text
O(N)
```

每次查詢都掃描一次。

---

排序後：

```cpp
lower_bound
```

二分搜尋：

```text
O(log N)
```

更快。

---

## 時間複雜度

排序：

```text
O(N log N)
```

每次查詢：

```text
O(log N)
```

總共：

```text
O(N log N + Q log N)
```

---

## 測資範例

### 輸入

```text
4 1
2
3
5
1
5
0 0
```

### 輸出

```text
CASE# 1:
5 found at 4
```

---

## 核心觀念

排序：

```cpp
sort(marbles.begin(), marbles.end());
```

搜尋：

```cpp
auto it = lower_bound(
    marbles.begin(),
    marbles.end(),
    x
);
```

判斷：

```cpp
if(it != marbles.end() && *it == x)
```

找到：

```cpp
it - marbles.begin() + 1
```

即可得到第一次出現的位置。

這題是 UVa 最經典的 Binary Search 入門題之一。