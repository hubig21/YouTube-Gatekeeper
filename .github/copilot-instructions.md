# Userscript (油猴腳本) 專案開發與維護規範

本檔案旨在引導 GitHub Copilot 理解本專案的架構、程式碼風格及 Issue 維護邏輯。

---

## 1. 專案類型與技術棧
- **專案類型**：瀏覽器使用者腳本 (Userscript / 油猴腳本)。
- **目標環境**：Tampermonkey / Violentmonkey / Greasyfork。
- **語言標準**：Modern JavaScript (ES6+)，確保免編譯或打包後即可直跑。

---

## 2. 油猴標頭區塊 (UserScript Header Block) 規範
- 任何新增的腳本或入口檔案，必須包含完整的 `// ==UserScript==` 宣告。
- **存取權限控管**：
  - 嚴格限制 `@grant` 權限，預設優先使用 `GM_getValue`, `GM_setValue`, `GM_xmlhttpRequest`, `GM_registerMenuCommand`。若無特別需求，盡量填寫 `@grant none`。
  - 使用 `@match` 替代廣泛的 `@include`，避免無謂觸發腳本。
- **加載時機**：
  - 預設優先使用 `@run-at document-idle`，避免阻塞頁面渲染。

---

## 3. DOM 操作與 MutationObserver 最佳實踐
- **動態元素監聽**：
  - 現代網頁（如 React/Vue 渲染）元素常有延遲或動態載入狀況，**切勿直接寫死 `setTimeout`**。
  - 請統一使用 `MutationObserver` 或安全封裝的 `waitForElement(selector)` 異步函式來等待 DOM 出現。
- **選擇器穩定性**：
  - 儘量避免使用易變動的動態 class（如 `css-1ynq2zp`），優先選擇 `data-*` 屬性、固定 `id` 或層級結構穩定的 CSS Selector。
- **DOM 節點清理**：
  - 在注入自訂 UI 時，確保清理舊有重複節點，避免記憶體洩漏 (Memory Leak)。

---

## 4. 效能與相容性要求
- **頁面影響**：
  - 避免在 `window.onscroll` 或高頻率 DOM 事件中直接執行密集運算，必須搭配 `debounce` 或 `throttle`。
- **網路請求**：
  - 若跨網域請求需使用 `GM_xmlhttpRequest`，請妥善處理跨域與 CORS 相關例外處理。

---

## 5. Issue 重構與維護邏輯
當進行 Issue 修復或程式碼維護時：
1. **分析網站 DOM 變動**：若 Issue 為「功能失效」，請優先檢查目標網站是否更新了 DOM 結構或 Selector。
2. **保持單一檔案可讀性**：若專案為單一 `.user.js` 發布，重構時需維持結構模組化（使用 Closure 或 IIFE 包裹），避免污染全域 `window` 命名空間。
3. **錯誤處理 (Error Handling)**：所有非同步操作與 DOM 尋找必須加上 try-catch 或 safe-guard，確保腳本崩潰時不影響原網站正常運作。
