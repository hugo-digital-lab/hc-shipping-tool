# 📦 宏勤生活科技 - 出貨明細轉單系統 (Hong Qin Order Conversion System)

**當前版本 (Version)**: v3.4.2  
**系統屬性**: 前端單頁應用程式 (SPA) / 無伺服器架構 (Serverless)  
**主要技術棧**: HTML5, Vanilla JavaScript, SheetJS (xlsx), html2pdf.js, Sortable.js  

---

## 📑 系統概述 (System Overview)
本系統專為宏勤生活科技（Hong Qin Life Technology）出貨部門打造，旨在解決各大電商平台或內部系統匯出之非結構化 Excel/CSV 訂單報表，將其標準化並批次轉換為適合列印與歸檔的 PDF 出貨明細單。系統採用 **100% 客戶端運算 (Client-Side Processing)**，無需依賴後端伺服器，確保企業營運資料的高效處理與絕對機密安全。

---

## ✨ 核心架構與功能特色 (Key Features)

### 1. 智慧資料解析與清洗 (Intelligent Data Parsing)
* **日期序列化修復**：內建自動轉換器，精準攔截並解析 Excel 底層的 1900 紀元日期序號 (Epoch time)，並自動格式化為標準的 `YYYY-MM-DD`，徹底解決匯出報表常見的日期亂碼問題。
* **動態欄位映射與留白機制 (Dynamic Data Mapping & Blanking)**：系統載入原始資料後會自動匹配核心欄位。針對不需要顯示的欄位（如無備註的訂單），新增了 **`[無]`** 的彈性選項，確保生成的 PDF 單據完美留白，避免強制輸出冗餘字元，提升單據視覺整潔度。

### 2. 進階狀態管理與覆蓋機制 (State Management & Override Logic)
* **單據全域客製化 (Full-Document Mutation)**：突破唯讀限制，提供單筆訂單的深度編輯面板。支援修改「出貨日期」、「備註」以及「陣列層級的商品明細 (SKU / 品名 / 數量)」。
* **編輯鎖定保護 (Edit-Lock Protection)**：當使用者對特定訂單進行手動修改後，系統會將變更寫入記憶體的快取字典中。再次渲染時會優先調用手動覆寫的資料，避免客製化內容被原 Excel 設定覆蓋。系統亦提供單筆「重設」與全域「清除修改」之防呆解鎖機制。

### 3. 動態客製化渲染 (Dynamic Component Rendering)
* **自訂延伸欄位 (Custom Extra Fields)**：支援無限擴充 PDF 表頭資訊。可指定讀取 Excel 中的特定欄位，或手動輸入常數值。
* **拖曳排序 (Drag-and-Drop Sortability)**：整合 Sortable.js，使用者可直覺拖曳 (⠿) 調整延伸欄位的渲染優先級與排列順序。

---

## 📖 標準操作流程 (SOP)

1. **資料載入**：將匯出的 `.xlsx` 或 `.csv` 報表拖曳至系統指定的 Dropzone 區域。
2. **參數配置**：檢視並確認「核心欄位對應」是否準確。若特定欄位不需顯示，請於下拉選單選擇 `[無]`；並可依需求新增「客製額外資訊」。
3. **編譯與預覽**：點擊 `[產出預覽]` 觸發虛擬 DOM 渲染，生成分頁預覽。
4. **單據微調 (選用)**：點擊左側 `[📝 修改此單內容]` 展開編輯面板，修改並儲存後，系統將自動鎖定該單據狀態。（*註：若因螢幕解析度較小導致左側面板被裁切，請按住 `Ctrl` + `滑鼠滾輪` 縮小網頁比例即可完整顯示。*）
5. **批次輸出**：確認無誤後，點擊 `[下載所有 PDF]`，系統將觸發引擎轉換為高解析度 A4 尺寸的 PDF 檔案。

---

## 👨‍💻 作者與版權聲明 (Author & Copyright)

* **Developer & Architect**: 黃兆聰 (Hugo) - 通路營運經理 (Manager of Channel Operations)
* **維護聲明**：本系統為本人於宏勤生活科技任職期間，為解決內部出貨流程痛點、提升營運效率而獨立開發之專案。
* **Portfolio Notice**：未來本人若自本公司離職，本專案將停止技術支援與功能更新，並將直接轉為個人職涯之軟體開發與流程優化作品集 (Portfolio) 展示用途。
