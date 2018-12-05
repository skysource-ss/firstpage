---
layout: analysis
---

# 相關性指標：NPMI
PMI (Pointwise Mutual Information) 可用來描述兩變數間的相關性：

$PMI(x, y) = \log \frac {p(x,y)}{p(x)p(y)},$  

$-\infty < PMI(x, y) < \min[-\log p(x), -\log p(y)]$ 

但因不同變數間的 PMI 值域不同，無法跨變數比較，故採用 NPMI (Normalized PMI):

$NPMI(x, y) = \frac {PMI(x, y)}{-\log p(x, y)}, -1 < NPMI(x, y) < 1$  

在實驗中，NPMI 能更好的表達`職務`與`科系類別`及`專業證照`的關係

# 競爭力分析
## Q1.1：我就讀的科系，對哪些工作更相關？
對每個職業進行「科系的相關性排名」，可橫向比較具更高相關度的職業。  
範例：`醫藥工程學類`, `會計學類`, `風險管理學類`, `食品科學類`, `競技運動學類`, `公共衛生學類`

{% include table1.html %}

## Q1.2：哪些科系，對我有興趣的職業更相關？
[1] 輸入關鍵字，透過 FastText 找出相似的職業

  ![醫療](/data/fasttext_1.png)
  ![食品](/data/fasttext_2.png)

[2] 選擇職業 (範例： `醫療器材研發工程師`)

{% include table3.html %}

## Q2.1：我擁有的證照，在哪些工作更相關？  
範例：`甲級廢水處理專責人員`, `結構型商品銷售人員`, `高考會計師`

{% include table2.html %}

## Q2.2：哪些證照，對我有興趣的職業更相關？
範例： `環保／環境工程師／技師`, `投資理財人員`, `會計師`

{% include table4.html %}

## 最後，用特徵選擇找出「加分項目」
除了利用 NPMI 估計相關度，Linear SVM 以及特徵選擇，找出每份工作中最具有預測能力的學類/證照  
範例： `環保／環境工程師／技師`, `投資理財人員`, `會計師`

{% include table5.html %}