# UVa 10226 - Hardwood Species

##  題目說明
給定多筆樹種名稱（字串），需要統計每種樹出現的比例，並依字典序輸出結果。

輸入格式：
- 每一筆測資是一棵樹的名稱
- 測資之間以空行分隔
- 直到 EOF 結束

輸出格式：
- 每個樹種名稱 + 出現百分比（小數點四位）
- 依字典序排列

---

##  解題思路
1. 讀入測資組數 t
2. 每組測資：
   - 使用 map<string, int> 統計樹種數量
   - 計算總數 total
3. 讀入每個樹名直到空行或 EOF
4. 統計完後：
   - 依字典序輸出 map
   - 計算百分比：
     - count / total * 100
5. 每組測資之間輸出空行

---

##  注意事項
- 使用 getline 讀整行
- 注意空行代表測資分隔
- map 會自動排序（字典序）
- 百分比需固定輸出 4 位小數

---

##  時間複雜度
- Time: O(n log n)
- Space: O(n)

---

##  測資範例

3
Red Alder
Ash
Aspen

2
Red Alder
Red Alder


### 輸出

Ash 33.3333
Aspen 33.3333
Red Alder 33.3333

Red Alder 100.0000