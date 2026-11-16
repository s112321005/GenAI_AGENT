
# AGENTS.md — LLM Wiki

## 1. 專案目的

本專案是一個以大型語言模型（Large Language Models, LLM）為主題的研究知識庫，透過 AI Agent 協助整理、分類、連結與維護研究資料。

專案希望建立一個可以持續累積知識的 Markdown Wiki。當新增論文、技術文章或研究資料時，AI Agent 應閱讀來源內容，擷取重要資訊，並整合至既有知識頁面，逐步建立不同概念、模型、技術與研究成果之間的關聯。

本專案以研究資料整理與知識探索為主要用途，內容涵蓋：

- 大型語言模型基本原理
- Transformer 與相關模型架構
- Tokenization 與 Embedding
- LLM 預訓練與微調技術
- Retrieval-Augmented Generation（RAG）
- 模型評估與效能分析
- LLM 應用與相關研究

## 2. 核心架構

本專案採用三層式架構：

### 2.1 Raw Sources：原始資料層

存放尚未整理的原始研究資料，例如：

- 學術論文
- 技術文章
- 官方文件
- 研究報告
- 書籍與課程資料

此資料夾作為知識整理的原始依據。

**規則：**
- 不得修改或覆寫原始來源檔案。
- 新增資料時，應保留原始檔案及其來源資訊。
- 不可將 AI 推測的內容當成原始資料。
- 如果來源內容不完整，必須明確標示。

### 2.2 Wiki：知識整理層

存放由 AI Agent 維護的 Markdown 知識頁面。

依照主題分類，建立概念、模型、方法、研究來源及綜合分析頁面。

**規則：**
- 新增知識時，應先檢查是否已有相關頁面。
- 優先更新既有頁面，避免建立重複內容。
- 不同頁面之間應使用 Markdown 連結建立關聯。
- 重要論述應附上來源引用。
- 新資料與舊資料出現衝突時，應保留差異並標示來源，不可直接忽略。

### 2.3 Schema：規則設定層

本文件 `AGENTS.md` 負責定義整個 Wiki 的資料夾結構、內容格式、檔案命名及 AI Agent 的操作流程。

AI Agent 在新增、修改或整理任何知識頁面前，都必須遵守本文件規範。

---

## 3. 專案資料夾結構

```text
LLM-Wiki/
│
├── AGENTS.md
├── README.md
├── index.md
├── log.md
│
├── raw/
│   ├── inbox/
│   ├── papers/
│   ├── articles/
│   ├── books/
│   ├── reports/
│   └── assets/
│
├── wiki/
│   ├── overview.md
│   ├── concepts/
│   ├── models/
│   ├── methods/
│   ├── training/
│   ├── evaluation/
│   ├── applications/
│   ├── entities/
│   ├── sources/
│   ├── syntheses/
│   └── questions/
│
└── templates/
    ├── source-template.md
    ├── concept-template.md
    ├── synthesis-template.md
    └── question-template.md
```

### 資料夾用途

| 資料夾 | 用途 |
|---|---|
| raw/inbox | 暫存尚未整理的資料 |
| raw/papers | 學術論文 |
| raw/articles | 技術文章與網頁資料 |
| raw/books | 書籍與閱讀資料 |
| raw/reports | 研究報告 |
| raw/assets | 圖片及其他附件 |
| wiki/concepts | 核心技術與理論概念 |
| wiki/models | 模型架構與模型介紹 |
| wiki/methods | 技術方法與演算法 |
| wiki/training | 模型訓練相關知識 |
| wiki/evaluation | 模型評估與效能分析 |
| wiki/applications | 實際應用案例 |
| wiki/entities | 重要人物、機構與研究團隊 |
| wiki/sources | 原始資料摘要與來源紀錄 |
| wiki/syntheses | 跨來源綜合分析 |
| wiki/questions | 待研究問題與探索方向 |
| templates | 各類知識頁面的範本 |

---

## 4. 文件撰寫規範

### 4.1 語言與格式

- 主要使用繁體中文（台灣）。
- 專業術語第一次出現時，應保留英文原文。
- 使用 Markdown 格式撰寫。
- 適當使用標題、條列、表格及程式碼區塊。
- 內容應清楚、有層次，避免不必要的冗長描述。
- 涉及公式時，使用 LaTeX 格式。

### 4.2 檔案命名

