# 📬 Email and Job Management Workflow (n8n)

這個 n8n 工作流程自動化了郵件和求職管理的多個關鍵環節，結合了 Gmail、OpenAI、Telegram、Google Sheets 和一個客製化的網路爬蟲服務。

This n8n workflow automates several key aspects of email and job application management using Gmail, OpenAI, Telegram, Google Sheets, and a custom web scraping service.

---

## 🚀 功能特色 / Features

### 智慧郵件摘要 / Intelligent Email Summarization

* 使用 GPT-4o-mini 自動將郵件摘要為繁體中文
* 包括寄件人、時間、郵件類型（政府、保險、推廣等）
* 重要性評級（1-5 星）
* 生成摘要及建議是否回覆
* 自動起草英文回覆

### 自動郵件分類與管理 / Automated Email Categorization & Management

* **垃圾郵件**: 根據關鍵字自動移除垃圾郵件
* **資料夾歸檔**: 將特定郵件自動歸檔至 Gmail 資料夾（如 Job Ads / Enomars\_Achieve）

### 即時 Telegram 通知 / Real-time Telegram Notifications

* 發送以下項目的即時通知：

  * 新摘要郵件
  * 被移至垃圾桶的郵件
  * 被歸檔的郵件

### 自動職位提取與處理 / Automated Job Posting Extraction & Processing

* **Indeed 郵件解析**：擷取職位、公司、地點、薪資、描述等資訊
* **完整描述爬取**：透過 Selenium 爬蟲抓取完整內容
* **AI 職位摘要**：利用 GPT 整理職責與描述
* **Google Sheets 整合**：新增或更新工作清單至 Google Sheet
* **Telegram 職位提醒**：發送完整職位資訊至 Telegram

---

## ⚙️ 工作原理 / How It Works

### 1. 收件郵件觸發器 / Incoming Email Trigger

* Gmail Trigger 監控收件箱的新郵件（排除草稿）

### 2. 郵件管理與通知分支 / Email Management & Notification Branch

* **內容擷取**：獲取郵件完整內容
* **分類邏輯**：用 Python node 判斷是否屬於垃圾或應歸檔
* **條件路由**：

  * 若為垃圾，移除並發送通知
  * 若應歸檔，搜尋標籤並移動，然後通知
* **AI 摘要**：傳送郵件至 OpenAI 並取得 JSON 格式摘要結果
* **Telegram 傳送**：格式化並將摘要訊息發送至 Telegram

### 3. Indeed 職位處理分支 / Indeed Job Processing Branch

* **擷取資料**：用子工作流程擷取職位列表與連結
* **逐項處理**：每一個職位由 Split in Batches 單獨處理
* **網頁爬取**：透過 HTTP 與 Selenium 爬蟲取得完整 HTML
* **內容擷取**：用 HTML node 擷取職位描述
* **AI 分析**：使用 OpenAI 建構職責摘要
* **儲存至 Google Sheets**：更新 Jobs 工作表
* **通知 Telegram**：將職位詳情發送至 job alerts chat

---

## 🛠️ 設定要求 / Setup Requirements

* ✅ n8n 實例（本機 / Docker / 雲端）
* ✅ Gmail OAuth2 憑證
* ✅ OpenAI API Key
* ✅ Telegram Bot Token + chatId
* ✅ Google Sheets OAuth 憑證，包含權限
* ✅ Selenium 網路爬蟲服務端點（如：[https://selenium.org/scrape）](https://selenium.org/scrape）)
* ✅ 子工作流程：`Convert Indeed Gmail to HTML`

---

## ⚠️ 重要注意事項 / Important Notes

* **Markdown 轉義**：如郵件或職位內容含特殊字元，請啟用 Telegram Markdown 轉義邏輯（Code 節點）
* **爬蟲可靠性**：職位內容成功與否依賴於 Selenium 爬蟲的穩定性
* **move\_list 與 trash\_list**：在 Code1 node 自定義分類邏輯

---

💡 歡迎提問、fork、改進，或者 PR！如果有咩唔明，開個 issue 啦～
