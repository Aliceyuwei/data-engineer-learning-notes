# Continue 使用指南

> 搭配 GitHub Copilot 使用的設定與技巧

---

## 主要功能

| 功能 | 說明 | 快捷鍵 |
|------|------|--------|
| **Chat** | 對話式問答 | `Cmd+L` |
| **Inline Edit** | 直接在程式碼裡修改 | `Cmd+I` |
| **專案索引** | 讀整個專案後回答問題 | `@codebase` |
| **檔案引用** | 指定特定檔案提問 | `@filename` |

---

## 與 Copilot 搭配的建議方式

| 情境 | 用哪個 |
|------|--------|
| **打字時自動補全** | GitHub Copilot |
| **問單一函式/片段** | Copilot Chat |
| **問整個專案架構** | Continue + `@codebase` |
| **跨檔案搜尋問題** | Continue + `@codebase` |

- **Continue**：開源方案，讀整個專案能力強（`@codebase`），可接多種模型（包含本地模型），支援自訂工作流；建議與 Copilot 搭配，補全交給 Copilot，專案級問答交給 Continue

### 避免補全衝突
建議關掉 Continue 的 inline 補全，讓補全完全交給 Copilot：

> Continue 的強項在於外部知識與本地索引

| 指令 | 說明 |
| :--- | :--- |
| **`@codebase`** | **Continue 版全域搜尋**：讀取整個專案索引 |
| **`@docs`** | **最強功能**：讀取妳索引的官方文件 (Python 3, SQLite) |
| **`@file`** | 快速引用專案內的檔案 |
| **`@terminal`** | 抓取終端機輸出 (Continue 專屬介面) |

## ⚙️ 必做設定
- **關掉補全**：`"continue.enableTabAutocomplete": false` (交給 Copilot)
- **索引設定**：`"continue.indexing.enabled": true`