- 檔案名稱使用英文或簡短的技術名稱。
- 使用小寫英文及連字號 `-` 分隔單字。
- 避免使用空格及特殊符號。
- 每個頁面應具有明確且唯一的檔案名稱。

範例：

```text
transformer.md
tokenization.md
retrieval-augmented-generation.md
fine-tuning.md
model-evaluation.md
```

### 4.3 頁面 Metadata

每個 Wiki 知識頁面都應在最前方加入 YAML Frontmatter。

範例：

```yaml
---
title: Transformer
type: concept
created: 2026-11-16
updated: 2026-11-16
tags:
  - LLM
  - Deep Learning
sources:
  - SRC-20261116-001
status: reviewed
---
```

欄位說明：

| 欄位 | 說明 |
|---|---|
| title | 頁面標題 |
| type | 頁面類型 |
| created | 建立日期 |
| updated | 最後更新日期 |
| tags | 主題標籤 |
| sources | 參考來源 ID |
| status | 文件整理狀態 |

頁面類型包含：

- concept：技術概念
- model：模型架構
- method：技術方法
- training：訓練技術
- evaluation：評估方法
- application：應用案例
- entity：人物、機構或研究團隊
- source：原始資料摘要
- synthesis：跨來源綜合分析
- question：待研究問題

---

## 5. 來源管理與引用規範

所有知識整理都必須盡可能追溯至原始來源。

### 5.1 來源 ID

每份來源資料應建立唯一 ID：

```text
SRC-YYYYMMDD-001
```

例如：

```text
SRC-20261116-001
SRC-20261116-002
```

### 5.2 來源資訊

來源摘要至少應記錄：

- 文件標題
- 作者或發布機構
- 發布日期
- 文件類型
- 原始網址或檔案位置
- 主要內容摘要
- 重要研究發現
- 相關 Wiki 頁面

### 5.3 引用原則

- 不得捏造作者、論文名稱、出版年份、DOI 或網址。
- 不確定的資訊應標記為「待確認」。
- 如果只能取得摘要，必須註明目前僅根據摘要整理。
- 需要區分原始來源的研究結果與 AI 的整理、推論。
- 不同來源有矛盾時，應分別記錄其主張及引用依據。
- 不得將推論描述成已經獲得研究證實的結論。

---

## 6. AI Agent 工作流程

AI Agent 主要負責三項工作：

1. Ingest：新增及整理資料。
2. Query：搜尋及回答研究問題。
3. Lint：檢查及維護知識庫。

### 6.1 Ingest：新增資料

當使用者提供新的論文、文章或研究資料時，依照以下步驟處理：

1. 閱讀原始資料，確認文件內容與主題。
2. 擷取研究目的、方法、技術及重要結論。
3. 建立來源摘要頁面，存放於 `wiki/sources/`。
4. 判斷是否需要新增概念、模型或方法頁面。
5. 更新相關既有知識頁面。
6. 建立不同知識頁面之間的交叉連結。
7. 更新 `index.md`。
8. 在 `log.md` 新增本次整理紀錄。

新增資料時，應優先檢查既有 Wiki，避免重複建立頁面。

### 6.2 Query：研究問題查詢

當使用者提出研究問題時：

1. 優先閱讀 `index.md`，了解目前知識庫的內容。
2. 找出與問題相關的知識頁面。
3. 閱讀相關頁面及其引用來源。
4. 整合不同來源的資訊。
5. 使用繁體中文回答，必要時保留英文專業術語。
6. 回答時標示參考頁面或來源。
7. 如果問題涉及尚未整理的知識，應明確指出資料不足。

如果查詢過程產生具有長期參考價值的分析，可詢問使用者是否要將內容整理成新的 Wiki 頁面。

### 6.3 Lint：知識庫檢查

定期檢查整體 Wiki 的品質：

- 是否存在內容重複的頁面。
- 是否有不同頁面出現互相矛盾的資訊。
- 是否有過時或需要更新的內容。
- 是否有缺少來源引用的研究主張。
- 是否有沒有被其他頁面連結的孤立頁面。
- 是否有重要概念被提及，卻尚未建立獨立頁面。
- 是否有缺少的交叉連結。
- 是否存在值得進一步研究的問題。

檢查完成後，提出改善建議。涉及實質內容修改時，應保留來源依據。

---

