# 🛠️ 我的 n8n Workflow 集合 | My n8n Workflow Collection

呢個 repo 係我自己設計嘅 [n8n](https://n8n.io/) 自動化流程合集，幫手處理唔同類型嘅日常任務，例如 API 整合、內容創作、行銷、或者系統通知。

This repository contains a collection of my custom-designed [n8n](https://n8n.io/) automation workflows for handling various daily tasks such as API integration, content generation, marketing automation, and system notifications.

📌 有興趣嘅話可以 fork 或 star 呢個 repo！

Feel free to fork or star this repo if you're interested!

---

## 🚀 安裝 n8n | How to Install n8n

你可以用以下幾種方法安裝 n8n：

You can install n8n using one of the following methods:

### 方法 1：用 npm 安裝 | Method 1: Install via npm

```bash
npm install n8n -g
n8n
```

### 方法 2：用 Docker 安裝 | Method 2: Install with Docker

```bash
docker run -it --rm \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n
```

### 方法 3：用 Desktop App | Method 3: Use Desktop App

n8n 官方有提供 Windows / macOS / Linux 嘅桌面版，適合初學者安裝。

The official desktop app is available for Windows, macOS, and Linux, suitable for beginners.

👉 [下載連結 | Download here](https://n8n.io/download/)

---

## 📦 使用方式 | How to Use

1. 安裝好 n8n 之後，打開 `http://localhost:5678`
2. 匯入本 repo 裡面的 workflow（JSON 檔）
3. 根據需要修改節點，例如 API key、Webhook URL 等
4. 開始運行 🎉

After installing n8n:

1. Open `http://localhost:5678`
2. Import any workflow from this repo (JSON files)
3. Modify credentials, API keys, or webhook URLs as needed
4. Run and automate 🎉

---

## 📬 聯絡我 | Contact Me

如果你對某個 workflow 有興趣或者建議，可以開 Issue 或聯絡我：

If you're interested in a workflow or have suggestions, feel free to open an Issue or contact me:

📧 Email: `catowabisabi@gmail.com`

---

🧠 *持續更新中... 歡迎貢獻！*
*Always updating... Contributions are welcome!*
