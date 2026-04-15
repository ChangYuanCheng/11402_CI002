# UVa 11349 - Symmetric Matrix

##  題目說明
給定一個 n × n 的矩陣，判斷它是否為「對稱矩陣」。

對稱矩陣定義：
- 對所有 i, j：

M[i][j] == M[n-1-i][n-1-j]

- 且矩陣中所有數字必須為非負數

---

##  解題思路
1. 讀入測資數 T
2. 每組測資：
 - 讀入矩陣大小 n
 - 讀入 n × n 矩陣
3. 檢查對稱性：
 - 比較 M[i][j] 與 M[n-1-i][n-1-j]
4. 若全部相等且皆為非負數 → symmetric
5. 否則 → non-symmetric

---

##  注意事項
- 必須檢查所有對應位置
- 只要有一個不符合 → 直接判定 non-symmetric
- n 可能為 0 或 1（一定 symmetric）

---

##  時間複雜度
- Time: O(n²)
- Space: O(n²)

---

##  測資範例

1
3
5 1 3
2 0 2
3 1 5


### 輸出

Test #1: Symmetric.