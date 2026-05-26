# UVa 490 - Rotating Sentences

## 題目說明
給定多行字串，請將整個文字矩陣順時針旋轉 90 度後輸出。

旋轉規則：
- 原本的列會變成新的行
- 由下往上組成新的字串
- 若某行長度不足，需要補空白

---

## 解題思路

1. 使用 `getline()` 讀入所有字串
2. 找出最長字串長度 `maxLen`
3. 依照旋轉規則輸出：
   - 外層：從 `0 ~ maxLen-1`
   - 內層：從最後一行往第一行掃描
4. 若目前位置超出字串長度：
   - 輸出空白 `' '`
5. 否則輸出對應字元

---

## 注意事項

- 必須使用 `getline()`
- 行數不固定，直到 EOF
- 短字串要補空白
- 不可刪除尾端空白

---

## 時間複雜度

- Time Complexity: `O(n × m)`
- Space Complexity: `O(n × m)`

其中：
- `n` = 行數
- `m` = 最長字串長度

---

## 測資範例

### Input

```txt
Rene Decartes once said,
"I think, therefore I am."
```

### Output

```txt
"R
ne
e "
tD
he
ic
na
kr
,t
 s
ta
h,
eo
rf
eo
rr
ee
  c
Ia
 m
."
```