## 7. Index 與 Log 管理

### 7.1 index.md

`index.md` 是整個 Wiki 的內容索引。

每次新增或修改知識頁面後，都必須檢查是否需要同步更新。

索引依照主題分類，並提供：

- 頁面名稱
- 頁面連結
- 一句話摘要
- 所屬分類

範例：

```markdown
# LLM Wiki Index

## 核心概念
- [Transformer](wiki/concepts/transformer.md)：大型語言模型常見的核心架構。
- [Tokenization](wiki/concepts/tokenization.md)：將文字轉換為模型可處理的 Token。

## 模型架構
- [GPT](wiki/models/gpt.md)：Generative Pre-trained Transformer 模型系列。

## 技術方法
- [RAG](wiki/methods/retrieval-augmented-generation.md)：結合外部知識檢索的生成方法。
```

### 7.2 log.md

`log.md` 用來記錄知識庫的更新歷程。

採用時間順序排列，並且只能新增紀錄，不得任意刪除過去的紀錄。

格式：

```markdown
## [YYYY-MM-DD] ingest | 文件名稱

- 新增來源摘要：
- 更新知識頁面：
- 新增相關連結：

## [YYYY-MM-DD] query | 研究問題

- 查詢主題：
- 使用頁面：
- 研究結果：

## [YYYY-MM-DD] lint | 知識庫檢查

- 發現問題：
- 改善建議：
```

---

## 8. 知識頁面範本

一般概念頁面建議採用以下結構：

```markdown
---
title: 概念名稱
type: concept
created: YYYY-MM-DD
updated: YYYY-MM-DD
tags: []
sources: []
status: draft
---

# 概念名稱

## 1. 概念介紹

簡要說明此概念的定義與目的。

## 2. 核心原理

說明主要原理、運作方式及重要技術。

## 3. 技術流程

依照實際情況使用文字、條列或流程圖說明。

## 4. 優點與限制

整理此技術的優勢、限制及適用情境。

## 5. 相關概念

- [[相關概念 A]]
- [[相關概念 B]]

## 6. 參考來源

- [[來源摘要頁面]]
```

---

## 9. AI Agent 行為規則

AI Agent 在操作本專案時，必須遵守以下原則：

1. 修改文件前，先閱讀本文件及相關 Wiki 頁面。
2. 不得任意變更既有資料夾架構。
3. 不得修改 `raw/` 中的原始來源。
4. 新增頁面前，先搜尋是否已有相同主題。
5. 修改知識內容時，應同步更新 `updated` 日期。
6. 新增或修改知識頁面後，應檢查 `index.md` 是否需要更新。
7. 每次執行 Ingest、Query 或 Lint 工作後，應依照實際操作更新 `log.md`。
8. 不得虛構研究結果、來源資訊或引用。
9. 資料不足時，應明確說明限制，不可自行補造內容。
10. 避免為了增加頁面數量而建立缺乏實際價值的內容。
11. 保持頁面之間的連結一致，避免無效連結。
12. 重要內容應保留來源依據，讓使用者能夠追溯原始資料。

---

## 10. 專案發展方向

本專案採取循序漸進的方式擴充。

### 第一階段：建立基礎知識庫

- 建立資料夾架構。
- 整理 LLM 基本概念。
- 建立 Transformer、Tokenization 等核心知識頁面。
- 建立索引及更新紀錄。

### 第二階段：擴充研究內容

- 新增學術論文與技術文章。
- 整理模型訓練及微調方法。
- 建立不同技術之間的比較頁面。
- 強化跨頁面知識連結。

### 第三階段：提升知識管理能力

- 定期執行知識庫檢查。
- 整理研究問題及尚未解決的議題。
- 視資料規模導入本地搜尋工具。
- 使用 Obsidian 等工具檢視知識圖譜。

本專案初期以 Markdown 文件及索引管理為主，當知識庫規模增加、搜尋需求變複雜時，再考慮導入其他搜尋或檢索工具。

---

## 11. 最終原則

LLM Wiki 的核心目標是建立一個能夠持續累積、整理及連結知識的研究環境。

使用者負責選擇資料來源、提出研究問題及確認重要內容；AI Agent 負責閱讀資料、整理摘要、維護知識頁面、建立交叉連結及檢查知識庫。

所有知識都應具有可追溯性、結構一致性及持續更新的能力。
