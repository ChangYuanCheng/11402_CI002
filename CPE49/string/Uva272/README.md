# UVa 272 - TEX Quotes

## 題目說明
將文章中的雙引號 `"` 替換成 TEX 格式引號。

替換規則：
- 第一個 `"` 替換成：
  `` 
- 第二個 `"` 替換成：
  ''

之後持續交替替換。

---

## 解題思路

1. 使用 `getline()` 讀入每一行直到 EOF
2. 使用布林變數 `open` 紀錄目前是：
   - 開引號
   - 還是閉引號
3. 掃描每個字元：
   - 若不是 `"`：
     - 直接輸出
   - 若是 `"`：
     - `open == true`
       - 輸出 `` 
     - 否則：
       - 輸出 ''
4. 每次替換後切換 `open`

---

## 注意事項

- 必須使用 `getline()`
- 題目輸入直到 EOF
- 每遇到一個 `"` 就交替替換
- 不是英文雙引號，而是 TEX 格式引號

---

## 時間複雜度

- Time Complexity: `O(n)`
- Space Complexity: `O(1)`

其中：
- `n` = 所有字元總數

---

## 測資範例

### Input

```txt
"To be or not to be," quoth the Bard, "that is the question".
```

### Output

```txt
``To be or not to be,'' quoth the Bard, ``that is the question''.
```