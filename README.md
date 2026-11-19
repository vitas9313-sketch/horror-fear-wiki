# HORROR LAB｜恐怖心理與恐怖敘事 LLM Wiki

## 1. LLM Wiki 主題與簡介

本 Wiki 的主題是「恐怖心理與恐怖敘事中的觀眾反應」。內容整理恐怖作品如何透過聲音、未知感、預測誤差與情緒設計，引發觀眾的恐懼、興奮與享受。

本專案以五篇學術資料為基礎，建立可追溯的 Wiki 草稿，並將研究內容轉化為適合初學者閱讀的教學型 HTML 簡報。

## 2. LLM Wiki 成果

Wiki 成果位於 [`wiki/`](./wiki/) 資料夾，共有五篇條目。每篇包含定義、核心敘述、證據與引用、限制及延伸連結。

1. [Paper 1｜聲音與恐怖情緒](./wiki/paper-1-sound-nonlinear-analogues-film-soundtracks.md)
2. [Paper 2｜預測處理與恐怖片](./wiki/paper-2-predictive-processing-horror-engagement.md)
3. [Paper 3｜恐怖場景中的興奮與享受](./wiki/paper-3-excitement-enjoyment-horror-scenes.md)
4. [Paper 4｜恐怖電影心理反應研究綜述](./wiki/paper-4-horror-psychology-review.md)
5. [Paper 5｜Need for Affect 與恐怖／戲劇觀影](./wiki/paper-5-need-for-affect-horror-drama.md)

五篇來源與檔案驗證資料記錄於 [`workflow/ingest-manifest.json`](./workflow/ingest-manifest.json)。

## 3. 教學 HTML 簡報

▶ [開啟教學 HTML 簡報：為什麼人會享受恐怖？](./slides/horror-lab-research.html)

簡報以初學者為對象，依序說明害怕與喜歡可以同時存在、預測處理、五篇研究的角色，以及恐懼、興奮、享受與後設情緒的差異。

## 4. Loop／Graph 設計

### 簡報生成流程

```text
五篇來源
  ↓
AI 整理研究重點
  ↓
人檢查證據與研究限制
  ↓
AI 提出簡報大綱
  ↓
人確認教學順序
  ↓
逐頁生成投影片內容
  ↓
逐頁回查引用與邏輯
  ↓
產生 HTML
  ↓
瀏覽器檢查與修正
```

### 每個節點的輸入、輸出與檢查

| 節點 | 輸入 | 輸出 | 檢查方式 |
|---|---|---|---|
| 來源整理 | 5 篇 PDF | 研究重點與限制 | AI 初整理，人核對來源 |
| 簡報大綱 | 研究重點 | 教學順序與頁面目的 | 人確認初學者是否能理解 |
| 逐頁生成 | 已確認大綱 | 每頁標題、說明與引用 | 逐頁回查 Wiki 與 DOI |
| HTML 生成 | 已確認的投影片內容 | HTML 簡報 | 瀏覽器、可讀性與引用檢查 |

Graph 的節點包含來源、研究概念、Wiki 條目、簡報大綱、逐頁內容、檔案驗證與投影片主張；邊表示支持、提出框架、轉換或通過檢查。完整 Graph 見 [`workflow/graph.json`](./workflow/graph.json)。

Loop 會重複執行來源驗證、引用回查與瀏覽器驗收。若 PDF 檢查失敗，退回來源驗證；若主張找不到引用，退回 Wiki 整理；若大綱不適合初學者，退回大綱設計；若 HTML 顯示錯誤，退回逐頁生成。

## 5. 實際執行結果與檢查紀錄

- 完成五篇資料的受控 ingest。
- 五個 PDF 均確認以 `%PDF-` 開頭，並完成頁數與 SHA-256 記錄。
- 五篇來源各自對應一篇 Wiki 條目。
- HTML 簡報已用瀏覽器開啟檢查，可正常閱讀，且不依賴外部圖片或腳本。
- 已執行 `git diff --check`；文字檔檢查通過，PDF 維持二進位檔保存。
- 檢查結果與來源雜湊記錄於 [`workflow/ingest-manifest.json`](./workflow/ingest-manifest.json)。

## 6. 反思與流程調整

最常出錯的節點是「資料下載後的檔案驗證」。錯誤網址曾回傳 404 或 Cloudflare HTML，而不是 PDF。

因此我把檢查往前移到 ingest 之前：先確認 PDF 標頭與檔案大小，再確認頁數、計算 SHA-256，最後才允許資料進入 Wiki。這項調整也加入 Graph 的檔案驗證 gate，避免錯誤檔案污染 Wiki 或簡報。

---

GitHub Repository：[horror-fear-wiki](https://github.com/vitas9313-sketch/horror-fear-wiki)
