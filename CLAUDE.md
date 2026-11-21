# FD AOI Monitor（畫檢 AOI 監控平台）— Claude 開場卡

> 這個資料夾開任何新對話都會自動讀到本檔。用繁體中文回覆 Johnny。
> ⚠ 本檔要放進公開 repo `JohnnyBabaYaga/FD-AOI-Monitor`：**不可寫權杖、內網 IP、客戶機密、人名清單**。
> 2026-10-27 依 `Claude工作規範.md`（在 Mac 的 `Johnny Agent/` 底下）整理；規範裡的通用規則這裡只摘重點。

## 這是什麼
- 部門追蹤各廠區畫檢 AOI 導入進度的單檔網頁：總覽、能力矩陣（產線 × 軟體版本能力）、產線面板（PDCA 關卡、光學調整）、主檔設定（軟體版本 → 技術能力 → 檢測項目）、導入指引
- 給部門同仁一起編輯；光學計算不自己做，連到 AOI Calculator（`AOI_CALC_URL`）算完填回
- 網站 `https://johnnybabayaga.github.io/FD-AOI-Monitor/`（repo：`index.html`、`auo-logo.png`、平台 icon `icons/`、`beta/` 轉址頁，加上 `CLAUDE.md`／`CONTEXT_MAP.md`／`notes/`）；資料在私有 repo `FD-AOI-Monitor-Data` 的 `aoi-monitor-data.json`
- 主要在公司電腦開發

## 開工讀這些
1. `CONTEXT_MAP.md`（還沒建就先建：一行一個現況＋路徑）
2. `notes/` 最新一份的頂端「現況／待辦／已定決策」
3. 要改哪裡再 grep `index.html` 找行號，只讀那段（檔案約 30 萬字元，不整份讀）

## 必守規則
- 動手前先 `git pull`，跟線上 `index.html` 比對（Mac 和公司電腦可能都改過）
- 只能用 FD AOI Monitor 自己的權杖，不借 AOI Calculator、Manager Platform 的；權杖不寫進任何檔案、不印出、不貼進對話
- **這裡說「平台」就是 FD AOI Monitor**；指令對象不明時預設是本專案，要動 AOI Calculator 或 Manager 看板先問
- 推上線前先問 Johnny（他說「改完直接推」才可以直接推）
- 改 UI 要瀏覽器實測 → 查 console → 截圖才回報；每個受影響的分頁都看過（總覽、能力矩陣、產線面板、主檔、導入指引、手機寬度）
- 多人同時編輯：逐筆三方合併、清單欄位逐項合併、標記刪除 90 天、停止編輯 3 秒上傳（最多 15 秒）——**改資料結構時這套不能壞**
- 改存檔格式要升 `SCHEMA` 並寫升級程式：只補缺少的欄位，先讀到雲端再升級
- 個人狀態（特別關注 ★）用「安靜存檔」：不改 updatedAt／updatedBy、不寫變更紀錄
- **CSS 不要再加 `/* ── vX.Y */` 補丁段落往下覆蓋**（目前已有約 20 段）：直接改原本的規則；有空時整理
- 新的計算定義（例：Pitch、完成度怎麼算）先寫「是什麼＋公式＋一個例子」給 Johnny 確認再寫程式

## 版本
- `APP_VER` 常數：**資料架構或使用方式整個改變才升大版號，升之前先問 Johnny**；一般功能升小版號，修正用第三碼（10/27 曾升到 v4.0、v4.1 又改號回 v3.10、v3.11）
- 大版代號用太空望遠鏡（v1 Hubble、v2 Chandra、v3 Spitzer；之後 Kepler、Gaia、TESS、Webb、Euclid、Roman），名字要對得上該版最大特點
- 每次發布在 `CHANGELOG` 最上面加一筆：給使用者看的 2～4 條白話，不寫實作細節；升大版時把 CHANGELOG 濃縮成一行一版搬進 `ERAS`
- 載入畫面、雲朵同步圖示、關於本平台、更新提示是跟 AOI Calculator 共用的元件（AOI 是正本）；改到時在回報裡提一句，問要不要同步

## 收尾
每段工作完成：結論寫進 `notes/YYYY-MM-DD_FD-主題.md`（頂端固定「現況／待辦／已定決策」），更新 `CONTEXT_MAP.md` 那一行，連同本檔一起 commit。
