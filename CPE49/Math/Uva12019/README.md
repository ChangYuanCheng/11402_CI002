# UVa 12019 - Doom's Day Algorithm

##  題目說明
給定年份中的「月 + 日」，需要計算該日期是星期幾。

本題使用固定基準日（Doomsday Algorithm），根據已知每年規則推算星期。

---

##  解題思路
1. 讀入測資數 T
2. 建立每個月份的固定偏移（基準日）
3. 對每筆測資：
   - 計算該月該日與「基準日」差距
   - 加上已知星期基準（2011/1/1 = Saturday）
4. 對 7 取模得到星期
5. 輸出對應英文星期

---

##  星期對應

0 = Sunday
1 = Monday
2 = Tuesday
3 = Wednesday
4 = Thursday
5 = Friday
6 = Saturday


---

##  注意事項
- 使用模運算 `% 7`
- 月份天數需正確處理
- 每組測資獨立計算

---

##  時間複雜度
- Time: O(1)
- Space: O(1)

---

##  測資範例

3
1 6
2 28
12 25


### 輸出

Thursday
Monday
Sunday