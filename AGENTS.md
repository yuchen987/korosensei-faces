# AGENTS.md - 《暗殺教室》殺老師表情圖鑑開發規範

## 1. 專案目的
本專案為「《暗殺教室》殺老師（Koro-sensei）表情圖鑑」靜態網站，系統化收錄殺老師在不同情緒與情境下的臉部顏色變化、觸發條件與危險指數，方便日後持續擴充新表情卡片。

## 2. 網頁整體風格與配色系統
- **技術架構**：純 HTML5 + CSS3（無需框架，確保可直接部署於 GitHub Pages）。
- **視覺風格**：校園黑板與漫畫圖鑑風。頂部橫幅採用殺老師經典亮黃色（`#FACC15`）搭配深炭灰文字（`#1E293B`），頁面背景為淺灰白（`#F8FAFC`）。
- **卡片配色規則**：每張表情卡片的頂部色條（`border-top`）與情緒標籤背景色，**必須對應殺老師該表情的臉部主色**（透過 CSS 自訂屬性 `--face-color` 控制）。

## 3. 檔案結構與命名規則
- `index.html`：圖鑑主頁面，以響應式網格（Grid）展示所有表情卡片。
- `style.css`：全站統一樣式表，定義版面、卡片樣式與響應式斷點。
- `images/`：存放所有表情圖片，檔名一律採用 `兩位數編號-英文情緒關鍵字.png`（全小寫、不可有空白或中文字），例如 `01-normal.png`、`13-pout.png`。

## 4. 單張表情卡片 HTML 結構規範
每新增一個表情，必須在 `index.html` 的 `<main class="card-grid">` 區塊內，嚴格依照以下 HTML 模板新增 `<article>` 元素：

```html
<article class="face-card" style="--face-color: #色碼;">
  <div class="card-img-wrap">
    <img src="images/編號-檔名.png" alt="殺老師-表情名稱">
  </div>
  <div class="card-body">
    <div class="card-header">
      <span class="face-id">#編號</span>
      <span class="face-tag">代表情緒</span>
    </div>
    <h2>表情名稱（臉色特徵）</h2>
    <p class="trigger"><strong>觸發條件：</strong>說明什麼情況會出現此表情。</p>
    <p class="danger"><strong>危險指數：</strong>★☆☆☆☆（1 至 5 顆星）</p>
  </div>
</article>