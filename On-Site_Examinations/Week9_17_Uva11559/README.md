# UVa 11559 - Event Planning

## 題目說明

有：

- N 個參加者
- 預算 B
- H 間旅館
- W 個週末

每間旅館會提供：

- 每人住宿價格
- 每個週末可提供的床位數

要求找出：

```text
能夠容納所有人
且不超過預算
的最低總花費
```

若沒有任何方案符合：

```text
stay home
```

---

## 解題思路

### 住宿總費用

若某旅館每人價格為：

```text
price
```

共有：

```text
N 人
```

總花費：

```cpp
price * N
```

---

### 床位條件

某週末必須滿足：

```cpp
beds >= N
```

才能容納所有人。

---

### 預算條件

找到所有符合：

```cpp
beds >= N
```

的方案後，

取最小：

```cpp
price * N
```

最後判斷：

```cpp
ans <= B
```

即可。

---

## 演算法流程

### 讀入資料

```cpp
cin >> N >> B >> H >> W;
```

其中：

```text
N = 人數
B = 預算
H = 旅館數
W = 週末數
```

---

### 掃描所有旅館

```cpp
for(int i=0;i<H;i++)
```

讀入：

```cpp
price
```

---

### 掃描所有週末

```cpp
for(int j=0;j<W;j++)
```

讀入：

```cpp
beds
```

---

### 判斷是否住得下

```cpp
if(beds >= N)
```

表示：

```text
此週末有足夠床位
```

---

### 更新最小花費

```cpp
ans = min(ans, price * N);
```

---

### 最後判斷

```cpp
if(ans <= B)
```

輸出最小花費。

否則：

```text
stay home
```

---

## 範例分析

### 輸入

```text
3 1000 2 3
200
3 3 3
300
3 3 3
```

---

旅館 1

```text
每人 200 元
```

總費用：

```text
200 × 3 = 600
```

符合。

---

旅館 2

```text
每人 300 元
```

總費用：

```text
300 × 3 = 900
```

符合。

---

取最小：

```text
600
```

輸出：

```text
600
```

---

## 程式碼講解

### 初始化答案

```cpp
int ans = 1e9;
```

先設成很大的數。

---

### 讀取房價

```cpp
int price;
cin >> price;
```

---

### 讀取每個週末床位

```cpp
int beds;
cin >> beds;
```

---

### 若可容納

```cpp
if(beds >= N)
```

更新答案：

```cpp
ans = min(ans, price * N);
```

---

### 最終輸出

```cpp
if(ans <= B)
    cout << ans << endl;
else
    cout << "stay home" << endl;
```

---

## 時間複雜度

共有：

```text
H 間旅館
W 個週末
```

需要檢查：

```text
H × W
```

次。

因此：

```text
Time: O(H × W)
```

```text
Space: O(1)
```

---

## 測資範例

### 輸入

```text
3 1000 2 3
200
3 3 3
300
3 3 3
```

### 輸出

```text
600
```

---

## 核心觀念

對每間旅館：

```cpp
cost = price * N;
```

若某週末：

```cpp
beds >= N
```

代表可以入住。

從所有可入住方案中找：

```cpp
最小 cost
```

最後判斷：

```cpp
cost <= 預算
```

即可。

這題是 UVa 經典的模擬與條件判斷題。