# UVa 10935 - Throwing Cards Away I

## 題目說明

有一疊編號：

```text
1 ~ n
```

的牌。

每次進行以下兩個動作：

1. 丟掉最上面的牌
2. 將新的最上面牌移到牌堆底部

重複執行直到只剩下一張牌。

要求輸出：

- 所有被丟掉的牌
- 最後剩下的牌

---

## 解題思路

這題非常適合使用 Queue。

Queue 特性：

```text
先進先出（FIFO）
```

剛好符合牌堆操作。

---

## 模擬流程

建立：

```cpp
queue<int> q;
```

放入：

```cpp
1 ~ n
```

---

### Step 1：丟掉最上面牌

```cpp
q.pop();
```

但在丟掉前要先記錄：

```cpp
q.front()
```

加入輸出。

---

### Step 2：第二張移到底部

例如：

```text
2 3 4 5
```

取出：

```cpp
q.front()
```

再放回：

```cpp
q.push(q.front());
q.pop();
```

結果：

```text
3 4 5 2
```

---

### Step 3：重複

直到：

```cpp
q.size() == 1
```

停止。

---

## 範例分析

### n = 7

初始：

```text
1 2 3 4 5 6 7
```

丟掉：

```text
1
```

剩：

```text
2 3 4 5 6 7
```

移動：

```text
3 4 5 6 7 2
```

---

丟掉：

```text
3
```

剩：

```text
4 5 6 7 2
```

移動：

```text
5 6 7 2 4
```

---

丟掉：

```text
5
```

剩：

```text
6 7 2 4
```

移動：

```text
7 2 4 6
```

---

丟掉：

```text
7
```

剩：

```text
2 4 6
```

移動：

```text
4 6 2
```

---

丟掉：

```text
4
```

剩：

```text
6 2
```

移動：

```text
2 6
```

---

丟掉：

```text
2
```

剩：

```text
6
```

---

輸出：

```text
Discarded cards: 1, 3, 5, 7, 4, 2
Remaining card: 6
```

---

## 為什麼用 Queue？

題目操作：

```text
從前面拿牌
放到後面
```

正是 Queue 的典型應用。

操作：

```cpp
q.front()
q.pop()
q.push()
```

即可完成模擬。

---

## 時間複雜度

每張牌最多進出 Queue 一次：

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
7
19
10
6
0
```

### 輸出

```text
Discarded cards: 1, 3, 5, 7, 4, 2
Remaining card: 6

Discarded cards: ...
Remaining card: ...

...
```

---

## 核心觀念

使用 Queue 模擬：

```cpp
丟牌：
q.pop();

移到底部：
q.push(q.front());
q.pop();
```

直到：

```cpp
q.size() == 1
```

即可得到答案。

這題是 UVa 中最經典的 Queue 入門題之一。