# 第十週作業提交說明

## 1. LLM Wiki 主題與簡介

主題是「恐怖心理與恐怖敘事中的觀眾反應」。Wiki 以六大主題中的「恐怖心理」為主軸，連接聲音設計、預測處理、興奮／享受、研究綜述與後設情緒。

## 2. Wiki 成果

專案 GitHub：[horror-fear-wiki](https://github.com/vitas9313-sketch/horror-fear-wiki)。五篇來源登錄於 [`workflow/ingest-manifest.json`](../workflow/ingest-manifest.json)，對應五篇 [`wiki/`](../wiki/) 草稿；每篇都包含定義、核心敘述、證據、限制與引用。

## 3. 教學 HTML 簡報

[`slides/horror-lab-research.html`](../slides/horror-lab-research.html) 是靜態、可直接瀏覽的入門簡報，依序說明問題、理解框架、五篇研究、三個結論與工作流程。

## 4. Loop / Graph

流程是「取得資料 → 登錄來源 → PDF／SHA-256 檢查 → 受控 ingest → Wiki 整理 → 主張回查 → 產生 HTML → 瀏覽驗收」。Graph 以來源、概念、檔案檢查與投影片檢查為節點，關係標示支持、提出框架、測量與 gate；詳見 [`workflow/graph.json`](../workflow/graph.json) 與 [`workflow/loop-checklist.md`](../workflow/loop-checklist.md)。

來源檢查、引用回查與瀏覽驗收會重複執行；若主張找不到來源或來源檔案不是有效 PDF，就退回前一節點，不直接生成。

## 5. 實際執行與檢查紀錄

- 5 篇 PDF 均驗證 `%PDF-` 標頭、頁數與 SHA-256。
- 000–002 由使用者提供；003 來自 Frontiers 公開全文；004 來自 Open Access LMU submitted version。
- 5 個來源各有對應 Wiki 草稿；簡報中的研究卡片與核心結論可回到 Wiki 與 DOI。
- HTML 使用本機 CSS，沒有外部腳本、圖片或下載資產；已以瀏覽器開啟檢查。
- 文字檔 `git diff --check` 通過；PDF 以二進位檔保留，不用文字空白檢查誤判。

## 6. 反思

最常出錯的是「資料取得後的檔案驗證」：錯誤下載路徑曾回傳 404/Cloudflare HTML。調整後先檢查 `%PDF-` 與檔案大小，再計算 hash、確認頁數，最後才允許 ingest。這使檔案驗證從 ingest 後移到 ingest 前，並在 Graph 加入 gate，避免錯誤檔案污染 Wiki。
