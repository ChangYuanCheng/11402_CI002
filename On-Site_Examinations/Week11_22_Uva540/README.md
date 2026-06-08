# UVa 540 - Team Queue

## 題目說明

一般 Queue：

```text
1 2 3 4 5
```

遵守：

```text
FIFO (First In First Out)
```

但這題加入了「隊伍」概念。

假設：

```text
Team 1 : 101 102 103

Team 2 : 201 202 203
```

若依序進入：

```text
ENQUEUE 101
ENQUEUE 201
ENQUEUE 102
```

隊伍變成：

```text
101 102 201
```

不是：

```text
101 201 102
```

因為：

```text
102 和 101 同隊
```

所以必須排在同隊成員後面。

---

## 題目要求

支援兩種操作：

### ENQUEUE x

加入隊伍。

若：

```text
x 所屬隊伍已經在隊列中
```

則：

```text
插入該隊伍最後面
```

---

### DEQUEUE

輸出隊首元素並移除。

---

### STOP

結束目前測資。

---

## 解題思路

直接維護整個 Queue 很麻煩。

使用：

```cpp
隊伍 Queue
+
成員 Queue
```

即可。

---

## 資料結構

### teamQueue

存放：

```text
目前有哪些隊伍正在排隊
```

例如：

```text
Team1 Team2 Team3
```

```cpp
queue<int> teamQueue;
```

---

### memberQueue

每個隊伍自己的 Queue。

例如：

```text
Team1:
101 102 103

Team2:
201 202
```

```cpp
queue<int> memberQueue[1000];
```

---

### teamOf

紀錄：

```text
某人屬於哪個隊伍
```

例如：

```text
101 -> Team1
102 -> Team1
201 -> Team2
```

```cpp
map<int,int> teamOf;
```

---

## ENQUEUE

加入成員：

```cpp
int team = teamOf[x];
```

---

### 如果隊伍不在隊列中

```cpp
if(memberQueue[team].empty())
{
    teamQueue.push(team);
}
```

代表：

```text
第一次有人進來
```

要把隊伍加入。

---

### 放入該隊伍尾端

```cpp
memberQueue[team].push(x);
```

---

## DEQUEUE

取得目前最前面的隊伍：

```cpp
int team = teamQueue.front();
```

---

輸出該隊伍最前面的成員：

```cpp
memberQueue[team].front()
```

---

刪除：

```cpp
memberQueue[team].pop();
```

---

若隊伍空了：

```cpp
if(memberQueue[team].empty())
{
    teamQueue.pop();
}
```

把整個隊伍移出。

---

## 範例模擬

### Team

```text
Team1:
101 102 103

Team2:
201 202 203
```

---

### ENQUEUE 101

```text
TeamQueue:

[Team1]

Team1:
101
```

---

### ENQUEUE 201

```text
TeamQueue:

[Team1 Team2]

Team1:
101

Team2:
201
```

---

### ENQUEUE 102

因為：

```text
102 屬於 Team1
```

直接接到 Team1 後面：

```text
TeamQueue:

[Team1 Team2]

Team1:
101 102

Team2:
201
```

---

### DEQUEUE

輸出：

```text
101
```

剩：

```text
Team1:
102

Team2:
201
```

---

### DEQUEUE

輸出：

```text
102
```

Team1 空了：

```text
TeamQueue:

[Team2]
```

---

## 時間複雜度

每次操作：

```text
push
pop
front
```

都是：

```text
O(1)
```

因此：

```text
Time: O(N)
```

```text
Space: O(N)
```

---

## 測資範例

### 輸入

```text
2
3 101 102 103
3 201 202 203
ENQUEUE 101
ENQUEUE 201
ENQUEUE 102
DEQUEUE
DEQUEUE
STOP
0
```

### 輸出

```text
Scenario #1
101
102
```

---

## 核心觀念

維護兩層 Queue：

```cpp
teamQueue
```

管理：

```text
隊伍順序
```

以及：

```cpp
memberQueue[team]
```

管理：

```text
隊員順序
```

如此即可在 O(1) 時間完成所有操作。

這題是 UVa 最經典的 Queue 進階題之一。