# UVa 10035 - Primary Arithmetic

> 📄 **Original Problem:**  
> https://onlinejudge.org/external/100/10035.pdf

## 題目說明
給定兩個非負整數 `a` 和 `b`，需要計算在直式加法過程中產生的進位次數（carry operations）。

規則如下：
- 從個位數開始逐位相加
- 若相加結果大於等於 `10`，則產生一次進位（carry）
- 進位會影響下一位的計算
- 計算整個加法過程中的進位總次數

---

## 解題思路
1. 使用 `while (cin >> a >> b)` 讀入多筆測資
2. 當 `a == "0"` 且 `b == "0"` 時結束輸入
3. 從個位數開始逐位相加
4. 每次計算：
   - `digit1 + digit2 + carry`
   - 若結果大於等於 `10`：
     - carry 次數加一
     - 下一位 carry = 1
   - 否則 carry = 0
5. 輸出 carry 次數

---

## 注意事項
- 數字可能非常大，建議使用字串處理
- 需完整模擬直式加法
- 輸入以 `0 0` 作為結束
- 根據 carry 次數輸出不同格式：
  - `No carry operation.`
  - `1 carry operation.`
  - `n carry operations.`

---

## 時間複雜度
- **Time:** O(n)
- **Space:** O(n)（字串解法）

---

## 測資範例

### Input
```text
123 456
555 555
123 594
0 0
```

### Output
```text
No carry operation.
3 carry operations.
1 carry operation.
```
