# 地圖翻譯準則（草案）

> [!IMPORTANT] 前言
> 地圖翻譯技術要點較多、翻譯困難，且鑒於現時WTEM仍可能出現無法預測的錯誤，若無標準化翻譯準則將導致翻譯工作量加大、質量低、工期長和稽核困難等一系列問題，囙此現擬一份地圖翻譯準則，用於幫助大家翻譯地圖。
>版本：1.1.0 By X209

## 一、關於WTEM提取
> [!TIP] 提示
> （本部分主要針對管理者）

### 1. 檢查選取是否出錯、出漏

WTEM選取後，應在翻譯工作開展前檢查選取是否出錯、出漏。 其檢查內容應至少包括：
- 新版本新增內容，WTEM可能還沒有支持；
- **是否有不支持翻譯鍵的JSON文字，導致WTEM不選取； 含轉義符的內容；** （特別關注）
-所有數据包是否正常運行，沒有語法錯誤。
- ~~含宏的內容~~（已支持）

選取完成後，應進地圖實地考察，查漏補缺並確保所有機制運行正常。

### 2. 重複鍵是否需要保留

一般情况下，只保留告示牌的鍵。若遇到特殊情况，如語序問題，則可能還需要保留實體的鍵。

**示例**：DE告示牌中的作者名和盔甲架名稱。

### 3. 剔除無需翻譯的鍵
在翻譯初期，先把無需翻譯的鍵隱藏以大幅减少無意義的工作。

無需翻譯的鍵包括：被丟棄的重複鍵、開發房中的絕大部分內容、數据包中用於協助開發的文字、等號或箭頭等分隔符和圖標，以及作者的遊戲內ID等。

**這一部分工作較難，切忌不要把該翻譯的東西省略了。**

## 二、關於文字翻譯
> [!TIP] 提示
> （這一部分主要面向翻譯者）

### 1. 翻譯實地求證

缺乏上下文、無法確定的翻譯通過在`data.json`或WTEM的log日誌中蒐索鍵值，複製座標後在世界中查證。 務必結合脉络！

示例：`play`可能是遊玩，也可能是播放！

### 2. 告示牌的翻譯
告示牌的翻譯較為特殊，因為有獨特的字數限制、行數限制與排版要求。

翻譯時要確保字數不超限，排版儘量美觀，沒有把握的話可以自己寫在告示牌上測試。

### 3. 物品描述的翻譯
物品描述通常有多行，將整句翻譯完成後按字數斷句，確保每行字數儘量相等，儘量不要出現空行。

斷句儘量在完整單詞的末尾，標點不要放在行首。 對於有特殊格式的文字，要確保文字與行數對應。

**示例：**
```
描述1
描述2
描述3.1 描述3.2（特殊格式） 描述3.3
描述4
```
### 4. 長文字的翻譯
長文字包括：`成書的內容`、`聊天框內容`等可能會因為文字過長而換行的文字。

長文字的翻譯較為特殊，由於Mojang閹割過的換行機制，文字太長會導致換行會出現問題。

此時需要手動在合適的字數後添加分行符號`\n`。
或使用較為特殊的管道，將原文的`<…> ` 等空格替換為`\u00a0`不間斷空格，來保證不會出現下麵的情况。

**錯誤示例：**
```
<某人>
   很長很長的一段話
```

**正確示例：**
```
<某人> 很長很長的\n
      一段話
```
```
<某人>\u00a0很長很長的
一段話
```

### 5. 關於專有名詞的翻譯
對於一些可能出現的原版名詞或常見的地圖術語，務必統一。 某些譯名尤其容易搞錯，多加小心，不確定的可以查閱wiki。

**示例**:`Leather Tunic皮革外套`、`Pink Wool粉紅色羊毛`、`Monument紀念碑`等等。

### 6. 關於自造詞、俚語的翻譯（較難）
翻譯中可能會出現一些自造詞、俚語、國外或社區一些梗，這些詞的翻譯工作比較困難，若無法解决可以求助。

比較好用的一些網站：

[ETYM](https://www.etymonline.com/tw)（詞源詞根詞綴）

[Wiktionary](https://zh.wiktionary.org/wiki/Wiktionary:%E9%A6%96%E9%A1%B5) （查詞的來源、詞根和詞綴，非常方便）

[Urban Dictionary](https://www.urbandictionary.com/) （查俚語，用的不多）
