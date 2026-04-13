# UVa 10035 - Primary Arithmetic

##  題目說明
給定兩個非負整數 `a` 和 `b`，需要計算在直式加法過程中產生的進位次數（carry operations）。

規則如下：
- 從個位數開始逐位相加
- 若相加結果 ≥ 10，則產生進位（carry）
- 進位會影響下一位的計算
- 計算整個加法過程中的進位總次數

---

##  解題思路
1. 使用 `while(cin >> a >> b)` 讀入多筆測資
2. 當 `a == 0 && b == 0` 時結束輸入
3. 將兩數從個位數開始逐位相加
4. 每次計算：
   - digit sum + carry
   - 若 ≥ 10，carry 次數 +1
5. 輸出 carry 次數

---

##  注意事項
- 數字可能很大，建議用字串處理
- 需模擬「逐位加法」
- 輸入以 `0 0` 作為結束

---

##  時間複雜度
- Time: O(n)
- Space: O(1)

---

##  測資範例

123 456
555 555
123 594
0 0


### 輸出

No carry operation.
3 carry operations.
1 carry operation.