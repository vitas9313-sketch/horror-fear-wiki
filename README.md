# HORROR LAB｜恐怖心理與恐怖敘事 LLM Wiki

## 1. LLM Wiki 主題與簡介

本 Wiki 的主題是「恐怖心理與恐怖敘事中的觀眾反應」。內容整理恐怖作品如何透過聲音、未知感、預測誤差與情緒設計，引發觀眾的恐懼、興奮與享受。

本專案以五篇學術資料為基礎，建立可追溯的 Wiki 條目，並將研究內容轉化為適合初學者閱讀的教學型 HTML 簡報。

## 2. LLM Wiki 成果

Wiki 成果位於 [`wiki/`](./wiki/) 資料夾，共有五篇條目。每篇包含定義、核心敘述、證據與引用、限制及延伸連結。

1. [Paper 1｜聲音與恐怖情緒](./wiki/paper-1-sound-nonlinear-analogues-film-soundtracks.md)
2. [Paper 2｜預測處理與恐怖片](./wiki/paper-2-predictive-processing-horror-engagement.md)
3. [Paper 3｜恐怖場景中的興奮與享受](./wiki/paper-3-excitement-enjoyment-horror-scenes.md)
4. [Paper 4｜恐怖電影心理反應研究綜述](./wiki/paper-4-horror-psychology-review.md)
5. [Paper 5｜Need for Affect 與恐怖／戲劇觀影](./wiki/paper-5-need-for-affect-horror-drama.md)

五篇來源與檔案驗證資料記錄於 [`workflow/ingest-manifest.json`](./workflow/ingest-manifest.json)。

## 3. 教學 HTML 簡報（主要繳交成果）

依老師規定，本專案將五篇資料整合成**一份**教學型 HTML 簡報，主題是「為什麼人會享受恐怖？」。簡報依序介紹聲音設計、預測處理、恐怖片段數據、心理研究回顧與 Need for Affect，讓不熟悉主題的讀者能從基本概念一路理解研究證據。

- [開啟整合版教學 HTML 簡報](https://htmlpreview.github.io/?https://raw.githubusercontent.com/vitas9313-sketch/horror-fear-wiki/main/slides/horror-lab-teaching.html)
- [整合版 HTML 原始檔](./slides/horror-lab-teaching.html)

封面圖案為本專案自行繪製的 inline SVG，未使用外部圖片、電影海報、角色、商標或下載素材。

`slides/paper-1.html` 至 `slides/paper-5.html` 為先前製作的個別研究補充頁，不是本次作業的主要繳交成果。

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

Graph 的節點包含五篇來源、研究證據類型、研究概念、Wiki 條目、整合簡報大綱、逐頁內容、檔案驗證與投影片主張；邊表示支持、提出框架、轉換或通過檢查。完整 Graph 見 [`workflow/graph.json`](./workflow/graph.json)，可直接使用的 Graph 生成指令見 [`workflow/graph-generation-prompt.md`](./workflow/graph-generation-prompt.md)。

Loop 會重複執行來源驗證、引用回查與瀏覽器驗收。若 PDF 檢查失敗，退回來源驗證；若主張找不到引用，退回 Wiki 整理；若大綱不適合初學者，退回大綱設計；若 HTML 顯示錯誤，退回逐頁生成。

## 5. 實際執行結果與檢查紀錄

- 完成五篇資料的受控 ingest。
- 五個 PDF 均確認以 `%PDF-` 開頭，並完成頁數與 SHA-256 記錄。
- 五篇來源各自對應一篇 Wiki 條目。
- HTML 簡報已用瀏覽器開啟檢查，可正常閱讀，且不依賴外部圖片或腳本。
- 已執行 `git diff --check`；文字檔檢查通過，PDF 維持二進位檔保存。
- 檢查結果與來源雜湊記錄於 [`workflow/ingest-manifest.json`](./workflow/ingest-manifest.json)。

## 6. 反思與流程調整

本次執行中，最常出錯的節點有兩個：

### 6.1 資料下載後的檔案驗證

錯誤網址曾回傳 404 頁面或 Cloudflare HTML，而不是 PDF。如果直接把檔案交給後續整理，可能會把錯誤頁面誤當成研究資料，進而污染 Wiki 與簡報。

因此我把檢查前移到 ingest 之前，形成來源驗證 gate：先確認檔案標頭是 `%PDF-`、檔案大小合理，再確認頁數、計算 SHA-256，最後才允許資料進入研究整理。這樣可以在最早的節點攔截錯誤來源，避免錯誤一路傳到 Wiki 或投影片。

### 6.2 Wiki 內容過度摘要化

第二個問題出現在 Wiki 生成階段。原本的指令為了讓一般讀者容易理解，過度強調簡潔，結果部分條目只剩定義、摘要與結論，缺少研究案例、樣本／材料、分析方式、數據、限制，以及「這些證據究竟支持什麼」的說明。這會讓 Wiki 看起來像短摘要，而不是可供簡報查詢的知識庫。

因此我修改 Wiki 生成指令，移除「摘要式」生成要求，改成每篇條目必須完成以下結構：研究問題、核心概念、研究設計或理論流程、原文案例與關鍵數據、結果如何支持主張、限制與不可推論、與其他 Paper 的關聯，以及來源追溯。對於理論文章與回顧文章，也要明確標記它們不是同型的原始實驗數據。

我把這項檢查前移到「研究整理完成、建立簡報大綱之前」，新增 Wiki 深度與證據檢查節點。若條目缺少案例或數據，就退回研究整理重新生成；通過後才允許進入簡報大綱。這樣修改 workflow 的原因，是避免先用過度簡略的 Wiki 生成簡報，最後才發現簡報內容不足而必須整份重做。

經過調整後，Wiki 不只服務一般讀者，也能作為簡報的可追溯知識來源；AI 負責初步整理與改寫，人則檢查證據深度、研究類型、數據與限制。

---

GitHub Repository：[horror-fear-wiki](https://github.com/vitas9313-sketch/horror-fear-wiki)
