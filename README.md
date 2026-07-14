# 🏮 燭之武退秦師：墨韻尋蹤填空小遊戲

一款專為國文課堂設計的互動教學網頁小遊戲，融合古典水墨視覺風格，將《左傳·燭之武退秦師》的核心課文段# 🏮 燭之武退秦師：網頁遊戲建置與 GitHub 部署復盤筆記

這份筆記完整記錄了 **2026 年 7 月 14 日**，我們一起將互動小遊戲從無到有設計、轉型，並成功發布至網際網路（GitHub Pages）且**串接 Google 試算表自動收分後台**的完整歷程與關鍵知識點，方便您日後隨時查閱、快速複習。

---

## 📅 今日執行成果與歷程 (Recap)

### 第一階段：遊戲設計、轉型與視覺古風化
* **設計理念：** 打造一款沉浸感十足、兼具課堂投影互動與課後複習價值的「國文水墨小遊戲」。
* **內容轉型：** 由原先的「唐詩尋蹤記」全面升級為經典課文 **《左傳·燭之武退秦師》** 核心外交辭令與名句填空。
* **古典美學設計：** 採用淡雅水墨山水背景、宣紙質感容器，以及硃砂紅與墨黑配色，提升美感體驗。

### 第二階段：建立 GitHub 雲端專案
* **GitHub 帳號：** `samotaxie`
* **專案（Repository）名稱：** `tang-poetry-game`
* **專案連結：** [https://github.com/samotaxie/tang-poetry-game](https://github.com/samotaxie/tang-poetry-game)
* **狀態設定：** 已設定為 **Public (公開)**，這是確保學生能順利看見網頁的關鍵設定。

### 第三階段：後台自動收分系統（Apps Script）調試歷程
這是今日最核心的技術進展！我們捨棄了繁瑣且容易出錯的 Google 表單 `entry.ID` 盲測，改用 **Google Apps Script 網頁應用程式（Web App）** 作為「自動收分小秘書」：

1. **工作表路徑迷失（getActiveSheet 錯誤排查）：**
   * **問題：** 測試時網頁結算畫面跳出 `TypeError: Cannot read properties of null (reading 'getActiveSheet')` 錯誤。
   * **原因：** Google 系統暫時無法辨識獨立腳本附屬於哪張試算表，或是在背景執行時無法鎖定作用中的工作表。
   * **解決：** 我們在 Apps Script 程式碼中，改用 `SpreadsheetApp.openByUrl("試算表網址")` **強制綁定試算表**，並用 `getSheets()[0]` 鎖定第一個分頁，徹底解決路徑迷失問題。

2. **部署版本更新（重新部署的黃金法則）：**
   * **關鍵學習：** 在 Google Apps Script 中，**只要修改程式碼，就必須在部署設定中選擇「新版本 (New version)」重新發布**，網址與代碼才會正式生效。
   * **最終網址：** 成功部署並取得最新、可暢通接收資料的 Web App 執行 URL。

---

## 🔗 本專案關鍵網址

* **您的專案後台 (修改原始碼用)：** 
  [https://github.com/samotaxie/tang-poetry-game](https://github.com/samotaxie/tang-poetry-game)
* **您的後台成績接收試算表：**
  [https://docs.google.com/spreadsheets/d/1tnZIoq0XYif3EfZJgjvo7Wu1-qYc3AFlOkxt8oM8yIg/edit](https://docs.google.com/spreadsheets/d/1tnZIoq0XYif3EfZJgjvo7Wu1-qYc3AFlOkxt8oM8yIg/edit)
* **學生的線上遊戲遊玩網址：** 
  👉 **[https://samotaxie.github.io/tang-poetry-game/](https://samotaxie.github.io/tang-poetry-game/)**

---

## 🛠️ 基礎維護：未來如何修改/新增題目？

如果您之後想要更換題目，不需要重新上傳檔案，可以直接在 GitHub 網頁上編輯[cite: 2]：

1. 進入您的 [tang-poetry-game 專案頁面](https://github.com/samotaxie/tang-poetry-game)。
2. 點擊 **`index.html`** 檔案。
3. 點擊右上角的 **「筆刷圖示 ✏️」** 進入編輯模式[cite: 2]。
4. 滾動到程式碼中下方的 `const allQuestions = [...]` 區塊，按照以下格式直接修改文字與答案：
   ```javascript
   {
       id: 題號,
       q: "欲呈現的課文，想挖空的部分請用 <span class='blank'> </span> 代替",
       options: ["選項A", "選項B", "選項C", "選項D"],
       answer: 正確答案的索引值 (從 0 開始計算：0=A, 1=B, 2=C, 3=D),
       text: "正確答案的完整文字說明"
   }落轉化為趣味填空關卡。

### 🔗 遊戲線上遊玩網址
👉 **[點我立即進入歷史現場](https://samotaxie.github.io/tang-poetry-game/)**

---

## 📅 專案發展歷程
本專案最初為「唐詩尋蹤記」互動遊戲，於 2026 年 7 月進行全面性的「古風化」視覺與內容升級：
1. **風格翻新**：全面採用淡雅水墨山水背景、宣紙質感容器，以及硃砂紅、墨黑色古典配色。
2. **教材整合**：將經典課文《燭之武退秦師》的名句外交辭令融入填空設計。
3. **後台自動化**：首創「夫子案頭」成績自動回傳功能，學生遊玩結束後，成績與錯題紀錄將直接同步至老師的 Google 表單後台，免去人工登記的繁瑣流程。

---

## 🎮 遊戲核心功能

* **古典美學介面**：沉浸式的水墨風格，提升學生在課堂互動或自主練習時的學習樂趣。
* **姓名/座號登錄**：進入遊戲前需輸入基本資訊，方便教師辨識與集中打分數。
* **精選五大關卡**：
  *  *第一關*：晉侯、秦伯圍鄭，以其無禮於晉，且貳於**楚**也。
  *  *第二關*：臣之壯也，猶不如人；今老矣，**亦無能為矣**。
  *  *第三關*：若舍鄭以為東道主，**行李之往來**，君亦無所害。
  *  *第四關*：夫晉，何厭之有？既東封鄭，又欲肆其**西封**。
  *  *第五關*：因人之力以敝之，**不仁**；失其所與，不知；以亂易整，不武。
* **古典評語導引**：根據得分給予「才高八斗，墨韻琴心」或「冥頑不靈，重修舊好」等富含文學底蘊的互動評語與學習建議。

---

## 🛠️ 教師維護與題目修改指南

如果您未來想要微調課文題目、更換填空挖空位置，不需要重新編寫網頁，直接在 GitHub 線上即可完成：

1. 點擊進入 `index.html` 檔案。
2. 點擊右上角的 **「筆刷圖示 ✏️」** 進入編輯模式。
3. 尋找程式碼中下方的 `const allQuestions = [...]` 區塊。
4. 按照以下格式修改文字與答案索引：
   ```javascript
   {
       id: 題號,
       q: "欲呈現的課文，想挖空的部分請用 <span class='blank'> </span> 代替",
       options: ["選項A", "選項B", "選項C", "選項D"],
       answer: 正確答案的索引值 (從 0 開始計算：0=A, 1=B, 2=C, 3=D),
       text: "正確答案的完整文字說明"
   }
