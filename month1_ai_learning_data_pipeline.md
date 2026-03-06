# 🚀 Month 1 專案：AI Learning Data Pipeline

> 目標：建立一個完整的 **Data Engineering ETL Pipeline**  
> 將 Markdown 學習筆記轉換為結構化資料，並建立自動化學習報告。

------------------------------------------------------------------------

# 專案名稱

    ai-learning-data-pipeline

------------------------------------------------------------------------

# 系統目標

將 Markdown 學習紀錄：

- 解析為結構化資料
- 存入 SQLite 資料庫
- 自動產生學習分析
- 發送 Telegram 通知

------------------------------------------------------------------------

# 系統架構

    Markdown Learning Notes
            │
            │ (Extract)
            ▼
    Markdown Parser
            │
            │ (Transform)
            ▼
    Structured Data (JSON)
            │
            │ (Load)
            ▼
    SQLite Database
            │
            ▼
    Data Analysis
            │
            ▼
    Telegram Daily Report

------------------------------------------------------------------------

# Markdown 學習紀錄格式

資料來源：

    learning_notes/
        2026-03-01.md
        2026-03-02.md

Markdown 範例：

    # Learning Log - 2026-03-01

    ## 今日主題
    Python File IO

    ## 學習進度
    - 了解 open()
    - 讀取 txt
    - 寫入 JSON

    ## 學習困難
    - 不懂 generator

    ## 解決方式
    - 查 Python 官方文件
    - 用 AI 解釋 yield

    ## 學習時間
    3

------------------------------------------------------------------------

# Parser 輸出 JSON

    {
     "date": "2026-03-01",
     "topic": "Python File IO",
     "progress": [
       "了解 open()",
       "讀取 txt",
       "寫入 JSON"
     ],
     "difficulty": [
       "不懂 generator"
     ],
     "solution": [
       "查 Python 官方文件",
       "用 AI 解釋 yield"
     ],
     "hours": 3
    }

這一步就是：

    Extract + Transform

------------------------------------------------------------------------

# SQLite 資料表設計

Table

    learning_logs

Schema

    id INTEGER PRIMARY KEY
    date TEXT UNIQUE
    topic TEXT
    progress TEXT
    difficulty TEXT
    solution TEXT
    hours INTEGER
    created_at TIMESTAMP

說明：

- `progress` / `difficulty` / `solution` 使用 JSON 儲存
- `date` 設為 UNIQUE，避免重複資料

------------------------------------------------------------------------

# ETL Pipeline 設計

流程：

    掃描 Markdown
    ↓
    解析資料
    ↓
    資料轉換
    ↓
    存入資料庫

程式流程：

    scan_md_files()
            ↓
    parse_markdown()
            ↓
    transform_data()
            ↓
    save_to_database()

------------------------------------------------------------------------

# 分析功能

每日產生學習摘要

SQL 範例：

    SELECT
    date,
    topic,
    hours
    FROM learning_logs
    ORDER BY date DESC
    LIMIT 7

輸出：

    本週學習報告

    Python ETL - 3h
    SQL Aggregation - 2h
    Docker Basics - 2h

    總學習時間: 7h

------------------------------------------------------------------------

# Telegram 通知

通知內容：

    📊 今日學習報告

    日期: 2026-03-01
    主題: Python File IO
    學習時間: 3h

    困難:
    - generator

    解法:
    - 官方文件
    - AI解釋

------------------------------------------------------------------------

# 專案資料夾結構

    ai-learning-data-pipeline
    │
    ├─ data
    │   └─ learning_notes
    │
    ├─ src
    │
    │   ├─ parser
    │   │   └─ markdown_parser.py
    │
    │   ├─ etl
    │   │   └─ pipeline.py
    │
    │   ├─ db
    │   │   └─ sqlite_manager.py
    │
    │   ├─ notifier
    │   │   └─ telegram_bot.py
    │
    │   └─ main.py
    │
    ├─ tests
    │
    ├─ requirements.txt
    │
    └─ README.md

------------------------------------------------------------------------

# Month 1 每週目標

## Week 1 --- Python 專案與 Markdown Parser

**本週任務**

- [ ] 建立 Git repository 與 Python 專案環境
- [ ] 建立 `ai-learning-data-pipeline` 專案目錄結構
- [ ] 設計並定義 Markdown 學習筆記格式規範
- [ ] 實作 `markdown_parser.py` 將文字轉為 Python Dict
- [ ] 實作 CLI 介面並輸出 JSON

**學習重點**

- Python File I/O
- JSON 資料處理
- Regular Expression (Regex)
- Project Structure (專案結構化)

------------------------------------------------------------------------

## Week 2 --- 建立 ETL Pipeline

**本週任務**

- [ ] 實作 `pipeline.py` 進行批次掃描
- [ ] 實作 Data Transformation (資料轉換)
- [ ] 建立 SQLite Database 並定義 Schema
- [ ] 將解析後的資料 Upsert 入資料庫

**學習重點**

- ETL Pipeline 工作流
- Data Modeling (資料建模)
- SQLite 語法與 Python 操作
- Module Design (模組化設計)

------------------------------------------------------------------------

## Week 3 --- Telegram Bot

**本週任務**

- [ ] 申請並建立 Telegram Bot
- [ ] 實作 `telegram_bot.py` 模組
- [ ] 串接 Pipeline：當 ETL 完成後發送通知
- [ ] 產出每日學習 Summary 報表

**學習重點**

- API Integration (API 串接)
- Token & Environment Variables (環境變數管理)
- 異步/同步通知處理

------------------------------------------------------------------------

## Week 4 --- 程式品質

**本週任務**

- [ ] 建立 Logging 系統記錄執行軌跡
- [ ] 加入 Error Handling 異常處理機制
- [ ] 撰寫 `pytest` 單元測試與整合測試

**學習重點**

- Logging 最佳實踐
- Unit Testing (單元測試)
- Maintainability (程式碼可維護性)

------------------------------------------------------------------------

# Month 1 最終作品

GitHub 專案：

    AI Learning Data Pipeline

README 描述：

> A simple data pipeline that extracts learning notes from Markdown, transforms them into structured data, stores them in SQLite, and sends daily reports through Telegram.

------------------------------------------------------------------------

# 面試時可以這樣描述

> 我建立了一個 ETL pipeline，  
> 將 Markdown 學習筆記轉換為結構化資料並儲存到資料庫，  
> 並建立自動化學習報告通知系統。
