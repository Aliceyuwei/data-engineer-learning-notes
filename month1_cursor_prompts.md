# Month 1 VS Code + Copilot + Gemini CLI Prompt 套件（Week1～Week4）

本文件提供 **VS Code + Copilot + Gemini CLI 開發流程的 Prompt 套件**。  
使用方式：你可以將這些 Prompt 提供給 Gemini CLI，讓它直接協助你進行專案開發與檔案操作。

------------------------------------------------------------------------

# Week 1：Python 專案與 Markdown Parser

## W1-P0：建立專案骨架

    你是資深 Python 工程師。請幫我建立專案骨架，專案名稱 ai-learning-data-pipeline。

    需求：
    1) 建立資料夾結構：data/learning_notes、src/parser/、src/etl/、src/db/、src/notifier/、tests/
    2) 建立 requirements.txt（包含：python-dotenv、requests、pytest）
    3) 建立 README.md（中文），包含：專案目的、安裝方式、如何執行、資料格式範例
    4) 建立 .gitignore（Python 常見）
    5) src/main.py 先印出 "hello pipeline"

    請直接在當前目錄下建立這些資料夾與檔案。

------------------------------------------------------------------------

## W1-P1：定義 Markdown 資料格式

    請幫我定義「學習紀錄 Markdown」的格式規範（用中文），並在 data/learning_notes/ 下建立 2 份範例檔案：
    - 2026-03-01.md
    - 2026-03-02.md

    規範要求：
    1) 必須包含：今日主題、學習進度、學習困難、解決方式、學習時間
    2) 學習進度/困難/解法使用清單（- 開頭）
    3) 學習時間是整數（小時）
    4) 標題第一行為：# Learning Log - YYYY-MM-DD

------------------------------------------------------------------------

## W1-P2：實作 Markdown Parser

    請用 Python 實作一個 Markdown 解析器，檔案路徑為 src/parser/markdown_parser.py。

    功能：
    - 輸入：Markdown 文字字串（str）
    - 輸出：dict，格式如下：

    {
     "date": "YYYY-MM-DD",
     "topic": "...",
     "progress": ["..."],
     "difficulty": ["..."],
     "solution": ["..."],
     "hours": 3
    }

    解析規則：
    1) date 從第一行 # Learning Log - YYYY-MM-DD 取得
    2) 主題從「## 今日主題」段落取得（下一行文字）
    3) progress/difficulty/solution 從對應段落下的 - 清單取得
    4) hours 從「## 學習時間」下一行取得整數

    另外：
    - 提供 parse_markdown(text: str) 函式
    - 對格式錯誤丟出 ValueError
    - 提供簡單 __main__ 測試，並確保可以執行。

------------------------------------------------------------------------

## W1-P3：Parser 單元測試

    請用 pytest 為 src/parser/markdown_parser.py 撰寫單元測試，檔案路徑為 tests/test_markdown_parser.py。

    測試需求：
    1) 正常案例解析成功
    2) 缺少「## 今日主題」要拋 ValueError
    3) 學習時間不是整數要拋 ValueError
    4) 清單段落允許空清單，但欄位輸出空陣列

    撰寫完成後，請協助執行測試以確保正確。

------------------------------------------------------------------------

## W1-P4：命令列工具

    請修改 src/main.py，將其改裝為一個命令列工具。

    用法：
    python -m src.main parse data/learning_notes/2026-03-01.md

    功能：
    1) 讀取 md 檔
    2) parse_markdown
    3) 印出 JSON

    要求：
    - 參數錯誤提示用法
    - 找不到檔案提示
    - 成功時 exit code 0，失敗時 exit code 1

------------------------------------------------------------------------

# Week 2：建立 ETL Pipeline + SQLite

## W2-P1：SQLite Schema + DB 模組

    請幫我設計 SQLite 資料表 learning_logs，並實作 src/db/sqlite_manager.py。

    需求：
    1) DB 檔案路徑：data/learning.db
    2) Table learning_logs

    欄位：
    id INTEGER PRIMARY KEY
    date TEXT UNIQUE
    topic TEXT
    progress TEXT
    difficulty TEXT
    solution TEXT
    hours INTEGER
    created_at TEXT

    提供方法：
    - init_db()
    - upsert_learning_log(log: dict)
    - get_recent_logs(limit=7)

------------------------------------------------------------------------

## W2-P2：建立 ETL Pipeline

    請幫我實作 src/etl/pipeline.py。

    功能：
    1) 掃描 data/learning_notes/*.md
    2) 使用 parser 解析
    3) 存入 SQLite

    執行後回傳 summary：
    - 總檔案數
    - 成功數
    - 失敗數
    - 失敗原因

------------------------------------------------------------------------

# Week 3：Telegram Bot

## W3-P1：Telegram 通知模組

    實作 src/notifier/telegram_bot.py。

    需求：
    1) 從環境變數讀取：TELEGRAM_BOT_TOKEN, TELEGRAM_CHAT_ID
    2) 實作 send_message(text)
    3) 呼叫 Telegram API sendMessage 進行傳送

------------------------------------------------------------------------

## W3-P2：ETL 完成通知

    整合 ETL 流程：當 ETL 完成後，自動執行以下步驟：

    1) 從 DB 取得最新 log
    2) 組合 Telegram 訊息（包含：日期、主題、學習時間、困難、解法）
    3) 發送通知

------------------------------------------------------------------------

# Week 4：程式品質

## W4-P1：加入 Logging

    實作 src/utils/logger.py。

    需求：
    - logging 格式包含時間、level、模組
    - 預設等級為 INFO
    - 可透過 LOG_LEVEL 環境變數控制

------------------------------------------------------------------------

## W4-P2：資料品質檢查

    在 Parser 或 Pipeline 中加入 Data Quality Rule：

    1) date 格式必須為 YYYY-MM-DD
    2) topic 不能為空
    3) hours 範圍必須在 0~24 之間
    4) progress/difficulty/solution 必須為 list[str]

------------------------------------------------------------------------

## W4-P3：Pipeline 整合測試

    使用 pytest 建立整合測試，路徑為 tests/test_pipeline_integration.py。

    測試情境：
    1) 放入 2 個範例 md 檔
    2) 執行 pipeline
    3) 確認 DB 是否正確寫入 2 筆資料
    4) 測試容錯：若其中 1 個檔案損毀，是否能成功處理另一個並回報失敗。
